<link rel ="stylesheet" href="style2.css">
  <div class = "heading">
    <h1>Cookie Clicker Game</h1>
  </div>
  <nav class = "topbar">
    <button onclick="window.location.href='index.html';">About</button>
    <div class="dropdown">
      <button class = "dropbtn">Portfolio</button>
        <div class="dropdown-content">
          <a href="Python.html">Python</a>
          <a href="Javascript.html">Javascript</a>
        </div>
    </div>
    <button onclick="window.open('https://www.youtube.com/@shellysachdev/videos', '_blank')">YouTube</button>
  </nav>

Did the title remind you of those nutty, mushy, assorted, delicious, freshly baked cookies?

Well, yes we did design a game around those cookies. But, hard luck :( We only get to click on those cookies to earn points but not eat them. 

Cookie Clicker is everyone's favorite. It's addictive. The hunger to earn more cookies never ends even if the fingers hurt. 

With Year 12, we designed a mini version of the cookie clicker and once again, it was fun-based learning. 

Let us look at the code:


## HTML

```{HTML}
  <html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="style.css">
    <title>Cookie Clicker</title>
    <script src="script.js" defer></script>
  </head>
  <body>
    <img src="Cookie.png" id="cookie">
    <br>
    <h1>Score: <span id="score"></span></h1>
    <br>
    <img src=" " id="grandma">
  </body>
  </html>
```

The body section of the webpage will have an image of a cookie and a space to display the clicks as the Score.

Notice that we have another image which has the **source(src)** tag blank. This image only has an **id as grandma**. We have consciously kept src for this image blank because we will display an image of a grandma for clicks only when we earn 100 points from the first image of a cookie. 

## CSS

The stylesheet too is going to have bare minimum code because we want the page to only have a clickable cookie and a score to begin with. 

```{CSS}
  body{
  background-color: aqua;
  }

  img{
    width: 200px;
    height: 200px;
  }

  img:active{
    transform: scale(0.5);
  }
```

Notice that we have set the cookie width and height to be 200 pixels. However, once the image is clicked, we want the image to scale down to 50% and then get back to its normal size. The **transform: scale(0.5)** can achieve this effect.

## Javascript Code

Let us now look at the Javascript code. 

First and foremost, we will set the score to 0.

```{Javascript}
  var score = 0;
```

Second of all, let us pull in the **cookie image** and the **grandma image** by their respective ids. 

```{Javascript}
  const cookie = document.getElementById("cookie");
  const grandma = document.getElementById("grandma");
```

Next, we want to listen to the clicks on the Cookie image and increment the score by 1. The score should be constanly updated on our webpage on the designated space that we created using the **span** tags. Let us add that to our code now.

```{Javascript}
  cookie.addEventListener('click',()=>{
  score = score + 1;
  document.getElementById('score').textContent = score;
```

In our cookie clicker game, we want that once the clicks on the cookie image reach 50, we want grandma to appear and bake more cookies for us. So, we will use an **if statement** to check if the score has reached 50 points and if it has, then let us set the **src tag** for the image with id as grandma to an actual image of a grandma which you can download off the web.

```{Javascript}
  if (score==50){
    grandma.src="grandma.png";
```

Once the grandma appears on our webpage, we must add an Event Listener on this new image too which listens to clicks and increments the score by 5 points. 

```{Javascript}
  grandma.addEventListener('click',(event)=>{
    event.stopImmediatePropagation();
    score = score + 5;
    document.getElementById('score').textContent = score; 
```

Please note that the first line of code inside the Click function is **event.stopImmediatePropagation()**. This function is often used to fix any strange behavior on your webpage such as one click of a button being read as multiple clicks and score getting updated by a number much bigger than 5 or something of this sort. This function stops the 'Click' event being propagated any further and counts one click as one score point.

A usual cookie cliker game is is endless. You can add as many levels and as many objects to it for extending it further.

[The entire code is here](https://github.com/Shelly1986/cookieclicker.git)






  
