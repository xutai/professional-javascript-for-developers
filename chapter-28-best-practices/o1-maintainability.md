## maintainability

### anchors
- what-is-maintainable-code
- code-conventions
- loose-coupling
- programming-practices

### indexes
- what-is-maintainable-code
- code-conventions
    - readability
    - variable-and-function-naming
    - variable-type-transparency
- loose-coupling
    - decouple-html-or-javascript
    - decouple-css-or-javascript
    - decouple-application-logic-or-event-handler
- programming-practices
    - respect-object-ownership
    - avoid-globals
    - avoid-null-comparisons
    - use-constants

> p1037-1047

In early websites, JavaScript was used primarily for small effects or form validation. Today’s web applications are filled with thousands of lines of JavaScript executing all types of complicated processes. This evolution requires that developers take maintainability into account. As with software engineers in more traditional disciplines, JavaScript developers are hired to create value for their company, and they do that not just by delivering products on time but also by developing intellectual property that continues to add value long after.

Writing maintainable code is important because most developers spend a large amount of their time maintaining other people’s code. It’s a truly rare occurrence to be able to develop new code from scratch; it’s often the case that you must build on work that someone else has done. Making sure that your code is maintainable ensures that other developers can perform their jobs as well as possible.

### what-is-maintainable-code

Maintainable code has several characteristics. In general, code is said to be maintainable when it is all of the following:

**Understandable** —Someone else can pick up the code and figure out its purpose and general approach without a walk-through by the original developer.

**Intuitive** —Things in the code just seem to make sense, no matter how complex the operation.

**Adaptable** —The code is written in such a way that variation in data doesn’t require a complete rewrite.

**Extendable**—Care has been given in the code architecture to allow extension of the core functionality in the future.

**Debuggable** —When something goes wrong, the code gives you enough information to identify the issue as directly as possible.

Being able to write maintainable JavaScript code is an important skill for professionals. This is the difference between hobbyists who hack together a site over the weekend and professional developers who really know their craft.

### code-conventions

One of the simplest ways to start writing maintainable code is to come up with code conventions for the JavaScript that you write. Code conventions have been developed for most programming languages, and a quick Internet search is likely to turn up thousands of documents. Professional organizations have long instituted code conventions for developers in an attempt to make code more maintainable for everyone. The best-run open-source projects have strict code convention requirements that allow everyone in the community to easily understand how code is organized.

Code conventions are important for JavaScript because of the language’s adaptability. Unlike most object-oriented languages, JavaScript doesn’t force developers into defining everything as objects. The language can support any number of programming styles, from traditional object-oriented approaches to declarative approaches to functional approaches. A quick review of several opensource JavaScript libraries can easily yield multiple approaches to creating objects, defining methods, and managing the environment.

The following sections discuss the basics of how to develop code conventions. These topics are important to address, although the way in which they are addressed may differ, depending on your individual needs.


#### readability

For code to be maintainable, it must first be readable. Readability has to do with the way the code is formatted as a text file. A large part of readability has to do with the indentation of the code. When everyone is using the same indentation scheme, code across an entire project becomes much easier to read. Indentation is usually done by using a number of spaces instead of by using the tab character, which is typically displayed differently by different text editors. A good general indentation size is four spaces, although you may decide to use less or more.

Another part of readability is comments. In most programming languages, it’s an accepted practice to comment each method. Because of JavaScript’s ability to create functions at any point in the code, this is often overlooked. Because of this, it is perhaps even more important to document each function in JavaScript. Generally speaking, the places that should be commented in your code are as follows:

**Functions and methods**—Each function or method should include a comment that describes its purpose and possibly the algorithm being used to accomplish the task. It’s also important to state assumptions that are being made, what the arguments represent, and whether or not the function returns a value (since this is not discernible from a function definition).

**large sections of code** —Multiple lines of code that are all used to accomplish a single task should be preceded with a comment describing the task.

**Complex algorithms**—If you’re using a unique approach to solve a problem, explain how you are doing it as a comment. This will not only help others who are looking at your code but also help you the next time you look at it.

**Hacks**—Because of browser differences, JavaScript code typically contains some hacks. Don’t assume that someone else who is looking at the code will understand the browser issue that such a hack is working around. If you need to do something differently because one of the browsers can’t use the normal way, put that in a comment. It reduces the likelihood that someone will come along, see your hack, and “fix” it, inadvertently introducing the bug that you had already worked around.

