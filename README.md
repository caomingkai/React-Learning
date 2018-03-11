 # React Learning Demos 

 ## 0.1 Before diving into project
 - In <head>, we needs 3 <script> in order to use React, that is, "react.js","react-dom.js","browser.min.js"
 - In <body> where we manipulate JSX, we use a special <script type="text/babel" >, whose typel is "text/babel"

 ## 0.2 After finishing project
 In order to make faster rendering at client-side, use " $ babel src --out-dir build ", parsing all JSX file at directory 'src' into javascript files at directory 'build', where browser could recognize.

 ## 1. ReactDOM.render();
 It is a basic method:
 - converting JSX into HTML;
 - inserting HTML at specified DOM point


 ## 2. JSX - JavaScript XML
 ### "logic" + "view"
 - not spring (no quotes "" )
 - not HTML ( more of XML )
 - support "tag + expression"

 ### How to parse?
 - for tags (begin with "<"), parse as HTML
 - for code block(begin with "{"), parse as JavaScript

 ## 3. JSX can contain tag array
 JSX can unfold all tag in a array

 ## 4. Component
 A component is function,
 - accepting "input"(props), 
 - returnnig "view"(HTML tag)
 ### How to create a component?
 - functional component
 ```
 function Welcome(props) {
    return <h1>Hello, {props.name}</h1>;
 }
 ```
 - class component
 ```
 class Welcome extends React.Component {
    render() {
       return <h1>Hello, {this.props.name}</h1>;
    }
 }
 ```

 