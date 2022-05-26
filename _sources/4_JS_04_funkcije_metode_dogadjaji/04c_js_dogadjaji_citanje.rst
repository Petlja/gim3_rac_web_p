Догађаји
========

До сада смо видели један мали део могућности језика *JavaScript* у манипулисању садржајем и изгледом веб страна. Највећи недостатак у досадашњим примерима је што се програмски кôд извршава одмах по учитавању стране. Сада ћемо видети како можемо да пишемо *JavaScript* кôд који ће се извршавати као одговор на задати догађај, чиме наше веб стране постају интерактивне.

*JavaScript* нам омогућава да дефинишемо каква акција треба да се изврши када се нешто деси у веб страни или на неком њеном елементу. Примери таквих догађаја су: завршено учитавање веб стране, клик на неки елемент, прелазак мишем преко неког елемента, истек неког задатог времена и слично.

Догађаји на елементима стране
-----------------------------

Да бисмо омогућили реаговање на догађаје, потребно је да некако повежемо изабрани догађај са *JavaScript* функцијом која ће се извршити при настанку тог догађаја. 

Када се ради о догађајима који се дешавају на одређеном *HTML* елементу, један начин да повежемо догађаје са *JavaScript* функцијама је да у *JavaScript* коду дохватимо тај *HTML* елемент и позовемо његов методу ``addEventListener``. Ова метода може да буде позвана са различитим листама параметара. Најједноставнији начин позивања је са само два параметра: стринг који представља назив догађаја и име функције која се извршава на тај догађај. Примери назива неких догађаја су:

.. csv-table:: Неки често коришћени догађаји
    :header: "Назив догађаја", "Опис догађаја"
    :widths: 20, 80
    :align: left

    ``click``,      "Клик мишем на *HTML* елемент"
    ``mouseenter``, "Наилазак мишем на *HTML* елемент"
    ``mouseover``,  "Померање миша по *HTML* елементу"
    ``mouseout``,   "Излазак (показивача) миша из области елемента"
    ``keydown``,    "Притисак на тастер на тастатури (док је дати *HTML* елемент у фокусу)"
    ``change``,     "Промена *HTML* елемента. Ово је догађај који се углавном користи на елементима за унос података, о чему ће бити речи ускоро."

Назив догађаја је осетљив на мала и велика слова и важно је да буде написан тачно како је наведено.

Следећи *HTML* кôд садржи пример коришћења догађаја ``click``, ``mouseenter`` и ``mouseout``. Покрените пример и испробајте функционисање догађаја. Да не бисте мењали положај миша при затварању ``alert`` дијалога, за затварање користите тастер *Enter* или тастер *Escape*.
                                                    
.. activecode:: dogadjaji_paragraf_html
    :language: html
    :nocodelens:
    
    <!DOCTYPE html>
    <html>
        <head>
            <title>Догађаји</title>
        </head>
        <body>
            <h2>Пример дефинисања догађаја</h2>

            <p id="prvi">Кликни на овај параграф.</p>
            <p id="drugi">Кликни или пређи мишем преко овог параграфа.</p>
         </body>
        <script>

            function klik(dogadjaj) {
                alert(`Кликнули сте на параграф у коме пише "${dogadjaj.currentTarget.innerText}"`);
            }
            
            function dolazakMisa(dogadjaj) {
                alert(`Наишли сте мишем на параграф у коме пише "${dogadjaj.currentTarget.innerText}"`);
            }

            function odlazakMisa(dogadjaj) {
                alert(`Напустили сте мишем параграф у коме пише "${dogadjaj.currentTarget.innerText}"`);
            }

            let p1 = document.getElementById('prvi');
            p1.addEventListener('click', klik);
            
            let p2 = document.getElementById('drugi');
            p2.addEventListener('click', klik);
            p2.addEventListener('mouseenter', dolazakMisa);
            p2.addEventListener('mouseout', odlazakMisa);
            
        </script>
    </html>

