Flexbox – примери
=================

YouTube видео
-------------

.. questionnote::

    Стилизовати део стране са веб-сајта *YouTube* која обухвата видео-фајл, опис и контролну траку видеа као што је приказано на слици.

    .. figure:: ../../_images/css/primer_youtube.jpg
        :width: 780
        :align: center
        :class: screenshot-shadow

Контролна трака је ``flex`` елемент чији су елементи вертикално центрирани (``align-items: center``) и између којих постоји празан простор тако да се леви и десни део примакну ивицама (``justify-content: space-between``).

.. petlja-editor:: css_flexbox_youtube

    style.css
    * {
        box-sizing: border-box;
    }

    body {
        font-family: Arial, sans-serif;
    }

    .okvir {
        width: 700px;
    }

    .traka {
        display: flex;
        /* леви део (прегледи) и десни (акције) вертикално центрирани */
        align-items: center;
        justify-content: space-between;
    }

    .pregledi {
        font-size: 14px;
        color: rgb(96, 96, 96);
    }

    .akcije {
        display: flex;
        /* дугмад вертикално центрирана
           са размаком од 8 пиксела*/
        align-items: center;
        gap: 8px;
    }

    .akcije button {
        display: flex;
        /* текст и икона дугмета вертикално центрирани
           са размаком од 8 пиксела */
        align-items: center;
        gap: 8px;

        background: transparent;
        border: 0;
        padding: 5px;
        color: rgb(3, 3, 3);
    }

    .akcije .material-icons, .akcije .material-icons-outlined {
        color: #555;
    }
    ~~~
    index.html
    <!doctype html>
    <html>
    <head>
        <meta charset="utf-8"/>
        <link rel="stylesheet" href="style.css">
        <link href="https://fonts.googleapis.com/icon?family=Material+Icons|Material+Icons+Outlined"
              rel="stylesheet">
    </head>
    <body>
        <div class="okvir">
            <iframe width="700" height="393" src="https://www.youtube.com/embed/s9KCMku_StY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

            <h3>1. Robot Karel - Uvodna lekcija</h1>

            <div class="traka">
                <div class="pregledi">
                    16.854 прегледа • 18. 1. 2019.
                </div>
                <div class="akcije">
                    <button>
                        <span class="material-icons-outlined">
                        thumb_up
                        </span>
                        1
                    </button>
                    <button>
                        <span class="material-icons-outlined">
                        thumb_down
                        </span>
                        Несвиђање
                    </button>
                    <button>
                        <span class="material-icons-outlined">
                        share
                        </span>
                        Дели
                    </button>
                    <button>
                        <span class="material-icons-outlined">
                        playlist_add
                        </span>
                        Сачувај
                    </button>
                    <button>
                        <span class="material-icons">
                        more_horiz
                        </span>
                    </button>
                </div>
            </div>
        </div>
    </body>
    </html>


Мени
----

.. questionnote::

    Направити мени са ставкама „Измени“, „Обриши“ и „Подешавања“.

    .. figure:: ../../_images/css/primer_meni_flexbox.png
        :width: 300px
        :align: center
        :class: screenshot-shadow

Ово је пример који смо обрадили у претходној лекцији када смо причали о селекторима, и тада је коришћен ``inline-block``.

Ставке менија су ``flex`` елементи који центрирају садржај вертикално (``align-items: center``). Икона и текст пречице имају фиксирану ширину, док текст ставке попуњава простор између јер користимо ``flex: 1 1 auto``. Подсећамо да је то скраћеница за:

.. code-block:: css

    flex: 1 1 auto;

    /** или написати овако **/
    flex-grow: 1;
    flex-shrink: 1;
    flex-basis: auto;

Својстом ``flex`` је описано да елемент може да повећа своју ширину уколико има простора. Да би упоредили разлику, измените ширину менија са 250 пиксела на 350 пиксела и видећете да се пречица увек лепи уз десну страну ивице ставке.

