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
        domShift.init();
    </script>

### With [Webpack](https://webpack.js.org), [Browserify](http://browserify.org) or [RequireJS](http://requirejs.org)

Install *dom-shift* from NPM

    npm install dom-shift --save-dev

Consume as an ES6 module

    import * as domShift from 'dom-shift';

or

    import { executeAfterDelay, shiftDom } from 'dom-shift';

Consume as a CommonJS module

    var domShift = require('dom-shift');

Consume as an AMD

    require(['dom-shift'], function (domShift) {
        // Consume domShift
    }

Note: You may have to use [Babel](https://babeljs.io) for ES6 transpilation.

### Simple usage

1. Import *dom-shift* functions

        import { executeAfterDelay, shiftDom } from 'dom-shift';

2. Shift DOM through states

        shiftDom(
            [
                {
                    name: 'start-logs',
                    step: done => {
                        executeAfterdelay(done, 2000)
                    },
                }, // Adds a CSS class 'state-start-logs' to body tag and runs for 2000 milliseconds
                {
                    name: 'spawn-terminal',
                    step: () => {
                        print(
                            document.querySelector('.frame'),
                            mateInstall,
                            30
                        );
                    },
                    duration: 4000
                }, // Adds a CSS class 'state-spawn-terminal to body tag and runs for 4000 milliseconds
                {
                    name: 'flip',
                    step: () => {},
                    duration: 1500
                }  // Adds a CSS class 'state-flip to body tag and runs for 1500 milliseconds
            ]
        );

You can either use the function `executeAfterDelay` as shown in the example or use the key `duration` to supply a step duration in milliseconds.

## Demo [coming-soon]

You can view a demo [here](https://myterminal.github.io/dom-shift/examples).

## To-do

* Write unit-tests
