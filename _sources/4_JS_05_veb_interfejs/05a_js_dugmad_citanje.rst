Дугмад
======

Догађаји се дешавају на неким *HTML* елементима и на њима се постављају *JavaScript* функције које реагују на те догађаје и врше акције. У примерима у претходној секцији смо директно постављали функције на елементе на којима ће се дешавати догађаји. У правим веб-странама чест је случај да треба поставити дугме на које ће неко да кликне да би покренуо акцију.

.. code-block:: html

    <button type="button">Кликни на ово дугме</button>

Као и у случају претходних елемената, на ово дугме се може поставити функција која треба да буде извршена када неко кликне на дугме:

.. code-block:: html

    <button type="button" id="dugme1">Кликни на ово дугме</button>

    ...
    
    <script>
        document.getElementById("dugme1").addEventListener('click', function(dogadjaj) {
            // telo anonimne funkcije
        });
    </script>

Као и код других догађаја и других *HTML* елемената, и овде је могуће као други аргумент поставити само име функције, или уметнути анонимну функцију, као што је овде учињено.

Функција (било анонимна или именована) и даље има приступ свим информацијама о догађају, а тиме и о *HTML* елементу на којем се десио догађај. Међутим, у случају дугмади се такве информације знатно ређе користе.

.. comment

    У случају да користите *Twitter Bootstrap* за стилизовање страна, можете лако да примените различите стилове за дугмад, као на пример:

    .. image:: ../../_images/bootstrap/dugmad_stil.png
        :width: 624px
        :align: center

    Примарни и секундарни стилови дугмета су стилови који се најчешће користе на странама. Често би требало да обележите неку дугмад тако да означите да је то дугме које треба да се притисне да би се успешно извршила нека акција (енгл. *success*) или да ће се десити нека потенцијално опасна акција или акција која ће приказати упозорење. 

    Дугмад се могу лако стилизовати помоћу библиотеке *Twitter Bootstrap* додавањем класа ``btn-primary``, ``btn-secondary``, ``btn-success``, ``btn-danger`` и слично као што је приказано у следећем примеру:

    .. code-block:: html

        <button type="button" class="btn btn-primary">Primary</button>
        <button type="button" class="btn btn-secondary">Secondary</button>
        <button type="button" class="btn btn-success">Success</button>
        <button type="button" class="btn btn-info">Info</button>
        <button type="button" class="btn btn-warning">Warning</button>
        <button type="button" class="btn btn-danger">Danger</button>
        <button type="button" class="btn btn-dark">Dark</button>
        <button type="button" class="btn btn-light">Light</button>
        <button type="button" class="btn btn-link">Link</button>

    Када поставите неко од оваквих дугмади на страну, на њега можете поставити функцију која ће бити извршена када се притисне дугме, као на пример:

    .. code-block:: html

        <button type="button" class="btn btn-primary" onclick="mojaFunkcija()">Притисни ово дугме</button>

    Више информација о дугмади можете наћи на 
    *w3schools* страни `о дугметима <https://www.w3schools.com/bootstrap4/bootstrap_buttons.asp>`_ или 
    *Bootstrap* `документацији о дугметима <https://getbootstrap.com/docs/4.1/components/buttons/>`_.

Пример – Слике
''''''''''''''

На следећој веб-страни налазе се слика и дугме за прелазак на следећу слику. Кликом на дугме повећавамо бројач ``trenutna`` за 1. Тренутну слику бирамо из низа, а коју по реду ћемо изабрати добијамо рачунањем остатка са дељењем бројача и броја слика.

.. csv-table:: Рачунање редног броја слике која се приказује
    :header: "Бројач", "Модуо"
    :widths: 20, 80
    :align: left

    ``0``,  :math:`0 \mod 3 = 0`
    ``1``,  :math:`1 \mod 3 = 1`
    ``2``,  :math:`2 \mod 3 = 2`
    ``3``,  :math:`3 \mod 3 = 0`
    ``4``,  :math:`4 \mod 3 = 1`

.. petlja-editor:: rotacija_slika_html

    main.js
    const url = 'https://petljamediastorage.blob.core.windows.net/root/Media/Default/Kursevi/OnlineNastava/kurs-treci-gim-prirodni/'
    
    const slike = [
        url + 'emo1.png',
        url + 'emo2.png',
        url + 'emo3.png'
    ];
    let trenutna = 0;

    const slika = document.getElementById('slika');
    document.getElementById('sledeca').addEventListener('click', function () {
        trenutna++;
        slika.src = slike[trenutna % slike.length];
    });
    ~~~
    index.html
    <!doctype html>
    <head>
        <meta charset="utf-8"/>
    </head>
    <body>

        <img id="slika" src="https://petljamediastorage.blob.core.windows.net/root/Media/Default/Kursevi/OnlineNastava/kurs-treci-gim-prirodni/emo1.png" alt=""/>
        <br/>
        <button id="sledeca">Следећа</button>

        <script src="main.js"></script>
    </body>
    </html>


Пример – Вишејезична страна
'''''''''''''''''''''''''''

На следећој веб-страни се у засебним одељцима налази исти садржај на ћирилици, латиници и на енглеском. Сваки одељак има одговарајући идентификатор (``cirilica``, ``latinica``, или ``english``).

У врху стране су три дугмета, помоћу којих бирамо на ком језику/писму ће бити приказана страна. Сва три дугмета покрећу исту функцију, али са различитим аргументом. Свако дугме као аргумент прослеђује идентификатор оне секције која треба да буде видљива. Функција најпре све одељке учини невидљивим, тако што им дода класу ``nevidljiv`` (стил те класе је ``display: none``, што значи да се елементи те класе не приказују), а затим ту класу уклони из одељка који треба да остане видљив.

.. petlja-editor:: biranje_jezika_i_pisma_html

    main.js
    function postaviPismo(izabranoPismo) {
      document.querySelector('#cirilica').classList.add('nevidljiv');
      document.querySelector('#latinica').classList.add('nevidljiv');
      document.querySelector('#english').classList.add('nevidljiv');

      document.querySelector(`#${izabranoPismo}`).classList.remove('nevidljiv');
    }

    document.addEventListener('DOMContentLoaded', function() {
        postaviPismo('cirilica');
    });

    document.getElementById('cir').addEventListener('click', function(d) {
        postaviPismo('cirilica');
    });
    document.getElementById('lat').addEventListener('click', function(d) {
        postaviPismo('latinica');
    });
    document.getElementById('eng').addEventListener('click', function(d) {
        postaviPismo('english');
    });
    ~~~
    style.css
    .nevidljiv { display: none; }
    ~~~
    index.html
    <!DOCTYPE html>
    <html>
        <head>
            <title>MultiLang</title>

            <link rel="stylesheet" href="style.css"/>
        </head>
        <body>
            <button type="button" id="cir">Ћирилица</button>
            <button type="button" id="lat">Latinica</button>
            <button type="button" id="eng">English</button>
            <div id="cirilica">
              <h1>Биографија</h1>
              <p>…</p>
              <h1>Остало</h1>
              <p>…</p>
              <h1>Референце</h1>
              <p>…</p>
            </div>
            <div id="latinica">
              <h1>Biografija</h1>
              <p>…</p>
              <h1>Ostalo</h1>
              <p>…</p>
              <h1>Reference</h1>
              <p>…</p>
            </div>
            <div id="english">
              <h1>Biography</h1>
              <p>…</p>
              <h1>Other</h1>
              <p>…</p>
              <h1>References</h1>
              <p>…</p>
            </div>
        </body>
        <script src="main.js"></script>
    </html>
