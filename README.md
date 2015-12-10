# The Rise

Install all dependencies - **npm install**

Run webpack - **npm start**

More tasks - package.json "scripts"

###Used technologies

React, Redux + devtools

>devtools are possible to enable in (**Root** component by changing debug prop from 'debug={false}' to 'debug={true}' and then reload browser tab. Every triggered action that is connected to Redux will be shown in the sidebar.

###Technologies to add

Axios (Ajax requests)

###Architectural decisions

I decided to have as much logic as possible, but also considering readability, in parent (**Mines**) component. That means that props are passed to child components, so the Redux **dispatch** is in only in parent. Which makes easier to trace actions and the whole application has higher performance. But in some cases it's better to have more Redux **connects** for readability and maintainability.

