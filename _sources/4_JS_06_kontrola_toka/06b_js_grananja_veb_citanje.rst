Употреба гранања у веб странама
===============================

Овде ћемо кроз неколико примера илустровати употребу гранања у *JavaScript* програмима у оквиру веб стране.

Пример - Број отварања стране
-----------------------------

.. questionnote::
    
    Направити веб страну која показује колико пута је та страна отворена.

За решавање овог задатка је потребно ван *HTML* стране некако запамтити претходни број посета. У ту сврху можемо да употребимо објекат
``localStorage`` (локално складиште). Помоћу овог објекта можемо да сачувамо разне вредности на нашем рачунару, тако да су нам на располагању када отворимо било коју веб страну са *JavaScript* програмом који приступа објекту ``localStorage``.

Објекат ``localStorage`` има методе:

* ``setItem(kljuc, vrednost)`` - Уписује вредност под именом првог аргумента ”кључ”.
* ``getItem(kljuc)`` - Чита вредност кључа. Уколико вредност није уписана, враћа ``null``.

У следећем решењу најпре проверавамо да ли је нека вредност већ уписана. Ако нема уписане вредности, уписујемо 0 као почетну вредност. Након тога поново читамо вредност (сада знамо да вредност постоји и да је то број), повећавамо је, приказујемо у веб страни и памтимо увећану вредност у локалном складишту.

.. activecode:: broj_otvaranja_strane_html_js
    :language: html
    :nocodelens:

    <!DOCTYPE html>
    <html lang="sr">
      <head>
        <title>Бројач</title>
      </head>
      <body>
        <h1>Број учитавања ове стране: <span id="brp">0</span></h1>
        <script>
          if (!localStorage.getItem('counter')) {
              localStorage.setItem('counter', 0);
          }

          let counter = parseInt(localStorage.getItem('counter'));
          counter++;
          document.querySelector('#brp').innerHTML = counter;
          localStorage.setItem('counter', counter);
        </script>
      </body>
    </html>

.. infonote::

    Уколико вредност постоји, ``localStorage.getItem`` враћа тип ``string``!

    Испробајте следећи код у конзоли:

    .. code-block:: javascript

        localStorage.setItem('broj', 1);
        let vrednost = localStorage.getItem('broj');
        console.log(`Прочитана вредност: ${vrednost}`);
        console.log(`Тип: ${typeof vrednost}`);

Пример - Листа послова са валидацијом података
----------------------------------------------

.. questionnote::
    
    Направити веб страну која одржава листу послова (*to-do list*). Омогућити да се при покушају уноса (клик на дугме) проверава да су подаци заиста унети.

Језик *HTML* (тачније, верзија *HTML5*) омогућава и проверу ваљаности, односно валидацију унетих података. Да бисмо користили валидацију, најпре је потребно да све елементе за унос података окружимо таговима ``<form>`` ... ``</form>``, то јест да те елементе сместимо у формулар. Након тога, валидација се постиже додавањем одређених атрибута појединим пољима за унос и другим елементима. На пример:

- додавањем атрибута ``required`` (без вредности) дефинишемо да поље мора да буде попуњено да би подаци били прихваћени као ваљани;
- додавањем атрибута ``minlength`` и ``maxlength`` дефинишемо најмању, односно највећу дозвољену дужину унетог текста;
- додавањем атрибута ``min`` и ``max`` задајемо најмању, односно највећу бројчану вредност (као што смо раније видели, користе се када је ``type="number"``);

Постоје и други атрибути за наметање додатних ограничења за унете податке ради њиховог прихватања, али њима се нећемо бавити у овом курсу.

Од *HTML* елемената, у веб страну ћемо ставити формулар за задавање послова и табелу која ће да садржи листу послова. Формулар се састоји од поља за опис посла, поља за рок извршења (датум) и дугмета за уписивање посла у табелу. Табела треба на почетку да има само заглавље са две колоне, које смо назвали "шта" и "до кад".

Догађај клика на дугме везујемо за функцију ``posalji``:

.. code-block:: html

    <button type="button" id="dugme_ok">Унеси</button>
    
    ...
    
    document.getElementById('dugme_ok').addEventListener('click', posalji);

Овде смо додали и атрибут ``type="button"``, зато што је за дугме у формулару подразумевани тип ``submit``. Улога таквог дугмета је да податке из формулара проследи на обраду неком другом фајлу, који може да буде и на другом рачунару и оно се понаша нешто другачије. У нашем примеру податке не шаљемо никуда, па нам је потребна функционалност обичног дугмета. Дакле, тип ``button`` постављамо да бисмо добили "обично дугме".

Функција ``posalji`` најпре проверава да ли су при уносу података поштована ограничења. То се постиже линијом

.. code-block:: javascript

    if (stavka.checkValidity() && datum.checkValidity())
    
Метод ``checkValidity()`` поља за унос враћа логичку вредност, која говори да ли је податак унет у пољу у складу са ограничењима.

Ако су подаци коректни, ова функција дохвата тело табеле, формира нови ред у табели и у том реду два пута формира нову ћелију. Обратите пажњу на то да текст који се појављује у ћелији представља посебан објекат (текстуални чвор) у објектном моделу документа стране. Ћелију попуњавамо текстом тако што формирамо текстулани чвор, а затим га додамо ћелији као њен дете-чвор:

