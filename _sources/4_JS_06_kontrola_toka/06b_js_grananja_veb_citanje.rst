Употреба гранања у веб-странама
===============================

Овде ћемо кроз неколико примера илустровати употребу гранања у *JavaScript* програмима у оквиру веб-стране.

Пример – Број отварања стране
-----------------------------

.. questionnote::
    
    Направити веб-страну која показује колико пута је та страна отворена.

За решавање овог задатка је потребно ван *HTML* стране некако запамтити претходни број посета. У ту сврху можемо да употребимо објекат
``localStorage`` (локално складиште). Помоћу овог објекта можемо да сачувамо разне вредности на нашем рачунару, тако да су нам на располагању када отворимо било коју веб-страну са *JavaScript* програмом који приступа објекту ``localStorage``.

Објекат ``localStorage`` има методе:

* ``setItem(kljuc, vrednost)`` – Уписује вредност под именом првог аргумента ”кључ”.
* ``getItem(kljuc)`` – Чита вредност кључа. Повратна вредност је ``null`` уколико вредност није уписана под кључем.

У следећем решењу најпре проверавамо да ли је нека вредност већ уписана. Ако нема уписане вредности, уписујемо 0 као почетну вредност. Након тога поново читамо вредност (сада знамо да вредност постоји и да је то број), повећавамо је, приказујемо у веб-страни и памтимо увећану вредност у локалном складишту.

.. petlja-editor:: broj_otvaranja_strane_html_js

    main.js
    function procitajBrojOtvaranja() {
        const brojOtvaranja = parseInt(localStorage.getItem('counter'));
        // parseInt може да врати NaN (Not a Number) у случају да
        // је записана погрешна вредност, или је вредност одсутна
        console.log(brojOtvaranja);
        if (isNaN(brojOtvaranja)) {
            return 0;
        }
        return brojOtvaranja;
    }

    function snimiBrojOtvaranja() {
        localStorage.setItem('counter', brojOtvaranja);
    }

    let brojOtvaranja = procitajBrojOtvaranja();
    brojOtvaranja++;
    snimiBrojOtvaranja(brojOtvaranja);

    document.querySelector('#brp').innerText = brojOtvaranja;
    ~~~
    index.html
    <!DOCTYPE html>
    <html lang="sr">
      <head>
        <title>Бројач</title>
      </head>
      <body>
        <h1>Број учитавања ове стране: <span id="brp">0</span></h1>
        <script src="main.js"></script>
      </body>
    </html>

.. infonote::

    Уколико вредност постоји, ``localStorage.getItem`` враћа тип ``string``. Погледајмо следећи пример где уписујемо број, али је прочитана вредност типа ``string``.

    .. petlja-editor:: local_storage_typeof_html

        main.js
        localStorage.setItem('broj', 1);
        let vrednost = localStorage.getItem('broj');
        document.write(`Прочитана вредност: ${vrednost}`);
        document.write('<br/>');
        document.write(`Тип: ${typeof vrednost}`);
        ~~~
        index.html
        <!doctype html>
        <html>
        <head>
            <meta charset="utf-8"/>
        </head>
        <body>
            <script src="main.js"></script>
        </body>
        </html>

Пример – Листа послова са валидацијом података
----------------------------------------------

.. questionnote::
    
    Направите веб-страну која одржава листу послова (*to-do list*). Омогућити да се при покушају уноса (клик на дугме) проверава да ли су подаци заиста унети исправно.

Језик *HTML* (тачније, верзија *HTML5*) омогућава и проверу ваљаности, односно валидацију унетих података. Да бисмо користили валидацију, најпре је потребно да све елементе за унос података окружимо таговима ``<form>`` ... ``</form>``, то јест да те елементе сместимо у формулар. Након тога, валидација се постиже додавањем одређених атрибута појединим пољима за унос и другим елементима. На пример:

- додавањем атрибута ``required`` (без вредности) дефинишемо да поље мора да буде попуњено да би подаци били прихваћени као ваљани;
- додавањем атрибута ``minlength`` и ``maxlength`` дефинишемо најмању, односно највећу дозвољену дужину унетог текста;
- додавањем атрибута ``min`` и ``max`` задајемо најмању, односно највећу бројчану вредност (као што смо раније видели, користе се када је ``type="number"``).

