# The Rise

To install all dependencies - **npm install**

Run webpack - **npm start**, then open the browser of your choice and point it to *http://localhost:3000/*

More tasks described in - **package.json** {'scripts': ...}

###Used technologies

Webpack, Babel 5, React, Redux + devtools, SASS

>It is possible to enable devtools in the **Root** component by changing the debug prop from 'debug={false}' to 'debug={true}' and then reloading the browser tab. Every triggered action that is connected to Redux will be shown in the sidebar.

###Technologies to add

Axios (Ajax requests)

###Architectural decisions

I decided to have as much logic as possible - also taking into account readability - in the parent (**Mines**) component. That means that props are passed to children components (data-flow parent > children), so that the Redux **dispatch** is only in the parent (in Minesweeper Game). This makes it easier to trace actions and the whole application has higher performance in general. Note that in some cases it is better to have more Redux **connects** for readability and maintainability.

Basic Front-end validation is handled using React's PropTypes. As you can see, included in the files are basic validations of components. If validation fails then you can see warnings in the console.

###File structure
Files are structured in the following manner: parent > children components for better orientation.

Example - in /src/components are four main components (Navigation, Content, Chat, Footer). If any of these components have child components then we create a folder with the same name as the component. 

For example **Content** component has the child component **Mines**. Here is a "schema":

/Content.js
/Content/Mines.js *"Mines.js has so let's add a new folder with the same name"*
/Content/Mines/...

If a component is reused in multiple places then the component is located in the closest logical directory. An example is Notification.js.

Directory tree to get to Notification.js:

/Content/Mines/Notification.js

If you open the file you can see that there is a comment at the top of the file: 

>// used in Game/Tile.js

>// used in Sidebar/Deposit.js

As we can see, the component is reused twice and is in the closest accessible directory for both reuse locations.

This approach makes sense, is easy to follow and in one glance it is possible to see whether or not a component has children. It's also easy to scale the application by following the steps mentioned above.
