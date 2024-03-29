Нумеричке вредности и изрази
============================

Тип који садржи нумеричке вредности (бројеве) је тип *number*. За разлику од већине других програмских језика, *JavaScript* користи један тип за целе и реалне бројеве. Правила за писање бројева су практично иста у свим програмским језицима. Неки примери исправно написаних вредности (константи) типа *number* су дати у следећој табели.

.. csv-table:: Бројчане вредности
    :header: "JavaScript", "Математика"
    :widths: 20, 80
    :align: left

    ``0``,                :math:`0`
    ``123``,              :math:`123`
    ``-57``,              :math:`-57`
    ``37.4``,             :math:`37.4`
    ``0.217e-9``,         :math:`0.217\cdot 10^{-9}`
    ``-1e6``,             :math:`-1 \cdot 10^6`

**Бројчани изрази** се формирају слично као у математици, користећи бројчане вредности (променљиве и константе), знакове операција, математичке функције и заграде. На пример:

.. csv-table:: Бројчани изрази
    :header: "JavaScript", "Математика"
    :widths: 20, 80
    :align: left

    ``a + b``,                         :math:`a + b`
    ``a * b``,                         :math:`a \cdot b` (или само :math:`a b`)
    ``a / b - c``,                     :math:`{a \over b} - c`
    ``a / (b - c)``,                   :math:`a \over {b-c}`
    ``a / b / c``,                     :math:`{a \over b} \over c`
    ``a / (b / c)``,                   :math:`a \over {b \over c}`
    ``2 ** (n + 1)``,                  :math:`2^{n+1}`
    ``2 ** n + 1``,                    :math:`2^n + 1`
    ``Math.sqrt(Math.abs(x)+1)``,      :math:`\sqrt{|x| + 1}`
    ``Math.sqrt(Math.abs(x))+1``,      :math:`\sqrt{|x|} + 1`
    ``Math.sqrt(x ** 2 + y ** 2)``,    :math:`\sqrt{x^2 + y^2}`
    ``Math.sin(2*x + Math.PI/4)``,     :math:`\sin(2 \cdot x + {\pi \over 4})`

На пример, следећи програм исписује вредност 5, јер је :math:`\sqrt{3^2 + 4^2} = 5`.

.. petlja-editor:: koren_primer_js

    main.js
    const x = 3;
    const y = 4;
    alert(Math.sqrt(x ** 2 + y ** 2));
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

Приоритет операција је у суштини исти као у математици. Ако нисте сигурни у вези са приоритетом, користите заграде (непотребне заграде нису грешка).

Поред ових оператора који имају своје парњаке у математици, у Јаваскрипту постоје још неки оператори.

Оператор ``%`` представља рачунање остатка при дељењу. На пример, остатак при дељењу 7 са 3 је један, па израз ``7 % 3`` има вредност један. Проверимо:

.. petlja-editor:: ostatak_js

    main.js
    alert(7 % 3); // 1
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

Оператор ``++`` повећава дату вредност за један (ово је унарни оператор, што значи да се примењује на једну нумеричку вредност). Слично томе, оператор ``--`` смањује дату вредност за један. Извршавањем следећег примера потврдите своје разумевање ових оператора.

.. petlja-editor:: plusplus_minusminus_js

    main.js
    let a = 5;
    a++;
    a++;
    alert(a); // 7
    a--;
    alert(a); // 6
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

Оператор ``+=`` је бинарни оператор којим се вредност лево од оператора (која мора бити променљива) увећава за вредност десно од оператора. На пример, наредбом ``а+=3;`` се вредност ``a`` увећава за 3. На сличан начин, операторима ``-=``, ``*=`` и ``/=`` се лева вредност умањује, множи или дели десном вредношћу. Проверите ово на следећем примеру:

.. petlja-editor:: plusjednako_js

    main.js
    let a = 0;
    a += 3;
    a *= 4;
    alert(a); // 12
    a -= 4;
    a /= 2;
    alert(a); // 4
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

**Специјалне вредности** типа *number*

У Јаваскрипту у тип *number* додатно спадају и специјалне вредности ``Infinity``, ``-Infinity`` и ``Nan``. Ове вредности нису бројеви, али су корисна и смислена допуна скупа бројчаних вредности.
    ``-Infinity``,        минус бесконачно (:math:`-\infty`)

.. csv-table:: Специјалне вредности типа *number*
    :header: "JavaScript", "Значење"
    :widths: 20, 80
    :align: left

    ``Infinity``,         плус бесконачно (:math:`+\infty`)
    ``Nan``,              није број (енгл. *Not A Number*)
   
Ове вредности се могу добити као резултат неких рачунских операција, на пример:

.. petlja-editor:: specijalne_vrednosti_js

    main.js
    alert(1/0); // плус бесконачно
    alert(-1/0); // минус бесконачно
    alert(Math.sqrt(-1)); // не-број
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

Наведене операције (дељење нулом, кореновање негативног броја) немају резултат у скупу реалних бројева, па би, када специјалних вредности не би било, програм морао да пријави грешку током извршавања и пукне (*runtime error*). Увођењем специјалних вредности омогућено је да програм настави да ради на смислен начин. Уколико се нека од специјалних вредности појави међу резултатима, она може имати смисла за корисника иако она није број.

Пример – тригонометрија
-----------------------

За правоугли троугао са задатим катетама израчунати углове α и β у степенима.

.. comment

    додати слику

Да израчунамо угао α када су нам познате катете можемо да искористимо тангенс.

.. math::

    \tan(\alpha) &= {b \over a} \\
    \alpha &= \arctan({b \over a})

Резултат позива ``Math.atan`` у Јаваскрипту је у радијанима и морамо га сами конвертовати у степене. Ако знамо да :math:`\pi` представља :math:`180°` у радијанима, угао у степенима добијамо тако што резултат у радијанима помножимо са :math:`180° \over \pi`.

.. code-block:: javascript

    const alfa = Math.atan(b / a) * 180 / Math.PI;

Угао β можемо да израчунамо ако знамо два угла троугла јер је збир свих углова у троуглу :math:`180°`. Обзиром да је правоугли троугао, знамо да је један од углова :math:`90°`, док смо угао α израчунали у претходном кораку. Тако долазимо да је:

.. math::

    \beta &= 180° - 90° - \alpha \\
    \beta &= 90° - \alpha

.. petlja-editor:: js_ugao

    main.js
    const a = parseInt(prompt('a=?'));
    const b = parseInt(prompt('b=?'));
    const alfa = Math.atan(b / a) * 180 / Math.PI;
    const beta = 90 - alfa;
    alert('Угао α: ' + alfa.toFixed(2) + '°');
    alert('Угао β: ' + beta.toFixed(2) + '°');
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
