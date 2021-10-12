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


### How can we do this?
[In the example of our library](https://github.com/jambsik-labs/ui-components)

We have demonstrated small components with a storybook to visualise the content.

We worked with the rollup bundelizer to make the compilation of libraries easier.

In each merge to master, github actions are executed to update our deployed storybook and to create an npm package and publish it.

All this is made easier with a good change history, for this we use semantic release which helps us to version our libraries and create an automatic log. To create this log, commits need to comply with a specific specification.
Before each commit a pre hook will be run to validate errors in both the commit message and any other errors that may be reported by the eslint. Depends the every commit message the semantic release can publish a new version (PATCH, MINOR, MAJOR).




