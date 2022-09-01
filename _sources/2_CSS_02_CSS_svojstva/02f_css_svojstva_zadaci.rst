CSS својства – задаци
=====================

.. questionnote::

    **Задатак 2.2.1**

    У следећем *HTML/CSS* кôду можете да испробавате подешавање својстава ``margin`` и ``padding`` у стиловима наслова и параграфа. За све елементе је постављен и оквир, да би се јасније видело дејство различитих подешавања својстава ``margin`` и ``padding``.
    
    Испробајте и посебно подешавање ових својстава за сваку страну елемента: ``margin-top``, ``margin-bottom``, ``margin-right``, ``margin-left`` за растојање споља (margin), односно ``padding-top``, ``padding-right``, ``padding-bottom``, ``padding-left`` за растојање изнутра (padding).

    .. petlja-editor:: margin_padding_html

        style.css
        * {
            border: 1px solid #ff0000;
        }
        h1 {
            margin: 15px;
            padding: 3px;
        }
        h2 {
            margin: 10px;
            padding: 2px;
        }
        p {
            margin: 5px;
            padding: 10px;
        }
        ~~~
        index.html
        <!doctype html>
        <html>
        <head>
            <link rel="stylesheet" href="style.css"/>
        </head>
        <body>
            <h1>Наслов</h1>
            <h2>Први поднаслов</h2>
            <p>
                Произвољан текст који служи да попуни параграф. Овај текст
                не трба да читате, нити да у њему тражите скривене поруке.
            </p>
            <p>
                Ако ипак читате, можете да станете овде, јер се испод следећег
                наслова текст понавља. Мада, ако сте читали довде, вероватно ћете
                проверити и наставак.
            </p>
            <h2>Други поднаслов</h2>
            <p>
                Произвољан текст који служи да попуни параграф. Овај текст
                не треба да читате, нити да у њему тражите скривене поруке.
            </p>
            <p>
                Ако ипак читате, можете да станете овде, јер се испод следећег
                наслова текст понавља. Мада, ако сте читали довде, вероватно ћете
                проверити и наставак.
            </p>
        </body>
        </html>

.. questionnote::

    **Задатак 2.2.2**

    У примеру је дат *HTML* кôд који треба стилизовати приближно као што је представљено сликом:

    * ширина картице је 300 пиксела,
    * боја ивице оквира је ``#e7e7e7`` и
    * боја позадине линка је ``blue``.

    .. image:: ../../_images/css/model_okvira_vezba_1.png
        :width: 300px
        :align: center

    .. petlja-editor:: margin_padding_2_html

        style.css
        * {
          box-sizing: border-box;
        }

        body {
          font-family: Arial, sans-serif;
        }

        img {
        }

        div {
        }

        p {
        }

        a {
        }
        ~~~
        index.html
        <html>
        <head>
            <link rel="stylesheet" href="style.css"/>
        </head>
        <body>
            <div>
                <img src="https://petljamediastorage.blob.core.windows.net/root/Media/Default/Kursevi/OnlineNastava/kurs-treci-gim-drustveni/_static/macka_1.jpeg" alt="Мачка"/>
                <h1>Мачка</h1>
                <p>
                    Мачка, такође звана и домаћа мачка или кућна мачка, мали је месождер, врста сисара из рода Felis.
                    Верује се да је њен предак била афричка дивља мачка (Felis silvestris lybica).
                    Мачке живе у блиској вези са људима најмање 9.500 година.
                </p>
                <a href="#">Погледај слике</a>
            </div>
        </body>
        </html>