.. comment

    Други начин да повежемо догађаје са *JavaScript* функцијама је да *HTML* елементу додамо атрибут који одговара изабраном догађају, а као вредност атрибута упишемо позив *JavaScript* функције која се том догађају придружује. На пример:

    .. activecode:: dogadjaji_paragraf_atributi_html
        :language: html
        :nocodelens:
        
        <!DOCTYPE html>
        <html>
            <head>
                <title>Догађаји</title>
                <script>

                    function klik(element) {
                        alert(`Кликнули сте на параграф у коме пише "${element.innerText}"`);
                    }
                    
                    function dolazakMisa(element) {
                        alert(`Наишли сте мишем на параграф у коме пише "${element.innerText}"`);
                    }

                    function odlazakMisa(element) {
                        alert(`Напустили сте мишем параграф у коме пише "${element.innerText}"`);
                    }
                    
                </script>
            </head>
            <body>
                <h2>Пример дефинисања догађаја</h2>

                <p onclick="klik(this)">Кликни на овај параграф.</p>
                <p onclick="klik(this)" onmouseenter="dolazakMisa(this)" onmouseout="odlazakMisa(this)">Кликни или пређи мишем преко овог параграфа.</p>
             </body>
        </html>

    Аргумент ``this`` увек означава сам *HTML* елемент у коме се ``this`` помиње, то јест елемент на коме се десио догађај (тачније, ``this`` означава *JavaScript* објекат који представља поменути *HTML* елемент). На пример, у контексту


    .. code-block:: html

        <p onclick="klik(this)">Кликни на овај параграф.</p>

    аргумент ``this`` представља параграф у коме пише "Кликни на овај параграф." (у облику *JavaScript* објекта).

У овом примеру функције ``klik``, ``dolazakMisa`` и ``odlazakMisa`` се позивају када наступи одговарајући догађај. Ове функције као параметар добијају објекат који садржи информације о догађају. Између осталог, поље ``currentTarget`` овог објекта представља *HTML* елемент на коме се десио догађај. На тај начин функција "зна" одакле је позвана и може да прочита вредности атрибута или текстуални садржај прослеђеног елемента.

*JavaScript* објекти који представљају *HTML* елементе имају поље ``innerHTML``, које представља садржај елемента. Коришћењем овог поља, функција може не само да чита него и да мења садржај елемента. Испробајте!


Остали догађаји
---------------

Неки догађаји нису везани за одређени *HTML* елемент. У том случају можемо да користимо методу ``document.addEventListener`` да бисмо повезали дати догађај са *JavaScript* кодом који се на тај догађај извршава. И у овом случају ћемо методи ``addEventListener`` прослеђивати два аргумента: назив догађаја и назив функције коју на тај догађај желимо да извршимо.

.. comment

    ``onload`` дешава се када се учита страна.

На пример, догађај ``DOMContentLoaded`` наступа када се садржај стране учита у објектни модел. Овом догађају можемо да придружимо функцију ``postavi`` на следећи начин:

.. code-block:: javascript

    document.addEventListener('DOMContentLoaded', postavi);

Овим постижемо да се функција ``postavi`` изврши након учитавања стране у објектни модел. На овај начин можемо да извршавамо и разна почетна подешавања изгледа и садржаја веб стране из *JavaScript* кода убрзо по отварању те стране.

Веб страна се учитава и интерпретира редом како је написана. Ако *JavaScript* кôд пишемо у заглављу документа, покушај да приступимо *HTML* елементима из кода који се одмах извршава (на пример, написан је ван функција) доводи до грешке, јер страна још није у потпуности учитана. Један од начина да овај проблем превазиђемо је употреба метода ``document.addEventListener`` са параметром ``DOMContentLoaded``.

Осим методе ``document.addEventListener`` можемо да користимо и методу ``setInterval``. Ова метода се користи када неку *JavaScript* функцију желимо да извршавамо периодично, на сваких *n* милисекунди. Први аргумент методе ``setInterval`` је име функције коју извршавамо, а други аргумент је интервал у милисекундама између узастопних покретања функције. Извршавањем методе ``setInterval`` постижемо да се догађај часовника који је повезан са наведеном *JavaScript* функцијом генерише у задатим интервалима. На пример, позивом

.. code-block:: javascript

    setInterval(tik, 1000);

постижемо да се догађај који покреће функцију ``tik`` генерише на сваких 1000 милисекунди, тј. једном у секунди. Свако генерисање овог догађаја покреће функцију ``tik``.

