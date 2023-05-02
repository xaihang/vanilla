# VANILLA JS & DOM - You don't need that library

> "I want you to also love vanilla js" - Max

- core language and browser APIs to create web apps without any additonal libraries or frameworks added on top

why vanilla? aka is the BASE of the webcode / plain no other flavor

- always new framework that appears but stick to the core concept of vanilla JS you have advantages 

- 50-60 librarys; but in term of performance stick to the vanilla JS! It is always faster!

## why we need to care about vanilla js?
- add one more tool to your toolbox
- understand your library is doing
- extend your library with plugins
- be a better web dev
- mix with libraries
- vanilla js - is fast!
- use it! You can create simple and fast webapps with no CLI, no build process

## Main advantages of Vanilla JS
- lightweight
- control and power
- flexiablity
- performance
- no node-module

## fear of vanilla js
- lack of routing
- too verbose and time consuming
- state management ~ global 
- templating 
- complexity
- reusable components
- maintance
- learning curve
- browser compatibility
- scalability 
- reinventing the wheel everytime

> In this workshipm we will be using different tech and design patterns parallel

## DOM
- the dom connects web pages to js by representing the structure of a doc in memory

## DOM API
- a browser API exposed to dev to manipulate the DOM from an scripting language
- is avail on many objects
    * window global object
    * document object
    * one obj per html element and other nodes in your doc

```js
<html>
    <body>
        <header>
            <h1>the dom</h1>
            <p class="tagline"> document object model </p>
            <img hidden src="dom.pgn">
        </header>

    </body>
</html>
```
- each elem is repr by an obj of htmlele interface or other interface that inherits
- instance prop/methodss
- changes in prop or children will trigger updates in the user interface - when you release the thread
- listen to event happening in that elem annd react accordingly

## work with DOM element we can...,
- pick them from the current DOM
- create them and then inject them into the DOM

## when we have a reference to an elem we can
- read it
- remove it
- update the content
- create a new element and attach to html
- release the thread aka listening event, operation order
- web worker 

## select dele from the DOM
- by ID
- by class name
- by name (html attribute only on form)
- by css selector
- nav dom structure 

## when selecting elem some functions return
- one html elem (HTMLElement)
- a live html ele collection (HTMLCollection)
- static element collection (NodeList)

## func to get refer to ONE DOM elem
- getElementById
- querySelector - first elem matching the html
- when finding one elem it always check for null 

## func to get a ref to multi DOM elem:
- getElementsbyTagID
- querySelectorAll
- getElementsByClassName

### HTMLCollection by creating an Array from using it -> array.from(.....) to
```js
elements.filter(e=>e.tagName === "p");
```

## html elem in js you can:
- read/change attr to values
- read/change styles
- hook event listeners
- add/remove/move child ele
- read/change
- more api

## change styles of a DOM elem
- you can use dot syntax to access a style obj
- obj will have a map to every css property you can inline iin html
```js
element.style.color = "blue";
```

## listen to events ofn html ele
- you can use dot syntax and bind a func to an event name using 'addeventlistener'
```js
element.addEventListener('click', (event) => {
    // do something!
})
```

## accessing/editing contents of the elem:
- accessing textcontent
- working with DOM APIs to create/edit content
```js
const contents = element.innerHTML
```
- accessing innerhtml
- using DOM apis to create new nodes

## Event binding
- each DOM ele has a list of possible events we can listen to
- pointer and touch event
- basic: load, click, dbclick
- value: change
- scroll, focus, more apis
- keyboard events
- mouse events
- special events: popstate in window, DOMContentLoad 

## binding func to events in DOM obj
- onevent properties
- addEventListener
- onclick on the DOM with js is all lowered case

## advance event handling
- you can attach more than one event handler per event/obj combinattion
```js
function eventHandler(event) {
    // do something
}
const options = {
    once: true,
    passive: true
}
element.addEventListener("load", eventHandler, options);
element.removeEventListener("load", eventHandler); // remove is use only when inject or removing element that we donot use anymore 
```

## dispatching custom events
- reuse the same system for our own custom events and msg
```js
const event = new Event("mycustomname");
element.dispatchEvent(event); 
```
- can create our own class, interfaces 

## SPA (single page appliation) & Router
- how to change content? 
    * remove previous pg and inject new page into the DOM
    * hide previous page and show current page
- we want to change the content of the page based on what the user select:
    * Home page: menu
    * details of one particular product
    * order: cart details/order form
- use the DOM and APIs, web component, history API to push to new entries to the nav history
```js
//pushing a new url; the second argument is unused
history.pushState(optional_state, null, "/new-url");
//to listen for changes in url within the same page nav
window.addEvevntListener("popstate", event => {
    let url = location.href;
});
```
**Popstate won't be fired if the user clicks on external link or changes the url manually**

**when creating a SPA config your server properly and check theurl when tthe whole page loads for the first time.**

## Web Components
- make each page its own component 
- a modular, reusable building block for web dev that encapsulates a set of related functionality and user interface elements
- in short, your own custom html element
- compatible with every browser
- set of standards:
    * custom elements
    * html template
    * shadow DOM
    * declarative shadow dom (new) - safari user
- freedom of choice on how to define them and use them

### custom element 
we can define our own html tags using the customer elements api
**The html tag we define must contain a hyphen(-) to assure future compatiblity**
- we can define our own custom attributes using the data-* spec. 
- we can override some methods of th super class
- express as string - jsx won't be able to define value from html
- customer 
- dom challenge 
- attrbute changedcallback 
- slots = is the content that we can define as the component child with template we can have more than one slot
- customized builtins 
```js
<div is="my-element"> </div>
```

### template element 
fragments of markup that can be cloned  - browser ignored template before 
create a dom in memorie that can be rendered 
- we clone them aka template 
- `connectedcallback` method of the custom elem - clone it and then we use it
by default the node of our cust element are 

### shadow DOM 
a private, isolated DOM tree within a web component that is separated from the main documents DOM tree
- control over styling
- css declared in the main dom won't be applied to the shadow dom
- shadow dom can be opened or closed defining visibility from the outer dom
- html import
```js
class MyElement extends HTMLElement {
    constructor() {
        super();
        this.root = this.attachShadow({})
    }
}
```
### Where to define HTML for a custom Element
There are several alternatives:
 - use DOM APIs
 - Use a <template> in the main HTML
 - use an external HTML file loaded with fetch 
    * using innerHTML
    * using DOM

### Where to define CSS for a Custom Element
There are several alternatives:
 - use CSSOM APIs
 - add a <script> to a <template>
 - add a <link> in the <template>
 - use externaml CSS file loaded with fetch (it can be prefetched) and injected in the shadow DOM

## Reactive Programming with Proxies
A wrapper object that lets you intercept and modify operations performed on the wrapped object, allowing you to add custom behavior or validation to the object's properites and methods
```js
const original = {
    new: 'John Doe',
    age: 30
};

const s = new Proxy(original, handler);
console.log(s.age); // 30 years old

const handler = {
    get: function(target, prop) {
        if (property  === 'age') {
            return ....
        }
    }
}
```
**Proxies work with objects only!**

### Most used Proxy Traps aka Hooks
* get
* set
* has
* deleteProperty
* apply
* construct ....

## Wrapped-up
- vanilla js
- fetch 
- DOM API
- Design patterns
- SPA
- Web components
- Routing
- Reactive Programming 
