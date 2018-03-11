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
 - If a group of tags don't need its own props or states, just declare it as *const*, rather than component. [ see demo14 & demo14-2]
 - Component should have no more than one top tag


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
 Reuse components just like "li" in "ul"


 ## 7. Extracting Components
 #### What?
 Split components into smaller components, to achieve more flexibility and reusability.
 #### How?
 Split by functionality
 One component can contain multiple sub-components

 ## 8. State (like 'props')
 #### Purpose?
 A non-static component, has its own "state"
 #### What?
 Actually it's like pros, but "state" is private to component class, compared to "props"
 #### How?
 - Use "state" in render(), when state changed, React will can render again.
 - Must use a **Class Component**, rather than __function component__.
 #### Diff
 - this.props(*public:passed-in*) 表示那些一旦定义，就不再改变的特性
 - this.state(*private:built-in*)是会随着用户互动而产生变化的特性。
 - both are belongs to __this__.
 #### Constructor of component class
 First, always call **super(props):**
 Second, set *this.state=...;**


 ## 9. Adding Lifecycle Methods to a Class
 #### purpose
 In order to save CPU and memory
 #### what involved?
 componentDidMount()
 componentWillUnmount()
 setState()
 #### about setState()?
 Do Not Modify State Directly=>instead using **setState()**
 State Updates May Be Asynchronous=> instead,again using setState() with its another form: use a function accepting 'provState' as it passed-in parameter to set the state

 #### How - work flow?
 1. When <Clock /> is passed to ReactDOM.render(), React calls the constructor of the Clock component. Since Clock needs to display the current time, it initializes this.state with an object including the current time. We will later update this state.
 2. React then calls the Clock component’s render() method. This is how React learns what should be displayed on the screen. React then updates the DOM to match the Clock’s render output.
 3. When the Clock output is inserted in the DOM, React calls the componentDidMount() lifecycle hook. Inside it, the Clock component asks the browser to set up a timer to call the component’s tick() method once a second.
 4. Every second the browser calls the tick() method. Inside it, the Clock component schedules a UI update by calling setState() with an object containing the current time. Thanks to the setState() call, React knows the state has changed, and calls the render() method again to learn what should be on the screen. This time, this.state.date in the render() method will be different, and so the render output will include the updated time. React updates the DOM accordingly.
 5.If the Clock component is ever removed from the DOM, React calls the componentWillUnmount() lifecycle hook so the timer is stopped.

 #### state: parent & children ?
 0. state is isolated among components 
 1. Parent and Child shall not know if the other is stateful of stateless.
 2. But there is a way for parent to pass down its own state to its children, by using **'props'**


 ## 10. Events
 #### What?
 Substitute addEventListener(): to add listeners to a DOM element after it is created.

 #### Diff ( virtual DOM vs. real DOM)
 - React events are named using camelCase, rather than lowercase.
 - With JSX you pass a function as the event handler, rather than a string. 统一采用expression表达方法，写在'{}'中
 	+ button onClick={activateLasers}
 	+ button onclick="activateLasers()"
 - Cannot return false to prevent default behavior in React. You must call preventDefault explicitly
 	+ a href="#" onclick="console.log('The link was clicked.'); return false"
 	+
 	```
 	function ActionLink() {
	  function handleClick(e) {
	    e.preventDefault();
	    console.log('The link was clicked.');
	  }

	  return (
	    <a href="#" onClick={handleClick}>
	      Click me
	    </a>
	  );
	}
	```
 #### be carefull with 'e' & 'this'

 ## 11. Conditional Rendering 
 #### what?
 display optionally between several components, based on a *state variable*

 #### How?
 Have two _button components_ as child_component of a parent component, toggling state of parent component, then resulting in another _display component_ shows up or hide away. [see demo14]

 ## 12. List and keys

 #### What?
 - Array can produce a list of 'li', by using _map()_ function.
 - 'Keys' help React identify which items have changed, are added, or are removed. Keys should be given to the elements inside the array, in order to give the elements a stable identity

 #### Where to put 'keys'?
 A good rule of thumb is that elements inside the map() call need keys.


 ## 13. Forms -> controlled component
 #### What ?
 - Let React __"state"__ be the “single source of truth”。
 用React的state来保存form的用户输入
 - With a controlled component, every state mutation will have an associated handler function. This makes it straightforward to modify or validate user input. 
	```
		handleChange(event) {
  			this.setState({value: event.target.value.toUpperCase()});
		}

	```

 #### Which ?
 1. input element <---> state & state_handler
 ```
 <input type="text" value={this.state.value} onChange={this.handleChange} />
 ```
 2. textarea <---> state & state_handler
 ```
 <textarea value={this.state.value} onChange={this.handleChange} />
 ```
 3. select <---> state & state_handler[similar to above ones: has its own "value" props]
 ```
 <select value={this.state.value} onChange={this.handleChange}>
 // notice: 'value' in <select> is not 'value' in <option>
 ```

 #### Handling Multiple Inputs
 add a name attribute to each element and let the handler function choose what to do based on the value of event.target.name.

 ## 14. Lifting State Up ( __share state__ among components in their parent component )
 Sharing state is accomplished by moving it up to the closest common ancestor of the components that need it. This is called **“lifting state up”**. 

 #### How
 1. parent component maintains several __state variables__
 2. child componnets receive parent's __state && functions__ as their own __props__ ( function can be passed to children component )
 3. when children get updated, it will call parent's function, and modify parent's state, thus leading to re-rendering all its children components

  #### Work flow
  Let’s recap what happens when you edit an input:

  1. React calls the function specified as onChange on the DOM <input>. In our case, this is the handleChange method in TemperatureInput component

  2. The handleChange method in the TemperatureInput component calls this.props.onTemperatureChange() with the new desired value. Its props, including onTemperatureChange, were provided by its parent component, the Calculator

  3. When it previously rendered, the Calculator has specified that onTemperatureChange of the Celsius TemperatureInput is the Calculator’s handleCelsiusChange method, and onTemperatureChange of the Fahrenheit TemperatureInput is the Calculator’s handleFahrenheitChange method. So either of these two Calculator methods gets called depending on which input we edited

  4. Inside these methods, the Calculator component asks React to re-render itself by calling this.setState() with the new input value and the current scale of the input we just edited.

  5. React calls the Calculator component’s render method to learn what the UI should look like. The values of both inputs are recomputed based on the current temperature and the active scale. The temperature conversion is performed here

  6. React calls the render methods of the individual TemperatureInput components with their new props specified by the Calculator. It learns what their UI should look like

  7. React DOM updates the DOM to match the desired input values. The input we just edited receives its current value, and the other input is updated to the temperature after conversion.