Ако постоји потреба да се касније престане са генерисањем овог догађаја, запамтићемо вредност коју враћа метода ``setInterval``:

.. code-block:: javascript

    tiktanje = setInterval(tik, 1000);

а на другом месту у коду можемо на овај начин да прекинемо са генерисањем догађаја који покреће функцију ``tik``:

.. code-block:: javascript

    clearInterval(tiktanje);

Следи комплетан пример који илуструје употребу метода ``document.addEventListener`` и ``clearInterval``. Испробајте га!

.. activecode:: casovnik_html
    :language: html
    :nocodelens:

    <!DOCTYPE html>
    <html>
        <head>
            <title>Часовник</title>
            <script>

                function tik() {
                    document.querySelector('h1').innerHTML = `${new Date().toLocaleTimeString()}`;
                }
                
                function postavi() {
                    setInterval(tik, 1000);
                }

                document.addEventListener('DOMContentLoaded', postavi);

            </script>
        </head>
        <body>
            <h1></h1>
        </body>
    </html>

.. comment

    Пример – Тренутно време
    -----------------------

    Потребно је направити веб страну у којој ће се налазити једно заглавље (нпр. елемент <h1>). Када корисник пређе мишем преко тог заглавља потребно је приказати тренутно време у њему.

    .. code-block:: html

        <!DOCTYPE html>
        <html>
        <body>

        <h1 onmouseover="prikaziVreme(this)">Пређи мишем да видиш колико је сати!</h1>

        <script>
        function prikaziVreme(zaglavlje) {
          zaglavlje.innerHTML = `${new Date().toLocaleString()}. Пређи мишем опет!`;
        }
        </script>
        </body>
        </html>

Пример - Повећавање слике
'''''''''''''''''''''''''

У следећем примеру дата је веб страна са ове 3 слике:

.. image:: ../../_images/js/emo1.png
    :width: 100px
.. image:: ../../_images/js/emo2.png
    :width: 100px
.. image:: ../../_images/js/emo3.png
    :width: 100px


За сваку слику догађај наиласка мишем на слику (``onmouseover``) и догађај одласка миша из области слике (``onmouseout``) повезани су са функцијом која мења величину слике. Конкретно, при наиласку мишем на слику, она постаје два пута већа од њене природне величине, а при одласку миша са слике она се враћа на природну величину.

.. activecode:: vece_i_manje_slike_html
    :language: html
    :nocodelens:

    <!DOCTYPE html>
    <html lang="sr">
        <head>
            <title>Слике</title>
        </head>
        <body>
            <h2>Повећавање и смањивање слика</h2>
           
            <img id="emo1" src="../_images/emo1.png" alt="Prva slika">
            <img id="emo2" src="../_images/emo2.png" alt="Druga slika">
            <img id="emo3" src="../_images/emo3.png" alt="Treca slika">

            <p> Позиционирањем миша на слику, она се увећава. </p>
         </body>
        <script>

            // funkcija menja velicinu slike
            function vel(slika, faktor) {
                slika.style.width = `${slika.naturalWidth * faktor}px`;
                slika.style.height = `${slika.naturalHeight * faktor}px`;
            }
            
            function dolazakMisa(dogadjaj) {
                vel(dogadjaj.currentTarget, 2);
            }
            function odlazakMisa(dogadjaj) {
                vel(dogadjaj.currentTarget, 1);
            }

            document.getElementById('emo1').addEventListener('mouseenter', dolazakMisa);
            document.getElementById('emo1').addEventListener('mouseout', odlazakMisa);
            document.getElementById('emo2').addEventListener('mouseenter', dolazakMisa);
            document.getElementById('emo2').addEventListener('mouseout', odlazakMisa);
            document.getElementById('emo3').addEventListener('mouseenter', dolazakMisa);
            document.getElementById('emo3').addEventListener('mouseout', odlazakMisa);

        </script>
    </html>

Догађаји и анонимне функције
----------------------------

Исти ефекат привременог повећавања слике при преласку мишем преко ње може да се постигне и мало другачијим кодом. Као други параметар методе ``addEventListener`` уместо назива функције можемо да наведемо комплетну дефиницију функције. Приметимо да тако уметнуте функције нигде нису именоване, па су због тога познате као анонимне функције (а понекад их називамо и ламбда-функције). Пошто немају име, анонимне функције се могу користити само на једном месту у коду и само у једну сврху (за употребу функције на другим местима у коду потребно је да функција има име).