Постоје и други атрибути за наметање додатних ограничења за унете податке ради њиховог прихватања, али њима се нећемо бавити у овом курсу.

Од *HTML* елемената, у веб-страну ћемо ставити формулар за задавање послова и табелу која ће да садржи листу послова. Формулар се састоји од поља за опис посла, поља за рок извршења (датум) и дугмета за уписивање посла у табелу. Табела треба на почетку да има само заглавље са две колоне, које смо назвали „шта“ и „до кад“.

Догађај клика на дугме везујемо за функцију ``posalji``:

.. code-block:: html

    <button type="button" id="dugme_ok">Унеси</button>
    
    ...
    
    document.getElementById('dugme_ok').addEventListener('click', posalji);

Овде смо додали и атрибут ``type="button"``, зато што је за дугме у формулару подразумевани тип ``submit``. Улога таквог дугмета је да податке из формулара проследи на обраду неком другом фајлу, који може да буде и на другом рачунару и оно се понаша нешто другачије. У нашем примеру податке не шаљемо никуда, па нам је потребна функционалност обичног дугмета. Дакле, тип ``button`` постављамо да бисмо добили „обично дугме“.

Функција ``posalji`` најпре проверава да ли су при уносу података поштована ограничења. То се постиже линијом:

.. code-block:: javascript

    if (stavka.checkValidity() && datum.checkValidity())
    
Метод ``checkValidity()`` поља за унос враћа логичку вредност, која говори да ли је податак унет у пољу у складу са ограничењима.

Ако су подаци коректни, ова функција дохвата тело табеле, формира нови ред у табели и у том реду два пута формира нову ћелију. Обратите пажњу на то да текст који се појављује у ћелији представља посебан објекат (текстуални чвор) у објектном моделу документа стране. Ћелију попуњавамо текстом тако што формирамо текстулани чвор, а затим га додамо ћелији као њено дете-чвор:

.. code-block:: javascript

    tekst  = document.createTextNode("текст који желимо да упишемо");
    novaCelija.appendChild(tekst);

Следи комплетан кôд, који можете да испробате:

.. petlja-editor:: todo_validacija_html_js

    main.js
    function posalji() {
        let stavka = document.querySelector(`#stavka`);
        let datum = document.querySelector(`#datum`);
        if (stavka.checkValidity() && datum.checkValidity()) {
            let tabela = document.getElementById('tabela').getElementsByTagName('tbody')[0];
            let noviRed = tabela.insertRow(tabela.rows.length);

            let novaCelija  = noviRed.insertCell(0);
            let tekst  = document.createTextNode(stavka.value);
            novaCelija.appendChild(tekst);

            novaCelija  = noviRed.insertCell(1);
            tekst  = document.createTextNode(datum.value);
            novaCelija.appendChild(tekst);
        } else {
            alert('Унесите исправне податке');
        }
        return false;
    }

    document.getElementById('dugme_ok').addEventListener('click', posalji);
    ~~~
    style.css
    input:invalid {
        border: 2px dashed red;
    }
    input:valid {
        border: 2px solid black;
    }
    ~~~
    index.html
    <!DOCTYPE html>
    <html>
      <head>
      <link rel="stylesheet" href="style.css"/>
      </head>
      <body>
        <form>
          <label for="stavka">Шта желиш да урадиш:</label><br>
          <input type="text" id="stavka" required><br>
          
          <label for="datum">Рок:</label><br>
          <input type="date" id="datum" required><br>
          
          <br>
          <button type="button" id="dugme_ok">Унеси</button>
        <form>
        <br><br><br><br><br>
        <table id="tabela" border="solid 1px">
          <caption>Послови</caption>
          <thead>
            <tr>
              <th>Шта</th>
              <th>До кад</th>
            </tr>
          </thead>
          <tbody>            
          </tbody>            
        </table>
        <script src="main.js"></script>
      </body>
    </html>

