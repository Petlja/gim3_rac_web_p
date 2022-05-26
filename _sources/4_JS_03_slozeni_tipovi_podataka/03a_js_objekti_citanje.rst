Објекти
=======

У досадашњим примерима смо се сусретали са променљивама које имају једноставне вредности. Свака променљива има у себи само један податак, који може да буде број, текст, итд. (такозвани основни, или прости типови). Међутим, често je потребно користити сложеније структуре података, које у себи садрже по неколико једноставнијих вредности. На пример, да би се сачувале информације о особи, згодно је податке као што су име, презиме, датум рођења и слично објединити у једну целину. У ту сврху користе се објекти. 

Објекат је вредност сложеног типа, коју можемо замислити као групу именованих вредности. Замислите да у програму желимо да користимо разне податке о неком ученику, као што су његово име, старост, град у коме живи, број телефона, имејл, контакт на некој друштвеној мрежи, школа и разред у који иде. Уместо да употребимо осам засебних променљивих за ове податке, могли бисмо да групишемо ове податке и ставимо их у једну променљиву. Такве променљиве можемо да правимо и за друге ученике:

.. image:: ../../_images/js/ucenik_kartoteka.png
    :width: 600px
    :align: center

У језику *JavaScript* се овакви објекти праве тако што се у витичасте заграде ставе имена поља и вредности које ће бити у тим пољима:

.. code-block:: javascript

    let ucenik1 = { ime: "Петар Петровић", godiste: 1998, telefon: "012 345 678" }
    let ucenik2 = { ime: "Марко Марковић", godiste: 1997, telefon: "098 765 432" }

Направили смо две променљиве (``ucenik1`` и ``ucenik2``) које садрже објекте. Имена поља морају да буду у складу са правилима именовања променљивих у *JavaScript*-у (тј. почињу словима, доларом или доњом цртом, а после могу да садрже и цифре), а вредности могу да буду бројеви, стрингови или вредности било којег другог типа, укључујући и друге објекте.

Објекат можемо да направимо и тако што почнемо од потпуно празног објекта

.. code-block:: javascript

    let x = {};

a касније таквом објекту додајемо поља.

.. code-block:: javascript

    x.polje = vrednost;

Пољима у објекту се може приступити по имену коришћењем тачке (нпр. ``имеОбјекта.имеПоља``). У следећем примеру можете да видите како се прави објекат, како се чита податак из њега и како се уписује вредност у неко поље објекта.

.. activecode:: azuriranje_objekta_1_js
    :language: javascript
    :nocodelens:

    let ucenik = { ime: "Петар Петровић", tel: "012 345 678", razred: 6 };
    let razred = ucenik.razred;
    razred = razred + 1;
    ucenik.razred = razred;
    alert(ucenik.razred);
    
У овом случају, вредност објекта је могла да буде промењена и једноставније:

.. activecode:: azuriranje_objekta_2_js
    :language: javascript
    :nocodelens:

    let ucenik = { ime: "Петар Петровић", tel: "012 345 678", razred: 6 };
    ucenik.razred++;
    alert(ucenik.razred);

Ако покушамо да дохватимо вредност непостојећег поља у објекту, добићемо специјалну вредност ``undefined``:

.. activecode:: nepostojece_polje_objekta_js
    :language: javascript
    :nocodelens:

    let ucenik = { ime: "Петар Петровић", tel: "012 345 678", razred: 6 };
    alert(ucenik.eposta);

Поред неиницијализованих поља објеката, вредност ``undefined`` имају и декларисане променљиве које нису иницијализоване:

.. code-block:: javascript

    let n;
    var m;

Вредност ``undefined`` треба схватити као одсуство вредности.

|

Приликом приказивања вредности објекта долази до претварања (конверзије) објекта у стринг, али не на нарочито користан начин:

.. activecode:: ispisivanje_objekta_js
    :language: javascript
    :nocodelens:

    let ucenik = { ime: "Петар Петровић", tel: "012 345 678", razred: 6 };
    alert(ucenik);

Да бисмо уместо резултата ``[object Object]`` добили смисленији запис објекта, треба писати

.. activecode:: ispisivanje_objekta_2_js
    :language: javascript
    :nocodelens:

    let ucenik = { ime: "Петар Петровић", tel: "012 345 678", razred: 6 };
    alert(JSON.stringify(ucenik));

Обрнуто, ако је ``s`` стринг који садржи запис објекта, овако можемо да формирамо објекат на основу таквог стринга и да користимо поља тог објекта (важно је да су у стрингу називи поља и вредности баш под овим, двоструким наводницима, као у примеру):

.. activecode:: ispisivanje_objekta_3_js
    :language: javascript
    :nocodelens:

    let s = '{ "ime": "Петар Петровић", "tel": "012 345 678", "razred": 6 }';
    let ucenik = JSON.parse(s);
    alert(ucenik.ime);