.. code-block:: javascript

    tekst  = document.createTextNode("текст који желимо да упишемо");
    novaCelija.appendChild(tekst);

Следи комплетан кôд, који можете да испробате.

.. activecode:: todo_validacija_html_js
    :language: html
    :nocodelens:

    <!DOCTYPE html>
    <html>
      <head>
      <style>
        input:invalid { border: 2px dashed red; }
        input:valid { border: 2px solid black; }
      </style>
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
      </body>
      <script>
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

      </script>
    </html>

.. questionnote::

    **Вежба**

    Измените пример тако да дугме ”Унеси” буде онемогућено док је форма неисправна.

    *Савет:* атрибут ``disabled`` (`HTML button disabled attribute <https://www.w3schools.com/tags/att_button_disabled.asp>`_) се може користити да се дугме онемогући. Догађај ``change`` (`onchange Event <https://www.w3schools.com/jsref/event_onchange.asp>`_) може да послужи за проверу исправности форме приликом промене вредности.


Пример - Штоперица
------------------

.. questionnote::
    
    Направити веб страну која приказује функционалну штоперицу са два дугмета. Кликом на једно дугме се штоперица покреће и зауставља, а на друго се ресетује (враћа на 0).

.. activecode:: stoperica_html_js
    :language: html
    :nocodelens:

    <!DOCTYPE html>
    <html lang="sr">
        <head>
            <title>Штоперица</title>
        </head>
        <body>
            <h1>0</h1>
            <button id="start_stop">Старт</button>
            <button id="reset">Ресет</button>
        </body>
            <script>

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

            </script>
    </html>

.. questionnote::

    **Вежба**

    Штоперицу желе да користе тркачи да измере време сваког круга атлетске стазе. Изменити претходни пример да се дода додатно дугме ”Круг”. Притиском на дугме ”Круг”, време штоперице у тренутку се исписује у листи са редним бројем круга.

Пример - Тајмер
---------------

.. questionnote::
    
    Направити веб страну са тајмером, којим се може задати за колико времена ће бити одсвиран звучни сигнал (аудио фајл који ви одаберете).

Садржај веб стране ће читини 

- један ``audio`` елемент који ће свирати изабрани аудио фајл, 
- ``input`` поље типа ``time`` којим се задаје време преостало до активирања звука
- ``input`` поље типа ``checkbox`` за укључивање тајмера, тј за отпочињање одбројавања.

Клик на ``checkbox`` поље активираће анонимну функцију задату испод коментара ``promenjeno stanje prekidaca``, а свака промена на пољу ``time`` активираће анонимну функцију задату испод коментара ``promenjena vrednost tajmera``.

.. code-block:: html

    <body>
        <h1>Тајмер</h1>
        <audio id="muzikica" controls>
          <source src="../../_images/js/ding.mp3" type="audio/mpeg">
          Ваш прегледач не подржава аудио елемент.
        </audio>

        <form>
            <span margin-right="2px">Преостало време</span>
            <input autofocus id="vreme" type="time" step="1" value="00:00:10""/>
            Укључи: <input type="checkbox" id="prekidac"/>
        </form>
    </body>

Функција везана за промену вредности тајмера зауставља претходно одбројавање (ако је било покренуто) и омогућава кориснику да укључи тајмер и тиме почне, односно настави одбројавање.

Функција везана за промену стања прекидача прво проверава да ли је тајмер управо укључен или искључен кликом на ``checkbox`` поље. Ако је укључен, израчунава се преостало време у секундама и започиње одбројавање. Ако је тајмер искључен, зауставља се одбројавање.

Осим ове две функције, потребна је још функција која се извршава сваке секунде (док траје одбројавање) и ажурира преостало време (функција ``tik``), и функција која покреће аудио и искључује тајмер (функција ``sviraj``).

У оквиру ове веб странице можете да испробате сву функционалност осим покретања звучног фајла. Да би пример био потпуно функционалан, предлажемо да га копирате у неки фајл са екстензијом *.html* на вашем рачунару, а затким да измените атрибут *src* елемента *source*, тако да садржи путању до постојећег фајла на вашем рачунару.

Следи комплетан кôд:

.. activecode:: tajmer_html_js
    :language: html
    :nocodelens:

    <!DOCTYPE html>
    <html lang="sr-Cyrl">
        <head>
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
        </body>
            <script>

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
                        if (preostaloVreme == 0) {
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
            </script>
    </html>

Пример - Аларм
--------------

.. questionnote::
    
    Направити веб страну која омогућава да се у задато време активира аларм (аудио фајл који одаберете).

Пример је веома сличан претходном, тако да ћете га вероватно разумети и без објашњавања.

.. activecode:: alarm_html_js
    :language: html
    :nocodelens:

    <!DOCTYPE html>
    <html lang="sr-Cyrl">
        <head>
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
        </body>
            <script>

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
                        tajmer = setInterval(sviraj, zadato - sada);
                    }
                    else {
                        clearInterval(tajmer);
                    } 
                });

                function sviraj() { 
                    document.getElementById("muzikica").play(); 
                    document.getElementById("prekidac").checked = false;
                    clearInterval(tajmer);
                } 

            </script>
    </html>
