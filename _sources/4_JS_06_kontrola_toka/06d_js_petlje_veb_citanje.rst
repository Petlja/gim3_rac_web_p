Употреба петљи у веб-странама
=============================

Пример – Слајд-шоу
------------------

.. questionnote::
    
    Направити веб-страну која садржи слајд-шоу. На почетку је приказана једна слика и испод ње онолико тачака колико укупно има слика. Слике се редом периодично мењају, док се не кликне на неку од тачака испод слика. Од тог тренутка се на сваки клик на тачку приказује одговарајућа слика.


Ми ћемо у решењу користити ове слике:

.. image:: ../../_images/js/emo1.png
    :width: 100px
.. image:: ../../_images/js/emo2.png
    :width: 100px
.. image:: ../../_images/js/emo3.png
    :width: 100px

Ако желите, можете да преузмете кôд (копирате га у фајл са екстензијом *html*) и прилагодите га, тако да када га отворите директно у прегледачу – он приказује слике по вашем избору.

Приликом стилизовања ограничавамо ширину одељка који садржи слике на 300 пиксела и постављамо га по средини ширине екрана. Ширину овог одељка можете да подесите по жељи, у складу са величином свог екрана.

Класа ``tacka`` представља тачке испод слике, помоћу којих бирамо слику коју желимо да видимо. Тачка је реализована као простор од 15 × 15 пиксела, заобљених углова, тако да се уместо квадрата добије круг (испробајте и вредности мање од 50%, или тачке које су мање или веће од  15 × 15 пиксела). Када је курсор на тачки, мењамо изглед курсора тако да кориснику буде јасно да може да кликне на тачку.

Део дефинисања стила завршавамо подешавајући нешто тамнију боју за тачку која одговара тренутно приказаној слици, као и за тачку изнад које се налази миш.

Од *HTML* елемената имамо само одељак са сликама и одељак са тачкама.

Функција ``prikaziSlajd`` има два аргумента. Први аргумент је редни број слике коју желимо да прикажемо (бројећи од 0), а други говори да ли треба искључити тајмер за периодично мењање слика. Када функцију позивамо због протеклог времена, као други аргумент прослеђујемо ``false`` (периодично мењање се не искључује), а када је позивамо због клика на тачку, прослеђујемо ``true`` (периодично мењање се прекида).

Функција ``sledeciSlajd`` омогућава прелазак на следећу слику. Она се позива на сваких 1500 милисекунди, што такође можете лако да промените.

Следи комплетно решење:

.. activecode:: slajd_sou_html_js
    :language: html
    :nocodelens:

    <!DOCTYPE html>
    <html>
      <head>
        <style>
          
          .omot_slajdova {
            max-width: 300px;
            position: relative;
            margin: auto;
          }
          
          .tacka {
            cursor: pointer;
            height: 15px;
            width: 15px;
            background-color: #bbb;
            border-radius: 50%;
            display: inline-block;
          }
          
          .aktivna_tacka, .tacka:hover {
            background-color: #717171;
          }

        </style>
      </head>
      <body>

        <div class="omot_slajdova">
          <img class="slajd" src="../_images/emo1.png" style="width:100%">
          <img class="slajd" src="../_images/emo2.png" style="width:100%">
          <img class="slajd" src="../_images/emo3.png" style="width:100%">
        </div>

        <div style="text-align:center">
          <span class="tacka" id="t0"></span> 
          <span class="tacka" id="t1"></span> 
          <span class="tacka" id="t2"></span> 
        </div>

        <script>
            let brSlajda = 0;

            function prikaziSlajd(n, klik) {

              // sakrij sve slajdove
              let slajdovi = document.getElementsByClassName("slajd");
              for (let i = 0; i < slajdovi.length; i++) {
                  slajdovi[i].style.display = "none";  
              }

              // neka su sve tacke neaktivne
              let tacke = document.getElementsByClassName("tacka");
              for (let i = 0; i < tacke.length; i++) {
                  tacke[i].classList.remove("aktivna_tacka");
              }

              // prikazi tekucu sliku i oznaci odgovarajucu tacku
              slajdovi[n].style.display = "block";  
              tacke[n].classList.add("aktivna_tacka");

              // ako je kliknuto na tacku, zaustavi tajmer (trajno)
              if (klik) {
                  clearInterval(tajmer);
              }
            }

            function sledeciSlajd() {
                brSlajda++;
                let slajdovi = document.getElementsByClassName("slajd");
                if (brSlajda == slajdovi.length) {
                    brSlajda = 0;
                }
                prikaziSlajd(brSlajda, false);
            }

            prikaziSlajd(0, false);
            let tajmer = setInterval(sledeciSlajd, 1500);

            document.getElementById('t0').addEventListener('click', function(dogadjaj) {
                prikaziSlajd(0, true);
            });
            document.getElementById('t1').addEventListener('click', function(dogadjaj) {
                prikaziSlajd(1, true);
            });
            document.getElementById('t2').addEventListener('click', function(dogadjaj) {
                prikaziSlajd(2, true);
            });

        </script>
      </body>
    </html> 

