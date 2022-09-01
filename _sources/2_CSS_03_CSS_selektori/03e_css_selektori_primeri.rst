CSS селектори – примери
=======================

Слике љубимаца
--------------

У једној од претходних лекција направили смо мобилну апликацију за приказивање слика кућних љубимаца, и тада смо користили елементе као што су ``main``, ``nav`` и ``section``. Следи исти пример где ћемо користити идентификаторе и класе.

.. figure:: ../../_images/css/primer_kucni_ljubimci.png
    :width: 450px
    :align: center
    :class: screenshot-shadow

.. petlja-editor:: css_selektori_slike_ljubimaca

    style.css
    /* Поставимо на све елементе модел оквира и величину фонта */
    * {
        box-sizing: border-box;
        font-family: 'Arial', sans-serif;
    }

    #glavni {
        border: 1px solid grey;
        width: 542px;
    }

    #navigacija a {
        /* padding не ради без inline-block */
        display: inline-block;
        padding: 20px;
        /* Прегледач додаје маргине које не желимо */
        margin: 0;
        /* Додајемо доњу ивицу без боје */
        border-bottom: 2px solid transparent;
        /* Стилизујемо текст */
        color: #b587f6;
        text-align: center;
        text-decoration: none;
    }

    /* Стил који се додељује на прелаз мишем */
    #navigacija a:hover {
        color: white;
        border-bottom-color: white;
    }

    /* Навигациона трака */
    #navigacija {
        background-color: #6200ee;
        /*
            box-shadow својство додаје сенку.
            Више о својству на W3Schools: https://www.w3schools.com/cssref/css3_pr_box-shadow.asp
        */
        box-shadow: 0px 2px 2px rgba(0, 0, 0, 0.2);
    }

    /* Место за слике */
    #slike {
        font-size: 0px;
    }

    /* Појединачна слика */
    .ljubimac {
        object-fit: cover;

        /* Величина слике */
        width: 256px;
        height: 256px;

        /* Маргине слика */
        margin: 10px 0 10px 10px;
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

        <div id="glavni">
            <div id="navigacija">
                <a href="#">ПСИ</a>
                <a href="#">МАЧКЕ</a>
                <a href="#">ПТИЦЕ</a>
            </div>

            <div id="slike">
                <img class="ljubimac" src="http://localhost:1234/macka_1.jpeg" alt="Мачка која лежи"/>
                <img class="ljubimac" src="http://localhost:1234/macka_2.jpeg" alt="Мачка која се смеје"/>
                <img class="ljubimac" src="http://localhost:1234/macka_3.jpeg" alt="Мачка задовољна ручком"/>
                <img class="ljubimac" src="http://localhost:1234/macka_4.jpeg" alt="Мачка задовољна ручком"/>
            </div>
        </div>

    </body>
    </html>

Табела
------

Направити табелу предмета трећег семестра смера одсека Рачунарска техника и информатика са Електротехничког факултета.

.. figure:: ../../_images/css/primer_tabela_etf.png
    :width: 780px
    :align: center
    :class: screenshot-shadow

.. petlja-editor:: css_selektori_tabela

    style.css
    .tabela {
        font-family: 'Arial', sans-serif;

        /* border-spacing представља простор између ивица ћелија */
        border-spacing: 0;
        /* border-collapse спаја ивице ћелија - обришите својство да видите разлику */
        border-collapse: collapse;
        border: 2px solid black;
    }

    /*
        ћелије заглавља и ћелије тела деле стилове
        стилови ће бити примењени на два одвојена селектора
    */
    .tabela th, .tabela td {
        margin: 0;
        border: 1px solid black;
        padding: 10px;
    }

    .tabela th {
        background-color: #f2f2f2;
    }

    .centriran {
        text-align: center;
    }

    .tabela-ukupno {
        font-weight: bold;
        text-align: center;
    }
    ~~~
    index.html
    <!doctype html>
    <html>
    <head>
        <meta charset="utf-8"/>
        <link rel="stylesheet" href="style.css">
    </head>
    <body>
        <table class="tabela">
            <thead>
                <tr>
                    <th>Шифра</th>
                    <th>Предмет</th>
                    <th>Статус</th>
                    <th>Часови (П+В+Л)</th>
                    <th>Кредити</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td>13Е112АСП</td>
                    <td>Алгоритми и структуре података</td>
                    <td class="centriran">О</td>
                    <td class="centriran">3+2+0</td>
                    <td class="centriran">6</td>
                </tr>
                <tr>
                    <td>13Е082НАД</td>
                    <td>Нумеричка анализа и дискретна математика</td>
                    <td class="centriran">О</td>
                    <td class="centriran">2+2+1</td>
                    <td class="centriran">6</td>
                </tr>
                <tr>
                    <td>13Е112ОО1</td>
                    <td>Објектно-оријентисано програмирање 1</td>
                    <td class="centriran">О</td>
                    <td class="centriran">2+2+1</td>
                    <td class="centriran">6</td>
                </tr>
                <tr>
                    <td>13Е112ОРТ2</td>
                    <td>Основи рачунарске технике 2</td>
                    <td class="centriran">О</td>
                    <td class="centriran">2+2+1</td>
                    <td class="centriran">6</td>
                </tr>
                <tr>
                    <td>13Е052СИСР</td>
                    <td>Сигнали и системи</td>
                    <td class="centriran">О</td>
                    <td class="centriran">3+1+1</td>
                    <td class="centriran">6</td>
                </tr>
                <tr class="tabela-ukupno">
                    <td colspan="3">Укупно</td>
                    <td>25</td>
                    <td>30</td>
                </tr>
            </tbody>
        </table>
    </body>
    </html>

Мени
----

Направићемо мени са ставкама „Измени“, „Обриши“ и „Подешавања“.

.. figure:: ../../_images/css/primer_meni.png
    :width: 300px
    :align: center
    :class: screenshot-shadow
    
Да унапредимо изглед менија користићемо иконе коју пружа бесплатна библотека `Material Icons <https://fonts.google.com/icons?selected=Material+Icons>`_. Можете прочитати `упутство за додавање библиотеке <https://developers.google.com/fonts/docs/material_icons#setup_method_1_using_via_google_fonts>`_.

.. petlja-editor:: css_selektori_meni

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
        padding: 6px 16px;
        font-size: 0;
    }

    .meni li:hover {
        cursor: pointer;
        background-color: rgba(0, 0, 0, 0.12);
    }

    .meni .ikona {
        width: 32px;
    }

    .meni .tekst {
        display: inline-block;
        width: 134px;
    }

    .meni .precica {
        display: inline-block;
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

