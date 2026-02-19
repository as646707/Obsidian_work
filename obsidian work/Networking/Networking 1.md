## The GET and POST Requests and the Use of CURL for It

**NEXT** --> [[Networking 2]] all about stateful and stateless check it out !!!

**GET** - a get request is an http request that is used to "get " something from a server and it is the most used service in a http server , you get something from www.google.com or sometthing or reddit something .

### How to Look at It?
![[Pasted image 20260219112036.png]]

look at an page in the browser and open inspect and go to the networks tab and there you can see all the requests that are being made or have been made in this place you can see as you change and the site how it works .

you can also make the get an post requests from the terminal itself but using the **curl** command from the terminal .

### CURL VS BROWSER
well the curl thing in the terminal is the linux tool and is only useful for only one time use and its inherently different from the browser but the following ways -

- when you do curl -X GET <address of something > you are asking the server to send you whatever is with that domain and what is returned is just a raw html that is all it has many links to other html files and images and other stuff , and the terminal doesnt bother to open it meaning it only gives you that raw html file that is it .
- when you look at the network tab on the browser you can see as all the other sub links are being opened that is the special feature of a browser it opens all that there in the send back html file .
- There are other methods to use for a better imagination of this process something like Postman and insomnia

**POST** - this is an important thing to understand in http models .

- in a post we send something to the server with the body of the request .
- the server sees the things that is send with the body and then decides what to do with the data . examples " posting a comment ", " licking a video " etc .
- then the server sends something in return meaning something like a **redirect** or a page ( html) so that the browser can open it .

### What is a Redirect?
a redirect is something that the server sends back its not a page rather its the address of another page that the browser goes to instantly without asking the user for his permission . you can see this when you send the post request and see that in the response the server sends a location in the html header .

### What is the HTML Headers and the HTML and What is the Difference Between the Two Things?
ans - consider a mail and the html header is the envelope and the html is the letter insider it so the html header tells the address of where the message has to go and the html is the thing that is insider it so that is the actuall code .

example of this --
```
curl -X POST "http://al-blackjack.herokuapp.com/new_player" \
  -d "player_name=Albert" -m 30 -v
```
if you send this you would get something like this --
 
![[Pasted image 20260219152742.png]]

The lines starting with > are the request headers your client sends.
The lines starting with < are the response headers from the server.
After a blank line, you’ll see the response body (the HTML).

i dont know why the color is yellow just ignore it alright ? now lets move on as you saw in this you send a message on the server with a message in it namely name= something and you can also have what the server send you back alright ?

* Host al-blackjack.herokuapp.com:80 was resolved.
 this means that the curl found the public ip throught the dns lookup and it sends conformation message of it namely this .
 
if you try to connect it to a non existing address you would get a dns error or a couldnot resolve error something like this --
```
avirals554@Avirals-MacBook-Air ~ % curl -X GET "https://fuckyouaviral.com" -m 30 -v
Note: Unnecessary use of -X or --request, GET is already inferred.
* Could not resolve host: fuckyouaviral.com
* Closing connection
curl: (6) Could not resolve host: fuckyouaviral.com
```


**wait so if i do the curl thing to a server and it sends me a redirect i wont be redirected cause its not a browser ?**

ans - yes the browser does the redirect not the curl this is the property of the browser not the terminal . the browser does 302 status ---> location redirect 

**what is the status ?** 
in the network tab on the inspect window in a browser there is also a column for the status it is basically the status that is send by the server about what happened with the request there are some of the common ones that goes something like -
200.    --  got the request and got it processed 
302    --- got the request and processed it and also send a redirect to the user 
404- the resources that were asked were not found at all 



Q when you send something like google.com and want to seach something like what is an apple , what kind of request is send meaning you are getting something but i have to post the thing that you have to get right ? so what is it ?

Ans- we send a get request that looks something like this -
curl "https://google.com/search?q=what+is+an+apple" 
this is a get request that asks the google search engine server about hey can you tell me about apples ?

