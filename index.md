# What is the main idea?

##### The main idea of the project is to build an ecosystem of applications and libraries that communicate with each other.

##### And at the end of this document there is a small example of how to integrate our own library with a series of automated steps into one of our "POC" projects.

![](https://github.com/jambsik-labs/jambsik-labs.github.io/blob/171dce733caa9e49814d3cd4f6f0110ff46972d1/img/flow_1.png?raw=true)

#### Let's talk about each of them, how they relate to each other and what they are used for.

# UI - components library

### [source code link](https://github.com/jambsik-labs/ui-components)

This a reusable react library for shared components with design system methodology in our apps.
It is a component library in which we can create all those common components between our applications. It will give us the ability to reduce code copied by our projects.

These components must be transversal to our business and at no time should they have any logic to it.
In order to know which component to put in the library, we can follow the rule that if it is needed in more than one project, it is reusable. If it is something customised or only for a specific project, it should not be added to our library.

### What kind of components can we create here?

<strong>Atomic</strong>: These can be components such as buttons, links, labels, an input.

<strong>Molecules</strong>: Those more powerful components such as a searcheable input, a multi selector. They are also components that can contain some of the previous section in combination.

<strong>Organisms</strong>: A set of atomic components, molecules and even other organisms. They can be components such as a menu of sections, the header of the application.

<strong>Templates</strong>: This is a grouping of all our components represented in a layout in which they can be reused. Let's imagine a layout container for all our apps, consisting of a header, menu and main container. We could abstract the logic inside and simply based on a series of props serve as a layout for any of our apps, and even with a different theme.

On a day-to-day basis, we don't need to create a 100% own library. The effort would be too high for some components. We can focus on making components of template or organism types. For the rest of the components we can use ui libraries like [Theme-ui](https://theme-ui.com/) or [Material ui](https://mui.com/). These libraries give us enough components that we can use directly or make small modifications for our design, besides that they allow us a good theming with their providers and we can change the whole palette of colours according to the application we are interested in.

### How can we do this?

[In the example of our library](https://github.com/jambsik-labs/ui-components)

We have demonstrated small components with a [storybook](https://github.com/jambsik-labs/https://jambsik-labs.web.app/?path=/story/atoms-button--default-case) to visualise the content.

We worked with the [Rollup bundelizer](https://rollupjs.org/guide/en/) to make the compilation of libraries easier.

In each merge to master, github actions are executed to update our deployed storybook and to create an npm package and publish it.

![](https://github.com/jambsik-labs/jambsik-labs.github.io/blob/master/img/1.png?raw=true)
![](https://github.com/jambsik-labs/jambsik-labs.github.io/blob/master/img/1b.png?raw=true)
![](https://github.com/jambsik-labs/jambsik-labs.github.io/blob/master/img/1c.png?raw=true)

All this is made easier with a good change history, for this we use semantic release which helps us to version our libraries and create an automatic log. To create this log, commits need to comply with a specific specification.
Before each commit a pre hook will be run to validate errors in both the commit message and any other errors that may be reported by the eslint. Depends the every commit message the semantic release can publish a new version (PATCH, MINOR, MAJOR).

![](https://github.com/jambsik-labs/jambsik-labs.github.io/blob/master/img/2.png?raw=true)
![](https://github.com/jambsik-labs/jambsik-labs.github.io/blob/master/img/3.png?raw=true)
![](https://github.com/jambsik-labs/jambsik-labs.github.io/blob/master/img/4.png?raw=true)

# upcoming

Components to come in future iterations: a template of the application layout with its menu items.
![](https://github.com/jambsik-labs/jambsik-labs.github.io/blob/master/img/poc_design.png?raw=true)


# Common Library

This library will have a common base with the one mentioned above. The main difference would be how to approach it. In this case we would not have a component library but a library that includes helpers,module, customs hooks and testing utilities and even models. All of this can become repetitive between the different applications we have. A kind of connector between all of them that facilitates development and avoids the repetitive propagation of code.

# Applications

I suggest you get Nextjs + typescript + Redux toolkit. Based on SSR.

### [Next JS](https://nextjs.org/)

Nextjs allows us to develop work with React Js in a faster and easier way. It saves us all the management and configuration of Babel, webpack, Hot module replacement to be able to make changes without the need for a full reload during development. It gives us a better performance in the application because we avoid work to the browser to serve directly the pages in html.
It gives us the advantage of creating routes from its folder structure without the need to configure it. It is a full stack frame work in which we can even create Api routes.
```
Dev build system
Production build system
Prerendering
    SSR
    Build time
    Static
    Routing
API routes 
```

![](https://github.com/jambsik-labs/jambsik-labs.github.io/blob/master/img/ssr.png?raw=true)

### [Redux Toolkit](https://redux-toolkit.js.org/)
Along the same line as next js. Redux toolkit is the solution or simplification of redux based on suggestions received by the redux team.

<em>
The Redux Toolkit package is intended to be the standard way to write Redux logic. It was originally created to help address three common concerns about Redux:

"Configuring a Redux store is too complicated"
"I have to add a lot of packages to get Redux to do anything useful"
"Redux requires too much boilerplate code"
</em>

### Scaffolding
![](https://github.com/jambsik-labs/jambsik-labs.github.io/blob/master/img/scaffolding.png?raw=true)

### Testing

I would concentrate on adding significant unit test coverage and a high level of effort in integration testing of all our components. That is, how the different parts of the application communicate and interact but with api mocks. In the future we could consider testing the most important things with cypress in e2e version.

![](https://github.com/jambsik-labs/jambsik-labs.github.io/blob/master/img/tests.png?raw=true)

### Based on the information above
The flow of our applications could be as follows:

![](https://github.com/jambsik-labs/jambsik-labs.github.io/blob/master/img/flow.png?raw=true)

# Demo Show Time

Referring to the first part that we have explained, I have based this as the first demo of many that we could do. But basically they are a demo of how to create a component library with the mentioned and a small next js application that logging us in firebase. It's just a premise of what could be done and together with this document everything we could build together.

The projects concerned are: [ui-components](https://github.com/jambsik-labs/ui-components) and [auth app](https://github.com/jambsik-labs/auth)

# Overview

I know I left out a lot of things like user information tracking, offiline, mobile, notifications, user information logs, authorisation, lazy loading, design, etc. But these are things that need to be solved step by step as they arise.