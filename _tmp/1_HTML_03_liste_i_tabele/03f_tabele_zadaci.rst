
..
  Табеле - задаци
  reading

Табеле - задаци
===============

У неким од задатака који следе, поновићемо табелу која приказује ордење додељено Николи Тесли, а о којој је већ било речи у овој лекцији, да бисте лакше могли да урадите вежбе.


.. questionnote::

    **Задатак 1.3.2**

    Промените дату табелу тако што ћете променити редослед колона и последњу колону у којој су наведене године поставите као прву колону. 

.. activecode:: tabela_okvir_zad2_html
   :language: html
   :nocodelens:

    <!DOCTYPE html>
    <html>
    <head>
      <meta charset="utf-8">
      <meta name="viewport" content="width=device-width">
      <title>JS Bin</title>
    </head>
    <body>
        <table border="solid 1px">
            <thead>
                <tr>
                    <th>Назив</th><th>Земља</th><th>Година</th>
                <tr>
            </thead>
            <tbody>
                <tr>
                    <td>Орден Светог Саве</td><td>Србија</td><td>1892</td>
                </tr>
                <tr>
                    <td>Медаља Универзитета у Паризу</td><td>Француска</td><td>1937</td>
                </tr>
                <tr>
                    <td>Орден белог лава</td><td>Чехословачка</td><td>1937</td>
                </tr>
            </tbody>
        </table>
    </body>
    </html>

.. questionnote::

    **Задатак 1.3.3**

    Допуните дату табелу и додајте и друге ордене које је Никола Тесла добио, тако што ћете за сваки орден убацити по један ред (``<tr>`` ... ``</tr>``) са по три колоне (``<td>`` ... ``</td>``), тако да подаци буду поређани хронолошки. Ордени које треба додати у табелу су:

    - Орден књаза Данила I, Црна Гора, 1895.
    - Орден Светог Саве I класе, Краљевина СХС, 1926.
    - Орден Југословенске круне, 1931.
    - Орден белог орла I класе, Краљевина Југославија, 1936.
    - Медаља Универзитета Св. Климент, Софија, 1939.

.. activecode:: tabela_okvir_zad3_html
   :language: html
   :nocodelens:

    <!DOCTYPE html>
    <html>
    <head>
      <meta charset="utf-8">
      <meta name="viewport" content="width=device-width">
      <title>JS Bin</title>
    </head>
    <body>
        <table border="solid 1px">
            <thead>
                <tr>
                    <th>Назив</th><th>Земља</th><th>Година</th>
                <tr>
            </thead>
            <tbody>
                <tr>
                    <td>Орден Светог Саве</td><td>Србија</td><td>1892</td>
                </tr>
                <tr>
                    <td>Медаља Универзитета у Паризу</td><td>Француска</td><td>1937</td>
                </tr>
                <tr>
                    <td>Орден белог лава</td><td>Чехословачка</td><td>1937</td>
                </tr>
            </tbody>
        </table>
    </body>
    </html>

.. questionnote::

    **Задатак 1.3.4**

    Проширите дату табелу тако што ћете додати прву колону (``<th>`` ... ``</th>``) у заглавље (``<thead>`` ... ``</thead>``) и у сваки ред, како бисте добили табелу са четири колоне. У прву колону упишите редне бројеве.

.. activecode:: tabela_okvir_zad4_html
   :language: html
   :nocodelens:

    <!DOCTYPE html>
    <html>
    <head>
      <meta charset="utf-8">
      <meta name="viewport" content="width=device-width">
      <title>JS Bin</title>
    </head>
    <body>
        <table border="solid 1px">
            <thead>
                <tr>
                    <th>Назив</th><th>Земља</th><th>Година</th>
                <tr>
            </thead>
            <tbody>
                <tr>
                    <td>Орден Светог Саве</td><td>Србија</td><td>1892</td>
                </tr>
                <tr>
                    <td>Медаља Универзитета у Паризу</td><td>Француска</td><td>1937</td>
                </tr>
                <tr>
                    <td>Орден белог лава</td><td>Чехословачка</td><td>1937</td>
                </tr>
            </tbody>
        </table>
    </body>
    </html>

.. questionnote::

    **Задатак 1.3.5**

    Направите нову табелу са пет колона (по једну колону за сваки радни дан у недељи) и направите свој распоред часова за ову недељу. 

.. activecode:: tabela_okvir_zad5_html
   :language: html
   :nocodelens:

    <!DOCTYPE html>
    <html>
    <head>
      <meta charset="utf-8">
      <meta name="viewport" content="width=device-width">
      <title>JS Bin</title>
    </head>
    <body>
        <!-- ovde ubaciti tabelu -->
    </body>
    </html>
