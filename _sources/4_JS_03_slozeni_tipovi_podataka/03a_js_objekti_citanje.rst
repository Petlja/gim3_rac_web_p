Објекти
=======

У досадашњим примерима смо се сусретали са променљивама које имају једноставне вредности. Свака променљива има у себи само један податак, који може да буде број, текст, итд. (То су такозвани основни, или прости типови.) Међутим, често je потребно користити сложеније структуре података, које у себи садрже по неколико једноставнијих вредности. На пример, да би се сачувале информације о особи, згодно је податке као што су име, презиме, датум рођења и слично објединити у једну целину. У ту сврху користе се објекти.

**Објекат је вредност сложеног типа**, коју можемо замислити као групу именованих вредности. Замислите да у програму желимо да користимо разне податке о неком ученику, као што су његово име, старост, град у коме живи, број телефона, имејл, контакт на некој друштвеној мрежи, школа и разред у који иде. Уместо да употребимо осам засебних променљивих за ове податке, могли бисмо да групишемо ове податке и ставимо их у једну променљиву. Такве променљиве можемо да правимо и за друге ученике.

.. image:: ../../_images/js/ucenik_kartoteka.png
    :width: 600px
    :align: center

У језику *JavaScript* се овакви објекти праве тако што се у витичасте заграде ставе имена поља и вредности које ће бити у тим пољима:

.. petlja-editor:: js_objects_1

    main.js
    let ucenik1 = {
        ime: "Петар Петровић",
        godiste: 1998,
        telefon: "012 345 678"
    };
    let ucenik2 = {
        ime: "Марко Марковић",
        godiste: 1997,
        telefon: "098 765 432"
    };
    alert(ucenik1.ime);
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

Направили смо две променљиве (``ucenik1`` и ``ucenik2``) које садрже објекте. Имена поља морају да буду у складу са правилима именовања променљивих у Јаваскрипту (тј. да почињу словима, доларом или доњом цртом, а после могу да садрже и цифре), а вредности могу да буду бројеви, стрингови или вредности било којег другог типа, укључујући и друге објекте.

Објекат можемо да направимо и тако што почнемо од потпуно празног објекта, a касније таквом објекту додајемо поља.

.. petlja-editor:: js_objects_2

    main.js
    let ucenik = {};
    ucenik.ime = "Петар Петровић";
    ucenik.godiste = 1998;
    ucenik.telefon = "012 345 678";
    alert(ucenik.ime);
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

Пољима у објекту се може приступити по имену коришћењем тачке (нпр. ``ucenik.ime``).

У следећем примеру можете да видите како се прави објекат, како се чита податак из њега и како се уписује вредност у неко поље објекта.

.. petlja-editor:: azuriranje_objekta_1_js

    main.js
    let ucenik = {
        ime: "Петар Петровић",
        tel: "012 345 678",
        razred: 6
    };
    // ученик прелази у следећи разред
    ucenik.razred = ucenik.razred + 1;
    // или
    // ucenik.razred++;
    alert(`Ученик ${ucenik.ime} је у ${ucenik.razred}. разреду.`);
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

Ако покушамо да дохватимо вредност непостојећег поља у објекту, добићемо специјалну вредност ``undefined``. Вредност ``undefined`` треба схватити као одсуство вредности.

.. petlja-editor:: nepostojece_polje_objekta_js

    main.js
    let ucenik = {
        ime: "Петар Петровић",
        tel: "012 345 678",
        razred: 6
    };
    alert(ucenik.eposta);
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

.. infonote::

    Поред неиницијализованих поља објеката, вредност ``undefined`` имају и декларисане променљиве које нису иницијализоване:

    .. code-block:: javascript

        let n;
        var m;

Хијерархија објеката
--------------------

Поменули смо да вредности у објекту могу да буду други објекти. На тај начин објекти могу да формирају хијерархијску структуру.

Погледајмо пример у ком ученик похађа школу. Можемо да ученику доделимо поље ``skolskaGodina`` која ће бити објекат и представљаће оцене и изостанке тренутне школске године. Оцене се заводе под предметима па нам је потребно да оцене такође буду објекат. Када желимо да приступимо оценама морамо да испратимо хијерархију: ученик → школска година → оцене → предмет.

.. petlja-editor:: hijerarhija_objekta_js

    main.js
    let ucenik = { 
        licniPodaci: {
            ime: "Петар Петровић",
            tel: "012 345 678"
        },
        skolskaGodina: {
            izostanci: { opravdani: 27, neopravdani: 1 },
            ocene: { srpski: 5, fizika: 4 }
        }
    };

    // Ученик је направио нови неоправдани изостанак
    ucenik.skolskaGodina.izostanci.neopravdani++;

    // Ученик је добио петицу из физике
    ucenik.skolskaGodina.ocene.fizika = 5;

    alert(`Ученик ${ucenik.licniPodaci.ime} има` + 
        ` ${ucenik.skolskaGodina.izostanci.neopravdani} неоправданих изостанака.`);
    alert(`Ученик ${ucenik.licniPodaci.ime} има оцену` +
        ` ${ucenik.skolskaGodina.ocene.fizika} из физике.`);
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

Објекат као стринг
------------------

Приликом приказивања вредности објекта долази до претварања (конверзије) објекта у стринг, али не на нарочито користан начин. Резултат конверзије било ког објекта у стринг је ``[object Object]``.

.. petlja-editor:: ispisivanje_objekta_js

    main.js
    let ucenik = {
        ime: "Петар Петровић",
        tel: "012 345 678",
        razred: 6
    };
    alert(ucenik);
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

Да бисмо добили смисленији запис објекта на располагању нам је метода ``JSON.stringify``. *JSON* је настао у оквиру језика *JavaScript* (скраћеница *JSON* долази од *JavaScript Object Notation*), али се често користи и у другим програмским језицима. Предност *JSON* формата је његова могућност да опише комплексне структуре података и притом одржи читљивост.

.. code-block:: json
    :caption: Ученик представљен форматом *JSON*

    {
      "licniPodaci": {
        "ime": "Петар Петровић",
        "tel": "012 345 678"
      },
      "skolskaGodina": {
        "izostanci": {
          "opravdani": 27,
          "neopravdani": 1
        },
        "ocene": {
          "srpski": 5,
          "fizika": 4
        }
      }
    }

.. petlja-editor:: ispisivanje_objekta_2_js

    main.js
    let ucenik = {
        licniPodaci: {
            ime: "Петар Петровић",
            tel: "012 345 678"
        },
        skolskaGodina: {
            izostanci: { opravdani: 27, neopravdani: 1 },
            ocene: { srpski: 5, fizika: 4 }
        }
    };
    alert(JSON.stringify(ucenik, null, 2));
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

Обрнуто, ако је ``s`` стринг који садржи запис објекта, овако можемо да формирамо објекат на основу таквог стринга и да користимо поља тог објекта (важно је да су у стрингу називи поља и вредности баш под овим, двоструким наводницима, као у примеру):

.. petlja-editor:: ispisivanje_objekta_3_js

    main.js
    let s = '{ "ime": "Петар Петровић", "tel": "012 345 678", "razred": 6 }';
    let ucenik = JSON.parse(s);
    alert(ucenik.ime);
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
