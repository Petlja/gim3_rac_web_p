Bootstrap класе
===============

Када се укључи `Bootstrap <https://getbootstrap.com/>`_ библиотека у *HTML* страну, стилови из библиотеке ће аутоматски бити примењени на стандардне *HTML* елементе, без икаквих додатних подешавања. Да би се користило ово основно стилизовање, није потребно додавати никакве класе *HTML* елементима стране. Без икаквог додатног напора ћете за велики број елемената добити мало бољи изглед од оног који дају прегледачи када користе подразумевани стил.

Поред основних стилова, `Bootstrap` обезбеђује унапред дефинисане *CSS* класе, чији стилови се могу додатно применити на *HTML* елементе. Ове класе примењујемо тако што имена *CSS* класа додамо у атрибуте ``class`` оних *HTML* елемената на које желимо да применомо стил из класе. Неке од класа које су на располагању за додатно стилизовање *HTML* елемената су:

- ``swatch-primary``, ``swatch-secondary``
- ``btn-primary``, ``btn-secondary``
- ``table``, ``list``, ``form``

Табеле
------

`Bootstrap` има унапред дефинисане класе за стилизовање табела. На самој табели можемо користити:

- класу ``table`` која додаје основни изглед табеле,
- класу ``table-striped`` која боји редове наизменично,
- класу ``table-bordered`` која додаје ивице редовима и колонама,
- класу ``table-hover`` која означи ред преко ког прелази миш и
- класу ``table-dark`` која ће табели доделити тамнији стил.

Наведене класе се могу комбиновати, нпр. ``table table-striped table-hover`` ће представљати табелу која има наизменично обојене редове и ред преко ког прелази миш биће означен.

У следећем примеру је основна табела. Испробајте неке комбинације горе наведених класа:

.. activecode:: bootstrap_klase_tabele
    :language: html
    :nocodelens:

    <html>
        <head>
            <title>Bootstrap табеле</title>
            <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0/dist/css/bootstrap.min.css" rel="stylesheet" crossorigin="anonymous">
        </head>
        <body>
            <table class="table">
                <thead>
                    <tr>
                        <td>#</td>
                        <td>Име</td>
                        <td>Време</td>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>1</td>
                        <td>Петар Петровић</td>
                        <td>01:05:13</td>
                    </tr>
                    <tr>
                        <td>2</td>
                        <td>Марко Марковић</td>
                        <td>01:07:52</td>
                    </tr>
                    <tr>
                        <td>3</td>
                        <td>Станко Станковић</td>
                        <td>01:07:55</td>
                    </tr>
                </tbody>
            </table>
        </body>
    </html>

Постоје класе које омогућавају напредно стилизовање редова и ћелија. Прочитајте више на `Bootstrap табеле <https://getbootstrap.com/docs/5.2/content/tables/>`_ веб-страни.


|

Листе
-----

У лекцијама о *HTML* листама смо се упознали са нумерисаним (``<ol>``) и не-нумерисаним (``<ul>``) листама, које служе да се наведе листа ставки. 

У самом језику *HTML* постоје атрибути помоћу којих се задаје како ће ставке бити означене (на пример словима, римским бројевима, арапским бројевима и слично). Испробајте формирање нумерисане листе са атрибутом ``type``, на пример ``<ol type="a">``, ``<ol type="A">``, или ``<ol type="I">``.

Сада ћемо видети како можемо да стилизујемо листе помоћу *Bootstrap* класа.

Груписане листе
'''''''''''''''

Стилизовање листе постижемо:

* додељивањем класе ``list-group`` елементу листе ``<ul>``,
* додељивањем класе ``list-group-item`` елементима листе (``<li>``).

Као резултат, листа почасних доктората Николе Тесле би била приказана следећим стилом:

.. activecode:: bootstrap_liste_1
    :language: html
    :nocodelens:

    <html>
        <head>
            <title>Bootstrap листе</title>
            <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0/dist/css/bootstrap.min.css" rel="stylesheet" crossorigin="anonymous">
        </head>
        <body>
            <h2>Почасни докторати</h2>
            <ul class="list-group">
                <li class="list-group-item">Техничка школа, Беч, 1908.</li>
                <li class="list-group-item">Универзитет у Београду, 1926.</li>
                <li class="list-group-item">Универзитет у Загребу, 1926.</li>
                <li class="list-group-item">Техничка школа, Праг, 1936.</li>
                <li class="list-group-item">Универзитет у Греноблу, 1938.</li>
            </ul>
        </body>
    </html>

Водоравне листе
'''''''''''''''
При употреби *Bootstrap* библиотеке, лист група не мора да стилизује само елементе ``<ul>``, ``<ol>`` и ``<li>``. Класе ``list-group`` и ``list-group-item`` могу да се поставе на неку сличну структуру елемената, на пример на елементе ``<div>`` и ``<a>``.

Додељивањем класе ``list-group-horizontal`` на листу, елементи листе се приказују водоравно (у низу, један до другог).

Осим тога, употребом класе ``list-group-item disabled`` постижемо да се појави онемогућени линк, тј. линк на који не може да се кликне.

.. activecode:: bootstrap_liste_2
    :language: html
    :nocodelens:

    <html>
        <head>
            <title>Bootstrap листе</title>
            <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0/dist/css/bootstrap.min.css" rel="stylesheet" crossorigin="anonymous">
        </head>
        <body>
            <div class="list-group list-group-horizontal">
                <a href="https://petlja.org/" class="list-group-item disabled">Прва онемогућена ставка</a>
                <a href="https://petlja.org/" class="list-group-item disabled">Друга онемогућена ставка</a>
                <a href="https://petlja.org/" class="list-group-item">Трећа ставка</a>
            </div>
        </body>
    </html>

Онемогућени линкови могу, на пример, да се користе за везе ка деловима нашег сајта за које смо испланирали везе, али још нисмо направили одговарајуће странице.

