# Lab Report 2
## ChatServer.java Code
![Image](ChatServer.png)

## Server.java Code
![Image](ServerFinal.png)

# Using /add-message
![Image](AddMessage1.png)

The method `handleRequest(URI url)` is called by the main method. The argument provided to this method is `URI url` the URL entered into their browser, which in this case is `http://localhost:4001/add-message?s=Hi&user=aryaman`. In the overarching Handler class, the field `String chatHistory` initially establishes the chat history to be displayed later as an empty string, since no user or message has been identified at this point. Next, within the `handleRequest(URI url)` method, the fields `String user` and `String message` are initialized to empty strings, then later updated with the name of the user and their chat message respectively determined from the url path. Then, `String userQuery` represents the user's custom query after the "?" in the url. Using `userQuery`, `int messageIndex`, `int userIndex`, and `int andIndex` are updated with the index positions of "s=", "user=", and "&" in order to splice the corresponding substrings of `userQuery` after "s=" indicating the message and "user=" indicating the user's name to be assigned to `message` and `user`, which are lastly concatenated and appended to the currently empty `chatHistory` to display "aryaman: Hi" on the webpage after `chatHistory` is returned.

![Image](AddMessage2.png)

------

`http://localhost:4001/add-message?s=What%27s%20up&user=joe`