Употреба анонимних функција (навођење целе функције тамо где се очекује њено име) је честа у језику *JavaScript*, а следећи пример показује како та употреба изгледа.

.. activecode:: vece_i_manje_slike_anonimne_funkcije_html
    :language: html
    :nocodelens:

    <!DOCTYPE html>
    <html lang="sr">
        <head>
            <title>Слике</title>
        </head>
        <body>
            <h2>Повећавање и смањивање слика</h2>
           
            <img id="emo1" src="../_images/emo1.png" alt="Prva slika" >
            <img id="emo2" src="../_images/emo2.png" alt="Druga slika">
            <img id="emo3" src="../_images/emo3.png" alt="Treca slika">

            <p> Позиционирањем миша на слику, она се увећава. </p>
         </body>
        <script>

            // funkcija menja velicinu slike
            function vel(slika, faktor) {
                slika.style.width = `${slika.naturalWidth * faktor}px`;
                slika.style.height = `${slika.naturalHeight * faktor}px`;
            }

            let sl1 = document.getElementById('emo1');
            sl1.addEventListener('mouseenter', function(dogadjaj) {
                vel(sl1, 2);
            });
            sl1.addEventListener('mouseout', function(dogadjaj) {
                vel(sl1, 1);
            });

            let sl2 = document.getElementById('emo2');
            sl2.addEventListener('mouseenter', function(dogadjaj) {
                vel(sl2, 2);
            });
            sl2.addEventListener('mouseout', function(dogadjaj) {
                vel(sl2, 1);
            });

            let sl3 = document.getElementById('emo3');
            sl3.addEventListener('mouseenter', function(dogadjaj) {
                vel(sl3, 2);
            });
            sl3.addEventListener('mouseout', function(dogadjaj) {
                vel(sl3, 1);
            });

        </script>
    </html>


.. comment

    Варијанта са атрибутима ``onmouseover`` ``onmouseout`` у *HTML* елементима који садрже слике.

    .. activecode:: vece_i_manje_slike_html2
        :language: html
        :nocodelens:

        <!DOCTYPE html>
        <html lang="sr">
            <head>
                <title>Слике</title>
                <script>

                    // funkcija menja velicinu slike
                    function vel(slika, faktor) {
                        slika.style.width = `${slika.naturalWidth * faktor}px`;
                        slika.style.height = `${slika.naturalHeight * faktor}px`;
                    }

                </script>
            </head>
            <body>
                <h2>Повећавање и смањивање слика</h2>
               
                <img onmouseover="vel(this, 2)" onmouseout="vel(this, 1)" src="../_images/emo1.png">
                <img onmouseover="vel(this, 2)" onmouseout="vel(this, 1)" src="../_images/emo2.png">
                <img onmouseover="vel(this, 2)" onmouseout="vel(this, 1)" src="../_images/emo3.png">

                <p> Позиционирањем миша на слику, она се увећава. </p>
             </body>
        </html>

.. comment

    помоћу ``for`` наредбе

    .. activecode:: vece_i_manje_slike_html3
        :language: html
        :nocodelens:
        
        <!DOCTYPE html>
        <html>
        <head>


        </head>
        <body onclick="popraviSlike(this)">

        <img id="emo1" src="../_images/emo1.png" alt="Prva slika">
        <img id="emo2" src="../_images/emo2.png" alt="Druga slika">
        <img id="emo3" src="../_images/emo3.png" alt="Treca slika">

        </body>
        <script>

            // funkcija menja velicinu slike
            function vel(slika, faktor) {
                slika.style.width = `${slika.naturalWidth * faktor}px`;
                slika.style.height = `${slika.naturalHeight * faktor}px`;
            }

            for (let sl of document.images) {
                sl.addEventListener('mouseenter', function(dogadjaj) { 
                    vel(dogadjaj.currentTarget, 2); 
                });
                sl.addEventListener('mouseout', function(dogadjaj) { 
                    vel(dogadjaj.currentTarget, 1); 
                });
            }

        </script>
        </html>