.. questionnote::

    **Вежба**

    Користећи петље, упростити следећи део кода:

    .. code-block:: javascript

        document.getElementById('t0').addEventListener('click', function(dogadjaj) {
            prikaziSlajd(0, true);
        });
        document.getElementById('t1').addEventListener('click', function(dogadjaj) {
            prikaziSlajd(1, true);
        });
        document.getElementById('t2').addEventListener('click', function(dogadjaj) {
            prikaziSlajd(2, true);
        });

Пример – Календар
-----------------

.. questionnote::
    
    Направите веб-страну која садржи календар за текући месец.

Структура фајла са решењем је овај пут једноставна. Од *HTML* елемената имамо само наслов и табелу са заглављем које садржи скраћене називе дана, а од кôда само функцију ``prikaziMesecniKalendar``, која обавља сав посао, мада је алгоритам по коме је ова функција написана нешто сложенији него у другим примерима.

Функција ``prikaziMesecniKalendar`` најпре боји наслов последње колоне (``нед``) у црвено, а затим дохвата *HTML* наслов и у њега уписује назив текућег месеца и године. У наставку, ова функција попуњава тело табеле датумима текућег месеца.

Петља  ``while`` се извршава докле год су потребни нови редови у календару. У оквиру ове петље имамо петљу ``for``, која попуњава један ред табеле. Приметимо да у првом и последњем реду неке ћелије треба да остану празне. О томе водимо рачуна помоћу пар трикова. Следећи део кôда је вероватно најтежи за разумевање:

.. code-block:: javascript

    let brojDanaUMesecu = new Date(godina, mesec + 1, 0).getDate();
    let prviDan = (new Date(godina, mesec)).getDay(); // 0=ned, 1=pon, 2=uto...
    let datumPrveCelije = [-5, 1, 0, -1, -2, -3, -4]; // ako je prvi u nedelju, prva celija je 'minus peti' itd.
    
    let dan = datumPrveCelije[prviDan];

Нулти датум у следећем месецу је за један мањи од првог датума у следећем месецу, а то је у ствари последњи датум у текућем месецу. Према томе, метода ``.getDate()`` нам враћа последњи датум у текућем месецу, односно број дана текућег месеца.

Метода ``getDay()`` враћа редни број дана у недељи - 0 за недељу , 1 за понедељак, итд, све до 6 за суботу.

На основу редног броја дана, потребно је одредити у коју колону се уписује први датум (број један). На пример, ако променљива ``prviDan`` има вредност 3, први датум текућег месеца је среда, и број 1 треба уписати у колону 3. Замислимо за тренутак да датуми могу да буду и нула или негативни и избројмо датуме уназад до понедељка у истој седмици у којој је први датум у месецу. Од интереса нам је да одредимо који датум би одговарао том понедељку, тј. првој ћелији табеле, макар тај датум био и негативан. Томе служи низ ``datumPrveCelije``. Погледајмо шта се дешава када је ``prviDan == 3``, тј. месец почиње у среду. Елемент низа ``datumPrveCelije`` са индексом 3 је -1, што значи да понедељку у истој седмици (првој ћелији табеле) одговара „минус први“. Заиста, тај понедељак је два дана пре среде првог, па му у овом начину бројања одговара датум -1. Табелу сада попуњавамо као да месец почиње у понедељак минус првог, само водимо рачуна да не приказујемо датуме који не постоје стварно у текућем месецу.

.. code-block:: javascript

    let tekstCelije = document.createTextNode(dan);
    if (dan < 1 || dan > brojDanaUMesecu) {
        tekstCelije = document.createTextNode("");
    }

Последњи детаљ је стављање оквира на датум који представља данашњи дан:

.. code-block:: javascript

    if (dan === datum.getDate()) {
        celija.style.border = "solid 1px";
    }
    
Следи комплетно решење:

