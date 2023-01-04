<link rel ="stylesheet" href="style2.css">
  <div class = "heading">
    <h1>Hangman in Python</h1>
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

Hangman is a very popular and classic letter guessing game which originated in the 17th century and since then it has remained a part of our growing up. 

Let us write some code in Python to create our own simple version of this letter guessing game. 

First and foremost, let us **import random** which is a library in Python and it will help choose a random word from a list of words that we will provide in our code.

```{Python}
  import random
```

Let us now provide a list of words and then let Python choose any random word for the guessing game.

```{Python}
  words = ['python','programming','ubuntu','linux','strawberry','watermelon','chocolate','bitcoin','technology','cybersecurity','mathematics','english','physics','universe','database']
  secret = random.choice(words)
```

We need a few more variables before we get started:

```{Python}
  used = [] # We need this list to keep a track of letters that have been used already.
  display = [] # We need this list to display hidden and revealed letters
  lives = 7 # We can give 7 chances to the player to guess a word
```

Let us now populate the **display[]** list with as many hyphens as there are letters in the secret word. The secret word will be displayed as all hyphens when the game starts.

```{Python}
  for i in range(len(secret)):
    display.append("_")
```

To start the game, we will place all game logic inside a *while True* loop.

The player will see the number of lives as 7 and all hyphens in the secret word when the game starts. The user will then be asked to enter one letter as his first guess.

We have also used a variable **found** with its initial value as False. We will use this variable later to keep track of the number of lives remaining. 

```{Python}
  print("Remaining Lives: ",lives)
  print(" ".join(display))
  guess = input("enter your guess")
  found = False
```

When the player enters a letter as their guess, we need to check two things:

1. If this letter was already guessed by the user earlier, then we need to display a message telling them that this letter has been used before.
2. Secondly, we need to see if this letter matches with any letter in the secret word or not. If a match is found, this letter will be added to the **used[]**list and we will also add this letter to the **display[]** list at the same position as it is in the secret word so that in the next try, the user sees this letter at its right position and other letters will remain hidden. We will also update the value of **found** to **True** when a match is found.
  
The code below does what we have described above:

```{Python}
  for count in range(len(secret)):
    if guess == secret[count]:
      used.append(guess)
      display[count] = guess
      found = True
```
  
What if the guessed letter does not match any letter in the secret word? In that case, we will deduct one life from the variable **lives**.

```{Python}
  if found == False:
    lives -= 1
  print(" ".join(display))
```

The code that we wrote above is sufficient enough to simulate the game. However, we need a condition to break out of the loop and end the game. 

There are two exit conditions in this game:

1. If the player has used up all the lives and has not been able to guess the correct word.
   
2. If the player has been able to guess the correct word within the given number of chances. 

Let us add these two into our code:

```{Python}
  if lives > 0 and "_" not in display:
    print("Well done")
    break
  if lives <=0:
    print("Well tried")
    break
```

Lastly, outside the loop, we will simply print the secret word.

```{Python}
  print("The secret word was: ",secret)
```

[The whole code can be found here](https://github.com/Shelly1986/hangman.git)




