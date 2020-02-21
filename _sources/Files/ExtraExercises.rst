Extra Exercises
---------------

.. activecode:: olympic_names
    :language: python
    :autograde: unittest
    :practice: T
    :available_files: olympics2.txt
    :topics: Files/ReadingCSVFiles

    There is a CSV-formatted file called ``olympics2.txt`` write code that will create a list of **unique** olympians (no name should appear more than once). Put your result in the variable ``olympians``.

    *Note 1: your code must ignore the header row*
    *Note 2: you may want to start by writing code that read and prints out the file content*

    ~~~~

    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

        def testOne(self):
            correctOlympians = ['A Dijiang', 'A Lamusi', 'Gunnar Nielsen Aaby', 'Edgar Lindenau Aabye', 'Christine Jacoba Aaftink', 'Per Knut Aaland', 'John Aalberg', '"Cornelia ""Cor"" Aalten (-Strannood)"', 'Antti Sami Aalto', '"Einar Ferdinand ""Einari"" Aalto"', 'Jorma Ilmari Aalto', 'Jyri Tapani Aalto', 'Minna Maarit Aalto', 'Pirjo Hannele Aalto (Mattila-)', 'Arvo Ossian Aaltonen', 'Juhamatti Tapio Aaltonen', 'Paavo Johannes Aaltonen', 'Timo Antero Aaltonen', 'Win Valdemar Aaltonen']
            self.assertEqual(olympians, correctOlympians, "Checking that olympians has the correct value")

    myTests().main()