> inadvertent adj. 疏忽的；不注意的（副词inadvertently）；无意中做的
Indentation and comments create more readable code that is easier to maintain in the future.

#### variable-and-function-naming

The proper naming of variables and functions in code is vital to making it understandable and maintainable. Because many JavaScript developers began as hobbyists, there’s a tendency to use nonsensical names such as "foo" and "bar" for variables and names such as "doSomething" for functions. A professional JavaScript developer must overcome these old habits to create maintainable code. General rules for naming are as follows:

- Variable names should be nouns, such as "car" or "person".
- Function names should begin with a verb, such as getName(). Functions that return Boolean values typically begin with is, as in isEnabled().
- Use logical names for both variables and functions, without worrying about the length. Length can be mitigated through postprocessing and compression (discussed later in this chapter).
- Variables, functions, and methods should begin with a lowercase letter and camelCase, such as getName() and isPerson. Classes like Person and RequestFactory should be capitalized. `Constant values should be all uppercase and underscores, such as REQUEST_TIMEOUT`.
- Be descriptive and sensible with names, but not too verbose. getName() intuitively will return a name value. PersonFactory will be producing some sort of Person object or entity.

> mitigate vt. 使缓和，使减轻

It’s imperative to avoid useless variable names that don’t indicate the type of data they contain. With proper naming, code reads like a narrative of what is happening, making it easier to understand.

#### variable-type-transparency

Because variables are loosely typed in JavaScript, it is easy to lose track of the type of data that a variable should contain. Proper naming mitigates this to some point, but it may not be enough in all cases. There are three ways to indicate the data type of a variable.

The first way is through initialization. When a variable is defined, it should be initialized to a value that indicates how it will be used in the future. For example, a variable that will hold a Boolean should be initialized to either true or false, and a variable to hold numbers should be initialized to a number, as in the following example:

```js
// variable type indicated by initialization
let found = false; // Boolean
let count = -1; // number
let name = ""; // string
let person = null; // object
```

Initialization to a particular data type is a good indication of a variable’s type. The downside of initialization is that it cannot be used with function arguments in the function declaration.

The second way to indicate a variable’s type is to use Hungarian notation. Hungarian notation prepends one or more characters to the beginning of a variable to indicate the data type. This notation is popular among scripted languages and was, for quite some time, the preferred format for JavaScript as well. The most traditional Hungarian notation format for JavaScript prepends a single character for the basic data types: "o" for objects, "s" for strings, "i" for integers, "f" for floats, and "b" for Booleans. Here’s an example:

```js
// Hungarian notation used to indicate data type
let bFound; // Boolean
let iCount; // integer
let sName; // string
let oPerson; // object
```

Hungarian notation for JavaScript is advantageous in that it can be used equally well for function arguments. The downside of Hungarian notation is that it makes code somewhat less readable, interrupting the intuitive, sentence-like nature of code that is accomplished without it. For this reason, Hungarian notation has started to fall out of favor among some developers.

The last way to indicate variable type is to use type comments. Type comments are placed right after the variable name but before any initialization. The idea is to place a comment indicating the data type right by the variable, as in this example:

```js
// type comments used to indicate type
let found /*:Boolean*/ = false;
let count /*:int*/ = 10;
let name /*:String*/ = "Nicholas";
let person /*:Object*/ = null;
```

Type comments maintain the overall readability of code while injecting type information at the same time. The downside of type comments is that you cannot comment out large blocks of code using multiline comments because the type comments are also multiline comments that will interfere, as this example demonstrates:

```js
// The following won't work correctly
/*
let found /*:Boolean*/ = false;
let count /*:int*/ = 10;
let name /*:String*/ = "Nicholas";
let person /*:Object*/ = null;
*/
```

Here, the intent was to comment out all of the variables using a multiline comment. The type comments interfere with this because the first instance of /* (second line) is matched with the first instance of */ (third line), which will cause a syntax error. If you want to comment out lines of code using type comments, it’s best to use single-line comments on each line (many editors will do this for you).

