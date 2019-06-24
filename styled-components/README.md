# Editted Airbnb/JSX Style Component Guide

*A mostly reasonable approach to React and JSX*

This portion is dedicated to using the styled-component library.

## Table of Contents

  1. [Basic Rules](#basic-rules)
  2. [Naming](#naming)
  3. [Refs](#refs)
  4. [Inheriting Styles](#inheriting_styles)
  5. [Docs](#docs)

 
## Basic Rules
Styles should live in their own separate file `styled-components` that is imported into the main component.  The idea here is to have a standard location that anyone can look to know how the styles for that component are being generated.  

``` jsx
//good

// "./styled-components.jsx"
import React from 'react'
import styled from 'styled-components'

const StyledCounter = styled.div`
  /* ... */
`
const Paragraph = styled.p`
  /* ... */
`
const Button = styled.button`
  /* ... */
`

export default {StyledCounter, Paragraph, Button}

// "./Counter.jsx"
import React from 'react'
import {StyledCounter, Paragraph, Button} from './styled-components.jsx'


export default class Counter extends React.Component {
  state = { count: 0 }

  handeIncrement = () => this.setState({ count: this.state.count + 1 })
  handleDecrement = () => this.setState({ count: this.state.count - 1 })

  render() {
    return (
      <StyledCounter>
        <Paragraph>{this.state.count}</Paragraph>
        <Button onClick={this.handleIncrement}>+</Button>
        <Button onClick={this.handleDecrement}>-</Button>
      </StyledCounter>
    )
  }
}
``` 
Mildly prefer self-contained styles to global css dependent styles.  To use global css styles on a styled component they can still use a className:

``` jsx
const StyledLink = styled.a`
  color: palevioletred;
  font-weight: bold;
`;

...
render(
  <div>
    <StyledLink className={this.props.className}/> exciting Link</StyledLink>
  </div>
);
```

more here: https://www.styled-components.com/docs/advanced#existing-css

## Naming

Avoid naming confusion.  For the outer element name this `Styled[ComponentName]`.  For interior components, name these as generally as possible related to their style.  If all you have are normal <p> tags that are styled name these `Paragraph`, if you have one strike-through paragraph e.g: `StrikeThroughParagraph`.  The resulting element should be a descriptive representation of your overall component.

## Refs
https://www.styled-components.com/docs/advanced#refs

## Inheriting Styles
In discussion: 
This is part of the overall project structure, but we can make global-styled-components library where we make general styles for theme'ing things.

``` jsx
// Example use of global style usage:
// file style-components.jsx
import React from 'react'
import {styled} from 'styled-components'
import {LargeButton} from 'styles/styled-components'; // global large button

const VioletButton = styled(LargeButton) `
  color: palevioletred;
  font-weight: bold;
`;

export {VioletButton};
```

## Docs
https://www.styled-components.com/docs

**[⬆ back to top](#table-of-contents)**