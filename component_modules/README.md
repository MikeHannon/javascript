# Editted Airbnb/JSX Style Component Guide

*A mostly reasonable approach to React and JSX*

This portion is dedicated to using the styled-component library.

## Table of Contents

  1. [Basic Rules](#basic-rules)
  2. [Naming](#naming)
   
## Basic Rules

React components should each live in their own folder and ideally be self-contained, small readable elements.  This will hopefully maximize our chance of generating re-usable, stable components in our applications:

The component module should consist of discrete parts:
* index.jsx -- this is responsible for importing and exporting critical files in the module.  That's all it does, no extra components etc.
* ComponentContainer.jsx -- this optional file is responsible for gathering props to feed to the Component to separate logic from presentation.
* Component.jsx -- this file is responsible for rendering the final component.
* constants.jsx -- this file feeds any constants to the Component or ComponentContainer.
* styled-components.jsx -- this file feeds th styled components to the Component.jsx.
* utils.jsx -- this file holds any utils that the Component or ComponentContainer and specific sub-components needs to use that aren't in the global utils.

Folders
* \_\_tests__: contains the .spec.js file for anything exported in index.jsx.
* storybook: optional, but read this: https://www.learnstorybook.com/react/en/get-started
* sub-components: optional, especially common in the specific component section, but these are unique components that are required by the parent component (and not found in the common component library).  Each submodule should be built using the same module structure described here.

**[⬆ back to top](#table-of-contents)**