Flexbox
=======

Често је потребно направити много комплексније распореде елемената које је веома тешко постићи уз леви и десни ток.

*CSS flexbox* (скраћено енг. *flexible box layout module*) подржава низ напредних контрола тока. Да би користили *flexbox* потребно је на неки родитељски елемент поставити ``display: flex;``.

.. petlja-editor:: css_flex_columns

    style.css
    .flex {
        display: flex;
        border: 1px solid red;
    }
    .kolona {
        border: 1px solid grey;
    }
    ~~~
    test.html
    <link rel="stylesheet" href="style.css"/>
    <div class="flex">
        <div class="kolona">
            Kolona 1
        </div>
        <div class="kolona">
            Kolona 2
        </div>
        <div class="kolona">
            Kolona 3
        </div>
        <div class="kolona">
            Kolona 4
        </div>
    </div>

.. questionnote::

    Пробајте да у примеру обришете ``display: flex;``. Који је резултат без тог својства?

Својства елемената унутар *flexbox*-а
-------------------------------------

Елементи који су директно унутар се понашају као колоне. Најчешће коришћена својства *flexbox*-a нам омогућују да контролишемо величину елемената:

.. table:: Најчешће коришћена својства *flexbox*-а

    =============== =================
    Својство        Дефиниција
    =============== =================
    ``flex-grow``   фактор раста, нула или позитиван број
    ``flex-shrink`` фактор скупљања, нула или позитиван број
    ``flex-basis``  почетна величина елемента
    =============== =================

.. infonote::

    Својство ``flex`` је скраћеница којом се могу задати сва 3 својства у формату ``flex: <flex-grow> <flex-shrink> <flex-basis>;`` нпр. ``flex: 1 1 auto``.

.. questionnote::

    Вратите се на претходни пример и пробајте неке од следећих вежби:

    #. Додајте ``flex: 1 1 auto`` свим колонама. Који је резултат?
    #. У *HTML*-у додајте првој колони ``style="flex-grow: 2"``. Који је резултат?
    #. У *HTML*-у додајте последњој колони ``style="flex-basis: 300px``. Који је резултат?

Угњеждавање *flex*-а
--------------------

Елементи унутар *flex*-а такође могу да садрже елементе који користе *flex*.

У претходној лекцији смо показали пример како постићи распоред елемената главне стране Википедије користећи леви ток.

Плавом бојом су обележени главни елементи који су подељени на леву колону са навигацијом и десну са садржајем.

Црвеном бојом је обележен садржај који се такође дели у две колоне.

.. petlja-editor:: css_wiki_flex

    style.css
    .flex {
        display: flex;
        gap: 10px;
    }
    .kolona {
        flex: 1 1 auto;
    }
    .leva-kolona {
        flex: 0 0 200px;
    }
    .plavi {
        border: 1px solid blue;
    }
    .crveni {
        border: 1px solid red;
    }
    ~~~
    test.html
    <link rel="stylesheet" href="style.css"/>
    <div class="flex plavi">
        <div class="leva-kolona plavi">
            <header>Википедија – слободна енциклопедија</heading>
            <nav>Линкови за навигацију</nav>
        </div>
        <div class="kolona plavi">
            <nav>Линкови за навигацију на врху</nav>
            <div>Картице и претрага сајта</div>
            <div>Добродошли</div>
            <div class="flex crveni">
                <div class="kolona crveni">Случајни чланци</div>
                <div class="kolona crveni">Недавни догађаји</div>
            </div>
        </div>
    </div>

Својства родитељског елемента
-----------------------------

Родитељски елемент који садржи својство ``display: flex`` може да има додатна својства која утичу на ток елемената.

.. table:: Најчешће коришћена својства *flexbox*-а

    =================== ====================
    Својство             Дефиниција
    =================== ====================
    ``gap``             простор између елемената
    ``justify-content`` распореда елемената у смеру ``flex-direction``
    ``align-items``     распоред елемената попреко смера ``flex-direction``
    =================== ====================

.. petlja-editor:: css_flex_parent

    style.css
    .flex {
        display: flex;
    }
    .leva {
        border: 1px solid red;
        width: 100px;
    }
    .desna {
        border: 1px solid blue;
        width: 100px;
    }
    ~~~
    test.html
    <link rel="stylesheet" href="style.css"/>
    <div class="flex">
        <div class="leva">
            Лева колона у два реда.
        </div>
        <div class="desna">
            Десна колона
        </div>
    </div>

.. questionnote::

    Пробајте следеће вежбе да откријете понашање атрибута:

    #. Испробајте својство ``justify-content`` на елементу ``.flex`` са вредностима: ``space-between``, ``space-around``, ``flex-end``. Који су резултати?
    #. Испробајте својство ``align-items`` на елементу ``.flex`` са вредностима: ``center``, ``flex-start``, ``flex-end``. Који су резултати?`

За више примера погледајте добар ресурс је `MDN Веб документација  <https://developer.mozilla.org/en-US/docs/Web/CSS/flex>`_.
