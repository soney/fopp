..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, Dario Mitchell, Pei-Yao Hung, and Steve Oney.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: seqmut-9-
   :start: 1

F-Strings
=========

The string ``.format()`` method allows us to format a string in a way that is similar to fill-in-the-blank.
The return value of ``.format()`` is a string that can then be used and displayed using the ``print()`` function.

Another (more modern) approach is to use an **f-string**.
F-strings are a Python-specific way of formatting a string (using a fill-in-the-blank mechanism like ``.format()``) without using a separate method call.

Let's revisit the example we used before. Pay attention to how the same outcome can be obtained first with the ``.format()`` method and then with the f-string approach.

.. activecode:: ac8_9_1

    name = "Peter Huang"
    score = "96.75"
    print("Hello {}. Your score is {}.".format(name, score))
    print(f"Hello {name}. Your score is {score}.")

In the above example, using the *f-strings* approach, we literally fill each placeholder (i.e., each pair of braces) with a variable whose value we want to display.

Note that to use an f-string, we must type the character "f" before the string content. We can then enter expressions within the string between curly braces ({}). We can use almost any values or expression inside the braces. It can be: a value; a variable that contains or references a value; an arithmetic expression; a string expression;  a method call that returns a value such as a string or a number. See the following examples that show how we can use values, variables, and different expressions inside the braces. Each ``print()`` statement produces the exact same output.

We can use values directly inside the braces.

.. activecode:: ac8_9_13

    first_name = "Peter"
    last_name = "Huang"
    score = 96.75
    print(f"Hello {'Peter Huang'}. Your score is {96.75}.")

We can use expressions (i.e., string operations and arithmetic operations) directly inside the braces.

.. activecode:: ac8_9_14

    first_name = "Peter"
    last_name = "Huang"
    score = 96.75
    print(f"Hello {'Peter' + ' ' + 'Huang'}. Your score is {90 + 6.75}.")

We can use expressions consisting of variables directly inside the braces.

.. activecode:: ac8_9_15

    first_name = "Peter"
    last_name = "Huang"
    score = 96.75
    print(f"Hello {first_name} {last_name}. Your score is {score}.")


We can call a method (also a type of expression) directly inside the braces. As an extreme example, we can even use the ``format`` method, which returns a string, inside *f-strings*. Note that in this example, we use ``max()``, a built-in method that will return the highest value among the values we provide. Since the value ``96.75`` is assigned to the variable ``score`` and is greater than ``60``, the value returned from ``max(score, 60)`` will be ``96.75``.

.. activecode:: ac8_9_16

    first_name = "Peter"
    last_name = "Huang"
    score = 96.75
    print(f"Hello {'{} {}'.format(first_name, last_name)}. Your score is {max(score, 60)}.")


Similar to the ``format()`` approach, we can use format specifiers (e.g., ``:.2f``) to further fine-tune the value being displayed. For instance, if we want to display a floating-point number with one decimal place, we can use ``:.1f`` inside the braces and after the expression. The example below shows how we can apply the format specifiers with both a variable and a method call inside the braces.

.. activecode:: ac8_9_17

    first_name = "Peter"
    last_name = "Huang"
    score = 96.75
    print(f"Hello {'{} {}'.format(first_name, last_name)}. Your score is {score:.1f}.")
    print(f"Hello {'{} {}'.format(first_name, last_name)}. Your score is {max(score, 60):.1f}.")

At this point, we might ask, is *f-strings* the best method to use for formatting strings? Well, as usual, it depends. Here we describe two caveats to keep in mind when using f-strings. 

First, we need to pay attention to using quotes inside *f-strings*. If we use quotes, that means we are embedding quotes inside the quotes required by f-strings. If we use the same type of quotes, such as double quotes, the Python interpreter will have trouble determining how these double-quotes are paired with one another, and it will have trouble understanding what we want a computer to do. A solution is to use a different kind of quotes, such as single quotes, so that the Python interpreter knows how to pair those quotes (e.g., double with double, single with single) and properly execute our code. Take a look at the following example, which produces an error, and see if we can fix the bug to have the correct output similar to the previous example (hint: replacing a pair of double quotes).

.. activecode:: ac8_9_18

    first_name = "Peter"
    last_name = "Huang"
    score = 96.75
    print(f"Hello {first_name + " " + last_name}. Your score is {score}.")

Note that, as the ``format()`` approach does not require using expressions directly inside the *format string*, we don't have to worry about the quotes-inside-quotes problem when using the ``format()`` approach. The following example uses double quotes throughout.

.. activecode:: ac8_9_19

    first_name = "Peter"
    last_name = "Huang"
    score = 96.75
    print("Hello {}. Your score is {}.".format(first_name + " " + last_name, score))


Second, similar to the ``format()`` approach, we need to pay attention when using braces inside *f-string*, as *f-strings* already require the use of braces as placeholders. To display a pair of braces inside f-strings, we need to double the pair of braces. If we need double braces in the output, we need to double the pair of double braces, namely four pairs.

Again, since the ``format()`` approach does not require using expressions directly inside the *format string*, we can avoid the braces-inside-braces problem as we described above. As we can see in the following example, since we provide two strings as arguments to ``format()``, we can include the braces as part of the strings for them to be displayed in the output.

.. activecode:: ac8_9_22

    print("{} {}".format("{I need braces.}", "{I also need braces.}"))

In summary, different string formatting methods have their own advantages and disadvantages in terms of readability and caveats. There are other considerations (e.g., speed), but we won't discuss them here. One of the potential solutions to mitigate the issues raised above is to pre-calculate the values using different expressions and store them in variables. We can then use mostly these variables with ``format()`` or *f-strings*, without using complex expressions directly. See the example inside the question below.

We have introduced various string methods in Python. Use the following question to check if you understand what has been discussed.

.. mchoice:: question8_8_5
   :answer_a: The percentage of R/r (all cases) in the sentence: 6.061%. The number of r: 4.
   :answer_b: The number of r: 4. The percentage of R/r (all cases) in the sentence: 6.061%.
   :answer_c: The percentage of R/r (all cases) in the sentence: 6.06%. The number of r: 3.
   :answer_d: The number of r: 3. The percentage of R/r (all cases) in the sentence: 6.06%.
   :correct: d
   :feedback_a: Check the decimal places, sentence order, and how many ‘r’ there are.
   :feedback_b: Check the decimal places and how many ‘r’ there are.
   :feedback_c: Check the sentence order.
   :feedback_d: Yes, the numbers and the order of sentences are correct.
   :practice: T

   What is printed by the following statements?

   .. code-block:: python

        s = "I saw the movie, Mary Poppins Returns, and I thought it was great."

        # all the expressions
        r_count = s.count("r")
        all_case_r_count = s.lower().count("r")
        r_precentage = all_case_r_count/len(s) * 100

        # use mostly variables inside f-strings or format()
        first_str = f"The number of r: {r_count}."
        second_str = "The percentage of R/r (all cases) in the sentence: {:.2f}%.".format(r_precentage)

        # display
        print( first_str + " " + second_str)