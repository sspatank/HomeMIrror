# Home Mirror

> Web-based home mirror, inspired by [Hannah Mitt's project](https://github.com/HannahMitt/HomeMirror).

![](https://cldup.com/Vw4FEaH8h1.png)

## Install

### [Meteor](https://www.meteor.com/):
1. [Install Meteor](https://www.meteor.com/install)
2. Clone this repo

    $ git clone git@github.com:lambtron/homemirror.git

3. Deploy to Meteor

    $ meteor deploy <your-name-here>.meteor.com

### [Heroku](http://heroku.com/)

[Deploy via Heroku]()

## Customize

I decided to use Meteor for its real-time nature and ability to organize server and client side JavaScript in the same folder.

Every "widget" on the screen can be found in the [`./widgets`]() folder. Let's look at the [`time`]() widget as an example:

1. Create the folder `time` with `./time/index.html` and `./time/index.js`

2. Define the `time` template in `index.html`

```
<template name="time">
  <div style="font-size: 3em">
    {{time}}
  </div>
</template>
```

3. Define the logic for rendering the `time` template in `index.js`

```
if (Meteor.isClient) {
  Template.time.helpers({
    time: function() {
      return Chronos.liveMoment().format("hh:mma");
    }
  });
}
```

4. Add the `time` template to `./client/index.html`

```
<head>
  <title>Mirror</title>
</head>

<body>
  {{> date}}
  {{> time}}
  {{> weather}}
  {{> news}}
</body>
```

## License (MIT)

```
WWWWWW||WWWWWW
 W W W||W W W
      ||
    ( OO )__________
     /  |           \
    /o o|    MIT     \
    \___/||_||__||_|| *
         || ||  || ||
        _||_|| _||_||
       (__|__|(__|__|
```

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the 'Software'), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
