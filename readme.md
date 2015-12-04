#Directory Slider
###Loads all images in a specified directory and creates a slide show
Based off of Justin W. Hall's Directory Slider. Added flexibility for filenames through an ajax call.


##Installation

###Step 1: Link required files
```html
<!-- jQuery library (served from Google) -->
<script src="//ajax.googleapis.com/ajax/libs/jquery/1.8.2/jquery.min.js"></script>
<!-- directorySlider Javascript file -->
<script src="/js/directorySlider.js"></script>
```

###Step 2: Create HTML markup
 ```html
<div class="directorySlider"></div>
```

###Step 3: Call The Directory Slider
```javascript
        $(document).ready(function(){

            var dir = "/img";
            var fileextension = ".jpg";
            $.ajax({
                //This will retrieve the contents of the folder if the folder is configured as 'browsable'
                url: dir,
                success: function (data) {
                    //List all .png file names in the page
                    $(data).find("a:contains(" + fileextension + ")").each(function () {
                        var filename = this.href.replace(window.location.host, "").replace("http://", "");
                        $(".-slide-wrap").append("<img src='" + dir + filename + "'>");
                    });
                }
            });

          $('.directorySlider').directorySlider();
        });
```

##Configuration Options

**animation**
Type of Animation.
```
default: 'fade'
options: 'fade', 'uncover'
```
**speed**
Transition speed in milliseconds.
```
default: 2000       // 2 second transition
options: integer
```
**timeout**
Slide display time.
```
default: 10000      // 10 second image
options: integer
```