.. questionnote::

    **Вежба**

    Измените пример тако да дугме „Унеси“ буде онемогућено док је форма неисправна.

    *Савет:* атрибут ``disabled`` (`HTML button disabled attribute <https://www.w3schools.com/tags/att_button_disabled.asp>`_) се може користити да се дугме онемогући. Догађај ``change`` (`onchange Event <https://www.w3schools.com/jsref/event_onchange.asp>`_) може да послужи за проверу исправности форме приликом промене вредности.


Пример – Штоперица
------------------

.. questionnote::
    
    Направите веб-страну која приказује функционалну штоперицу са два дугмета. Кликом на једно дугме се штоперица покреће и зауставља, а на друго се ресетује (враћа на 0).

Штоперицу можемо да направимо користећи наредбу ``setInterval``.

У овом примеру користимо исто дугме које ће покренути штоперицу, али такође је и зауставити. Променљива ``running`` садржи вредност ``true`` ако штоперица тренутно одбројава, или вредност ``false`` ако штоперица не ради.

.. code-block:: javascript

    document.getElementById('start_stop').addEventListener('click', function(dogadjaj) {
        if (running) {
            running = false;
            // ...
        } else {
            running = true;
            // ...
        }
    });

На сваки тик повећавамо вредност бројача за променљиву ``delta``. Ако штоперица ради, вредност ће бити 0.01 (10 милисекунди). Када зауставимо штоперицу, та вредност буде 0 и тако се бројач не повећава.

