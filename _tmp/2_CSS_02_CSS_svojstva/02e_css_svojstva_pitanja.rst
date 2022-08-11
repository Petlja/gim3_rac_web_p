
..
  CSS својства - питања
  quiz

CSS својства – питања
=====================

.. mchoice:: css_svojstva_q1
    :answer_a: Као за наслове другог нивоа.
    :answer_b: Два инча.
    :answer_c: Два пута 12 типографских тачака.
    :answer_d: Двоструко већа од тренутног фонта.
    :correct: d
    :feedback_a: Не.
    :feedback_b: Не.
    :feedback_c: Не.
    :feedback_d: Тачно!

    Која величина слова се задаје дефинисањем стила ``font-size: 2em;``?



.. mchoice:: css_svojstva_q2
    :multiple_answers:
    :answer_a: rgb(201, 76, 76);
    :answer_b: color: rgb(#ff, 0, 0);
    :answer_c: color: "255, 0, 0";
    :answer_d: color: #ff0000;.
    :correct: a, d

    Који начини задавања боје су исправни у језику *CSS* (означите све тачне одговоре)?



.. mchoice:: css_svojstva_q3
    :answer_a: margin > padding,
    :answer_b: margin < padding,
    :answer_c: margin = padding,
    :answer_d: не може се одредити са слике.
    :correct: b
    :feedback_a: Не.
    :feedback_b: Тачно!
    :feedback_c: Не.
    :feedback_d: Не.

    Сви блокови приказани на слици имају исти стил. Какав је однос величина својстава ``margin`` и ``padding``?

    .. image:: ../../_images/css/margin_padding_test1.png
        :width: 500px
        :align: center



.. mchoice:: css_svojstva_q4
    :answer_a: Виде им се границе.
    :answer_b: Подразумевана висина им је један ред текста.
    :answer_c: Подразумевана ширина им је цео ред надређеног елемента.
    :answer_d: Подразумевана ширина им је најмања ширина која им је потребна за приказ.
    :correct: c
    :feedback_a: Не.
    :feedback_b: Не.
    :feedback_c: Тачно!
    :feedback_d: Не.

    Шта је карактеристично за блок-елементе језика *HTML*?



.. mchoice:: css_svojstva_q5
    :answer_a: Виде им се границе.
    :answer_b: Подразумевана висина им је један ред текста.
    :answer_c: Подразумевана ширина им је цео ред надређеног елемента.
    :answer_d: Подразумевана ширина им је најмања ширина која им је потребна за приказ.
    :correct: d
    :feedback_a: Не.
    :feedback_b: Не.
    :feedback_c: Не.
    :feedback_d: Тачно!

    Шта је карактеристично за инлајн-елементе језика *HTML*?


.. comment

    mаterijal za pitanja i primere:

    јединице, боје

    својства текста
        font-size – које дефинише величину фонтова (најчешће у јединцима које се називају пиксели).
        color – које дефинише боју фонтова (нпр. red, blue, green).
        font-family
    
    Својства која дефинишу границе елемента
        padding (унутра), border (ивица), margin (напољу), background (боја)...

    Димензије елемената
        min-width, max-width, width
        min-height, max-height, height
        
        overflow: "hidden"
        overflow: "scroll"
