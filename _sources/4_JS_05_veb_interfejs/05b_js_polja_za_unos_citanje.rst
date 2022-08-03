Поља за унос података
=====================

У претходним лекцијама смо видели како могу да се унесу подаци помоћу *JavaScript* функције ``prompt`` којом можете да унесете једну вредност путем дијалога. *HTML* језик омогућава да у веб-страну поставимо разне *HTML* елементе за прихватање података. Најопштији и вероватно најчешће коришћени елемент је поље за унос, које се обележава тагом ``<input>``.

Елемент ``<input>`` омогућава да се у њега унесе неки податак као што је текст, датум, број и слично. Сваки елемент ``<input>`` има атрибут ``type`` који описује какав податак у њега може да се унесе (нпр. ``text``, ``date``, ``number``). Неки типови поља за унос имају додатне атрибуте, помоћу којих се може додатно ограничити вредност улазног податка коју је могуће унети. На пример, поље за унос бројева нам омогућава да дефинишемо минималну и максималу вредност која се може унети у њега. Поред атрибута ``type``, елемент ``<input>`` обично има и атрибут ``id``, како би му се лакше приступало помоћу *JavaScript* кôда.

Елемент ``<label>`` представља текст који описује шта треба унети у поље за унос. Елементи овог типа имају атрибут ``for``, који садржи вредност имена (атрибут ``name`` у пољу за унос) поља за унос на ког се односи. Овај елемент није само текст. Када кликнете на овај елемент, фокус ће се поставити на поље за које је везан, тако да можете да почнете да уносите податак.

У следећем примеру можете да испробате четири поља за унос података:

.. activecode:: polja_za_unos_html
    :language: html
    :nocodelens:
    
    <!DOCTYPE html>
    <html>
      <head>
      </head>
      <body>
        <label for="ime">Име:</label><br>
        <input type="text" id="ime" name="ime"><br>
        
        <label for="prezime">Презиме:</label><br>
        <input type="text" id="prezime" name="prezime"><br>
        
        <label for="ocena">Оцена (између 1 и 5):</label><br>
        <input type="number" id="ocena" name="ocena" min="1" max="5"><br>
        
        <label for="datum">Датум уноса:</label><br>
        <input type="date" id="datum" name="datum"><br>
      </body>
    </html>

Свако поље има своју ознаку (лабелу) која га референцира путем атрибута ``for``. Осим тога, свако поље за унос има и тип (атрибут ``type``), којим се задаје врста садржаја. Иза сваке лабеле и поља за унос се налази по један *HTML* елемент ``<br>``. Тиме се обезбеђује да се свака лабела и свако поље постави у нови ред. Покрените (ако већ нисте) претходни *HTML* кôд кликом на дугме да бисте видели и испробали поља за унос текста.

|

Као што можете да приметите, језик *HTML* нам омогућава да направимо и сложеније корисничке интерфејсе постављајући различите елементе за унос података. О овим елементима можете научити више на страни `типови улазних поља <https://www.w3schools.com/html/html_form_input_types.asp>`_ сајта *W3schools*. Поред једноставних поља за унос текста, можете да користите поља за потврду (енгл. *checkbox*), радио дугмад, вишелинијске текстове (енгл. *text area*) и слично.

Пошто сви елементи имају свој идентификатор, можемо их у програму лоцирати помоћу методе ``querySelector`` (или ``getElementById``), која ће вратити *JavaScript* објекат који представља то поље за унос. Враћени објекти имају поље ``value`` које садржи вредност која је унета у поље за унос текста.

Претходни пример можемо да допунимо једним дугметом и следећим *JavaScript* кôдом, тако да се кликом на дугме исписују сви унети подаци. Функција ``prikaz`` проналази поља за унос, чита им вредности и приказује поруку да је ученик добио оцену датог дана.

