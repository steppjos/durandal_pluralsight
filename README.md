# Learning Durandal with Pluralsight

Uses Require.js, jQuery, and Knockout.js for data binding.

Durandal is all about _Composition_. Composes smaller pieces into a larger application.

## Setup

Download and extract [html starter kit](durandaljs.com/downloads.html) to a project directory.

```
npm install -g http-server
cd ${projectdir}
http-server
```

Durandal app is available at [http://localhost:8080](http://localhost:8080)

## Add a view

Add `helloOSX.html` in `views` directory and `helloOSX.js` in `viewmodels` directory.

Durandal html templates always have a container element, example a `<div>`.

Html elements can have data binding to variables in the corresponding viewModel, for example:

```html
<h1 data-bind="text: message"></h1>
```

For the view model, call `define({...})` with object properties.
These properties represent the data that the view can bind to. For example:

```javascript
define({
  message: 'Hello, OSX'
});
```

Last step is to configure this view in the router. Router configuration is in `shell.js`.
Note that routes can have a title:

```
{ route: 'helloOSX', moduleId: 'viewmodels/helloOSX', title: 'Hello OS X', nav: true }
```

## Conventions and Architecture

### Model View Patterns

Variations such as MVC (controller), MVP (presenter), MVVM (viewModel).
They all have in common separation of view from state and behaviour.

Durandal calls itself MV*. Can be used with any of the above patterns. This course will use MVVM.

### View

HTML and stylesheets. Responsbile for visual portion of application. Has no behaviour.

### Model

Knowledge behind the application, has all data and application logic.

### ViewModel

Lies in between the view and the model. Data bound to the view.

As user updates the view, viewModel gets updated.

When viewModel gets updated, view is updated as well.

ViewModel holds the state for the view and handles the functionality.

ViewModel also has access to the model, and can pass user actions out to the model to execute application logic,
and then update the view as needed.

View and ViewModel are central to Durandal. Every page in the application has a View and ViewModel pair.
They have the same name except for the file extension.