These are the three most common ways to indicate the data type of variables. Each has advantages and disadvantages for you to evaluate before deciding on one. The important thing is to decide which works best for your project and use it consistently.


### loose-coupling
Whenever parts of an application depend too closely on one another, the code becomes too tightly coupled and hard to maintain. The typical problem arises when objects refer directly to one another in such a way that a change to one always requires a change to the other. Tightly coupled software is difficult to maintain and invariably has to be rewritten frequently.

Because of the technologies involved, there are several ways in which web applications can become too tightly coupled. It’s important to be aware of this and to try to maintain loosely coupled code whenever possible.

#### decouple-html-or-javascript

One of the most common types of coupling is HTML/JavaScript coupling. On the web, HTML and JavaScript each represent a different layer of the solution: HTML is the data, and JavaScript is the behavior. Because they are intended to interact, there are a number of different ways to tie these two technologies together. Unfortunately, there are some ways that too tightly couple HTML and JavaScript.

JavaScript that appears inline in HTML, either using a `<script>` element with inline code or using HTML attributes to assign event handlers, is too tightly coupled. Consider the following code examples:

```html
<!-- tightly coupled HTML/JavaScript using <script> -->
<script>
document.write("Hello world!");
</script>
<!-- tightly coupled HTML/JavaScript using event handler attribute -->
<input type="button" value="Click Me" onclick="doSomething()"/>
```

Although these are both technically correct, in practice they tightly couple the HTML representing the data with the JavaScript that defines the behavior. Ideally, HTML and JavaScript should be completely separate, with the JavaScript being included via external files and attaching behavior using the DOM.

> portion n. 部分

When HTML and JavaScript are too tightly coupled, interpreting a JavaScript error means first determining whether the error occurred in the HTML portion of the solution or in a JavaScript file. It also introduces new types of errors related to the availability of code. In this example, the button may be clicked before the doSomething() function is available, causing a JavaScript error. Maintainability is affected because any change to the button’s behavior requires touching both the HTML and the JavaScript, when it should require only the latter.

HTML and JavaScript can also be too tightly coupled when the reverse is true: HTML is contained within JavaScript. This usually occurs when using innerHTML to insert a chunk of HTML text into the page, as in this example:

```js
// tight coupling of HTML to JavaScript
function insertMessage(msg) {
    let container = document.getElementById("container");
    container.innerHTML = `<div class="msg">
        <p> class="post">${msg}</p>
        <p><em>Latest message above.</em></p>
    </div>`;
}
```

Generally speaking, you should avoid creating large amounts of HTML in JavaScript. This, once again, has to do with keeping the layers separate and being able to easily identify the source of errors. When using this example code, a problem with page layout may be related to dynamically created HTML that is improperly formatted. However, locating the error may be difficult because you would typically first view the source of the page to look for the offending HTML but wouldn’t find it there because it’s dynamically generated. Changes to the data or layout would also require changes to the JavaScript, which indicates that the two layers are too tightly coupled.

HTML rendering should be kept separate from JavaScript as much as possible. When JavaScript is used to insert data, it should do so without inserting markup whenever possible. `Markup can typically be included and hidden when the entire page is rendered such that JavaScript can be used to display the markup later, instead of generating it. Another approach is to make an Ajax request to retrieve additional HTML to be displayed; this approach allows the same rendering layer (PHP, JSP, Ruby, and so on) to output the markup, instead of embedding it in JavaScript.`

Decoupling HTML and JavaScript can save time during debugging by making it easier to identify the source of errors, and it also eases maintainability: changes to behavior occur only in JavaScript files, whereas changes to markup occur only in rendering files.

#### decouple-css-or-javascript

Another layer of the web tier is CSS, which is primarily responsible for the display of a page. JavaScript and CSS are closely related: they are both layers on top of HTML and as such are often used together. As with HTML and JavaScript, however, it’s possible for CSS and JavaScript to be too tightly coupled. The most common example of tight coupling is using JavaScript to change individual styles, as shown here:

```js
// tight coupling of CSS to JavaScript
element.style.color = "red";
element.style.backgroundColor = "blue";
```