.. activecode:: kalendar_html_js
    :language: html
    :nocodelens:

    <!DOCTYPE html>
    <html lang="sr-Cyrl">
        <head>
            <title>Календар</title>
            <script>

                function prikaziMesecniKalendar(datum) {
                    document.getElementById("nedelja").style.color = "red";

                    let meseci = [
                        "Јануар", "Фебруар", "Март", "Април", "Мај", "Јун",
                        "Јул", "Август", "Септембар", "Октобар", "Новембар", "Децембар"
                    ];
                    let mesec = datum.getMonth();
                    let godina = datum.getFullYear();
                    document.getElementById("mesec_i_godina").innerHTML = meseci[mesec] + " " + godina;

                    let teloTabele = document.getElementById("telo_tabele");
                    // nulti datum sledeceg meseca je u stvari poslednji tekuceg meseca
                    let brojDanaUMesecu = new Date(godina, mesec + 1, 0).getDate();
                    let prviDan = (new Date(godina, mesec)).getDay(); // 0=ned, 1=pon, 2=uto...
                    let datumPrveCelije = [-5, 1, 0, -1, -2, -3, -4]; // ako je prvi u nedelju, prva celija je 'minus peti' itd.

                    let dan = datumPrveCelije[prviDan];
                    while (dan <= brojDanaUMesecu) {
                        let redTabele = document.createElement("tr");
                        for (let kolona = 0; kolona < 7; kolona++) {
                            let celija = document.createElement("td");
                            let tekstCelije = document.createTextNode(dan);
                            if (dan < 1 || dan > brojDanaUMesecu) {
                                tekstCelije = document.createTextNode("");
                            }
                            celija.appendChild(tekstCelije);
                            if (dan === datum.getDate()) {
                                celija.style.border = "solid 1px";
                            }
                            redTabele.appendChild(celija);
                            dan++;
                        }
                        teloTabele.appendChild(redTabele);
                    }
                }
                document.addEventListener('DOMContentLoaded', function() {
                    prikaziMesecniKalendar(new Date());
                });

            </script>
        </head>
        <body>
            <h1>Календар</h1>
            <h3 id="mesec_i_godina"></h3>
            <table>
                <thead>
                <tr>
                    <th>Пон</th>
                    <th>Уто</th>
                    <th>Сре</th>
                    <th>Чет</th>
                    <th>Пет</th>
                    <th>Суб</th>
                    <th id="nedelja">Нед</th>
                </tr>
                </thead>

                <tbody id="telo_tabele">
                </tbody>
            </table>
            </body>
    </html>

.. questionnote::

    **Вежба**

    Календар у примеру увек приказује тренутни месец. Измените претходни пример тако да постоје дугмад „Претходни“ и „Следећи“.

    Дугме „Претходни“ треба да прикаже календар за претходни месец.

    Дугме „Следећи“ треба да прикаже календар за следећи месец.
    
Пример – Листа послова са валидацијом и памћењем података
---------------------------------------------------------

.. questionnote::
    
    Направите веб-страну која одржава листу послова (*to-do list*). Омогућите:
    
    - да се при новом отварању стране приказују раније унети послови.
    - да се при покушају уноса (клик на дугме) проверава да ли су подаци заиста унети.

Овај пример је надоградња примера листе послова, којим смо се већ бавили. Нови део се односи само на памћење раније унетих ставки. 

У скрипти имамо два глобална низа: ``stavke``, који памти описе унетих послова, и ``rokovi``, који памти датуме до којих треба обавити посао.

- Функција ``unesi`` уписује дати посао и рок у нови ред табеле, што смо радили и раније.
- Функција ``zapamti`` дописује дати посао и рок на глобалне низове ``stavke`` и ``rokovi`` редом, а затим памти нове вредности целокупних низова у локалном складишту. Пошто у локално складиште можемо да уписујемо само стрингове, потребно је низ претворити у стринг при уписивању, што постижемо методом ``JSON.stringify``.
- Функција ``popuni`` преузима вредности ставки и рокова из локалног складишта (ако постоје) и уписује их у табелу.
- Коначно, функција ``posalji``, која је везана за клик на дугме из формулара, проверава исправност података и, ако су исправни, уписује их у табелу (позивом функције ``unesi``) и памти их у локалном складишту (позивом функције ``zapamti``).

.. activecode:: todo_validation_and_storage_html_js
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
        <script>
            let stavke = [];
            
            function posalji() {
                let stavka = document.querySelector(`#stavka`);
                let datum = document.querySelector(`#datum`);
                if (stavka.checkValidity() && datum.checkValidity()) {
                    unesi(stavka.value, datum.value);
                    zapamti(stavka.value, datum.value);
                } else {
                    alert('Унесите исправне податке');
                }
                return false;
            }
            
            function unesi(stavka, datum) {
                let tabela = document.getElementById('tabela').getElementsByTagName('tbody')[0];
                let noviRed = tabela.insertRow(tabela.rows.length);

                let novaCelija  = noviRed.insertCell(0);
                let tekst  = document.createTextNode(stavka);
                novaCelija.appendChild(tekst);

                novaCelija  = noviRed.insertCell(1);
                tekst  = document.createTextNode(datum);
                novaCelija.appendChild(tekst);
            }

            function zapamti(stavka, datum) {
                stavke.push({
                    stavka,
                    datum
                });
                localStorage.setItem("stavke", JSON.stringify(stavke));
            }

            function popuni() {
                const sacuvaneStavke = JSON.parse(localStorage.getItem("stavke"));
                console.log(stavke);
                if (sacuvaneStavke) {
                    stavke = sacuvaneStavke;
                    for (let i = 0; i < stavke.length; i++) {
                        unesi(stavke[i].stavka, stavke[i].datum);
                    }
                }
            }
            
            popuni();
            document.getElementById('dugme_ok').addEventListener('click', posalji);

        </script>
      </body>
    </html>

.. questionnote::

    **Вежба – брисање ставки**

    Претходни пример памти све ставке које су икад унете. Додајте дугме „Очисти“ које брише све ставке са стране и из ``localStorage``.

.. questionnote::

    **Вежба - брисање појединачне ставке**

    За сваку ставку додајте дугме „Обриши“ које брише само ту ставку из листе и ``localStorage``.
