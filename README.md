[![MIT Licence](https://img.shields.io/github/license/gitbrent/bootstrap-switch-button.svg)](https://opensource.org/licenses/mit-license.php)   [![Bootstrap 4.2.1](https://img.shields.io/badge/bootstrap-4.2.1-green.svg?style=flat-square)](https://getbootstrap.com/docs/4.1)  [![Known Vulnerabilities](https://snyk.io/test/npm/bootstrap-switch-button/badge.svg)](https://snyk.io/test/npm/bootstrap-switch-button)   [![JSDelivr Badge](https://data.jsdelivr.com/v1/package/gh/gitbrent/bootstrap-switch-button/badge)](https://www.jsdelivr.com/package/gh/gitbrent/bootstrap-switch-button)

# Bootstrap Switch Button

**Bootstrap Switch Button** is a bootstrap plugin/widget that converts checkboxes into toggles.

Visit https://gitbrent.github.io/bootstrap-switch-button/ for interactive demos.

**************************************************************************************************

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Demos](#demos)
- [Installation](#installation)
  - [CDN](#cdn)
  - [Download](#download)
  - [NPM](#npm)
  - [Yarn](#yarn)
- [Usage](#usage)
  - [Initialize With HTML](#initialize-with-html)
  - [Initialize With Code](#initialize-with-code)
- [API](#api)
  - [Options](#options)
  - [Methods](#methods)
- [Events](#events)
  - [Event Propagation](#event-propagation)
  - [API vs Input](#api-vs-input)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

**************************************************************************************************

# Demos
Visit https://gitbrent.github.io/bootstrap-switch-button/ for interactive checkbox toggle demos.

# Installation

## CDN
```html
<link href="https://cdn.jsdelivr.net/gh/gitbrent/bootstrap-switch-button@1.0.0/css/bootstrap-switch-button.min.css" rel="stylesheet">  
<script src="https://cdn.jsdelivr.net/gh/gitbrent/bootstrap-switch-button@1.0.0/js/bootstrap-switch-button.min.js"></script>
```

## Download
[Latest GitHub Release](https://github.com/gitbrent/bootstrap-switch-button/releases/latest)

## NPM
```ksh
npm install bootstrap-switch-button
```

## Yarn
```ksh
yarn install bootstrap-switch-button
```

# Usage

## Initialize With HTML
Simply add `data-toggle="toggle"` to automatically convert a plain checkbox into a bootstrap 4 toggle.

```html
<input id="chkToggle" type="checkbox" data-toggle="toggle">
```

## Initialize With Code
Toggles can also be initialized via JavaScript code.  

EX: Initialize id `chkToggle` with a single line of JavaScript.
```html
<input id="chkToggle" type="checkbox" checked>
<script>
  $(function(){
    $('#chkToggle').bootstrapToggle();
  });
</script>
```

# API

## Options
* Options can be passed via data attributes or JavaScript
* For data attributes, append the option name to `data-` (ex: `data-on="Enabled"`)

```html
<input type="checkbox" data-toggle="toggle" data-on="Enabled" data-off="Disabled">
<input type="checkbox" id="toggle-two">
<script>
  $(function() {
    $('#toggle-two').bootstrapToggle({
      on: 'Enabled',
      off: 'Disabled'
    });
  })
</script>
```

Name      |Type       |Default    |Description                 |
----------|-----------|----------|----------------------------|
`on`      |string/html|"On"      |Text of the on toggle
`off`     |string/html|"Off"     |Text of the off toggle
`size`    |string     |"normal"  |Size of the toggle. Possible values are: `large`, `normal`, `small`, `mini`.
`onstyle` |string     |"primary" |Style of the on toggle. Possible values are: `primary`,`secondary`,`success`,`danger`,`warning`,`info`,`light`,`dark`
`offstyle`|string     |"light"   |Style of the off toggle. Possible values are: `primary`,`secondary`,`success`,`danger`,`warning`,`info`,`light`,`dark`
`style`   |string     |           |Appends the value to the class attribute of the toggle. This can be used to apply custom styles. Refer to Custom Styles for reference.
`width`   |integer    |*null*     |Sets the width of the toggle. if set to *null*, width will be auto-calculated.
`height`  |integer    |*null*     |Sets the height of the toggle. if set to *null*, height will be auto-calculated.

## Methods
Methods can be used to control toggles directly.

```html
<input id="toggle-demo" type="checkbox" data-toggle="toggle">
```

Method     |Example                                         |Description
-----------|------------------------------------------------|------------------------------------------
initialize | `$('#toggle-demo').bootstrapToggle()`          |Initializes the toggle plugin with options
destroy    | `$('#toggle-demo').bootstrapToggle('destroy')` |Destroys the toggle
on         | `$('#toggle-demo').bootstrapToggle('on')`      |Sets the toggle to 'On' state
off        | `$('#toggle-demo').bootstrapToggle('off')`     |Sets the toggle to 'Off' state
toggle     | `$('#toggle-demo').bootstrapToggle('toggle')`  |Toggles the state of the toggle on/off
enable     | `$('#toggle-demo').bootstrapToggle('enable')`  |Enables the toggle
disable    | `$('#toggle-demo').bootstrapToggle('disable')` |Disables the toggle

# Events

## Event Propagation
Note All events are propagated to and from input element to the toggle.

You should listen to events from the `<input type="checkbox">` directly rather than look for custom events.

```html
<input id="toggle-event" type="checkbox" data-toggle="toggle">
<div id="console-event"></div>
<script>
  $(function() {
    $('#toggle-event').change(function() {
      $('#console-event').html('Toggle: ' + $(this).prop('checked'))
    })
  })
</script>
```

## API vs Input
This also means that using the API or Input to trigger events will work both ways.

```html
<input id="toggle-trigger" type="checkbox" data-toggle="toggle">
<button class="btn btn-success" onclick="toggleApiOn()" >On by API</button>
<button class="btn btn-danger"  onclick="toggleApiOff()">Off by API</button>
<button class="btn btn-success" onclick="toggleInpOn()" >On by Input</button>
<button class="btn btn-danger"  onclick="toggleInpOff()">Off by Input</button>
<script>
  function toggleApiOn() {
    $('#toggle-trigger').bootstrapToggle('on')
  }
  function toggleApiOff() {
    $('#toggle-trigger').bootstrapToggle('off')  
  }
  function toggleInpOn() {
    $('#toggle-trigger').prop('checked', true).change()
  }
  function toggleInpOff() {
    $('#toggle-trigger').prop('checked', false).change()
  }
</script>
```