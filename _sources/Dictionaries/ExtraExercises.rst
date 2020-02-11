Extra Exercises
===============

.. activecode:: dict_extra_exercises_state_capitals
    :language: python
    :autograde: unittest
    :practice: T
    :topics: Dictionaries/intro-Dictionaries

    We have provided a list of tuples called ``state_capitals``. The first item in every tuple is the name of a US state and the second item in that tuple is the capital of that state. Write code that converts this data structure into a dictionary where the keys are state names and the values are state capitals. Assign the result to the variables ``capitals_dict``.
    ~~~~
    state_capitals = [ ('Michigan', 'Lansing'), ('Massachusetts', 'Boston'), ('Pennsylvania', 'Harrisburg'), ('New York', 'Albany')]
    =====
    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):
        def testOne(self):
            self.assertEqual(capitals_dict, {'Michigan': 'Lansing', 'Massachusetts': 'Boston', 'Pennsylvania': 'Harrisburg', 'New York': 'Albany' }, "Testing that the capitals_dict dictionary has the correct key-value pairs")

    myTests().main()

.. activecode:: dict_extra_exercises_calories
    :language: python
    :autograde: unittest
    :practice: T
    :topics: Dictionaries/intro-Dictionaries

    The dictionary ``calories`` contains calorie totals for different kinds of food. The list ``lunch`` is a list of food items in a meal. Write code that computes the total number of calories in ``lunch`` by adding up the calories associated with every item in the list. Put the result in the variable ``lunch_calories``
    ~~~~
    calories = {
        'pizza slice': 285,
        'french fries': 365,
        'ice cream': 137,
        'pancake': 64,
        'orange': 45,
        'cupcake': 131
    }

    lunch = ['pizza slice', 'orange', 'cupcake', 'cupcake']
    =====
    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):
        def testOne(self):
            self.assertEqual(lunch_calories, 285+45+131*2, "Testing that the lunch_calories has the correct value")

    myTests().main()

.. activecode:: dict_extra_exercises_snowfall
    :language: python
    :autograde: unittest
    :practice: T
    :topics: Dictionaries/intro-Dictionaries

    The dictionary ``snowfall`` maps keys (which represent a given month) to values that represent the amount of snowfall (in inches) for every time it snowed that month. Write code that creates a new dictionary named ``month_total_snowfall`` where the keys are months and the values are floats that represent the **total** snowfall for that month (the sum of the values in ``snowfall`` for that month).

    Then, create a new float called ``snowfall_all_months`` whoes value is the total snowfall for all months.
    ~~~~
    snowfalls = {
        'December': [0.2],
        'January': [1.5, 3, 2, 2.5],
        'February': [7, 2.3, 1.2, 4],
        'March': [1.5, 3, 4],
        'April': [0.2],
    }

    =====
    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):
        def testOne(self):
            answer1 = {k: sum(v) for (k,v) in snowfalls.items()}
            self.assertEqual(month_total_snowfall, answer1, "Testing that month_total_snowfall has the correct keys and values")
            answer2 = sum(list(answer1.values()))
            self.assertEqual(snowfall_all_months, answer2, "Testing that snowfall_all_months has the correct value")

    myTests().main()

