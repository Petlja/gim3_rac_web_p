Распоред елемената – задаци
===========================

.. questionnote::

    **Задатак 2.4.1**

    Дефинишите потребне класе за *HTML* елементе и напишите дефиниције стила, тако да се добије распоред што приближнији овом на слици.

    .. figure:: ../../_images/css/raspored_test5_pitanje.png
        :width: 550px
        :align: center

    .. petlja-editor:: html

        style.css
        * {
          box-sizing: border-box;
        }

        body {
          font-family: Arial, sans-serif;
        }

        h1 {
          margin: 0 0 10px 0;
        }
        ~~~
        index.html
        <!DOCTYPE html>
        <html>
        <head>
            <link rel="stylesheet" href="style.css" />
            <title>Veb</title>
        </head>
        <body>
            <div>
                <nav>
                    <a href="#">Algora</a>
                    <a href="#">Petlja</a>
                    <a href="#">Takprog</a>
                    <a href="#">Arena</a>
                </nav>
                <div>
                    <div>
                        <p>Kategorija</p>
                        <p>#</p>
                    </div>
                    <div>
                        <span>868</span>
                        <h1>Pitanja i problemi</h1>
                        <p>Sva vaša pitanja oko zadataka, algoritama, Petlja portala ili bilo čega što vas muči i mislite da na
                            Algori možete dobiti odgovor, postavite ovde. Pišite nam probleme na koje nailazite pri korišćenju
                            portala i vaš feedback.</p>
                    </div>
                    <div>
                        <span>256</span>
                        <h1>Takmičenja</h1>
                        <p>Sve o takmičenjima na Petlja portalu. Korisne informacije za početnike ali i iskusnije u takmičarskom
                            programiranju.</p>
                    </div>
                    <div>
                        <span>54</span>
                        <h1>Algoritam</h1>
                        <p>Objašnjenja, tekstovi, rešenja zadataka i diskusije namenjene svima koji uče ili se bave analizom
                            algoritama i struktura podataka.</p>
                    </div>
                </div>
                <div>
                    <p>Najnovije</p>
                    <div>
                        <h1>Dobrodošli na Algoru!</h1>
                        <p>0</p>
                        <p>Ostalo</p>
                        <p>Apr '21</p>
                    </div>
                    <div>
                        <h1>Zatražite profesorski nalog</h1>
                        <p>732</p>
                        <p>Zbornica</p>
                        <p>18h</p>
                    </div>
                </div>
            </div>
        </body>
        </html>

