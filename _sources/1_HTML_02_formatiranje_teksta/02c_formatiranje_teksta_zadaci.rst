Форматирање текста - вежбе и задаци
===================================

.. questionnote::

    **Вежба 1.2.1**

    У следећем кôду упишите одговарајуће тагове, тако да сваки параграф текста буде приказан онако како је у њему написано.

    .. petlja-editor:: bold_italic_underline_html

        index.html
        <!doctype html>
        <html>
        <body>
          <h2>Вежба форматирања</h2>
          <p>Обичан текст.</p>
          <p>Подебљан текст.</p>
          <p>Искошен текст.</p>
          <p>Подвучен и подебљан текст.</p>
        </body>
        </html>


.. questionnote::

    **Вежба 1.2.2**

    У следећем кôду упишите одговарајуће тагове тако да добијете исправне формуле, а то су:

    - у првом реду :math:`H_2O`, 
    - у другом реду :math:`a^2 + b^2 = c^2`, 
    - у трећем реду :math:`2^{10}=1024 \approx 1000 = 10^3`.
    
    .. petlja-editor:: indeksi_i_eksponenti_html

        index.html
        <!doctype html>
        <html>
          <body>
            <h2>Вежба форматирања</h2>
            <p>Хемијска формула за воду је H2O</p>
            <p>За странице правоуглог троугла важи a2 + b2 = c2</p>
            <p>2 10 = 1024 ≈ 1000 = 10 3</p>
          </body>
        </html>

.. comment

    resenje

    <html>
    <body>
      <h2>Вежба форматирања</h2>
      <p>Хемијска формула за воду је H<sub>2</sub>O</p>
      <p>За странице правоуглог троугла важи a<sup>2</sup> + b<sup>2</sup> = c<sup>2</sup></p>
      <p>2<sup>10</sup> = 1024 ≈ 1000 = 10<sup>3</sup></p>
    </body>
    </html>


.. questionnote::

    **Задатак 1.2.3**
    
    Напишите своју кратку биографију у пар наслова и пасуса и означите делове који имају неко посебно значење. Текст са посебним значењем ставите између тагова који су овде објашњени и погледајте како ће се приказати у прегледачу. *HTML* документ сачувајте на свом рачунару, или га унесите на неком од сајтова `HTML Fiddle <https://htmlfiddle.net>`_, `JSBin <https://jsbin.com/?html,output>`_  или `JSFiddle <https://jsfiddle.net>`_.

.. questionnote::

    **Задатак 1.2.4**
    
    Пронађите информације о неким научницима или спортистима на сајту *Википедија* и направите *HTML* документ са тим информацијама. Користите тагове који су објашњени у овој лекцији и погледајте како ће се текст приказати у прегледачу. *HTML* документ сачувајте на свом рачунару, или га унесите на неком од сајтова `HTML Fiddle <https://htmlfiddle.net>`_, `JSBin <https://jsbin.com/?html,output>`_  или `JSFiddle <https://jsfiddle.net>`_.