JSON је постао опште прихваћен као начин записивања сложених вредности, а настао је управо у оквиру језика *JavaScript* (скраћеница *JSON* долази од *JavaScript Object Notation*). 


Хијерархија објеката
--------------------

Поменули смо да вредности у објекту могу да буду други објекти. На тај начин објекти могу да формирају хијерархијску структуру. Ево како изгледа таква ситуација:

.. activecode:: hijerarhija_objekta_js
    :language: javascript
    :nocodelens:

    let ucenik = { 
        licniPodaci: { ime: "Петар Петровић", tel: "012 345 678" }, 
        skola: { 
            razred: 6, 
            ocene: { srpski: 5, fizika: 4 },
            izostanci: { opravdani: 27, neopravdani: 1 }
        }
    };

    // Ученик је направио нови неоправдани изостанак
    ucenik.skola.izostanci.neopravdani++;

    alert(`Ученик ${ucenik.licniPodaci.ime} има` + 
        ` ${ucenik.skola.izostanci.neopravdani} неоправданих изостанака.`);


Објектни модел документа стране
-------------------------------

У лекцијама о језику *HTML* смо видели да *HTML* кôд дефинише структуру стране у којој се налази заглавље са насловима и тело са различитим *HTML* елементима. 

.. image:: ../../_images/js/DOM.png
    :width: 600px
    :align: center

У *JavaScript* коду који се извршава у веб странама се може користити један специјалан објекат који се зове *document*. Овај објекат нам омогућава да приступимо *HTML* елементима који се налазе у веб страни и да их читамо и мењамо. Када лоцирамо неки објекат, који представља неки *HTML* елемент у страни, можемо да га променимо тако што му на пример променимо *CSS* стил.

.. activecode:: boja_teksta_html_js
    :language: html
    :nocodelens:

    <!DOCTYPE html>
    <html>
      <head>
      </head>
      <body>
        <p>Боја слова и позадине овог текста је постављена JavaScript наредбом.</p>
        <script>
          document.title = 'Ово је наслов стране';
          let body = document.body;
          body.style.backgroundColor = 'black';
          body.style.color = 'lightgreen';

          let boja = document.body.style.color;
          alert(`Bоја текста у страни је "${boja}"`);
        </script>
      </body>
    </html>

Хијерархија објеката која почиње од документа стране назива се **објектни модел документа** (енгл. *document object model*, скраћено *DOM*). Из *JavaScript* програма можемо да дохватимо сваки елемент стране, да убацујемо и избацујемо елементе, да их допуњујемо и мењамо на различите начине. Следећи пример показује један начин како можемо да дохватимо поједине елементе у хијерархији документа и да тим елементима задамо нови стил.

За сада ћемо употребити својства ``firstElementChild`` за дохватање првог детета и ``nextElementSibling`` за дохватање следећег елемента у истом нивоу хијерархије (следећи брат или сестра). Ова два својства *DOM* објеката су довољна за дохватање било ког елемента, а ускоро ћемо упознати и удобније начине за манипулисање *DOM* објектима.

**Пример - дохватање елемената кроз DOM**

.. activecode:: DOM_hijerarhija_html_js
    :language: html
    :nocodelens:

    <!DOCTYPE html>
    <html>
      <head>
      </head>
      <body>
        <div>
          <p>Овај документ има четири одељка.</p>
          <p>Ово је други параграф првог одељка.</p>
        </div>
        <div>
          <p>Ово је други одељак.</p>
          <p>Стил другог и трећег одељка је подешен програмски.</p>
        </div>
        <div>
          <p>Ово је трећи одељак.</p>
          <p>У трећем одељку други параграф је посебно стилизован.</p>
          <p>У осталим деловима трећег одељка примењује се стил одељка.</p>
        </div>
        <div>
          <p>Четврти одељак изгледа као и први.</p>
          <p>Њихов стил није програмски мењан.</p>
        </div>
        <script>
          let prviOdeljak = document.body.firstElementChild;
          let drugiOdeljak = prviOdeljak.nextElementSibling;
          let treciOdeljak = drugiOdeljak.nextElementSibling;
          let p31 = treciOdeljak.firstElementChild;
          let p32 = p31.nextElementSibling;
          drugiOdeljak.style.backgroundColor = '#C0FFFF';
          drugiOdeljak.style.color = 'blue';
          drugiOdeljak.style.fontSize = "16pt";
          
          treciOdeljak.style.backgroundColor = '#FFFFC0';
          treciOdeljak.style.color = 'brown';
          p32.style.color = 'red';
          p32.style.border = "1px solid red";
        </script>
      </body>
    </html>
