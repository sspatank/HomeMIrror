# Home Mirror

> Web-based home mirror, forked from [Andy Jiang's project](https://github.com/lambtron/homemirror).

## Install

1. [Install Meteor](https://www.meteor.com/install)
2. Clone this repo

    ```
    $ git clone git@github.com:sspatank/Smart-Mirror.git
    ```

3. Configure the settings.release.json file
      The configuration file is used to put in the relevant Api keys and tokens. You add the following keys:
      1. news_api: Get the API key from the New York Times by signing up. [http://developer.nytimes.com/apps/register]
      2. forecastio_api: Get the API key for the weather from Forecast.io [https://developer.forecast.io/register]
      3. geonames_api: This api is used to figure out your localized timezone and weather from your GPS location. Get a username from                        GeoNames. [http://www.geonames.org/login]
      4. telegram_api: This api is used to send a message and an image to the mirror through the Telegram app. The instructions for            getting the token are given [below.] (#telegram) [https://core.telegram.org/bots/api]
      5. defaultmessage: If you don't want to use telegram, it will load this message.

4. Add an image to the public/photos folder and name it image.jpg. This will be the default image that will show up if you don't use      telegram to upload a new image. 

5. Deploy to Meteor

    ```
    $ meteor deploy <your-name-here>.meteor.com --settings settings-release.json
    ```

4. Some of these features only work on chrome. I will add a guide on how to enable a Kiosk mode in android [below.] (#kiosk-mode)

5. Follow [Hannah Mitt's tutorial](https://github.com/HannahMitt/HomeMirror) for physically building the mirror or [lambtron's below](#hardware)

## Customize

Every "widget" on the screen can be found in the [`./widgets`](https://github.com/lambtron/homemirror/tree/master/widgets) folder. Let's look at the [`time`](https://github.com/lambtron/homemirror/tree/master/widgets/time) widget as an example:

1. Create the folder `time` with `./time/index.html` and `./time/index.js`

2. Define the `time` template in [`index.html`](https://github.com/lambtron/homemirror/blob/master/widgets/time/index.html)

    ```
    <template name="time">
      <div style="font-size: 3em">
        {{time}}
      </div>
    </template>
    ```

3. Define the logic for rendering the `time` template in [`index.js`](https://github.com/lambtron/homemirror/blob/master/widgets/time/index.js)

    ```
    if (Meteor.isClient) {
      Template.time.helpers({
        time: function() {
          return Chronos.liveMoment().format("hh:mma");
        }
      });
    }
    ```

4. Add the `time` template to [`./client/index.html`](https://github.com/lambtron/homemirror/blob/master/client/index.html#L7)

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

Have fun!

## Kiosk Mode
To enable kiosk mode, you will need:
 1. A rooted android tablet. There are root guides for the nexus 7 2012 available here [http://forum.xda-developers.com/showthread.php?t=1766475]
 2. The latest chrome browser
 3. Tasker (free) [https://play.google.com/store/apps/details?id=net.dinglisch.android.taskerm&hl=en]
 4. GMD Full Screen Immersive Mode (paid, if you don't want to get annoyed) [https://play.google.com/store/apps/details?id=com.gmd.immersive&hl=en]
 5. MyPhoneExplorer on your tablet and on your computer

Here are the steps:
 1. Root your device using the link I gave above or go here [http://forum.xda-developers.com/] to get the instructions for your device.
 2. Browse to your website and add it to the homescreen. Make sure this is on your homepage i.e. this is the screen that pops up when you power your device on. 
 3. Enable Developers Options on your tablet using this. [http://www.greenbot.com/article/2457986/how-to-enable-developer-options-on-your-android-phone-or-tablet.html]
 4. Follow these instructions to autostart your homescreen shortcut when your device powers on. [http://www.greenbot.com/article/2457986/how-to-enable-developer-options-on-your-android-phone-or-tablet.html]
 5. Enable fullscreen mode in GMD Full Screen Immersive Mode and try to minimize the trigger so that it doesn't show up on the mirror. I ended up getting the pro version. 
 6. Enable USB debugging and connect MyPhoneExplorer to your computer and try to control your tablet using the computer. This is for when you need to control your tablet after you have stuck a mirror on it. 
 7. All these steps are essentially so that you can get an immersive full screen experience. If you find an easier way to get this done, do follow it and let me know too. 

## Telegram

Telegram is a messaging app like Whatsapp. It has quite a few more features including bots. I used these bots to send messages and photos to the mirror remotely. In order to do that you will need to:
 1. Download and setup telegram on your phone. 
 2. Create a bot with the help of the BotFather [https://core.telegram.org/bots#botfather]
 3. Add the commands /test and /m to it. 
 4. Get the token and put it into the settings-release.json file. 


## Hardware

I followed [Hannah's guide](https://github.com/HannahMitt/HomeMirror) pretty closely.

### Items

- 12 inch by 18 inch by 1/8 inch two way mirror from [TAP Plastics](http://www.tapplastics.com/product/plastics/cut_to_size_plastic/two_way_mirrored_acrylic/558)
- 7 inch used Samsung Galaxy Tab
- [12 inch by 18 inch black construction paper, 50 sheets](http://www.amazon.com/gp/product/B000F7ASAU)
- [Two-sided adhesive strips](http://www.amazon.com/gp/product/B0084M68IO)
- [3M General Purpose 4S Spray Adhesive](http://www.amazon.com/gp/product/B000PCWRMC)

### Directions

#### 1. Cut a hole in the black construction paper for the device's viewport

Make sure the size of the hole that you are cutting is the size of the device's _viewport_ and not the size of the device itself. You're going to put the two-sided adhesives along the edge of the construction paper that will stick to the device's bevel.

#### 2. Glue the construction paper onto the back of the mirror

Use the spray adhesive at about 6-8 inches away from the construction paper. Don't get the construction paper too wet. After several seconds, slowly stick the sprayed side onto the back side of the mirror.

#### 3. Add adhesive strips to the back of the construction paper around the edge of the device's viewport cutout

#### 4. [Set the device up](#kiosk-mode).. last chance to touch your device! 

#### 5. Stick the device onto the two-way adhesive strips

Voila!

---

If the final product is facing the ground, this is how and where the pieces fit together:

![](http://i.imgur.com/KXqUMOI.jpg)

The completed mirror:

![](http://i.imgur.com/IxgfxQx.jpg)



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
