..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: hangman-
   :start: 1

Hangman Project
===============

.. activecode:: ps_7_hangman_base
   :language: python

   In the next few questions, you’ll build components and then a complete program that lets people play Hangman. Below is an image from the middle of a game...

   .. image:: Figures/HangmanSample.JPG

   See the flow chart below for a better understanding of what's happening in the code for the Hangman game overall.

   .. image:: Figures/HangmanFlowchart.jpg

   Your first task is just to understand the logic of the program, by matching up elements of the flow chart above with elements of the code below. In later problems, you'll fill in a few details that aren't fully implemented here.

   For this question, write which lines of code go with which lines of the flow chart box, by answering the questions in comments at the bottom of this activecode box.

   .. note::

      You may find it helpful to run this program in order to understand it. It will tell you feedback about your last guess, but won't tell you where the correct letters were or how much health you have, and it won't stop if you guess all the letters, so you can't *really* play with this version of the code. Allowing the game to do those things is what you'll do in later problems!

   ~~~~
   def blanked(word, guesses):
       return "blanked word"

   def health_prompt(x, y):
       return "health prompt"

   def game_state_prompt(txt ="Nothing", h = 6, m_h = 6, word = "HELLO", guesses = ""):
       res = "\n" + txt + "\n"
       res = res + health_prompt(h, m_h) + "\n"
       if guesses != "":
           res = res + "Guesses so far: " + guesses.upper() + "\n"
       else:
           res = res + "No guesses so far" + "\n"
       res = res + "Word: " + blanked(word, guesses) + "\n"

       return(res)

   def main():
       max_health = 3
       health = max_health
       secret_word = input("What's the word to guess? (Don't let the player see it!)")
       secret_word = secret_word.upper() # everything in all capitals to avoid confusion
       guesses_so_far = ""
       game_over = False

       feedback = "let's get started"

       # Now interactively ask the user to guess
       while not game_over:
           prompt = game_state_prompt(feedback, health, max_health, secret_word, guesses_so_far)
           next_guess = input(prompt)
           next_guess = next_guess.upper()
           feedback = ""
           if len(next_guess) != 1:
               feedback = "I only understand single letter guesses. Please try again."
           elif next_guess in guesses_so_far:
               feedback = "You already guessed that"
           else:
               guesses_so_far = guesses_so_far + next_guess
               if next_guess in secret_word:
                   if blanked(secret_word, guesses_so_far) == secret_word:
                       feedback = "Congratulations"
                       game_over = True
                   else:
                       feedback = "Yes, that letter is in the word"
               else: # next_guess is not in the word secret_word
                   feedback = "Sorry, " + next_guess + " is not in the word."
                   health = health - 1
                   if health <= 0:
                       feedback = " Waah, waah, waah. Game over."
                       game_over= True

       print(feedback)
       print("The word was..." + secret_word)

   import sys #don't worry about this line; you'll understand it next week
   sys.setExecutionLimit(60000)     # let the game take up to a minute, 60 * 1000 milliseconds
   main()

.. activecode:: ps_7_5

   Answer the questions in comments below. (The answers should be a number that corresponds to a line of code in the Hangman game code above!)
   ~~~~

   #What line(s) of code in the above code window do what's mentioned in the flowchart's Box 1?


   #What line(s) of code do what's mentioned in Box 2?


   #What line(s) of code do what's mentioned in Box 3?


   #What line(s) of code do what's mentioned in Box 4?


   #What line(s) of code do what's mentioned in Box 5?


   #What line(s) of code do what's mentioned in Box 6?


   #What line(s) of code do what's mentioned in Box 7?


   #What line(s) of code do what's mentioned in Box 8?


   #What line(s) of code do what's mentioned in Box 9?


   #What line(s) of code do what's mentioned in Box 10?


   #What line(s) of code do what's mentioned in Box 11?


.. activecode:: ps_7_6
   :language: python

   The next task you have is to create a correct version of the ``blanked`` function. It should take 2 inputs: a word, and a string of the letters that have been guessed already. The second argument should be optional: if omitted, then no letters have guessed yet.

   It should return a string with the same number of characters as the word, but with the unrevealed characters replaced by underscores (``_``).

   **HINT:** Iterate through the letters in the word, accumulating characters as you go. If you try to iterate through the guesses, it's harder.

   ~~~~
   # Sample calls to this function
   # (Remember, these won't work until you define the function blanked)
   print(blanked("hello", "elj"))
   #should output _ell_
   print(blanked("almost","amsvr"))
   # should output a_m_s_
   print(blanked("almost"))
   # should output ______


   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(blanked('hello', 'elj'), "_ell_", "testing blanking of hello when e,l, and j have been guessed.")
         self.assertEqual(blanked('hello', ''), '_____', "testing blanking of hello when nothing has been guessed.")
         self.assertEqual(blanked('ground', 'rn'), '_r__n_', "testing blanking of ground when r and n have been guessed.")
         self.assertEqual(blanked('almost', 'vrnalmqpost'), 'almost', "testing blanking of almost when all the letters have been guessed.")
         self.assertEqual(blanked('almost'), '______', "testing blanking of almost when no second argument is provided.")

   myTests().main()


.. activecode:: ps_7_7
   :language: python

   Now you have to create a good version of the ``health_prompt`` function:

   Define a function called ``health_prompt``. The first parameter should be the current health the player has (an integer), and the second parameter should be the maximum health a player can have (an integer).

   The function should return a string with ``+`` signs for the current health, and ``-`` signs for the health that has been lost so far.

   ~~~~
   # Define your function here.




   # Sample invocations of the function.

   print(health_prompt(3, 7))
   #this statement should produce the output
   # +++----

   print(health_prompt(0, 4))
   #this statement should produce the output
   # ----

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(health_prompt(3,7), "+++----", "Testing health_prompt(3,7)")
         self.assertEqual(health_prompt(0,4), "----", "Testing health_prompt(0,4)")
         self.assertEqual(health_prompt(5,5), "+++++", "Testing health_prompt(5,5)")

   myTests().main()


.. activecode:: ps_7_8

    You now have all the pieces of a fully functioning hangman program! Copy your health_prompt and blanked functions into the  activecode box and also all of the base hangman code. Then try running it.

    To get yourself more familiar with jupyter notebooks, also add your health_prompt and blanked functions  as new cells in the PS7 jupyter notebook. Run the hangman program from there, and make sure that all of the tests at the bottom of that notebook pass.


.. activecode:: ps_7_dyu

    Write code and/or a python comment that demonstrates your understanding of the material in this problem set. Be sure to click "Run" even if it's just a comment, because that's what will save it so that we can grade it. This assignment requires effort and demonstration of true understanding and will be evaluated carefully (this does not mean it needs to be long, just clear and accurate. In fact, it should be brief; ideally just 2-3 sentences!).

    Your submission must be your own work (i.e., don't collaborate with other students on this problem even if you've been collaborating with them on the rest of the problems), and you must credit any resources you reference (you do not need to reference any).

    After grading, you will receive a response, in a comment, from an instructor, which will be visible on this assignment page. If you do not receive full credit for this problem, you may initiate a conversation with your GSI by adding a comment *on Canvas* on the graded assignment. If you want to update code here and refer to it in your Canvas comment, you can do that. There may be several rounds of comments and responses on Canvas before the GSI is satisfied that you have demonstrated a correct understanding. You must respond to the GSI within 48 hours in order for that conversation to remain "open". When the GSI is satisfied, they will update your grade accordingly.

    ~~~~


