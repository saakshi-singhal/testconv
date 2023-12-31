# Creating a React Chatting app

Create a chatting app and chat with your friends and family
React Hooks are also used in this app

### Prerequistes:
1. Basic knowledge of React JS
2. IDE: Visual Studio Code


### Steps:

- To create a new app: npx create-react-app ./
this will create a react app in the same directory
- If this gives error like : You are running `create-react-app` 4.0.3, which is behind the latest release (5.0.0) or clear cache

- We no longer support global installation of Create React App.

- Please remove any global installs with one of the following commands:
- npm uninstall -g create-react-app
- yarn global remove create-react-app

The latest instructions for creating a new app can be found here:
https://create-react-app.dev/docs/getting-started/

To overcome this: npx create-react-app@5.0.0 ./




- npm install @ant-design/icons axios react-chat-engine
- ant-design:   React UI library antd that contains a set of high quality components and demos for building rich, interactive user interfaces.

#### Features
🌈 Enterprise-class UI designed for web applications.

📦 A set of high-quality React components out of the box.

🛡 Written in TypeScript with predictable static types.

⚙️ Whole package of design resources and development tools.

🌍 Internationalization support for dozens of languages.

🎨 Powerful theme customization in every detail.

- react-chat-engine: free chat API






- After installing all dependencies, inside App.js, import ChatEngine and App.css



- In App.js: return ChatEngine with some props like height, userID, userSecret(password)
- Go to ChatEngine.io : create a new project, there we get userID, password etc. paste them in App.js 
i.e. embed chat engine in app and add users on CreateEngine.io and all have same passwords to access our grp react community
make admin 

- npm start


- To have our own styles for chat room, use ChatFeed to change the styling of center of our chat room
- we now need my msgs file and a their msgs file 
- can read docs in ChatEngine.io to find out functions like renderChatFee etc.


ChatFeed.jsx:
* Now we have username, msgs, chats,activateChat as props
* Make a chat variable that searches for those chats that exist and are activeChat
* find keys of msgs and find key of last msg
* now check whether its my msg or not
* if my msg: call the mymsg component otherwise call their msg component and also set differnt styles for mymsg and theirmsg
* now if no chat then print loading otherwise, in the chat feed section, display chat title and map through each person and display their names
* call rendermsgs
* now we can make a msg form 
* now add props to mysmg and theirmsg


Mymsgs.jsx:
* take props as argument and check if the msg has img or text

Their_msgs.jsx:
* there are 2 props(message,lastMessage)
* chk whether it is firstmsg by that user, if yes then background will be that person's avatar
* for other msgs, do same as Mymsgs(check it is img or text) and change the css

MessageForm.jsx:
* Make a form in which user can input anything
* on submitting the form, if text lenght>0: sendMessage with credentials,chatid and text
* on change, update that with recent value
* to set value, we use useState hook
* setValue(''): whenver we send any msg, after sending also, that msg persists in our send to msg form, to clear that, use this
* sendMessage and isTyping is there in react-chat-engine
* now we want icons to send and upload: import from ant-design/icons and insert in label tag
* now input files(i.e. browse file) and call handleUpload
* create a button icon for sending msg

ChatFeed.jsx:
* implement read receipts funtion(find out people who read the msg) and show their avatar, then call this function 

LoginForm.jsx:
* to have people to chat with us, we can create a login form
* create an authobject to chk username, password and projectid
* if their credentials are corect, then only they can chat, else show error
* therefore we have used axios here to implement async code and promises
* store credentials in localstorage so that user remains logged in


App.jsx:
* if user doesnot exist in localstorage, open LoginForm
* modify the username and password and make them dynamic bcoz now the person who is logged in with their credentials will be the username
Eg: if I have put username as aparna, but I logged in as preeti but then also in the chat app it will show me as aparna, so this can be overome by dynamic modiffication
get that username and password that is stored in localstorage and not the static ones


* to chk what is stored in localstorage, go to console->application->localstorage-> here we can see username and password that is stored in localstorage
* if we delete that localstorage, browser will get refreshed and ask again for login



This app is fully responsive














react-chat-engine:

#### Props
- publicKey (UUID REQUIRED) - Public API key for your chatengine.io project
- userName (String REQUIRED) - Username of a person in this project
- userSecret (String REQUIRED) - Set a secret for this person and use it to authenticate.
- onConnect (Function) - Callback when the connection/authentication is complete
- onFailAuth (Function) - Callback when the connection/authentication fails
- onGetChats (Function) Callback when the person fetches their chats array
- onNewChat (Function) - Callback when the person creates a new chat
- onEditChat (Function) - Callback when the person edits a chat title
- onDeleteChat (Function) - Callback when the person deletes one of their chats (must the chat's admin)
- onAddPerson (Function) - Callback when a person is added to a chat
- onRemovePerson (Function) - Callback when a person is removed/deleted from a chat
- onGetMessages (Function) - Callback when the person gets a chat's messages
- onNewMessage (Function) - Callback when a person posts a new message in one of the chats
- onEditMessage (Function) - Callback when a person edits a new message in one of the chats
- onDeleteMessage (Function) - Callback when a person deletes a new message in one of the chats
- hideUI (Boolean) - Hides all UI components for a custom implementation (Warning: Advanced)



#### Functions
import `{ functionName }` from 'react-chat-engine'

...

- functionName(conn, args)
- getChats (conn) => void - Get a person's array of chats
- newChat (conn, title) => void - Create a new chat with this person as admin
- editChat (conn, chatId, chatObj) => void - Edit the title of an existing chat
- deleteChat (conn, chatId) => void - If you're admin, delete this existing chat
- addPerson (props, chatId, userName) => void - Add an existing person (in the project) to an existing chat
- removePerson (props, chatId, userName) => void - If you're admin, remove this user from an existing chat
- getMessages (props, chatId) => void - Get the messages for an existing chat
- sendMessage (props, chatId, messageObj) => void - Send a new message object into this chat
- editMessage (props, chatId, messageId, messageObj) => void - Edit an exiting message object in this chat
- deleteMessage (props, chatId, messageId) => void - Delete an exiting message object from this chat

#### Objects


##### Chat Object
- id (int) - Unique primary key to identify this chat
- admin (String) - Unique username of the person who created this chat
- title (String) - Optional title of this chat
- created (Datetime) - Date-time of chat creation
- people (Array) - Array of people added to this chat


##### Chat / Person Association
person (String) - Unique username of a person involved in this chat
{ person: "john_smith" }


##### Message Object
- id (int) - Unique primary key to identify this message
- sender (String) - Unique username of the person who sent this message
- text (String) - Contents of the message sent
- created (Datetime) - Date-time of message creation





##### To deploy this app;
Use netlify-> sign up and create a build folder by npm run build-> drag and drop that to netlify and share the link with frnds



##### Blog: 
https://chattingappusingreact.blogspot.com/