.. activecode:: ps_04_umich_schools
    :language: python
    :autograde: unittest
    :practice: T
    :topics: Iteration/TheAccumulatorPatternwithLists

    The dictionary ``umSchools`` maps the names of schools at Michigan to the year they were founded.
    Write code to add the name of every school that was founded in the 20th century (after 1900) into a list ``newer_schools``.

    Hard-coded answers will receive no credit.
    ~~~~
    umSchools = {
      "A. Alfred Taubman College of Architecture & Urban Planning": 1906,
      "College of Engineering": 1854,
      "College of Literature, Science, and the Arts": 1841,
      "Gerald R. Ford School of Public Policy": 1914,
      "Horace H. Rackham School of Graduate Studies": 1912,
      "Penny W. Stamps School of Art & Design": 1974,
      "School of Dentistry": 1875,
      "School of Education": 1921,
      "School of Information": 1996,
      "School of Kinesiology": 1984,
      "School of Law": 1859,
      "School of Medicine": 1850,
      "School of Music, Theatre & Dance": 1880,
      "School of Natural Resources & Environment": 1927,
      "School of Nursing": 1893,
      "School of Pharmacy": 1876,
      "School of Public Health": 1941,
      "School of Social Work": 1951,
      "Stephen M. Ross School of Business": 1924
    }
    =====
    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):
        def testOne(self):
            a = [s for s in umSchools if umSchools[s]>1900]
            self.assertEqual(sorted(newer_schools), sorted(a), "Testing that newer_schools has been set to the correct value")

    myTests().main()

.. activecode:: ps_04_newer_schools
    :language: python
    :autograde: unittest
    :practice: T
    :topics: Iteration/TheAccumulatorPatternwithLists

    The dictionary ``umSchools`` maps the names of schools at Michigan to the year they were founded.
    Write code to add the name of every school that was founded in the 20th century (after 1900) into a list ``newer_schools``.

    Hard-coded answers will receive no credit.
    ~~~~
    umSchools = {
      "A. Alfred Taubman College of Architecture & Urban Planning": 1906,
      "College of Engineering": 1854,
      "College of Literature, Science, and the Arts": 1841,
      "Gerald R. Ford School of Public Policy": 1914,
      "Horace H. Rackham School of Graduate Studies": 1912,
      "Penny W. Stamps School of Art & Design": 1974,
      "School of Dentistry": 1875,
      "School of Education": 1921,
      "School of Information": 1996,
      "School of Kinesiology": 1984,
      "School of Law": 1859,
      "School of Medicine": 1850,
      "School of Music, Theatre & Dance": 1880,
      "School of Natural Resources & Environment": 1927,
      "School of Nursing": 1893,
      "School of Pharmacy": 1876,
      "School of Public Health": 1941,
      "School of Social Work": 1951,
      "Stephen M. Ross School of Business": 1924
    }
    =====
    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):
        def testOne(self):
            a = [s for s in umSchools if umSchools[s]>1900]
            self.assertEqual(sorted(newer_schools), sorted(a), "Testing that newer_schools has been set to the correct value")

    myTests().main()

.. activecode:: ps_04_max_val
    :language: python
    :autograde: unittest
    :practice: T
    :topics: DictionaryAccumulation/AccumulatingaMaximumValue

    The dictionary ``umSchools`` maps the names of schools at Michigan to the year they were founded.
    Write code that determines which school is the oldest and store the name of the school into the variable ``oldest_school``.
    Hard-coded answers will receive no credit.
    ~~~~
    umSchools = {
      "A. Alfred Taubman College of Architecture & Urban Planning": 1906,
      "College of Engineering": 1854,
      "College of Literature, Science, and the Arts": 1841,
      "Gerald R. Ford School of Public Policy": 1914,
      "Horace H. Rackham School of Graduate Studies": 1912,
      "Penny W. Stamps School of Art & Design": 1974,
      "School of Dentistry": 1875,
      "School of Education": 1921,
      "School of Information": 1996,
      "School of Kinesiology": 1984,
      "School of Law": 1859,
      "School of Medicine": 1850,
      "School of Music, Theatre & Dance": 1880,
      "School of Natural Resources & Environment": 1927,
      "School of Nursing": 1893,
      "School of Pharmacy": 1876,
      "School of Public Health": 1941,
      "School of Social Work": 1951,
      "Stephen M. Ross School of Business": 1924
    }
    =====
    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):
        def testOne(self):
            a = sorted(umSchools, key=lambda x: umSchools[x])[0]
            self.assertEqual(oldest_school, a, "Testing that oldest_school has been correctly set")

    myTests().main()