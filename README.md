# dom-shift

[![npm version](https://badge.fury.io/js/dom-shift.svg)](https://badge.fury.io/js/dom-shift)
[![npm downloads](https://img.shields.io/npm/dt/dom-shift.svg)](https://www.npmjs.com/package/dom-shift)  
[![Build Status](https://travis-ci.org/myTerminal/dom-shift.svg?branch=master)](https://travis-ci.org/myTerminal/dom-shift)
[![Code Climate](https://codeclimate.com/github/myTerminal/dom-shift.png)](https://codeclimate.com/github/myTerminal/dom-shift)
[![js-myterminal-style](https://img.shields.io/badge/code%20style-myterminal-blue.svg)](https://www.npmjs.com/package/eslint-config/myterminal)
[![Coverage Status](https://img.shields.io/coveralls/myTerminal/dom-shift.svg)](https://coveralls.io/r/myTerminal/dom-shift?branch=master)  
[![Dependency Status](https://david-dm.org/myTerminal/dom-shift.svg)](https://david-dm.org/myTerminal/dom-shift)
[![devDependency Status](https://david-dm.org/myTerminal/dom-shift/dev-status.svg)](https://david-dm.org/myTerminal/dom-shift#info=devDependencies)
[![peer Dependency Status](https://david-dm.org/myTerminal/dom-shift/peer-status.svg)](https://david-dm.org/myTerminal/dom-shift#info=peerDependencies)  
[![License](https://img.shields.io/github/license/myTerminal/dom-shift.svg)](https://opensource.org/licenses/MIT)  
[![NPM](https://nodei.co/npm/dom-shift.png?downloads=true&downloadRank=true&stars=true)](https://nodei.co/npm/dom-shift/)

A minimal library to switch DOM states using a CSS class.

## How to Use

### Directly from a web page

One can use *dom-shift* directly from a web-page by attaching the *dom-shift.js* to the DOM.

    <!-- Attaching the dom-shift script -->
    <script type="text/javascript" src="path/to/library/dom-shift.js"></script>

    <!-- Usage -->
    <script type="text/javascript">
        pageChatter.init();
    </script>

### With [Webpack](https://webpack.js.org), [Browserify](http://browserify.org) or [RequireJS](http://requirejs.org)

Install *dom-shift* from NPM

    npm install dom-shift --save-dev

Consume as an ES6 module

    import * as pageChatter from 'dom-shift';

or

    import { init, listen, talk } from 'dom-shift';

Consume as a CommonJS module

    var pageChatter = require('dom-shift');

Consume as an AMD

    require(['dom-shift'], function (pageChatter) {
        // Consume pageChatter
    }

Note: You may have to use [Babel](https://babeljs.io) for ES6 transpilation.

### Simple usage

1. Import *dom-shift* functions

        import { init, listen, talk, broadcast, terminate } from 'dom-shift';

2. Initialize *dom-shift*

        init();

    The above line should be placed in the parent-most app, the one that can host *dom-shift* in a way that it can be accessed from any other contained app participating in the chatter. 

3. Listen to chatter from an app on the page

        listen(
            'sub-app1', // Own Id
            ({ event, payLoad }) => {
                // TODO: Consume messages
            }
        );

    The first argument to `listen` needs to be an identifier for the current participating app and the second is a handler that receives messages with an `event` and a `payLoad` (if at all there's one).

4. Talk to another app participating in the chatter

        talk(
            'sub-app2', // Id of the recipient
            'get-sum', // Event identifier
            {
                num1: 2,
                num2: 3
            } // Message data
        );

    The first argument to `talk` is the identifier of the recipient, the second is the `event` for the recipient to know the nature of the message and the third is the `payLoad`.

5. Talk to all other participants at once

        broadcast(
            'he-is-here' // Event identifier
            {
                who: 'someone'
            } // Message data
        );

    The arguments to `broadcast` are the same as `talk` but there is no `id` for the recipient, as all participants can listen.

6. [Optional] Terminate the chatter

        terminate();

    A call to `terminate` releases *dom-shift*'s control from the page and returns everything back to normal.

## Demo [coming-soon]

You can view a demo [here](https://myterminal.github.io/dom-shift/examples).

## To-do

* Write unit-tests
