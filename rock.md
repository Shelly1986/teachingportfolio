<link rel ="stylesheet" href="style2.css">
  <div class = "heading">
    <h1>Rock Paper Scissors</h1>
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

  [Rock Paper Scissors](https://en.wikipedia.org/wiki/Rock_paper_scissors) is a fun game which is played between two players using their hands. There are only three simple rules to the game:
  
  1. Rock wins over scissors because rock is powerful and it can smash the scissors.
  2. Paper wins over rock as it can cover the rock.
  3. Scissors wins over paper as it has the power to cut the paper.
   
  As a class activity in Year 12, we simulated this game between a player and the computer using simple HTML, CSS and Javascript. 

  We kept the HTML and CSS to a bare minimum in this project because the main focus was to start learning Javascript.

  Our main webpage looked like the one below. It had a title on top, three buttons for the player to choose from and some labels which display the chosen options. The moment player presses a button, his choice as well as computer's choice is displayed and the winner is also displayed. 

## HTML Code

  ```{HTML}
    <!DOCTYPE html>
    <html lang="en">
    <head>
      <meta charset="UTF-8">
      <meta http-equiv="X-UA-Compatible" content="IE=edge">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>Document</title>
    <link rel="stylesheet" href="style.css">
    </head>
  ```

The above code is called the **boilerplate** code which basically tells the browser that we are working in HTML and the content of the page needs to be rendered as a web page. If you are using an editor such as VS Code and you have the [Emmet](https://code.visualstudio.com/docs/editor/emmet) enabled, you can get the above code by simply typing an exclamation mark followed by Return. 

Do not forget to link your .css and .js file in the boilerplate else the code will not work.

In the main body section, you will see two divisions created using the <div> tag. In the first <div> with class **division1**, we have the main title and the three buttons and in **division2**, we have the labels which will be updated when any button is pressed. Usually we attach different divisions with different classes if we are planning to style them or program them in different ways in our projects. A class is like an official name of an element on a web page and we pull these elements into our code by calling them by their class names. 

### Code for the Body Section

```{HTML}
  <body>
  <h1>Rock Paper Scissors</h1>
  <div class = "division1">
      <button class = "button" id="Rock">Rock</button>
      <button class = "button" id="Paper">Paper</button>
      <button class = "button" id="Scissors">Scissors</button>
  </div>
  <div class = "division2">
      <h2>User's Choice: <span id="span1"></span></h2>
      <h2>Computer's Choice: <span id="span2"></span></h2>
      <h2>Winner: <span id="span3"></span></h2>
  </div>
  <script src = "script.js"></script>
  </body>
  </html>
```

In the above code , as you would have noticed, each button has a *class* as well as an *id*. The class for all the three buttons is the same but their ids are unique. This has been done because we wanted to keep the styling of the buttons same i.e. their width, height, background color, font style etc. and so all these buttons can be styled as a group of buttons. However, all three buttons when pressed would produce different results and these results would be used to figure out the winner. This is why their ids are unique. 
A class is basically a surname which you inherit from your family while your first name is unique to you. 

In division2 class, we have used this format **<h2>User's Choice: <span id="span1"></span></h2>** for each of the labels. The <h2> created a heading of size 2 and then we have created some space using '<span>' where the player's choice would be displayed when they press any of the three buttons. Since this space needs to be updated in our web page, we have given it a unique id *span1* so that we can identify which part of the web page will hold the player's choice. Computer's choice is therefore *span2* and winner would be displayed in the place which has the id *span3*.


## CSS Code

Once you have the HTML code, you would be able to see the basic elements on your web page minus the colors and the font styles. 

Let us add some basic styling to our webpage.

### Add some background-color and fonts

```{CSS}
  body 
  {
  background-color: aqua;
  font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
  font-size: large;
  }
```

### Align the top heading in center

```{CSS}
  h1 
  {
  text-align: center;
  }
```

### Align the heading, buttons and labels in center

```{CSS}
  .division1, .division2
  {
  text-align: center;
  }
```

### Styling the buttons

```{CSS}
  .button 
  {
  font-size: 20px;
  color: blue;
  background-color:chartreuse;
  }
```

## Javascript Code

Now that we have all the elements at the right positions on our webpage, let us add some code to make the game work.

First of all, we will use a method in Javascript which can get all the buttons from our HTML code and put them all in an array. We need to do this because when a button is pressed, we need to identify the id of it hence we need some way to iterate over an array which has these buttons. 

```{Javascript}
  const btns = document.getElementsByClassName("button")
```

The above line of code looks for all buttons which have a class values as *button* and it places them all in a constant array called *btns*

Next, we will use a **for** loop which will be able to iterate over this *btns* list and listen for button presses. 

```{Javascript}
  for (i of btns) {
    i.addEventListener("click", function () {
    /*Adds the id of the clicked button into variable player_choice*/
      var player_choice = this.id;
      document.getElementById("span1").innerText = player_choice;
```

The above code use a variable *i* as an iterator and we added an Event Listener on it so that it can listen to button clicks and places the id of the clicked button into a variable **player_choice**. Once we know what the player has choosen out of Rock, Paper or Scissors, we update it on the empty space on our webpage which has the id **span1**.

We have taken care of the player's choice but since the game is against the computer, we need to randomize the computer's choice. 

```{Javascript}
  var computer_choice = Math.floor(Math.random()*3 + 1)
  if (computer_choice == 1){
    document.getElementById("span2").innerText = "Rock"
  } else if(computer_choice == 2){
    document.getElementById("span2").innerText = "Paper"
  }
    else{
    document.getElementById("span2").innerText = "Scisccors"
  }
```
In the above code, we have used the Math.random() function of Javascript which will randomly choose numbers between 0 and 3. However, Math.random() can even choose decimal values which need to be rounded off to get an integer result. Hence, we also used Math.floor() and added 1 to the result so that we strictly get integer values 1,2 or 3 where the value of 1 means Rock, 2 means Paper and 3 signifies Scissors. 

Once we have an integer value placed in the variable **computer_choice**, the next lines of code are simply if-else statements which place the right text in the space designated for computer's choice i.e. the empty space with id **span2**

Lastly, we need a few more if-else statements to compare the values in **player's choice** and **computer_choice** to update the winner in the empty space which has the id **span3**

```{Javascript}
    /*Compare user and computer choices to declare the winner*/
          if((player_choice=="Rock" && computer_choice==1)||(player_choice=="Paper" && computer_choice==2) ||(player_choice=="Scissors" && computer_choice==3))
          {
            document.getElementById("span3").innerText ="Draw"
          } else if((player_choice=="Rock" && computer_choice==2) || 
          (player_choice == "Paper" && computer_choice==3)||
          (player_choice == "Scissors" && computer_choice==1))
          {
            document.getElementById("span3").innerText ="Computer Wins"
          }
          else {
            document.getElementById("span3").innerText ="User Wins"
          }
        })
      }
```

The whole project containing the HTML, CSS and Javascript can be found [here](https://github.com/Shelly1986/rockpaperscissors.git)


