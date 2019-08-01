..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: func-15-
   :start: 1

Chapter Assessment
==================

.. activecode:: ac11_15_1
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Functions/Returningavaluefromafunction

   Write a function called ``int_return`` that takes an integer as input and returns the same integer.
   ~~~~
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(int_return(10), 10, "Testing that function int_return(10) returns 10")

   myTests().main()

.. activecode:: ac11_15_2
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Functions/Returningavaluefromafunction

   Write a function called ``add`` that takes any number as its input and returns that sum with 2 added.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testTwo(self):
         self.assertEqual(add(-2), 0, "Testing that add(-2) returns 0")
         self.assertEqual(add(6), 8, "Testing that add(6) returns 8")
         self.assertEqual(add(4), 6, "Testing that add(4) returns 6")

   myTests().main()

.. activecode:: ac11_15_3
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Functions/Returningavaluefromafunction

   Write a function called ``change`` that takes any string, adds "Nice to meet you!" to the end of the argument given, and returns that new string.
   ~~~~
   
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testThree(self):
         self.assertEqual(change("I'm Bob. "), "I'm Bob. Nice to meet you!", "Tests that change('I'm Bob. '') returns 'I'm Bob. Nice to meet you!'")   
         self.assertEqual(change(""), "Nice to meet you!", "Tests that change() returns 'Nice to meet you!'")

   myTests().main()

.. activecode:: ac11_15_4
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Functions/Afunctionthataccumulates

   Write a function, ``accum``, that takes a list of integers as input and returns the sum of those integers.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testFourA(self):
         self.assertEqual(accum([5]), 5, "Tests that accum([5]) returns 5")
         self.assertEqual(accum([]), 0, "Tests that accum([]) returns 0")
         self.assertEqual(accum([2,4,6,8]), 20, "Tests that accum([2,4,6,8]) returns 20")

   myTests().main()

.. activecode:: ac11_15_5
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Functions/Returningavaluefromafunction

   Write a function, ``length``, that takes in a list as the input. If the length of the list is greater than or equal to 5, return "Longer than 5". If the length is less than 5, return "Less than 5".
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testFive(self):
         self.assertEqual(length([]), "Less than 5", "Tests that length([]) returns 'Less than 5'")
         self.assertEqual(length([2, 2]), "Less than 5", "Tests that length([2, 2]) returns 'Less than 5'")
         self.assertEqual(length([4, 4, 4, 3, 5, 6, 7, 8, 9]), "Longer than 5", "Tests that length([4, 4, 4, 3, 5, 6, 7, 8, 9]) returns 'Longer than 5'")
         self.assertEqual(length([1, 1, 1, 1, 1]), "Longer than 5", "Tests that length([1, 1, 1, 1, 1]) returns 'Longer than 5'")

   myTests().main()

.. activecode:: ac11_15_6
   :language: python
   :autograde: unittest
   :practice: T
   :topics: Functions/Functionscancallotherfunctions

   You will need to write two functions for this problem. The first function, ``divide`` that takes in any number and returns that same number divided by 2. The second function called ``sum`` should take any number, divide it by 2, and add 6. It should return this new number. You should call the ``divide`` function within the ``sum`` function. Do not worry about decimals.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testSixA(self):
         self.assertEqual(divide(4), 2, "Tests that divide(4) returns 2")
      def testSixB(self):
         self.assertEqual(sum(4), 8, "Tests that sum(4) returns 8")
         self.assertEqual(sum(2), 7, "Tests that sum(2) returns 7")
         self.assertEqual(sum(-6), 3, "Tests that sum(-6) returns 3")
         self.assertEqual(sum(0), 6, "Tests that sum(0) returns 6")

   myTests().main()


.. activecode:: ps_06_DYU
    :language: python

    Write code and/or a python comment that demonstrates your understanding of the material in this problem set. Be sure to click "Run" even if it's just a comment, because that's what will save it so that we can grade it. This assignment requires effort and demonstration of true understanding and will be evaluated carefully (this does not mean it needs to be long, just clear and accurate. In fact, it should be brief; ideally just 2-3 sentences!).

    Your submission must be your own work (i.e., don't collaborate with other students on this problem even if you've been collaborating with them on the rest of the problems), and you must credit any resources you reference (you do not need to reference any).

    After grading, you will receive a response, in a comment, from an instructor, which will be visible on this assignment page. If you do not receive full credit for this problem, you may initiate a conversation with your GSI by adding a comment *on Canvas* on the graded assignment. If you want to update code here and refer to it in your Canvas comment, you can do that. There may be several rounds of comments and responses on Canvas before the GSI is satisfied that you have demonstrated a correct understanding. You must respond to the GSI within 48 hours in order for that conversation to remain "open". When the GSI is satisfied, they will update your grade accordingly.

    ~~~~