.. petlja-editor:: css_flexbox_meni

    style.css
    * {
        box-sizing: border-box;
    }

    body {
        font-family: 'Arial', sans-serif;
    }

    .meni {
        margin: 0;
        padding: 8px 0px;
        width: 250px;
        border: 1px solid rgba(0, 0, 0, 0.12);
        list-style: none;
        background-color: white;
        color: rgba(0, 0, 0, 0.87);
        border-radius: 4px;
    }

    .meni hr {
        border-color: rgba(0, 0, 0, 0.12);
    }

    .meni li {
        display: flex;
        align-items: center;
        padding: 6px 16px;
    }

    .meni li:hover {
        cursor: pointer;
        background-color: rgba(0, 0, 0, 0.12);
    }

    .meni .ikona {
        width: 32px;
    }

    .meni .tekst {
        flex: 1 1 auto;
    }

    .meni .precica {
        width: 50px;
        text-align: right;
    }

    .meni span {
        font-size: 16px;
    }

    .meni .ikona, .meni .precica {
        color: rgba(0, 0, 0, 0.54);
    }
    ~~~
    index.html
    <!doctype html>
    <html>
    <head>
        <meta charset="utf-8"/>
        <link rel="stylesheet" href="style.css">
        <link href="https://fonts.googleapis.com/icon?family=Material+Icons"
              rel="stylesheet">
    </head>
    <body>
        <ul class="meni">
            <li>
                <span class="ikona material-icons">
                edit
                </span>
                <span class="tekst">Измени</span>
                <span class="precica">Ctrl+I</span>
            </li>
            <li>
                <span class="ikona material-icons">
                remove_circle
                </span>
                <span class="tekst">Обриши</span>
                <span class="precica">Ctrl+O</span>
            </li>
            <hr/>
            <li>
                <span class="ikona material-icons">
                settings
                </span>
                <span class="tekst">Подешавања</span>
            </li>
        </ul>
    </body>
    </html>


Петља веб-сајт
--------------

.. questionnote::

    Пример веб-сајта `Петље <https://petlja.org>`_ приказан је у лекцији `Распоред Елемената – примери <./04b_raspored_elemenata_primeri.html>`_ користећи *float*. Направити исти пример користећи *flexbox*.

    .. figure:: ../../_images/css/primer_petlja_org.jpg
        :width: 780px
        :align: center
        :class: screenshot-shadow

Навигациона трака распоређује леве и десне линкове исто као у примеру *YouTube* користећи својство ``justify-content: space-between``.

Испод навигационе траке налази се садржај који се дели у две колоне које су одвојене размаком (``gap``) од 20 пиксела. Десна колона (вести) је фиксирана на 25 процената својством ``flex: 0 0 25%``. Лева колона ће, као у претходном примеру менија, својством ``flex: 1 1 auto`` да заузме остатак простора.

.. code-block:: css

    .sadrzaj {
        display: flex;
        gap: 20px;
    }

    .levi-sadrzaj {
        flex: 1 1 auto;
    }

    .desni-sadrzaj {
        flex: 0 0 25%;
    }

Курсеви су подељени на колоне између којих је размак (``gap``) једнак 10 пиксела. Обзиром да све 3 колоне имају својство ``flex: 1``, резултат је да ће све колоне имати исту ширину.

