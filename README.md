# External Widget

Allows form submitter to record video/audio, take picture, do internet & typing speed tests without leaving your form!

Video/audio/image will be uploaded to submitter's Google Drive and external link of the uploaded file will be set as the value of the form's input field.

----
## How To Use
Copy the code snippet to `<head>` of the page containing your form.

    <!-- HOPLA WIDGET -->
    <script>
      var widgets = [
        
      ];
      (function (d, s, id) {
        var js, fjs = d.getElementsByTagName(s)[0];
        if (d.getElementById(id)) {
          return;
        }
        js = d.createElement(s);
        js.id = id;
        js.onload = function () {
          hopla_widget.init(widgets);
        };
        js.src = "https://cdn.hopla.tools/widgets/hopla-universal-widget.js";
    fjs.parentNode.insertBefore(js, fjs);
      }(document, 'script', 'hopla-widgets'));
    </script>
    <!-- HOPLA WIDGET -->

`widgets` in line 3 is an array containing the widgets that you want to add. 

Each widget must be in this format:

    {
        type: <type>,
        input_name: <name>
    }

where

`<type>` = Any of the values: `image`, `video`, `audio`, `internet_speed`, `type_speed`.

`<name>` = the **name** attribute of the *\<input>* field where the result of the widget will be saved.

### Example:
If your form has the inputs:

    Name: <input name="name">
    Record a video: <input name="your-video">
    Take a picture: <input name="your-image">
    Do an internet speed test: <input name="net-speed">

Then your `widgets` in line 3 of snippet should be:


    var widgets = [
        {
          type: 'video',
          input_name: 'your-video'
        }, 
        {
          type: 'image',
          input_name: 'your-image'
        },
        {
          type: 'internet_speed',
          input_name: 'net-speed'
        }
    ];

## Defaults
---
### WebRTCs (Image/Video/Audio)
Filename in Google Drive: `<domain> hh:mm:ss_dd-mm-yyyy.ext`

Max Duration: `1 Minute`

Output Format: `https://drive.google.com/uc?export=view&id=<file id>`

### Internet Speed Test
Output Format: `Down:Up:Ping`

### Typing Speed Test
Output Format: `<wpm>`