.. code-block:: javascript

    function tik() {
        counter += delta;
        // ...

Следи комплетан кôд, који можете да испробате:

.. petlja-editor:: stoperica_html_js

    main.js
    let running = false;
    let counter = 0;
    let delta = 0;

    function tik() {
        counter += delta;
        document.querySelector('h1').innerHTML = counter.toFixed(2);
    }

    document.getElementById('reset').addEventListener('click', function(dogadjaj) {
        counter = 0;
        delta = 0;
    });

    document.getElementById('start_stop').addEventListener('click', function(dogadjaj) {
        if (running) {
            running = false;
            delta = 0;
            this.innerHTML = "Старт";
            this.style.backgroundColor = "green";
            this.style.color = "white";
            document.querySelector('#reset').disabled = false;
        }
        else {
            running = true;
            delta = 0.01;
            this.innerHTML = "Стоп";
            this.style.backgroundColor = "red";
            this.style.color = "black";
            document.querySelector('#reset').disabled = true;
        }
    });

    document.querySelector('#start_stop').style.backgroundColor = "green";
    document.querySelector('#start_stop').style.color = "white";
    setInterval(tik, 10);
    ~~~
    index.html
    <!DOCTYPE html>
    <html lang="sr">
    <head>
        <meta charset="utf-8"/>
        <title>Штоперица</title>
    </head>
    <body>
        <h1>0</h1>
        <button id="start_stop">Старт</button>
        <button id="reset">Ресет</button>
        <script src="main.js"></script>
    </body>
    </html>

.. questionnote::

    **Вежба**

    Штоперицу желе да користе тркачи да измере време сваког круга атлетске стазе. Измените претходни пример да се дода додатно дугме „Круг“. Клик на дугме „Круг“ треба да омогући исписивање тренутног времена штоперице са редним бројем круга.

Пример – Тајмер
---------------

.. questionnote::
    
    Направити веб-страну са тајмером, којим се може задати за колико времена ће бити одсвиран звучни сигнал (аудио-фајл који ви одаберете).

Садржај веб-стране ће чинити:

- један ``audio`` елемент који ће свирати изабрани аудио-фајл,
- ``input`` поље типа ``time`` којим се задаје време преостало до активирања звука,
- ``input`` поље типа ``checkbox`` за укључивање тајмера, тј. за отпочињање одбројавања.

Клик на ``checkbox`` поље активираће анонимну функцију задату испод коментара ``promenjeno stanje prekidaca``, а свака промена на пољу ``time`` активираће анонимну функцију задату испод коментара ``promenjena vrednost tajmera``.

.. code-block:: html

    <!doctype html>
    <html>
    <body>
        <h1>Тајмер</h1>
        <audio id="muzikica" controls>
          <source src="../../_images/js/ding.mp3" type="audio/mpeg">
          Ваш прегледач не подржава аудио елемент.
        </audio>

        <form>
            <span margin-right="2px">Преостало време</span>
            <input autofocus id="vreme" type="time" step="1" value="00:00:10"/>
            Укључи: <input type="checkbox" id="prekidac"/>
        </form>
    </body>
    </html>

Функција везана за промену вредности тајмера зауставља претходно одбројавање (ако је било покренуто) и омогућава кориснику да укључи тајмер и тиме почне, односно настави одбројавање.

Функција везана за промену стања прекидача прво проверава да ли је тајмер управо укључен или искључен кликом на ``checkbox`` поље. Ако је укључен, израчунава се преостало време у секундама и започиње одбројавање. Ако је тајмер искључен, зауставља се одбројавање.

Осим ове две функције, потребна је још функција која се извршава сваке секунде (док траје одбројавање) и ажурира преостало време (функција ``tik``), и функција која покреће аудио и искључује тајмер (функција ``sviraj``).

У оквиру ове веб-странице можете да испробате сву функционалност осим покретања звучног фајла. Да би пример био потпуно функционалан, предлажемо да га копирате у неки фајл са екстензијом *.html* на вашем рачунару, а затим да измените атрибут *src* елемента *source*, тако да садржи путању до постојећег фајла на вашем рачунару.

Следи комплетан кôд:

.. petlja-editor:: tajmer_html_js

    main.js
    let tajmer = undefined;
    let preostaloVreme = 0;

    // promenjena vrednost tajmera
    document.getElementById('vreme').addEventListener('change', function(dogadjaj) {
        let checkBox = document.getElementById("prekidac");
        checkBox.disabled = false;
        checkBox.checked = false;
        clearInterval(tajmer);
    });

    // promenjeno stanje prekidaca
    document.getElementById('prekidac').addEventListener('click', function(dogadjaj) {
        let ukljucen = document.getElementById("prekidac").checked;
        if (ukljucen) {
            let t = document.getElementById("vreme").value;
            let hh = parseInt(t.slice(0, 2)) || 0;
            let mm = parseInt(t.slice(3, 5)) || 0;
            let ss = parseInt(t.slice(6, 8)) || 0;
            preostaloVreme = ((hh * 60 + mm) * 60 + ss);
            if (preostaloVreme === 0) {
                sviraj();
            } else {
                tajmer = setInterval(tik, 1000);
            }
        }
        else {
            clearInterval(tajmer);
        }
    });

    function tik() {
        preostaloVreme--;
        let n = preostaloVreme;
        let ss = (n % 60).toString().padStart(2, '0');
        n = Math.trunc(n/60);
        let mm = (n % 60).toString().padStart(2, '0');
        n = Math.trunc(n/60);
        let hh = n.toString().padStart(2, '0');
        let t = document.getElementById("vreme");
        t.value = `${hh}:${mm}:${ss}`;
        if (preostaloVreme == 0) {
            sviraj();
        }
    }

    function sviraj() {
        document.getElementById("muzikica").play();
        clearInterval(tajmer);
        let checkBox = document.getElementById("prekidac");
        checkBox.checked = false;
        checkBox.disabled = true;
    }
    ~~~
    index.html
    <!DOCTYPE html>
    <html lang="sr-Cyrl">
    <head>
        <meta charset="utf-8"/>
        <title>Тајмер</title>
    </head>
    <body>
        <h1>Тајмер</h1>
        <audio id="muzikica" controls>
          <source src="../../_images/js/ding.mp3" type="audio/mpeg">
          Ваш прегледач не подржава аудио елемент.
        </audio>

        <form>
            <span margin-right="2px">Преостало време</span>
            <input autofocus id="vreme" type="time" step="1" value="00:00:10"/>
            Укључи: <input type="checkbox" id="prekidac"/>
        </form>
        <script src="main.js"></script>
    </body>
    </html>

Пример – Аларм
--------------

.. questionnote::
    
    Направите веб-страну која омогућава да се у задато време активира аларм (аудио-фајл који одаберете).

Пример аларма је веома сличан претходном примеру тајмера.

Можемо да искористимо наредбу ``setTimeout`` која ће покренути догађај за пуштање аларма. Кључ је израчунати у милисекундама када треба покренути тај догађај што можемо да урадимо тако што задато време одузмемо од садашњег.

.. petlja-editor:: javascript

    main.js
    let sada = new Date(2022, 0, 1, 13, 0, 0);
    let zadato = new Date(2022, 0, 1, 13, 0, 5);
    document.write('Разлика: ');
    // исписаће 5000 јер је разлика 5 секунди између 2 датума
    // (5000 милисекунди)
    document.write(zadato - sada);
    ~~~
    index.html
    <!doctype html>
    <head>
        <meta charset="utf-8"/>
    </head>
    <body>
        <script src="main.js"></script>
    </body>
    </html>

Да би добили задато време аларма потребно је извући сате, минуте и секунде као у претходном примеру, а потом направити нов датум:

.. code-block:: javascript

    let zadato = new Date(sada.getFullYear(), sada.getMonth(), sada.getDate(), hh, mm, ss);

Претпостављамо да аларм треба да се покрене на исти дан као и садашњи датум. То не мора увек бити случај, нпр. сада је 14 часова али смо поставили да се аларм покреће у 13 часова. Да би решили тај проблем, потребно је да проверимо да ли је задато време у прошлости, и ако јесте да повећамо датум за 1 како би добили сутрашње време.

.. code-block:: javascript

    let sada = new Date();
    // hh, mm и ss израчунамо из задатог времена као у претходном примеру
    // претпоставимо да се аларм покреће данас
    let zadato = new Date(sada.getFullYear(), sada.getMonth(), sada.getDate(), hh, mm, ss);
    // време може бити задато тако да аларм треба тек сутра да се изврши
    // нпр. задамо време 13:00:00, али у тренутку извршавања је 14:00:00
    if (zadato < sada) {
        // у том случају само повећамо дан за један (сутра)
        zadato.setDate(zadato.getDate() + 1);
    }

Следи комплетан кôд:

.. petlja-editor:: alarm_html_js

    main.js
    let tajmer = undefined;

    // promenjena vrednost tajmera
    document.getElementById('vreme').addEventListener('change', function(dogadjaj) {
        let checkBox = document.getElementById("prekidac");
        checkBox.disabled = false;
        checkBox.checked = false;
    });

    // promenjeno stanje prekidaca
    document.getElementById('prekidac').addEventListener('click', function(dogadjaj) {
        let aktiviran = document.getElementById("prekidac").checked;
        if (aktiviran) {
            let sada = new Date();
            let t = document.getElementById("vreme").value;
            let hh = parseInt(t.slice(0, 2)) || 0;
            let mm = parseInt(t.slice(3, 5)) || 0;
            let ss = parseInt(t.slice(6, 8)) || 0;
            let zadato = new Date(sada.getFullYear(), sada.getMonth(), sada.getDate(), hh, mm, ss);
            if (zadato < sada) {
                zadato.setDate(zadato.getDate() + 1);
            }
            tajmer = setTimeout(sviraj, zadato - sada);
        }
        else {
            clearTimeout(tajmer);
        }
    });

    function sviraj() {
        document.getElementById("muzikica").play();
        document.getElementById("prekidac").checked = false;
        clearTimeout(tajmer);
    }
    ~~~
    index.html
    <!DOCTYPE html>
    <html lang="sr-Cyrl">
    <head>
        <meta charset="utf-8"/>
        <title>Аларм</title>
    </head>
    <body>
        <h1>Аларм</h1>
        <audio id="muzikica" controls>
          <source src="../../_images/js/ding.mp3" type="audio/mpeg">
          Ваш прегледач не подржава аудио елемент.
        </audio>

        <form>
            <span margin-right="2px">Време аларма</span>
            <input autofocus id="vreme" type="time" step="1"/>
            Укључи: <input type="checkbox" id="prekidac"/>
        </form>
        <script src="main.js"></script>
    </body>
    </html>
