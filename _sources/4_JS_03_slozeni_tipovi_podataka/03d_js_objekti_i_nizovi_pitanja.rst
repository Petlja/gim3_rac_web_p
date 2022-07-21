Сложени типови података - питања
================================

.. mchoice:: slozeni_tipovi_q1
    :answer_a: { x: 5 }
    :answer_b: { x: 5, y: 3 }
    :answer_c: { y: 3 }
    :answer_d: Наредбе нису синтаксно исправне.
    :correct: b
    :feedback_a: Не.
    :feedback_b: Тачно!
    :feedback_c: Не.
    :feedback_d: Не.

    Која је вредност променљиве ``a`` након ових наредби?
    
    .. code-block:: javascript

        a = { x: 5 };
        a.y = 3;


.. mchoice:: slozeni_tipovi_q2
    :answer_a: Програм пукне
    :answer_b: Програм је синтаксно неисправан и не може да се покрене.
    :answer_c: Програм испише "0".
    :answer_d: Програм испише "undefined".
    :correct: d
    :feedback_a: Не.
    :feedback_b: Не.
    :feedback_c: Не.
    :feedback_d: Тачно!

    Шта се дешава приликом извршавања ових наредби?
    
    .. code-block:: javascript

        a = { x: 5 };
        alert(a.y);



.. mchoice:: slozeni_tipovi_q3
    :answer_a: { x: 5 }
    :answer_b: a = { x: 5 }
    :answer_c: [object Object]
    :answer_d: undefined
    :correct: c
    :feedback_a: Не.
    :feedback_b: Не.
    :feedback_c: Тачно!
    :feedback_d: Не.

    Шта исписује следећи програм?
    
    .. code-block:: javascript

        a = { x: 5 };
        alert(a);



.. fillintheblank:: slozeni_tipovi_q4

    Дат је објекат ``ucenik``:
    
    .. code-block:: javascript

        let ucenik = {
            licniPodaci: { ime: "Петар Петровић", tel: "012 345 678" },
            skola: {
                razred: 6,
                ocene: { srpski: 5, fizika: 4 },
                izostanci: { opravdani: 27, neopravdani: 1 }
            }
        };

    Шта треба написати уместо црте у следећој наредби, да би била приказана ученикова оцена из српског (уписати најједноставнији одговор)?
    
    .. code-block:: javascript
    
        alert(_____________);
    
    - :ucenik.skola.ocene.srpski$: Тачан одговор!
      :.*: Покушај поново.



.. fillintheblank:: slozeni_tipovi_q5

    Шта исписује следећи програм?
    
    .. code-block:: javascript
    
        let a = [10, 30, 50, 70];
        alert(a.length);
    
    - :4$: Тачан одговор!
      :.*: Покушај поново.



.. fillintheblank:: slozeni_tipovi_q6

    Шта исписује следећи програм?
    
    .. code-block:: javascript

        let a = [3];
        alert(a[3]);
    
    - :undefined$: Тачан одговор!
      :.*: Покушај поново.
