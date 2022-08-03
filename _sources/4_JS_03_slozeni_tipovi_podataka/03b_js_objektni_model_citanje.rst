Објектни модел документа стране
===============================

У лекцијама о језику *HTML* смо видели да *HTML* кôд дефинише структуру стране у којој се налази заглавље са насловима и тело са различитим *HTML* елементима. 

.. image:: ../../_images/js/DOM.png
    :width: 600px
    :align: center

У *JavaScript* кôду који се извршава у веб-странама се може користити један специјалан објекат који се зове *document*. Овај објекат нам омогућава да приступимо *HTML* елементима који се налазе у веб-страни и да их читамо и мењамо. Када лоцирамо неки објекат, који представља неки *HTML* елемент у страни, можемо да га променимо тако што му на пример променимо *CSS* стил.

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
          alert(`Bоја текста у страни је "${boja}".`);
        </script>
      </body>
    </html>

Хијерархија објеката која почиње од документа стране назива се **објектни модел документа** (енгл. *document object model*, скраћено *DOM*). Из *JavaScript* програма можемо да дохватимо сваки елемент стране, да убацујемо и избацујемо елементе, да их допуњујемо и мењамо на различите начине. Следећи пример показује један начин како можемо да дохватимо поједине елементе у хијерархији документа и да тим елементима задамо нови стил.

За сада ћемо употребити својства ``firstElementChild`` за дохватање првог „детета“ и ``nextElementSibling`` за дохватање следећег елемента у истом нивоу хијерархије (следећи „брат“ или „сестра“). Ова два својства *DOM* објеката су довољна за дохватање било ког елемента, а ускоро ћемо упознати и удобније начине за манипулисање *DOM* објектима.

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
          p32.style.border = '1px solid red';
        </script>
      </body>
    </html>