Because CSS is responsible for the display of a page, any trouble with the display should be addressable by looking just at CSS files. However, when JavaScript is used to change individual styles, such as color, it adds a second location that must be checked and possibly changed. The result is that JavaScript is somewhat responsible for the display of the page and a tight coupling with CSS. If the styles need to change in the future, both the CSS and the JavaScript files may require changes. This creates a maintenance nightmare for developers. A cleaner separation between the layers is needed.

Modern web applications use JavaScript to change styles frequently, so although it’s not possible to completely decouple CSS and JavaScript, the coupling can be made looser. This is done by dynamically changing classes instead of individual styles, as in the following example:

```js
// loose coupling of CSS to JavaScript
element.className = "edit";
```

By changing only the CSS class of an element, you allow most of the style information to remain strictly in the CSS. JavaScript can be used to change the class, but it’s not directly affecting the style of the element. As long as the correct class is applied, then any display issues can be tracked directly to CSS and not to JavaScript.

Once again, the importance of keeping a good separation of layers is paramount. The only source for display issues should be CSS, and the only source for behavior issues should be JavaScript. Keeping a loose coupling between these layers makes your entire application more maintainable.

> paramount adj. 最重要的，主要的；至高无上的

#### decouple-application-logic-or-event-handler

Every web application is typically filled with lots of event handlers listening for numerous different events. Few of them, however, take care to separate application logic from event handlers. Consider the following example:

```js
function handleKeyPress(event) {
    if (event.keyCode == 13) {
        let target = event.target;
        let value = 5 * parseInt(target.value);
        if (value > 10) {
            document.getElementById("error-msg").style.display = "block";
        }
    }
}
```

This event handler contains application logic in addition to handling the event. The problem with this approach is twofold. First, there is no way to cause the application logic to occur other than through the event, which makes it difficult to debug. What if the anticipated result didn’t occur? Does that mean that the event handler wasn’t called or that the application logic failed? Second, if a subsequent event causes the same application logic to occur, you’ll need to duplicate the functionality or else extract it into a separate function. Either way, it requires more changes to be made than are really necessary.

> in addition to 除...之外（还有，也）

> twofold adj. 有两部分的，双重的；两倍的

> other than 除了；不同于

A better approach is to separate the application logic from event handlers, so that each handles just what it’s supposed to. An event handler should interrogate the event object for relevant information and then pass that information to some method that handles the application logic. For example, the previous code can be rewritten like this:

```js
function validateValue(value) {
    value = 5 * parseInt(value);
    if (value > 10) {
        document.getElementById("error-msg").style.display = "block";
    }
}
function handleKeyPress(event) {
    if (event.keyCode == 13) {
        let target = event.target;
        validateValue(target.value);
    }
}
```

This updated code properly separates the application logic from the event handler. The handleKey- Press() function checks to be sure that the Enter key was pressed (event.keyCode is 13) and then gets the target of the event and passes the value property into the validateValue() function, which contains the application logic. Note that there is nothing in validateValue() that depends on any event handler logic whatsoever; it just receives a value and can do everything else based on that value.

Separating application logic from event handlers has several benefits. First, it allows you to easily change the events that trigger certain processes with a minimal amount of effort. If a mouse click initially caused the processing to occur, but now a key press should do the same, it’s quite easy to make that change. Second, you can test code without attaching events, making it easier to create unit tests or to automate application flow.

Here are a few rules to keep in mind for loose coupling of application and business logic:

- Don’t pass the event object into other methods; pass only the data from the event object that you need.
- Every action that is possible in the application should be possible without executing an event handler.
- Event handlers should process the event and then hand off processing to application logic.

> hand off 不可触摸；切换，转换

Keeping this approach in mind is a huge maintainability win in any code base, opening up numerous possibilities for testing and further development.

### programming-practices

Writing maintainable JavaScript isn’t just about how the code is formatted; it’s also about what the code does. Web applications created in an enterprise environment are often worked on by numerous people at the same time. The goal in these situations is to ensure that the browser environment in which everyone is working has constant and unchanging rules. To achieve this, developers should adhere to certain programming practices.

#### respect-object-ownership

The dynamic nature of JavaScript means that almost anything can be modified at any point in time. It’s been said that nothing in JavaScript is sacred, as you’re unable to mark something as final or constant. This changed somewhat with ECMAScript 5’s introduction of tamper-proof objects, but by default, all objects can be modified. In other languages, objects and classes are immutable when you don’t have the actual source code. JavaScript allows you to modify any object at any time, making it possible to override default behaviors in unanticipated ways. Because the language doesn’t impose limits, it’s important and necessary for developers to do so.

