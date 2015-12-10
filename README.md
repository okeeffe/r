# The Rise

Install all dependencies - **npm install**

Run webpack - **npm start**, open browser of your choice on *http://localhost:3000/*

More tasks in - **package.json** {'scripts': ...}

###Used technologies

Webpack, Babel 5, React, Redux + devtools, SASS

>devtools are possible to enable in (**Root** component by changing debug prop from 'debug={false}' to 'debug={true}' and then reload browser tab. Every triggered action that is connected to Redux will be shown in the sidebar.

###Technologies to add

Axios (Ajax requests)

###Architectural decisions

I decided to have as much logic as possible, but also considering readability, in parent (**Mines**) component. That means that props are passed to child components (data-flow parent > children), so the Redux **dispatch** is in only in parent (in Minesweeper Game). Which makes easier to trace actions and the whole application has higher performance. But in some cases it's better to have more Redux **connects** for readability and maintainability.

###File structure
Files are structure like parent child components for better orientation.

Example - in /src/components are four main components (Navigation, Content, Chat, Footer). If some of these components has child(s) components then we create a folder with the same name as component. For example **Content** component has child component **Mines**. Now you can probably image the structure. Just in case there is a "schema"

/Content.js
/Content/Mines.js *"Mines has childs so let's add new folder with same name"*
/Content/Mines/...

If some component is reused in more components then the component is located in the closest directory possible to be accessable. An example is Notification.js

Directory tree to get to Notification.js

/Content/Mines/Notification.js

If you enter the file you can see that there is comment at the top of the file. 
*// used in Game/Tile.js*
*// used in Sidebar/Deposit.js*

As we can see the component is two times reused and in is the closest accessable directory for both reusabilities.

This approach makes sense, is easy to follow and from first sight you can recognize if component has childs or not. It's also easy to scale appliction with following steps mentioned above.

