# ScrollWithMe
Let an element easily scroll with the user.

> Written by Luuk Walstra
> 
> Discord: Luuk#8524
> 
> Github: [https://github.com/Luuk-Dev](https://github.com/Luuk-Dev)
> 
> Replit: [https://replit.com/@LuukDev](https://replit.com/@LuukDev)
> 
> Repository: [https://github.com/Luuk-Dev/ScrollWithMe](https://github.com/Luuk-Dev/ScrollWithMe)

## How to use
You need to call the ScrollWithMe class in your JavaScript. The class has two parameters. The first one is the element where you want to add the ScrollWithMe effect. This can be the element itself or a string to get the element. The second parameter is the custom options. This is an object with the following options:

- startAt: From which height (in pixels) the element should scroll with the user. Default is `0`.
- endAt: From which height (in pixels) the element should stop scrolling with the user. Default is `Infinity`.
- setTop: How far away the element should be away from the top (in pixels).
- callback: An object with callbacks which should get fired at some point.
   - onscroll: Gets fired when the element starts scrolling with the user.
   - onend: Gets fired when the element stops scrolling with the user.

## Demo
Watch a live demo [here](https://scrollwithme.luukdev.repl.co)

## Example
```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width">
    <title>ScrollWithMe</title>
    <style type="text/css">
    html, body{
      margin: 0;
      padding: 0;
      font-family: Arial;
      height: 300vh;
    }
    .huts{
      top: 0;
      height: 100vh;
      background-color: blue;
      width: auto;
      padding: 10px;
    }
    .scroll-with-me{
      position: absolute;
      top: 400px;
      width: 300px;
      height: 250px;
      left: 50px;
      background-color: red;
      padding: 20px;
    }
    </style>
    <script src="https://scrollwithme.luukdev.repl.co/ScrollWithMe.js" type="text/javascript"></script>
  </head>
  <body>
    <div class="huts">
      <h2>Some text over here</h2>
    </div>
    <div class="scroll-with-me">
      <h2 id="some-text">I can scroll with you!</h2>
    </div>
  </body>
  <script type="text/javascript">
    (() => {
      const el = document.querySelector(`.scroll-with-me`);
      const sometext = el.querySelector(`#some-text`);
      new ScrollWithMe(el, {
        startAt: 300,
        endAt: 900,
        setTop: 100,
        callback: {
          onscroll: () => {
            sometext.innerHTML = `WOW! I am scrolling with you!`;
          },
          onend: () => {
            sometext.innerHTML = `I can scroll with you!`;
          }
        }
      });
    })();
  </script>
</html>
```
