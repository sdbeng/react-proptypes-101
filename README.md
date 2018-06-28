# react-proptypes-101
## Introduction to PropTypes
If you're coming from a strictly typed language, you know the importance of types.

Below we have our Users component,
```
class Users extends React.Component {
  render() {
    return (
      <ul>
        {this.props.list.map(function (friend) {
          return <li>{friend}</li>
        })}
      </ul>
    )
  }
}
```
Looking at the component above, what would happen if when we rendered the component, instead of passing in list as an array, what if we accidentally passed in a string?
```
<Users list="Dani, Alan, Beatrice" />
```
Well, everything will break and you'll notice a typical red flag error in the console.The reason is because we're calling `list.map` inside of our component and obviously strings don't have a .map method.

This is where PropTypes come into play. PropTypes allow you to declare the "type" (string, number, function, object, array, etc) of each prop being passed to a component. Then, if a prop passed in isn't of the declared type, you'll get one of those warnings in the console.

Check the code and see that we're now using a new api by installing prop-types as a separate npm package(since React v15.5).
```
import react from 'react
import PropTypes from 'prop-types'
class Users extends React.Component {
  render() {
    return (
      <ul>
        {this.props.list.map(function (friend) {
          return <li>{friend}</li>
        })}
      </ul>
    )
  }
}
Users.propTypes = {
  list: PropTypes.array.isRequired
}
```
PropTypes are great for finding bugs in your components but what I like most about them is their ability to add documentation to a component.

The PropTypes api is very in depth and you can do even more things than just type checking (like making a property required or type checking specific properties of an object). To see the more in depth API, check [https://reactjs.org/docs/typechecking-with-proptypes.html].
