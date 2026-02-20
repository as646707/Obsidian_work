``` javascript 
<div class="title" > come forth the world!!</div> ;

```

this is a simple html tag now answer the following questions 
1. what is the title for ? 
ans . to connect this specific element to css and java script 
2. how do you connect it with js and css ?
  ans . well the css one goes something like this --
  
  .title {
  color:red ;
  width:90px;
  height:180px;
  }

what is DOM?
 well dom is just a hirarchial structure used by the web browser to open the html file it works something like a tree to load up all the elements of the html page .
 it works like `<body><div>...</div></body>`  - here one element is inside the other element and you are making a tree just to remeber where everthing is that is it .
 
what is the problem with it ? 
well the problem is that what happens once you change it will you reload the page over and over ? no the answer is no we wont do that for that we use react what react doest it just changes that part of the dom tree such that the file was always like that and not changed at all .

HTML file loads once
      ↓
Browser builds DOM
      ↓
User interacts / data changes
      ↓
Something has to update the DOM to reflect the change
      ↓
Browser repaints the screen

here are some of the code that i know you dont know but you should know about -

## What is `document.getElementById`?

Remember how the DOM is a tree of elements the browser builds from your HTML? Well, `document` is simply **JavaScript's reference to that entire DOM tree**. It's an object that JavaScript automatically has access to in the browser, representing the whole page.

So when you write `document` you're basically saying "hey, the entire page."

And `.getElementById` is just a way to **search through that tree and grab one specific element** by its ID.

1. `document.getElementById('like-count')` // finds that exact h1 and grabs it
2. this line document is the refering to the entire DOM tree file its used by JS to find elements from that tree with titles .
3. the title get used for this exact same reasons 
4. here are some of the examples that i have found for you to remeber in the future .
5.      `let element = document.getElementById('like-count')`
`element.innerText = 10        // change its text`
`element.style.color = 'red'   // change its color`
`element.remove()              // delete it from the page entirely`
this just shows you how the things are connected in real working enviroment .

**You're literally reaching into the live DOM and manipulating it with JavaScript. This is what "DOM manipulation" means.**

Summary 1-  A browser knows the stucture of the html and that is how it loads the page through this structure and that is structure is called the DOM file . because the dom file is directly connected to the loading of the html page whenever you change something in the html file the dom will change right ? so to counter that react has something very useful instead of changing the whole html react stuctures it in comonents and these components can be changed when we want so when we interact with these it literally changes that part of the DOM and that is it nothing more and nothing less this is how react maintain is seemless updating capabilities . 
react actually have a virtual dom too and the updates are made in the virtual dom rather than the real ones ,
**analogy to understand how the react works**  - the react virtual and the real dom works kind of like a git server just like how when you change a file the git local server maps out the changes made and then pushes it to the server on the github repo the same way the react works with the virtual and the real DOM it registers the changes and then pushes them onto the real one automatically .


**Fast refresh ( hot reloading ) vs react virtual DOM diffing**
- remember that the react virtual DOM diffing is not the same thing to when you see on the webpage when using the next js or expo and chnaging the webpages as you save they are simmilar but not the same thing at all .
- You save a file
      ↓
The dev server detects which file changed
      ↓
It only re-sends that specific module to the browser
      ↓
The browser swaps out just that piece without full reload