.. activecode:: olympics_by_country
    :language: python
    :autograde: unittest
    :practice: T
    :available_files: olympics.txt
    :topics: Files/ReadingCSVFiles

    There is a CSV-formatted file called ``olympics2.txt``. Write code that creates a dictionary named ``country_olympians`` where the keys are country names and the values are lists of **unique** olympians from that country (no olympian's name should appear more than once for a given country).

    ~~~~

    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

        def testOne(self):
            correctCountryOlympians = {'China': ['A Dijiang', 'A Lamusi'], 'Denmark': ['Gunnar Nielsen Aaby'], 'Sweden': ['Edgar Lindenau Aabye'], 'Netherlands': ['Christine Jacoba Aaftink', '"Cornelia ""Cor"" Aalten (-Strannood)"'], 'United States': ['Per Knut Aaland', 'John Aalberg'], 'Finland': ['Antti Sami Aalto', '"Einar Ferdinand ""Einari"" Aalto"', 'Jorma Ilmari Aalto', 'Jyri Tapani Aalto', 'Minna Maarit Aalto', 'Pirjo Hannele Aalto (Mattila-)', 'Arvo Ossian Aaltonen', 'Juhamatti Tapio Aaltonen', 'Paavo Johannes Aaltonen', 'Timo Antero Aaltonen', 'Win Valdemar Aaltonen']}

            self.assertEqual(sorted(country_olympians['China']), sorted(correctCountryOlympians['China']), "Testing country_olympians['China']")
            self.assertEqual(sorted(country_olympians['Netherlands']), sorted(correctCountryOlympians['Netherlands']), "Testing country_olympians['Netherlands']")
            self.assertEqual(sorted(country_olympians['United States']), sorted(correctCountryOlympians['United States']), "Testing country_olympians['United States']")
            self.assertEqual(sorted(country_olympians['Denmark']), sorted(correctCountryOlympians['Denmark']), "Testing country_olympians['Denmark']")

    myTests().main()

.. activecode:: write_songs
    :language: python
    :autograde: unittest
    :practice: T
    :topics: Files/ReadingCSVFiles

    Write the data in variable ``artist_songs`` into a csv file, ``'songs.txt'``, where the first column is singer name and second column is a song name. Each line should have a singer and a song name. Use ``"Name"`` and ``"Song``" as headers. Do not include double quotation marks (``"``) in your CSV but you should include apostrophes where necessary (for example, for the song ``"We Don't Talk Anymore"``).

    ~~~~
    artist_songs = {
        'Taylor Swift': ['Love Story', 'You need to Calm Down'],
        'Charlie Puth': ['Attention', "We Don't Talk Anymore", 'Change']
    }
    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

        def testOne(self):
            f = open('songs.txt')
            data = f.read()
            f.close()
            desiredResult = """Name,Song
    Taylor Swift,Love Story
    Taylor Swift,You need to Calm Down
    Charlie Puth,Attention
    Charlie Puth,We Don't Talk Anymore
    Charlie Puth,Change"""

            self.assertEqual(data.strip(), desiredResult.strip(), "Checking the contents of 'songs.txt'")

    myTests().main()

.. activecode:: school_stats
    :language: python
    :autograde: unittest
    :practice: T
    :available_files: school_stats.csv
    :topics: Files/ReadingCSVFiles

    The file ``school_stats.csv`` is CSV-formatted and contains statistics for several student across several assignments. Define three functions that reference ``school_stats.csv``:


    - ``getHighestScorer(assignment)``: Should return the **name** of the student with the **highest** score on the specified assignment (for example, ``assignment`` might be ``"problem set 1"``).
    - ``getLowestScorer(assignment)``: Should return the **name** of the student with the **lowest** score on the specified assignment (for example, ``assignment`` might be ``"problem set 1"``).
    - ``getMeanScore(assignment)``: Should return the **average** score across all students on the specified assignment (for example, ``assignment`` might be ``"problem set 1"``).

    **DO NOT hardcode the assignment column names**. Your code should work if new rows or columns are added. It is OK to assume that students' names will be in the first column.

    ~~~~

    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

        def testOne(self):
            self.assertEqual(getHighestScorer('problem set 1'), 'bill', "Checking that getHighestScorer('problem set 1') returns 'bill'")
            self.assertEqual(getLowestScorer('problem set 1'), 'sue', "Checking that getLowestScorer('problem set 1') returns 'sue'")
            self.assertEqual(getMeanScore('problem set 1'), 13.4, "Checking that getMeanScore('problem set 1') returns 13.4")
            self.assertEqual(getHighestScorer('exam 1'), 'sue', "Checking that getHighestScorer('exam 1') returns 'sue'")
            self.assertEqual(getLowestScorer('exam 1'), 'bill', "Checking that getLowestScorer('exam 1') returns 'bill'")
            self.assertEqual(getMeanScore('exam 1'), 22.4, "Checking that getMeanScore('exam 1') returns 22.4")
            self.assertEqual(getHighestScorer('problem set 2'), 'john', "Checking that getHighestScorer('problem set 2') returns 'john'")
            self.assertEqual(getLowestScorer('problem set 2'), 'joe', "Checking that getLowestScorer('problem set 2') returns 'joe'")
            self.assertEqual(getMeanScore('problem set 2'), 22.6, "Checking that getMeanScore('problem set 2') returns 22.6")

    myTests().main()

.. activecode:: add_one_no_mutate
    :language: python
    :autograde: unittest

    Define a function ``addOneNoMutate(L)`` that adds ``1`` to every item in its argument (``L``) and returns a new list.

    ~~~~

    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

        def testOne(self):
            L = []
            K = addOneNoMutate(L)
            self.assertEqual(K, [], "Checking addOneNoMutate([])")
            self.assertEqual(L, [], "Checking that addOneNoMutate([]) did not mutate the original list")
            L = [1,2,20]
            K = addOneNoMutate(L)
            self.assertEqual(K, [2,3,21], "Checking addOneNoMutate([1,2,20])")
            self.assertEqual(L, [1,2,20], "Checking that addOneNoMutate([1,2,20]) did not mutate the original list")

    myTests().main()

.. activecode:: add_one_mutate
    :language: python
    :autograde: unittest

    Define a function ``addOneMutate(L)`` that adds ``1`` to every item in its argument (``L``) by **mutating** its argument. ``addOneMutate(L)`` should return ``None``.

    ~~~~

    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

        def testOne(self):
            L = []
            K = addOneMutate(L)
            self.assertEqual(K, None, "Checking that addOneMutate([]) returns None")
            self.assertEqual(L, [], "Checking that addOneMutate([]) mutates the original list")
            L = [1,2,20]
            K = addOneMutate(L)
            self.assertEqual(K, None, "Checking that addOneMutate([1,2,20]) returns None")
            self.assertEqual(L, [2,3,21], "Checking that addOneMutate([1,2,20]) mutates the original list")

    myTests().main()

.. datafile:: school_stats.csv

    name,problem set 1,problem set 2,exam 1,final exam
    joe,10,15,20,30
    bill,23,16,19,22
    sue,8,22,27,24
    grace,12,28,21,45
    john,14,32,25,16

.. datafile:: olympics2.txt

    Name,Sex,Age,Team,Event,Medal
    A Dijiang,M,24,China,Basketball,NA
    A Lamusi,M,23,China,Judo,NA
    Gunnar Nielsen Aaby,M,24,Denmark,Football,NA
    Edgar Lindenau Aabye,M,34,Sweden,Tug-Of-War,Gold
    Christine Jacoba Aaftink,F,21,Netherlands,Speed Skating,NA
    Christine Jacoba Aaftink,F,21,Netherlands,Speed Skating,NA
    Christine Jacoba Aaftink,F,25,Netherlands,Speed Skating,NA
    Christine Jacoba Aaftink,F,25,Netherlands,Speed Skating,NA
    Christine Jacoba Aaftink,F,27,Netherlands,Speed Skating,NA
    Christine Jacoba Aaftink,F,27,Netherlands,Speed Skating,NA
    Per Knut Aaland,M,31,United States,Cross Country Skiing,NA
    Per Knut Aaland,M,31,United States,Cross Country Skiing,NA
    Per Knut Aaland,M,31,United States,Cross Country Skiing,NA
    Per Knut Aaland,M,31,United States,Cross Country Skiing,NA
    Per Knut Aaland,M,33,United States,Cross Country Skiing,NA
    Per Knut Aaland,M,33,United States,Cross Country Skiing,NA
    Per Knut Aaland,M,33,United States,Cross Country Skiing,NA
    Per Knut Aaland,M,33,United States,Cross Country Skiing,NA
    John Aalberg,M,31,United States,Cross Country Skiing,NA
    John Aalberg,M,31,United States,Cross Country Skiing,NA
    John Aalberg,M,31,United States,Cross Country Skiing,NA
    John Aalberg,M,31,United States,Cross Country Skiing,NA
    John Aalberg,M,33,United States,Cross Country Skiing,NA
    John Aalberg,M,33,United States,Cross Country Skiing,NA
    John Aalberg,M,33,United States,Cross Country Skiing,NA
    John Aalberg,M,33,United States,Cross Country Skiing,NA
    "Cornelia ""Cor"" Aalten (-Strannood)",F,18,Netherlands,Athletics,NA
    "Cornelia ""Cor"" Aalten (-Strannood)",F,18,Netherlands,Athletics,NA
    Antti Sami Aalto,M,26,Finland,Ice Hockey,NA
    "Einar Ferdinand ""Einari"" Aalto",M,26,Finland,Swimming,NA
    Jorma Ilmari Aalto,M,22,Finland,Cross Country Skiing,NA
    Jyri Tapani Aalto,M,31,Finland,Badminton,NA
    Minna Maarit Aalto,F,30,Finland,Sailing,NA
    Minna Maarit Aalto,F,34,Finland,Sailing,NA
    Pirjo Hannele Aalto (Mattila-),F,32,Finland,Biathlon,NA
    Arvo Ossian Aaltonen,M,22,Finland,Swimming,NA
    Arvo Ossian Aaltonen,M,22,Finland,Swimming,NA
    Arvo Ossian Aaltonen,M,30,Finland,Swimming,Bronze
    Arvo Ossian Aaltonen,M,30,Finland,Swimming,Bronze
    Arvo Ossian Aaltonen,M,34,Finland,Swimming,NA
    Juhamatti Tapio Aaltonen,M,28,Finland,Ice Hockey,Bronze
    Paavo Johannes Aaltonen,M,28,Finland,Gymnastics,Bronze
    Paavo Johannes Aaltonen,M,28,Finland,Gymnastics,Gold
    Paavo Johannes Aaltonen,M,28,Finland,Gymnastics,NA
    Paavo Johannes Aaltonen,M,28,Finland,Gymnastics,Gold
    Paavo Johannes Aaltonen,M,28,Finland,Gymnastics,NA
    Paavo Johannes Aaltonen,M,28,Finland,Gymnastics,NA
    Paavo Johannes Aaltonen,M,28,Finland,Gymnastics,NA
    Paavo Johannes Aaltonen,M,28,Finland,Gymnastics,Gold
    Paavo Johannes Aaltonen,M,32,Finland,Gymnastics,NA
    Paavo Johannes Aaltonen,M,32,Finland,Gymnastics,Bronze
    Paavo Johannes Aaltonen,M,32,Finland,Gymnastics,NA
    Paavo Johannes Aaltonen,M,32,Finland,Gymnastics,NA
    Paavo Johannes Aaltonen,M,32,Finland,Gymnastics,NA
    Paavo Johannes Aaltonen,M,32,Finland,Gymnastics,NA
    Paavo Johannes Aaltonen,M,32,Finland,Gymnastics,NA
    Paavo Johannes Aaltonen,M,32,Finland,Gymnastics,NA
    Timo Antero Aaltonen,M,31,Finland,Athletics,NA
    Win Valdemar Aaltonen,M,54,Finland,Art Competitions,NA
