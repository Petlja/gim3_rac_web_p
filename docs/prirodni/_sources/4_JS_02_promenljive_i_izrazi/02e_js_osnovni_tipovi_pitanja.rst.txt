Основни типови - питања
=======================

.. fillintheblank:: osnovni_tipovi_q1

    Која је вредност променљиве ``a`` након извршавања следећих наредби?
    
    .. code-block:: javascript

        let a = 2;
        a++;
        a *= 2;

    - :^6$: Тачан одговор!
      :.*: Покушај поново.



.. mchoice:: osnovni_tipovi_q2
    :answer_a: Програм пукне при извршавању те наредбе
    :answer_b: Такав програм уопште не може да се покрене
    :answer_c: Добије се резултат који није број
    :answer_d: Појави се дијалог који нуди корисника да измени програм
    :correct: c
    :feedback_a: Не.
    :feedback_b: Не.
    :feedback_c: Тачно!
    :feedback_d: Не.

    Шта се догоди при извршавању следеће наредбе?
    
    .. code-block:: javascript

        let x = 1/0;



.. mchoice:: osnovni_tipovi_q3
    :multiple_answers:
    :answer_a: 'don't'
    :answer_b: 'don''t'
    :answer_c: "don't"
    :answer_d: 'don\'t'
    :correct: c, d

    Који од наведених израза имају вредност ``don't``?



.. fillintheblank:: osnovni_tipovi_q4

    Која је вредност променљиве ``s`` након извршавања следећих наредби?
    
    .. code-block:: javascript

        let a = 14;
        let s = `a = ${a}`;

    - :^a = 14$: Тачан одговор!
      :.*: Покушај поново.



.. mchoice:: osnovni_tipovi_q5
    :multiple_answers:
    :answer_a: 2 === "2"
    :answer_b: 2 == "2"
    :answer_c: 2 !== "2"
    :answer_d: 2 != "2"
    :correct: b, c

    Који од наведених израза имају вредност ``true``?
