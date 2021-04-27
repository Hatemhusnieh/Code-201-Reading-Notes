# Readings: Passing Functions as Props

***

# Content

- [Lifting State Up](#lifting-state-up)
- [Lists and Keys](#lists-and-keys)
- [How to Use the Spread Operator](#how-to-use-the-spread-operator)
- [Reference](#reference)

***

# Lifting State Up

Frequently, multiple components must represent the same changing data. We propose that the mutual state be elevated to their mutual ancestor. When we change an input, other components should change as well (and vice versa). We demand that the reciprocal state be elevated to their most recent shared ancestor. "Lifting state up" is the term for this.

index.html
```html
<!DOCTYPE html>
<html>
  <body>
    <div id="root"></div>
  </body>
</html> 
```

index.js
```js
const scaleNames = {
  c: 'Celsius',
  f: 'Fahrenheit'
};

function toCelsius(fahrenheit) {
  return (fahrenheit - 32) * 5 / 9;
}

function toFahrenheit(celsius) {
  return (celsius * 9 / 5) + 32;
}

function tryConvert(temperature, convert) {
  const input = parseFloat(temperature);
  if (Number.isNaN(input)) {
    return '';
  }
  const output = convert(input);
  const rounded = Math.round(output * 1000) / 1000;
  return rounded.toString();
}

function BoilingVerdict(props) {
  if (props.celsius >= 100) {
    return <p>The water would boil.</p>;
  }
  return <p>The water would not boil.</p>;
}

class TemperatureInput extends React.Component {
  constructor(props) {
    super(props);
    this.handleChange = this.handleChange.bind(this);
  }

  handleChange(e) {
    this.props.onTemperatureChange(e.target.value);
  }

  render() {
    const temperature = this.props.temperature;
    const scale = this.props.scale;
    return (
      <fieldset>
        <legend>Enter temperature in {scaleNames[scale]}:</legend>
        <input value={temperature}
               onChange={this.handleChange} />
      </fieldset>
    );
  }
}

class Calculator extends React.Component {
  constructor(props) {
    super(props);
    this.handleCelsiusChange = this.handleCelsiusChange.bind(this);
    this.handleFahrenheitChange = this.handleFahrenheitChange.bind(this);
    this.state = {temperature: '', scale: 'c'};
  }

  handleCelsiusChange(temperature) {
    this.setState({scale: 'c', temperature});
  }

  handleFahrenheitChange(temperature) {
    this.setState({scale: 'f', temperature});
  }

  render() {
    const scale = this.state.scale;
    const temperature = this.state.temperature;
    const celsius = scale === 'f' ? tryConvert(temperature, toCelsius) : temperature;
    const fahrenheit = scale === 'c' ? tryConvert(temperature, toFahrenheit) : temperature;

    return (
      <div>
        <TemperatureInput
          scale="c"
          temperature={celsius}
          onTemperatureChange={this.handleCelsiusChange} />
        <TemperatureInput
          scale="f"
          temperature={fahrenheit}
          onTemperatureChange={this.handleFahrenheitChange} />
        <BoilingVerdict
          celsius={parseFloat(celsius)} />
      </div>
    );
  }
}

ReactDOM.render(
  <Calculator />,
  document.getElementById('root')
);
```

On the DOM data, React calls the function defined as `onChange`. This is where the temperature conversion takes place. With their new props, React calls the make methods of the individual Temperature input components. It knows how they like their user interface to appear. The value of the input we just changed is modified, and the temperature of the other input is converted. Based on the current temperature and the active scale of the input we edited, the values of both inputs are recalculated. The boiling verdict is updated in the React DOM, and the desired input values are matched.

[Back to Content](#content)

# Lists and Keys

Keys are one-of-a-kind identifiers that must be added to the map's top-level feature. React uses keys to figure out how to edit a list, whether it's by inserting, modifying, or deleting objects. This is one of the reasons React is so fast with long lists. Check out the official React docs for more information on keys.

I used it for previous Lab work:

[lab work class 01](https://github.com/MKAbuMattar/lab-work-calss01)

Main.js
```js
import React, { Component } from 'react'
import HornedBeast from './components/HornedBeast/HornedBeast'

export default class Main extends Component {
  render() {

    let animals = [{
      "image_url": "http://3.bp.blogspot.com/_DBYF1AdFaHw/TE-f0cDQ24I/AAAAAAAACZg/l-FdTZ6M7z8/s1600/Unicorn_and_Narwhal_by_dinglehopper.jpg",
      "title": "UniWhal",
      "description": "A unicorn and a narwhal nuzzling their horns",
      "keyword": "narwhal",
      "horns": 1
    },
    {
      "image_url": "https://images.unsplash.com/photo-1512636618879-bbe79107e9e3?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=bd9460ee6d1ddbb6b1ca7be86dfc4590&auto=format&fit=crop&w=1825&q=80",
      "title": "Rhino Family",
      "description": "Mother (or father) rhino with two babies",
      "keyword": "rhino",
      "horns": 2
    },
    {
      "image_url": "https://www.dhresource.com/0x0s/f2-albu-g5-M00-1A-11-rBVaI1hsIIiALxKzAAIHjSU3VkE490.jpg/wholesale-halloween-costume-prop-unicorn.jpg",
      "title": "Unicorn Head",
      "description": "Someone wearing a creepy unicorn head mask",
      "keyword": "unicorn",
      "horns": 1
    }];

    return (
      <>
        <main>
          <section className="grid grid-col-3">

            {animals.map(result => (
              <HornedBeast
                key={result.keyword}
                imageUrl={result.image_url}
                title={result.title}
                description={result.description}
                keyword={result.keyword}
                horns={result.horns}
              />
            ))}

          </section>
        </main>
      </>
    )
  }
}
```

HornedBeast.js
```js
import React, { Component } from 'react'

export default class HornedBeast extends Component {
  render() {
    return (
      <>
        <div className="card" key={this.props.keyword}>
          <img src={this.props.imageUrl} alt={`${this.props.description}, horns: ${this.props.horns}`} title={this.props.title} />
          <div className="cardInfo">
            <h2>{this.props.title}</h2>
            <p>Description: {this.props.description}</p>
          </div>
        </div>
      </>
    )
  }
}
```

[Back to Content](#content)

# How to Use the Spread Operator

The spread operator is a convenient and fast way to connect things to lists, combine arrays or elements, and spread an array across a function's arguments. The spread operator was first implemented in JavaScript ES6 (ECMAScript 6). Three dots... accompanied by the vector name is the spread operator or syntax. The spread operator expands an inerrable like an array expression or string in places where zero or more arguments (for function calls) or elements (for array literals) are predicted, or an object expression in places where zero or more key-value pairs (for object literals) are expected. The spread operator can be used to make forwarding respond props to a part easier. The spread operator is used in the react redux and reducer functions to calculate new states without mutating the current one. The code below shows how to use the spread operator in method calls, merge an array, merge an entity, use react props, and use the react redux reducer function.

[Back to Content](#content)

***

## Reference

## 1
Reactjs.org. (2020). Lifting State Up – React. [online] Available at: https://reactjs.org/docs/lifting-state-up.html [Accessed 26 Apr. 2021].

## 2
Reactjs.org. (2020). Lists and Keys – React. [online] Available at: https://reactjs.org/docs/lists-and-keys.html [Accessed 26 Apr. 2021].

## 3
Reactjs.org. (2020). Tutorial: Intro to React – React. [online] Available at: https://reactjs.org/tutorial/tutorial.html [Accessed 26 Apr. 2021].

## 4
Austin, D. (2019). How to Use the Spread Operator (…) in JavaScript - Coding at Dawn - Medium. [online] Medium. Available at: https://medium.com/coding-at-dawn/how-to-use-the-spread-operator-in-javascript-b9e4a8b06fab [Accessed 26 Apr. 2021].

[Back to Content](#content)

[⇐ Home Page](../../README.md)
