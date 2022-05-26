Функције, методе, догађаји -  питања
====================================

.. mchoice:: fun_met_dog_q1
    :answer_a: return x, y;
    :answer_b: return (x, y);
    :answer_c: return [x, y];
    :answer_d: return {x, y};
    :correct: c
    :feedback_a: Не.
    :feedback_b: Не.
    :feedback_c: Тачно!
    :feedback_d: Не.

    Када функција треба да врати две вредности, *x* и *y*, пишемо ...



.. mchoice:: fun_met_dog_q2
    :answer_a: a.add(x);
    :answer_b: a.push(x);
    :answer_c: a.append(x);
    :answer_d: a += x;
    :correct: b
    :feedback_a: Не.
    :feedback_b: Тачно!
    :feedback_c: Не.
    :feedback_d: Не.

    Којом наредбом вредност *x* додајемо као нови елемент на крај низа *a*?



.. mchoice:: fun_met_dog_q3
    :answer_a: [10]
    :answer_b: 10
    :answer_c: [10, 15]
    :answer_d: {10, 15}
    :correct: a
    :feedback_a: Тачно!
    :feedback_b: Не.
    :feedback_c: Не.
    :feedback_d: Не.

    Чему је једнако *x* након наредби
    
    .. code-block:: javascript
    
        a = [5, 10, 15, 20];
        x = a.slice(1, 2);



.. mchoice:: fun_met_dog_q4
    :answer_a: d = querySelector('poslednji_odeljak');
    :answer_b: d = document.getElementsByTagName('div').last;
    :answer_c: d = querySelector('.poslednji_odeljak');
    :answer_d: d = querySelector('#poslednji_odeljak');
    :correct: d
    :feedback_a: Не.
    :feedback_b: Не.
    :feedback_c: Не.
    :feedback_d: Тачно!

    Која наредба је еквивалентна са ``d = getElementById('poslednji_odeljak')`` ?



.. mchoice:: fun_met_dog_q5
    :answer_a: на сваких 10 секунди
    :answer_b: 10 пута у секунди
    :answer_c: на сваких 10 милисекунди
    :answer_d: само једном, након 10 милисекунди
    :correct: c
    :feedback_a: Не.
    :feedback_b: Не.
    :feedback_c: Тачно!
    :feedback_d: Не.

    Наредбом ``setInterval(f, 10);`` постижемо да се функција ``f`` изврши
