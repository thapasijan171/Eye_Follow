# Animated Eye with HTML, CSS, and JS

This markdown file provides an example of an animated eye created using HTML, CSS, and JavaScript. Let's discuss the key components of the code:

## HTML Structure

The HTML structure is straightforward, consisting of a container div for the eye with nested elements for the eye and pupil.

```html
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Eyes Following Mouse Cursor</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <div class="emoji-face">
      <div class="eyes">
        <div class="eye"></div>
        <div class="eye"></div>
      </div>
    </div>

    <script src="app.js"></script>
  </body>
</html>
```
## CSS Styling
The CSS styles define the appearance of the eye and pupil. It includes positioning, dimensions, border-radius for a circular shape, and transitions for a smooth animation.

```CSS
body {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  background-color: blueviolet;
}

.emoji-face {
  position: relative;
  width: 300px;
  height: 300px;
  background: rgba(255, 255, 0, 0.683);
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  transition: 0.5s;
}

.emoji-face::before {
  content: "";
  top: 180px;
  position: absolute;
  width: 150px;
  height: 70px;
  background: crimson;
  border-bottom-left-radius: 70px;
  border-bottom-right-radius: 70px;
  transition: 0.5s;
}

.eyes {
  position: relative;
  top: -40px;
  display: flex;
}

.eyes .eye {
  position: relative;
  width: 80px;
  height: 80px;
  display: block;
  background: white;
  border-radius: 50%;
  margin: 0 15px;
}

.eyes .eye::before {
  content: "";
  position: absolute;
  top: 50%;
  left: 25px;
  transform: translate(-50%, -50%);
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background: black;
}
```

## JavaScript Interaction
The JavaScript code adds interactivity to the eye. It tracks the mouse movement and adjusts the position of the pupil accordingly. The mousemove event listener calculates the angle between the mouse position and the eye center, then updates the pupil's position.
```js
document.querySelector("body").addEventListener("mousemove", eyeball);

function eyeball() {
  let eyes = document.querySelectorAll(".eye");
  eyes.forEach((eye) => {
    let x = eye.getBoundingClientRect().left + eye.clientWidth / 2;
    let y = eye.getBoundingClientRect().top + eye.clientHeight / 2;

    let radian = Math.atan2(event.pageX - x, event.pageY - y);
    let rotate = radian * (180 / Math.PI) * -1 + 270;
    eye.style.transform = `rotate(${rotate}deg)`;
  });
}
```
