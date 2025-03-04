# HTML
## 外部资源的加载
1. 外部资源的加载有两种方式，一种是通过`<link>`标签引入外部CSS文件，另一种是通过`<script>`标签引入外部JS文件。
2. 通过`<link>`标签引入外部CSS文件，需要用herf属性指定文件路径
   ```html
   <link rel="stylesheet" type="text/css" href="style.css">
3. 通过`<script>`标签引入外部JS文件,需要用src属性指定文件路径
   ```html
    <script type="text/javascript" src="script.js"></script>
    ```
## Thymeleaf
### 常用标签
|标签|作用|说明|
|-|-|-|
|th:id|替换id|`<input th:id="${user.id}"/>`|
|th:text|文本替换|`<p text:="${user.name}">bigsai</p>`|
|th:utext|支持html的文本替换|`<p utext:="${htmlcontent}">content</p>`|
|th:object|替换对象|`<div th:object="${user}"></div>`|
|th:value|替换值|`<input th:value="${user.name}">`|
|th:each|迭代|`<tr th:each="student:${user}" >`|
|th:href|替换超链接|`<a th:href="@{index.html}">超链接</a>`|
|th:src|替换资源|`<script type="text/javascript" th:src="@{index.js}"></script>`|
### ${} 变量表达式
1. 在 Thymeleaf 中，`${}` 是一种表达式语法，用于从模型数据（Model）中获取值。这些值通常是由后端（如 Spring MVC 的控制器）传递到前端模板的数据。简单来说，${} 指向的是服务器端提供的数据对象或变量，这些数据通常存储在模型（Model）、请求属性（Request Attributes）、会话（Session）或应用程序上下文（ServletContext）中。
2. 指向
   - 模型数据（Model）：在 Spring MVC 中，控制器通常通过 Model 对象或 @ModelAttribute 将数据传递给视图。
   - 例如
       ```java
       @GetMapping("/example")
       public String showExample(Model model) {
           model.addAttribute("username", "Alice");
           model.addAttribute("age", 25);
           return "example"; // 对应 templates/example.html
       }
       ```
     在前端使用${}进行访问
     ```html
     <span>username:${username}</span>
     <span>age:${age}</span>
     ```

### @{} 链接表达式
1. 在Thymeleaf 中，如果想引入链接比如link，href，src，需要使用`@{资源地址}`引入资源。其中资源地址可以static目录下的静态资源，也可以是互联网中的绝对资源。
2. 例如
   ```html
   <link rel="stylesheet" th:href="@{/css/style.css}" />
   <script th:src="@{/js/script.js}"></script>
   <img th:src="@{/images/logo.png}" />
   ```

### #{} 消息表达式
1. 在Thymeleaf 中，`#{}` 是一种消息表达式语法，用于从国际化资源文件中获取消息。这些消息通常用于国际化（i18n）和本地化（l10n）。
2. 例如
   ```html
   <span th:text="#{welcome.message}">Welcome</span>
   ```
   在国际化资源文件中定义
   ```properties
   welcome.message=Welcome to our website!
   ```
    当前语言为英文时，显示`Welcome to our website!`，当切换到其他语言时，显示对应的翻译。

### ~{} 片段表达式
1. 在Thymeleaf 中，`~{}` 是一种片段表达式语法，用于引入片段模板。片段模板通常是一个 HTML 片段，可以在多个页面中重复使用。
2. 例如
   ```html
   <div th:replace="~{fragments/header :: header}"></div>
   ```
   在`fragments/header.html`中定义
   ```html
   <header>
       <h1>Header</h1>
   </header>
   ```
