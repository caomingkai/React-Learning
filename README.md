 # React Learning Demos 

 ## 0.1 Before diving into project
 - In <head>, we needs 3 <script> in order to use React, that is, "react.js","react-dom.js","browser.min.js"
 - In <body> where we manipulate JSX, we use a special <script type="text/babel" >, whose typel is "text/babel"

 ## 0.2 After finishing project
 In order to make faster rendering at client-side, use " $ babel src --out-dir build ", parsing all JSX file at directory 'src' into javascript files at directory 'build', where browser could recognize.

 ## 1. ReactDOM.render();
 #### what?
 It is a basic method used everywhere
 - converting JSX into HTML;
 - inserting HTML at specified DOM point


 ## 2. JSX 
 #### what?JavaScript XML
 #### "logic" + "view"
 - not spring (no quotes "" )
 - not HTML ( more of XML )
 - support "tag + expression"

 #### How to parse?
 - for tags (begin with "<"), parse as HTML
 - for code block(begin with "{"), parse as JavaScript


 ## 3. JSX can contain tag array
 JSX can unfold all tag in a array


 ## 4. Component
 #### what?
 A component is function,
 - accepting "input"(props), 
 - returnnig "view"(HTML tag)
 #### How to create a component?
 1. functional component
 ```
 function Welcome(props) {
    return <h1>Hello, {props.name}</h1>;
 }
 const element = <Welcome name="Sara" />;
ReactDOM.render(
    element,
    document.getElementById('root')
);
 ```
 2. class component
 ```
 class Welcome extends React.Component {
    render() {
       return <h1>Hello, {this.props.name}</h1>;
    }
 }
 const element = <Welcome name="Sara" />;
 ReactDOM.render(
  element,
  document.getElementById('root')
 );
 ```
 #### Notice
 Component should have no more than one top tag


 ## 5. this.props.children
 #### what?
  All the properties of a Component belongs to its correspoinding HTML element, except "props.children", which represent components' children

 #### possible types for children
 - undefined, if no child at all;
 - object, if only have one child;
 - array, if have multiple children;

 #### How to traverse properly without error?
 use React.Children to ensure validity


 ## 6. Composing Components
 #### What?
 - A button, a form, a dialog, a screen: in React apps, all those are commonly expressed as components.
 - On the other hand, we typically have an 'App' component at the top level
 - *Best Practice:* start from bottom-up, work along to the top level

 #### How?
 Reuse components just like "<li>" in "<ul>"


 ## 7. Extracting Components
 #### What?
 Split components into smaller components, to achieve more flexibility and reusability.
 #### How?
 Split by functionality
 One component can contain multiple sub-components

 ## 8. State and Lifecycle
 #### Purpose?
 A non-static component, has its own "state"
 #### What?
 Actually it's like pros, but "state" is private to component class, compared to "props"
 #### How?
 Must use a **Class Component**, rather than __function component__.
 #### Diff
 - this.props(public:passed-in) 表示那些一旦定义，就不再改变的特性
 - this.state(private:built-in)是会随着用户互动而产生变化的特性。
 - both are belongs to __this__.
 #### Constructor of component class
 First, always call **super(props):**
 Second, set *this.state=...;**
 







