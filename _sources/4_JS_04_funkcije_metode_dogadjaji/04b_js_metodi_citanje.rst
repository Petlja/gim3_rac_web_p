Методе – функције у објектима
=============================

У претходним лекцијама смо се упознали са објектима који представљају групе повезаних података. Објекти поред података могу да садрже и локалне функције, које се називају методе. Методе су веома сличне обичним функцијама: свака има своје име, могу да добијају параметре и враћају резултат. Разлика је у томе што су методе тесно везане за објекат и служе да приликом позива промене објекат коме припадају или да израчунају неке вредности на основу поља објекта.

Ако објекат има методе, оне се користе слично пољима објеката. Као што се неком пољу приступа тако што се иза имена објекта стави тачка, а онда име поља, тако се и функције објекта (методе) позивају тако што се иза имена објекта коме припадају стави тачка и име функције са заградама, између којих се могу навести параметри:

.. code-block:: javascript

    imeObjekta.imeMetode(<parametri>)

Употребу једне методе смо већ видели у примеру функције ``prikaziTacnoVreme``. Објекти који садрже неки временски тренутак имају (поред осталих) методу ``toLocaleTimeString()``, која враћа стринг са временом тог тренутка, без датума.

.. code-block:: javascript

      function prikaziTacnoVreme() {
        const sada = new Date();
        alert(`Страница је отворена у ${sada.toLocaleTimeString()} сати.`);
      }

У језику *JavaScript* постоји велики број оваквих уграђених објеката, који имају разне готове методе које можемо да користимо.


Методе низова
-------------

Низови у језику *JavaScript* су флексибилне структуре, у које лако можемо да додајемо нове елементе или да из њих избацујемо неке елементе. Ако променљива ``ocene`` садржи низ неких вредности, можемо да користимо следеће функције:

- ``toString()`` ова метода ће вратити стринг који садржи све елементе низа са запетама (зарезима) између елемената.
- ``push(vrednost)`` када се ова метода примени над низом, она ће додати ``vrednost`` на крај низа као нови последњи елемент.
- ``pop()`` када се ова метода примени над низом, она ће уклонити последњи елемент из низа.
- ``join(separator)`` метода веома слична методи ``toString()``, враћа стринг који представља садржај низа. Једина разлика је то што ће уместо запете користити вредност параметра ``separator``, која је прослеђена као параметар.
- ``slice(pocetak, kraj)`` ова метода враћа нови низ, који представља део низа над којим је примењена. Нови низ ће садржати све елементе почевши од елемента на позицији ``pocetak`` до елемента испред позиције ``kraj``.

У следећем примеру можете видети како се користе ове методе над објектом који представља низ оцена:

.. petlja-editor:: metode_niza_js

    main.js
    let ocene = [5, 5, 4, 5];
    ocene.pop();	// ocene = [5,5,4]
    ocene.push(4); 	// ocene = [5,5,4,4]
    ocene.push(5); 	// ocene = [5,5,4,4,5]

    alert( ocene.toString() );  // приказаће се 5,5,4,4,5
    ocene = ocene.slice(1,4); 	// ocene = [5,4,4]
    alert( ocene.join( " : " ) ); // приказаће се 5 : 4 : 4
    ~~~
    index.html
    <!DOCTYPE html>
    <html>
      <head>
        <script src="main.js"></script>
      </head>
      <body>
        <p>Садржај стране (који није обавезан).</p>
      </body>
    </html>

Методе документа стране
-----------------------

Већ смо се упознали са објектом ``document``, преко којег можемо да приступимо *HTML* елементима у страни помоћу неких поља тог објекта. Поред поља са вредностима, овај објекат има и разне методе. Једна од његових метода је и ``document.write``, која може да послужи за додавање садржаја веб-страни. У следећем примеру употребљена је ова метода да дода један параграф:

.. petlja-editor:: novi_tekst_html_js

    main.js
    document.write('<p>Параграф дописан <i>JavaScript</i> наредбом.</p>');
    ~~~
    index.html
    <!DOCTYPE html>
    <html>
      <head>
      </head>
      <body>
        <p>Обичан <i>HTML</i> параграф.</p>

        <script src="main.js"></script>
      </body>
    </html>

На овај начин можемо да додајемо и сложеније структуре веб-страни:

.. petlja-editor:: nova_lista_html_js

    main.js
    document.write('<ul>');
    document.write('    <li>Палеозоик');
    document.write('        <ul>');
    document.write('            <li>Камбријум</li>');
    document.write('            <li>Ордовицијум</li>');
    document.write('            <li>Силур</li>');
    document.write('            <li>Девон</li>');
    document.write('            <li>Карбонифер</li>');
    document.write('            <li>Пермијум</li>');
    document.write('        </ul>');
    document.write('    </li>');
    document.write('    <li>Мезозоик');
    document.write('        <ul>');
    document.write('            <li>Тријас</li>');
    document.write('            <li>Јура</li>');
    document.write('            <li>Креда</li>');
    document.write('        </ul>');
    document.write('    </li>');
    document.write('    <li>Кенозоик');
    document.write('        <ul>');
    document.write('            <li>Терцијар</li>');
    document.write('            <li>Квартар</li>');
    document.write('        </ul>');
    document.write('    </li>');
    document.write('</ul>');
    ~~~
    index.html
    <!DOCTYPE html>
    <html>
      <head>
      </head>
      <body>
        <p>Обичан <i>HTML</i> параграф.</p>
        <script src="main.js"></script>
      </body>
    </html>

Методе документа стране – селектовање елемената
-----------------------------------------------

Објекат ``document`` има и неколико метода које нам омогућавају да пронађемо елементе на страни по идентификатору (атрибуту ``id``), типу елемента, или некој од класа. Најбитније методе објекта ``document`` за приступање *HTML* елементима су:

- ``document.querySelector(cssSelektor)`` проналази први *HTML* елемент у документу који одговара задатом *CSS* селектору.
- ``document.querySelectorAll(cssSelektor)`` проналази све *HTML* елементе у документу који одговарају задатом *CSS* селектору.

Помоћу ових метода проналажење елемената је једноставније од начина које смо до сада користили. Било који елемент који се може описати (и стилизовати) неким *CSS* селектором, може се и пронаћи помоћу ових метода тако што се тај исти селектор проследи као параметар.

Поред ових метода можемо користити још три методе за проналажење објеката по идентификатору, имену елемента, или класи:

- ``document.getElementById(id)`` проналази један *HTML* елемент у документу који има вредност идентификатора, која је прослеђена методи као параметар. Позив ``getElementById('naslov')`` је еквивалентан позиву методе ``querySelector('#naslov')``.
- ``document.getElementsByTagName(name)`` проналази низ *HTML* елемента задатог типа у документу. Позив ``getElementsByTagName('div')`` је еквивалентан позиву методе ``querySelectorАll('div')``.
- ``document.getElementsByClassName(name)``	проналази низ *HTML* елемента у документу, који имају задату класу. Позив ``getElementsByClassName('levo')`` је еквивалентан позиву методе ``querySelectorAll('.levo')``.

Ове методе објекта ``document`` нам омогућавају да претражимо *HTML* документ по различитим критеријумима, нађемо елементе који одговарају неком критеријуму и променимо им нека својства, изглед или чак и садржај. У следећем примеру ћемо *JavaScript* програмом лоцирати одељак *вести* помоћу методе ``getElementById``, а затим ћемо том одељку променити боју позадине:

.. petlja-editor:: lociranje_elementa_html_js

    main.js
    const odeljakVesti = document.getElementById("vesti");
    odeljakVesti.style.backgroundColor = '#C0FFFF';
    ~~~
    index.html
    <!DOCTYPE html>
    <html lang="sr">
        <head>
          <title>Вест</title>
        </head>
        <body>
          <h2>Убацивање текста</h2>
            
          <div id='aktivnosti'>
            <h4>Наше активности</h4>
            <p>Активност број 1</p>
            <p>Активност број 2</p>
          </div>
          <div id='vesti'>
            <h4>Вести</h4>
            <p>Вест број 1</p>
            <p>Вест број 2</p>
          </div>
          <script src="main.js"></script>
       </body>
    </html>

.. questionnote::

    **Вежба 1**

    Замените у претходном кôду наредбе:

    .. code-block:: javascript

        const odeljakVesti = document.getElementById("vesti");
        odeljakVesti.style.backgroundColor = '#C0FFFF';

    ...наредбама...

    .. code-block:: javascript

        const pojedinacneVesti = document.querySelectorAll('#vesti p');
        pojedinacneVesti[0].style.color = 'red';

    ...и покушајте да објасните, пре покретања примера, шта ће бити ефекат ових наредби. Покрените пример и проверите своју претпоставку.


.. questionnote::

    **Вежба 2**

    У претходном примеру додајте следећи кôд:

    .. code-block:: javascript

        const naslovi = document.querySelectorAll('#aktivnosti, #vesti');
        for (let i = 0; i < naslovi.length; i++) {
            const naslov = naslovi[i];
            naslov.style.color = 'green';
        }

    Који је очекиван резултат? Покрените пример и проверите своју претпоставку.


.. questionnote::

    **Вежба 3**

    Користећи ``querySelectorAll`` пронађите све наслове („Убацивање текста“, „Наше активности“ и „Вести“) и обојите им позадину у плаво, без додавања класе или идентификатора наслову „Убацивање текста“.

~~~~

Уместо постављања боје, могли смо, на пример, да убацимо параграф *Најновија вест* у одељак са вестима. Ради тога смо употребили и методе ``document.createElement()``, ``document.createTextNode()``, ``element.appendChild(cvor_dete)`` и ``element_roditelj.insertBefore(novi_element, element_dete)``, за које се не очекује да их у оквиру овог курса запамтите и детаљно познајете. У овом примеру, поменуте методе су употребљене само као илустрација и наговештај могућности употребе *JavaScript* програма у *HTML* странама. По потреби се увек можете вратити на овај пример, или сами пронаћи на интернету сличан пример и детаљнија објашњења.

.. petlja-editor:: nova_vest_html_js

    main.js
    // HTML параграф као објекат у DOM  моделу
    // садржи чвор са текстом као своје поље
    const novaVest = document.createElement("P");
    const cvor = document.createTextNode("Најновија вест");
    novaVest.appendChild(cvor);

    // Убацујемо параграф 'novaVest' у одговарајући одељак
    const odeljakVesti = document.getElementById("vesti");
    odeljakVesti.insertBefore(novaVest, odeljakVesti.children[1]);
    ~~~
    index.html
    <!DOCTYPE html>
    <html lang="sr">
        <head>
          <title>Вест</title>
        </head>
        <body>
          <h2>Убацивање текста</h2>
            
          <div id="aktivnosti">
            <h4>Наше активности</h4>
            <p>Активност број 1</p>
            <p>Активност број 2</p>
          </div>
          <div id="vesti">
            <h4>Вести</h4>
            <p>Вест број 1</p>
            <p>Вест број 2</p>
          </div>
          <script src="main.js"></script>
       </body>
    </html>

.. questionnote::

    **Вежба – нов одељак**

    У претходном примеру користећи ``document.createElement`` i ``document.createTextNode`` додајте нов одељак „Чланови“ са листом неколико имена.

