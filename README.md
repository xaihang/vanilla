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

## instance methods 