> tamper v. 做手脚，破坏 n. 夯工，拍压的人；打夯机

> proof adj. 防…的；不能透入的；证明用的；耐…的

> tamper-proof adj. 防干扰的 防篡改

Perhaps the most important programming practice in an enterprise environment is to respect object ownership, which means that you don’t modify objects that don’t belong to you. Put simply: if you’re not responsible for the creation or maintenance of an object, its constructor, or its methods, you shouldn’t be making changes to it. More specifically:

- Don’t add properties to instances or prototypes.
- Don’t add methods to instances or prototypes.
- Don’t redefine existing methods.

The problem is that developers assume that the browser environment works in a certain way. Changes to objects that are used by multiple people mean that errors will occur. If someone expects a function called stopEvent() to cancel the default behavior for an event, and you change it so it does that and also attaches other event handlers, it is certain that problems will follow. Other developers are assuming that the function just does what it did originally, so their usage will be incorrect and possibly harmful because they don’t know the side effects.

These rules apply not only to custom types and objects but also to native types and objects such as Object, String, document, window, and so on. The potential issues here are even more perilous because browser vendors may change these objects in unannounced and unanticipated ways.

> perilous adj. 危险的，冒险的

An example of this occurred in the popular Prototype JavaScript library, which implemented the getElementsByClassName() method on the document object, returning an instance of Array that had also been augmented to include a method called each(). John Resig outlined on his blog the sequence of events that caused the issue. In his post (http://ejohn.org/blog/getelementsbyclassname- pre-prototype-16/), he noted that the problem occurred when browsers began to natively implement getElementsByClassName(), which returns not an Array but rather a NodeList that doesn’t have an each() method. Developers using the Prototype library had gotten used to writing code such as this:

```js
document.getElementsByClassName("selected").each(Element.hide);
```

Although this code worked fine in browsers that didn’t implement getElementsByClassName() natively, it caused an error in the ones that did, as a result of the return value differences. You cannot anticipate how browser vendors will change native objects in the future, so modifying them in any way can lead to issues down the road when your implementation clashes with theirs.

The best approach, therefore, is to never modify objects you don’t own. You own an object only when you created it yourself, such as a custom type or object literal. You don’t own Array, document, and so on, because they were there before your code executed. You can still create new functionality for objects by doing the following:

- Create a new object with the functionality you need, and let it interact with the object of interest.
- Create a custom type that inherits from the type you want to modify. You can then modify the custom type with the additional functionality.

Many JavaScript libraries now subscribe to this theory of development, allowing them to grow and adapt even as browsers continually change.

#### avoid-globals

Closely related to respecting object ownership is avoiding global variables and functions whenever possible. Once again, this has to do with creating a consistent and maintainable environment in which scripts will be executed. At most, a single global variable should be created on which other objects and functions exist. Consider the following:

```js
// two globals - AVOID!!!
var name = "Nicholas";
function sayName() {
    console.log(name);
}
```

This code contains two globals: the variable name and the function sayName(). These can easily be created on an object that contains both, as in this example:

```js
// one global - preferred
var MyApplication = {
    name: "Nicholas",
    sayName: function() {
        console.log(this.name);
    }
};
```

This rewritten version of the code introduces a single global object, MyApplication, onto which both name and sayName() are attached. Doing so clears up a couple of issues that existed in the previous code. First, the variable name overwrites the window.name property, which possibly interferes with other functionality. Second, it helps to clear up confusion over where the functionality lives. Calling MyApplication.sayName() is a logical hint that any issues with the code can be identified by looking at the code in which MyApplication is defined.

An extension of the single global approach is the concept of namespacing. Namespacing involves creating an object to hold functionality. The Google Closure library utilizes namespaces to organize its contents. Here are some examples:

- goog.string—Methods for manipulating strings.
- goog.html.utils—Methods for working with HTML.
- goog.i18n—Methods for helping with internationalization (i18n).

The single global object goog serves as a container onto which other objects are defined. Whenever objects are used simply to group together functionality in this manner, they are called namespaces. The entire Google Closure library is built on this concept, allowing it to coexist on the same page with any other JavaScript library.

The important part of namespacing is to decide on a global object name that everyone agrees to use and that is unique enough that others aren’t likely to use it as well. In most cases, this can be the name of the company for which you’re developing the code, such as goog or Wrox. You can then start creating namespaces to group your functionality, as in this example:

```js
// create global object
var Wrox = {};
// create namespace for Professional JavaScript
Wrox.ProJS = {};
// attach other objects used in the book
Wrox.ProJS.EventUtil = { ... };
Wrox.ProJS.CookieUtil = { ... };
```

In this example, Wrox is the global on which namespaces are created. If all code for this book is placed under the Wrox.ProJS namespace, it leaves other authors to add their code onto the Wrox object as well. As long as everyone follows this pattern, there’s no reason to be worried that someone else will also write an object called EventUtil or CookieUtil because it will exist on a different namespace. Consider this example:

```js
// create namespace for Professional Ajax
Wrox.ProAjax = {};
// attach other objects
Wrox.ProAjax.EventUtil = { ... };
Wrox.ProAjax.CookieUtil = { ... };
// you can still access the ProJS one
Wrox.ProJS.EventUtil.addHandler( ... );
// and the ProAjax one separately
Wrox.ProAjax.EventUtil.addHandler( ... );
```

Although namespacing requires a little more code, it is worth the trade-off for maintainability purposes. Namespacing helps ensure that your code can work on a page with other code in a nonharmful way.


#### avoid-null-comparisons

Because JavaScript doesn’t do any automatic type checking, it becomes the developer’s responsibility. As a result, very little type checking actually gets done in JavaScript code. The most common type check is to see if a value is null. Unfortunately, checking a value against null is overused and frequently leads to errors due to insufficient type checking. Consider the following:

```js
function sortArray(values) {
    if (values != null) { // AVOID!!
        values.sort(comparator);
    }
}
```

The purpose of this function is to sort an array with a given comparator. The values argument must be an array for the function to execute correctly, but the if statement simply checks to see that values isn’t null. There are several values that can make it past the if statement, including any string or any number, which would then cause the function to throw an error.

Realistically, null comparisons are rarely good enough to be used. Values should be checked for what they are expected to be, not for what they aren’t expected to be. For example, in the previous code, the values argument is expected to be an array, so you should be checking to see if it is an array, rather than checking to see if it’s not null. The function can be rewritten more appropriately as follows:

```js
function sortArray(values) {
    if (values instanceof Array) { // preferred
       values.sort(comparator);
    }
}
```

This version of the function protects against all invalid values and doesn’t need to use null at all.

If you see a null comparison in code, try replacing it using one of the following techniques:

- If the value should be a reference type, use the instanceof operator to check its constructor.
- If the value should be a primitive type, use the typeof operator to check its type.
- `If you’re expecting an object with a specific method name, use the typeof operator to ensure that a method with the given name exists on the object.`

The fewer null comparisons in code, the easier it is to determine the purpose of the code and to eliminate unnecessary errors.

#### use-constants

The goal of relying on constants is to isolate data from application logic in such a way that it can be changed without risking the introduction of errors. Strings that are displayed in the user interface should always be extracted in such a way as to allow for internationalization. URLs should also be extracted because they have a tendency to change as an application grows. Basically, each of these has a possibility of changing for one reason or another, and a change would mean going into the function and changing code there. Any time you’re changing application logic code, you open up the possibility of creating errors. You can insulate application logic from data changes by extracting data into constants that are defined separately.

> insulate vt. 隔离，使孤立；使绝缘，使隔热

The key is to separate data from the logic that uses it. The types of values to look for are as follows:

- **Repeated values** —Any values that are used in more than one place should be extracted into a constant. This limits the chance of errors when one value is changed but others are not. This includes CSS class names.
- **User interface strings** —Any strings that are to be displayed to the user should be extracted for easier internationalization.
- **URLs** —Resource locations tend to change frequently in web applications, so having a common place to store all URLs is recommended.
- **Any value that may change** —Any time you’re using a literal value in code, ask yourself if this value might change in the future. If the answer is yes, then the value should be extracted into a constant.

Using constants is an important technique for enterprise JavaScript development because it makes code more maintainable and keeps it safe from data changes.