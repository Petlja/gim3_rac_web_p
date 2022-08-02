*Bootstrap* и распоређивање елемената
=====================================

*Bootstrap* за распоређивање елемената користи систем мреже (engl. *grid system*).

Хијерархија елемената у оваквом систему захтева да имамо контејнер елемент, у њему елементе који представљају редове, и у сваком реду елементе колона.

*Bootstrap* може да распореди елементе по контејнерима, који заузимају најмање дванаестину ширине стране:

.. image:: ../../_images/bootstrap/kontejneri.png
    :width: 624px
    :align: center

Контејнери ``col-1`` су најужи и може се ставити 12 блокова ове ширине у један ред. Блокови различитих ширина се могу комбиновати у једном реду (на пример ``col-4`` и ``col-8`` у трећем реду), под условом да не пређу укупну ширину 12.


У следећем примеру је приказан кôд реда који у себи има 3 ``<div>`` блока исте ширине:

.. activecode:: bootstrap_grid_1
    :language: html
    :nocodelens:

    <html>
        <head>
            <title>Bootstrap</title>
            <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0/dist/css/bootstrap.min.css" rel="stylesheet" crossorigin="anonymous">

            <style>
                .crvena { background-color: red; }
                .plava { background-color: blue; color: white; }
                .zelena { background-color: green; }
            </style>
        </head>
        <body>
            <div class="container">
                <div class="row">
                    <div class="col crvena">
                        Ред 1 Колона 1
                    </div>
                    <div class="col plava">
                        Ред 1 Колона 2
                    </div>
                    <div class="col zelena">
                        Ред 1 Колона 3
                    </div>
                </div>
            </div>
        </body>
    </html>

У овом примеру, ``<div>`` блокови ће заузети по трећину ширине стране (као ``col-4`` са горње слике), пошто ширине нису експлицитно наведене у *CSS* класама.

.. questionnote::

    **Вежба**

    Измените претходни пример тако да колоне буду распоређене:

    - прва колона ширине 2 блока,
    - друга колона ширине 6 блокова,
    - трећа колона ширине 4 блока.

    Након тога, пробајте да другој колони додате ширину 7 блокова. Тада збир прелази 12 (2 + 7 + 4 = 13). Који је резултат?

*Bootstrap* има и посебне класе са префиксима ``col-sm-``, ``col-lg-`` и слично. Више информација о овим класама се може наћи на сајту `Bootstrap <https://getbootstrap.com/docs/5.2/layout/grid/#responsive-classes/>`_.

Распоред – Пример 1
-------------------

Потребно је направити *Bootstrap* распоред за следећи дизајн  (занемарићемо садржај):

.. image:: ../../_images/bootstrap/raspored2.png
    :width: 500px
    :align: center

Један од начина да се имплементира овакав распоред је:

.. activecode:: bootstrap_grid_2
    :language: html
    :nocodelens:

    <html>
        <head>
            <title>Bootstrap</title>
            <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0/dist/css/bootstrap.min.css" rel="stylesheet" crossorigin="anonymous">

            <style>
                .row {
                    border: 1px dashed #ccc;
                }

                .col, .col-4, .col-6, .col-8 {
                    border: 1px dotted red;
                }

                .hello-world {
                    background-color: skyblue;
                }
            </style>
        </head>
        <body>
            <div class="row">
                <div class="col">Navbar…</div>
            </div>
            <div class="hello-world">
                <div class="container-sm">
                    <div class="row">
                        <div class="col">
                            <h1>Hello World</h1>
                            <p>...</p>
                        </div>
                    </div>
                </div>
            </div>
            <div class="container-sm">
                <div class="row">
                    <div class="col-4">
                        <h2>Heading</h2>
                        <p>...</p>
                    </div>
                    <div class="col-4">
                        <h2>Heading</h2>
                        <p>...</p>
                    </div>
                    <div class="col-4">
                        <h2>Heading</h2>
                        <p>...</p>
                    </div>
                </div>
                <div class="row">
                    <div class="col">&copy; Company 2017</div>
                </div>
            </div>
        </body>
    </html>

Елемент ``div`` са класом ``hello-world`` заузима целу ширину и има позадинску боју, као на слици. Користећи класу ``.container-sm`` постижемо да се ширина садржаја ограничи.

Распоред – Пример 2
-------------------

Потребно је направити распоред ``<div>`` блокова који одговара следећој страни (занемарићемо садржај):

.. image:: ../../_images/bootstrap/raspored1.png
    :width: 624px
    :align: center

Прва три реда заузимају пуну ширину стране, испод њих је ред са две колоне једнаких ширина, испод кога се налази ред у коме је лева колона два пута шира од десне. *Bootstrap* распоред који одговара овој страни је:

.. activecode:: bootstrap_grid_3
    :language: html
    :nocodelens:

    <html>
        <head>
            <title>Bootstrap</title>
            <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0/dist/css/bootstrap.min.css" rel="stylesheet" crossorigin="anonymous">

            <style>
                .row {
                    border: 1px dashed #ccc;
                }

                .col, .col-4, .col-6, .col-8 {
                    border: 1px dotted red;
                }
            </style>
        </head>
        <body>
            <div class="row">
              <div class="col text-center">
                <h1>Large</h1>
              </div>
            </div>
            <div class="row">
              <div class="col">
                World | U.S. | Technology | ...
              </div>
            </div>
            <div class="row">
              <div class="col p-5">
                <h1>
                    Title of a longer<br/>
                    featured blog post
                </h1>
              </div>
            </div>
            <div class="row">
              <div class="col-6">
                <h2>Featured post</h2>
                <p>...</p>
              </div>
              <div class="col-6">
                <h2>Post title</h2>
                <p>...</p>
              </div>
            </div>
            <div class="row">
              <div class="col-8">
                <h1>Sample blog post</h1>
                <p>...</p>
              </div>
              <div class="col-4">
                <h2>About</h2>
                <p>...</p>
              </div>
            </div>
        </body>
    </html>

Прва три реда имају само по један ``<div>`` у реду, како би ти унутрашњи блокови заузели пуну ширину. У четвртом реду постоје две једнако широке колоне (класа ``col-6``). У петом реду су такође две колоне, али овде је прва колона два пута шира од друге (класе ``col-8`` и ``col-4``).
