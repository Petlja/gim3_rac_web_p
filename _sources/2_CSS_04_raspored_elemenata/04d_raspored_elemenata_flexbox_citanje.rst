Flexbox
=======

Често је потребно направити много комплексније распореде елемената које је веома тешко постићи уз леви и десни ток.

*CSS flexbox* (скраћено енг. *flexible box layout module*) подржава низ напредних контрола тока. Да би користили *flexbox* потребно је на неки родитељски елемент поставити ``display: flex;``.

.. petlja-editor:: css_flex_columns

    style.css
    .container {
        display: flex;
        border: 1px solid red;
    }
    .column {
        border: 1px solid grey;
    }
    ~~~
    test.html
    <link rel="stylesheet" href="style.css"/>
    <div class="container">
        <div class="column">
            Kolona 1
        </div>
        <div class="column">
            Kolona 2
        </div>
        <div class="column">
            Kolona 3
        </div>
        <div class="column">
            Kolona 4
        </div>
    </div>

.. questionnote::

    Пробајте да у примеру обришете ``display: flex;``. Који је резултат без тог својства?

Својства елемената унутар *flexbox*-а
-------------------------------------

Елементи који су директно унутар се понашају као колоне, али то је тек почетак *flexbox*-а.

.. table:: Најчешће коришћена својства *flexbox*-а

    =============== =================
    Својство        Дефиниција
    =============== =================
    ``flex-grow``   фактор раста, нула или позитиван број
    ``flex-shrink`` фактор скупљања, нула или позитиван број
    ``flex-basis``  почетна величина елемента
    =============== =================

.. infonote::

    Својство ``flex`` је скраћеница којом се могу задати сва 3 својства у формату ``flex: <flex-grow> <flex-shrink> <flex-basis>;``.

Погледајмо пример распореда главне странице Википедије из претходне лекције:

.. petlja-editor:: css_wiki_flex

    style.css
    .container {
        display: flex;
        gap: 10px;
    }
    .column {
        flex: 1 1 auto;
        border: 1px solid grey;
    }
    .flex-30 {
        flex-basis: 30%;
    }
    ~~~
    test.html
    <link rel="stylesheet" href="style.css"/>
    <div class="container">
        <div class="column flex-30">
            <header>Википедија – слободна енциклопедија</heading>
            <nav>Линкови за навигацију</nav>
        </div>
        <div class="column">
            <nav>Линкови за навигацију на врху</nav>
            <div>Картице и претрага сајта</div>
            <div>Добродошли</div>
            <div class="container">
                <div class="column">Случајни чланци</div>
                <div class="column">Недавни догађаји</div>
            </div>
        </div>
    </div>

За више примера погледајте добар ресурс је `MDN Веб документација  <https://developer.mozilla.org/en-US/docs/Web/CSS/flex>`_.

Својства родитељског елемента
-----------------------------

.. table:: Најчешће коришћена својства *flexbox*-а

    =================== ====================
    Својство             Дефиниција
    =================== ====================
    ``gap``             простор између елемената
    ``justify-content`` распореда елемената у смеру ``flex-direction``
    ``align-items``     распоред елемената попреко смера ``flex-direction``
    =================== ====================

.. image:: ../../_images/css/primer_youtube.png
    :width: 624px
    :align: center

.. petlja-editor:: css_youtube_flex

    style.css
    .donja-traka {
        display: flex;
        gap: 10px;
        justify-content: space-between;
        align-items: center;
    }
    .akcije {
        display: flex;
        gap: 5px;
    }
    .akcija {
        display: flex;
        align-items: center;
        gap: 5px;
        font-size: 16px;
        text-transform: uppercase;
    }
    .ikona {
        width: 32px;
        height: 32px;
        border-radius: 3px;
        background-color: grey;
    }
    ~~~
    test.html
    <link rel="stylesheet" href="style.css"/>
    <div>
        <h2>Веома дугачак назив видео материјала</h2>
        <div class="donja-traka">
            <div class="pregledi">
                206,831 views * Jul 11, 2022
            </div>
            <div class="akcije">
                <div class="akcija">
                    <div class="ikona"></div>
                    15K
                </div>
                <div class="akcija">
                    <div class="ikona"></div>
                    Dislike
                </div>
                <div class="akcija">
                    <div class="ikona"></div>
                    Share
                </div>
                <div class="akcija">
                    <div class="ikona"></div>
                    Clip
                </div>
                <div class="akcija">
                    <div class="ikona"></div>
                    Save
                </div>
                <div class="akcija">
                    <div class="ikona"></div>
                </div>
            </div>
        </div>
    </div>