.. petlja-editor:: css_flexbox_petlja_org

    style.css
    * {
        box-sizing: border-box;
    }

    body {
        font-family: Arial, sans-serif;
    }

    /* Главни садржај стране је центриран са максималном ширином */
    .strana {
        margin: 0 auto;
        max-width: 960px;
    }

    /* Навигација */
    nav {
        display: flex;
        justify-content: space-between;

        overflow: hidden;
        padding: 8px;
        border-bottom: 1px solid grey;
        margin-bottom: 10px;
    }
    .navigacija-levo {
        padding: 0;
        margin: 0;
        list-style: none;
    }
    .navigacija-levo li {
        display: inline-block;
        margin-right: 8px;
    }
    .navigacija-desno {

    }

    /* Садржај стране */
    .sadrzaj {
        display: flex;
        gap: 20px;
    }

    /* Леви део садржаја */
    .levi-sadrzaj {
        flex: 1 1 auto;
    }

    /* Банер */
    .baner {
        background-image: url(https://petljamediastorage.blob.core.windows.net/root/Media/Default/images/slider/CppCS_osnovni_du%C5%BEe.jpg);
        height: 350px;
        padding: 30px 20px;
    }

    .kursevi {
        display: flex;
        gap: 10px;
    }

    .kurs {
        flex: 1;
        border-radius: 4px;
        background-color: #f2f2f2;
        padding: 0px 10px;
    }

    /* Десни садржај - вести */
    .desni-sadrzaj {
        /*
            Фиксирамо вести на четвртину.
            Еквивалентно:
            flex-grow: 0;
            flex-shrink: 0;
            flex-basis: 25%;
        */
        flex: 0 0 25%;
    }
    ~~~
    index.html
    <!doctype html>
    <html>
    <head>
        <meta charset="utf-8"/>
        <link rel="stylesheet" href="style.css"/>
    </head>
    <body>
        <div class="strana">
            <nav>
                <ul class="navigacija-levo">
                    <li>
                        <a href="#">NET.KABINET</a>
                    </li>
                    <li>
                        <a href="#">ZBIRKE</a>
                    </li>
                    <li>
                        <a href="#">ZBORNICA</a>
                    </li>
                </ul>
                <div class="navigacija-desno">
                    <a href="#">Uloguj se</a>
                </div>
            </nav>

            <div class="sadrzaj">
                <main class="levi-sadrzaj">
                    <div class="baner">
                        <p>Uči programiranje - rešavaj algoritamske zadatke</p>
                        <a href="#">Pogledaj zbirke</a>
                    </div>

                    <h2>Novo na Petlji</h2>

                    <div class="kursevi">
                        <div class="kurs">
                            <h3 class="naziv">
                                Примене савременог рачунарства за 4. разред гимназије
                            </h3>
                            <p>
                                Овај курс је намењен ученицима четвртог разреда гимназија свих смерова за предмет Рачунарство и информатика.
                            </p>
                        </div>
                        <div class="kurs">
                            <h3 class="naziv">
                                Budi data driven
                            </h3>
                            <p>
                                Овај курс намењен је средњошколцима, студентима и свима који су заинтересовани да уче анализу, обраду и визуелизацију података.
                            </p>
                        </div>
                        <div class="kurs">
                            <h3 class="naziv">
                                Базе података, рачунарске мреже и серверско веб програмирање за четврти разред гимназије природни смер
                            </h3>
                            <p>
                                Овај курс је намењен ученицима четвртог разреда гимназија природно-математичког смера за предмет Рачунарство и информатика.
                            </p>
                        </div>
                    </div>
                </main>
                <div class="desni-sadrzaj">
                    <h2>Petljine vesti</h2>

                    <div class="vest">
                        <h5>Letnja škola programiranja</h5>
                        <p>
                            Posle dugo vremena imamo priliku da se vidimo uživo i to na Letnjoj školi programiranja.
                            Poziv za prijavu je otvoren za sve učenike starijih razreda osnovnih škola.
                        </p>
                    </div>
                    <div class="vest">
                        <h5>Savremeno računarstvo – osnovni koncepti i primena</h5>
                        <p>
                            Novi kurs na net.kabinetu namenjen učenicima četvrtog razreda gimnazije se bavi temom savremene primene računarstva od IoT-a do mašinskog učenja, veštačke inteligencije i robotike
                        </p>
                    </div>
                </div>
            </div>
        </div>
    </body>
    </html>
