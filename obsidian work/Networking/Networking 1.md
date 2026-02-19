the Get and post requests and the use of curl for it -

**GET** - a get request is an http request that is used to "get " something from a server and it is the most used service in a http server , you get something from www.google.com or sometthing or reddit something .

how to look at it ? 
![[Pasted image 20260219112036.png]]
look at an page in the browser and open inspect and go to the networks tab and there you can see all the requests that are being made or have been made in this place you can see as you change and the site how it works .
you can also make the get an post requests from the terminal itself but using the **curl** command from the terminal . 
**CURL VS BROWSER**
well the curl thing in the terminal is the linux tool and is only useful for only one time use and its inherently different from the browser but the following ways -
- when you do curl -X GET <address of something > you are asking the server to send you whatever is with that domain and what is returned is just a raw html that is all it has many links to other html files and images and other stuff , and the terminal doesnt bother to open it meaning it only gives you that raw html file that is it .
-  when you look at the network tab on the browser you can see as all the other sub links are being opened that is the special feature of a browser it opens all that there in the send back html file .
- There are other methods to use for a better imagination of this process something like Postman and insomnia 
**POST** -  this is an important thing to understand in http models .
- in a post we send something to the server with the body of the request .
- the server sees the things that is send with the body and then decides what to do with the data . examples " posting a comment ", " licking a video " etc .
- then the server sends something in return meaning something like a **redirect** or a page  ( html) so that the browser can open it .
## - what is a redirect ? a redirect is something that the server sends back its not a page rather its the address of another page that the browser goes to instantly without asking the user for his permission . you can see this when you send the post request and see that in the response the server sends a location in the html header .

# what is the html headers and the html and what is the difference between the two things ?

ans - consider a mail and the html header is the envelope and the html is the letter insider it so the html header tells the address of where the message has to go and the html is the thing that is insider it so that is the actuall code .

example of this -- 

`curl -X POST "http://al-blackjack.herokuapp.com/new_player" \`
  `-d "player_name=Albert" -m 30 -v`