.. activecode:: polja_za_unos_html_js
    :language: html
    :nocodelens:

    <!DOCTYPE html>
    <html>
      <head>
      </head>
      <body>
        <label for="ime">Име:</label><br>
        <input type="text" id="ime" name="ime"><br>
        
        <label for="prezime">Презиме:</label><br>
        <input type="text" id="prezime" name="prezime"><br>
        
        <label for="ocena">Оцена (између 1 и 5):</label><br>
        <input type="number" id="ocena" name="ocena" min="1" max="5"><br>
        
        <label for="datum">Датум уноса:</label><br>
        <input type="date" id="datum" name="datum"><br>
        
        <br>
        <button id="dugme_ok">Потврди</button>
      </body>

      <script>

        function prikaz() {
            let ime = document.querySelector('#ime').value;
            let prezime = document.querySelector('#prezime').value;
            let ocena = document.querySelector('#ocena').value;
            let datum = document.querySelector('#datum').value;
            alert(`${ime} ${prezime} је дана ${datum} добио-добила оцену ${ocena}`);
        }

        document.getElementById("dugme_ok").addEventListener('click', prikaz);

      </script>

    </html>


Пример – Листа послова
''''''''''''''''''''''

Ево како би могло да се започне прављење веб-стране за одржавање листе актуелних послова (енгл. *to-do list*):

.. activecode:: todo_lista_html_js
    :language: html
    :nocodelens:

    <!DOCTYPE html>
    <html>
      <head>

      </head>
      <body>
          <label for="stavka">Шта желиш да урадиш:</label><br>
          <input type="text" id="stavka" required><br>
          
          <label for="datum">Рок:</label><br>
          <input type="date" id="datum" required><br>
          
          <br>
          <button id="dugme_ok">Унеси</button>
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
        function unesi() {
            let stavka = document.querySelector('#stavka');
            let datum = document.querySelector('#datum');

            let tabela = document.getElementById('tabela').getElementsByTagName('tbody')[0];
            let noviRed = tabela.insertRow(tabela.rows.length);

            let novaCelija  = noviRed.insertCell(0);
            let tekst  = document.createTextNode(stavka.value);
            novaCelija.appendChild(tekst);

            novaCelija  = noviRed.insertCell(1);
            tekst  = document.createTextNode(datum.value);
            novaCelija.appendChild(tekst);
        }
        
        document.getElementById("dugme_ok").addEventListener('click', unesi);

      </script>
    </html>

Да би употреба ове стране била удобна, недостаје бар још памћење раније унетих ставки и поништавање (прецртавање или брисање или оба) урађених послова. На овај пример ћемо се вратити и дорадити га касније.

.. comment

    Пример – поље за унос и *Bootstrap* стилови
    '''''''''''''''''''''''''''''''''''''''''''

    Уколико користите *Twitter Bootstrap*, имате могућност да лако додатно стилизујете поља за унос података. Помоћу библиотеке *Twitter Bootstrap* можете да окружите ознаку и поље за унос текста блоком који има класу ``form-group`` и у њега ставите елементе ``<label>`` и ``<input>``, без потребе да их одвајате елементом ``<br>``:

    .. activecode:: tb_input_html_js
        :language: html
        :nocodelens:

        <!DOCTYPE html>
        <html lang="en">
        <head>
          <title>Страна са укљученом Bootstrap библиотеком</title>
          <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css">
          <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.0/jquery.min.js"></script>
          <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.7/umd/popper.min.js"></script>
          <script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js"></script>
        </head>
        <body>
        <div class="container-fluid">
          <div class="form-group">
             <label for="ime">Име:</label>
             <input type="text" id="ime" name="ime" class="form-control"/>
          </div>
        </div>
        </body>
        </html>

    На поља за унос је потребно поставити класу ``form-control`` како би се применио *Bootstrap* стил. *Bootstrap* има велики број класа којима можете стилизовати оваква поља.

    На сајту *W3schools* можете наћи више информација 
    `о стилизовању поља за унос <https://www.w3schools.com/bootstrap4/bootstrap_forms_inputs.asp>`_ помоћу библиотеке *Twitter Bootstrap*.

