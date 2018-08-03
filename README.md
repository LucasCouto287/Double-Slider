# Double-Slider
Double-Slider ( pure javascript )

js file :
 var minAmount = 200;   // you can change it -> it's minimum number
    var maxAmount = 400;  // you can change it -> it's maximum number
    var dragging = false;
    var minSignOffset = 0;
    var lineDoubleSlider = document.getElementById('lineDoubleSlider'),
      minSign = document.getElementById('minSign'),
      lineDoubleSliderWidth = lineDoubleSlider.offsetWidth,
      lineDoubleSliderLeft = lineDoubleSlider.offsetLeft,
      //lineDoubleSliderRight = lineDoubleSliderLeft + lineDoubleSliderWidth,
      minSignWidth = minSign.offsetWidth,
      maxRight = lineDoubleSliderWidth - minSignWidth;

    // at first show min and max numbers
    document.getElementById('minNumber').innerHTML = minAmount.toString();
    document.getElementById('maxNumber').innerHTML = maxAmount.toString();

    // mousedown -> when mouse is clicked
    minSign.addEventListener('mousedown', function (e) {
      minSignOffset = e.clientX - minSign.offsetLeft;
      dragging = true;
    });

    // mouseup -> when mouse is released
    window.addEventListener('mouseup', function (e) {
      dragging = false;
    });

    // mousemove -> when mouse is moved
    window.addEventListener('mousemove', function (e) {

      if (dragging) {
        var offset = e.clientX - lineDoubleSliderLeft - minSignOffset;
        var fixAccident = maxSign.offsetLeft;
        fixAccident = fixAccident;
        if (offset < 0) {
          var offset = 0;
          document.getElementById('maxSign').style.zIndex = '2'; // fix z-index bug
        }
        else if (offset > fixAccident) {
          var offset = fixAccident;
          document.getElementById('maxSign').style.zIndex = '0'; // fix z-index bug
        }
        // else if(offset > maxRight) {
        //   var offset = maxRight;
        // }
        minSign.style.left = offset + "px";
        var finalNum = (offset * ((maxAmount - minAmount) / maxRight)) + minAmount;
        finalNum = parseInt(finalNum.toString());
        document.getElementById('minNumber').innerHTML = finalNum.toString();
      }
    });


    // define variables for signMax
    var dragging2 = false;
    var minSignOffset2 = 0;
    var lineDoubleSlider2 = document.getElementById('lineDoubleSlider'),
      maxSign = document.getElementById('maxSign'),
      lineDoubleSliderWidth2 = lineDoubleSlider2.offsetWidth,
      lineDoubleSliderLeft2 = lineDoubleSlider2.offsetLeft,
      // lineDoubleSliderRight2 = lineDoubleSliderLeft2 + lineDoubleSliderWidth2,
      minSignWidth2 = maxSign.offsetWidth,
      maxRight2 = lineDoubleSliderWidth2 - minSignWidth2;
    maxSign.style.left = maxRight2 + "px";

    // mousedown -> when mouse is clicked
    maxSign.addEventListener('mousedown', function (e) {
      minSignOffset2 = e.clientX - maxSign.offsetLeft;
      dragging2 = true;
    });

    // mouseup -> when mouse is released
    window.addEventListener('mouseup', function (e) {
      dragging2 = false;
    });

    // mousemove -> when mouse is moved
    window.addEventListener('mousemove', function (e) {
      if (dragging2) {
        var offset2 = e.clientX - lineDoubleSliderLeft2 - minSignOffset2;
        var fixAccident2 = minSign.offsetLeft;
        if (offset2 < fixAccident2) {
          var offset2 = fixAccident2;
          document.getElementById('maxSign').style.zIndex = '2'; // fix z-index bug
        }
        else if (offset2 > maxRight2) {
          var offset2 = maxRight2;
          document.getElementById('maxSign').style.zIndex = '0'; // fix z-index bug
        }
        maxSign.style.left = offset2 + "px";

        var finalNum2 = (offset2 * ((maxAmount - minAmount) / maxRight2)) + minAmount;
        finalNum2 = parseInt(finalNum2.toString());
        document.getElementById("maxNumber").innerHTML = finalNum2.toString();
      }
    });
