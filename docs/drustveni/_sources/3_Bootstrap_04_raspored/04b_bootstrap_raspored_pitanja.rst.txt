*Bootstrap* и распоређивање елемената - питања
==============================================

.. mchoice:: layout_q1
    :answer_a: Четвртину ширине реда.
    :answer_b: Трећину ширине реда.
    :answer_c: Четири инча.
    :answer_d: Четири сантиметра.
    :correct: b
    :feedback_a: Не.
    :feedback_b: Тачно!
    :feedback_c: Не.
    :feedback_d: Не.

    Колику ширину заузима блок ``div`` дефинисан овако: ``<div class="col-4">...</div>`` ?



.. mchoice:: layout_q2
    :answer_a: делилац броја 12.
    :answer_b: мањи или једнак 12.
    :answer_c: дељив са 12.
    :answer_d: једнак 12.
    :correct: d
    :feedback_a: Не.
    :feedback_b: Не.
    :feedback_c: Не.
    :feedback_d: Тачно!

    Нека је сваком блоку ``div`` у једном реду доедељена нека од класа ``col-1``, ``col-2``, ``col-3``, ``col-4``, и сл. 
    
    Ред је попуњен од ивице до ивице ако је збир суфикса у именима класа употребљених у једном реду ...



.. mchoice:: layout_q3
    :answer_a: Прва слика
    :answer_b: Друга слика
    :answer_c: Трећа слика
    :answer_d: Четврта слика
    :correct: c
    :feedback_a: Не.
    :feedback_b: Не.
    :feedback_c: Тачно!
    :feedback_d: Не.

    Која од понуђених слика одговара следећем *html* коду по распореду блокова:
    
    .. code-block:: html
    
        <div class="row">
          <div class="col">.</div>
        </div>
        <div class="row">
          <div class="col">.</div>
          <div class="col">.</div>
        </div>
        <div class="row">
          <div class="col">.</div>
        </div>
    
    .. image:: ../../_images/bootstrap/layout31.png
        :width: 220px
    .. image:: ../../_images/bootstrap/layout32.png
        :width: 220px
    .. image:: ../../_images/bootstrap/layout33.png
        :width: 220px
    .. image:: ../../_images/bootstrap/layout34.png
        :width: 220px



.. mchoice:: layout_q4
    :answer_a: Прва слика
    :answer_b: Друга слика
    :answer_c: Трећа слика
    :answer_d: Четврта слика
    :correct: a
    :feedback_a: Тачно!
    :feedback_b: Не.
    :feedback_c: Не.
    :feedback_d: Не.

    Која од понуђених слика одговара следећем *html* коду по распореду блокова:
    
    .. code-block:: html
    
        <div class="row">
          <div class="col">...</div>
        </div>
        <div class="row">
          <div class="col-2">...</div>
          <div class="col-10">...</div>
        </div>
        <div class="row">
          <div class="col-2">...</div>
          <div class="col-10">...</div>
        </div>
    
    .. image:: ../../_images/bootstrap/layout41.png
        :width: 220px
    .. image:: ../../_images/bootstrap/layout42.png
        :width: 220px
    .. image:: ../../_images/bootstrap/layout43.png
        :width: 220px
    .. image:: ../../_images/bootstrap/layout44.png
        :width: 220px



.. mchoice:: layout_q5
    :answer_a: Прва слика
    :answer_b: Друга слика
    :answer_c: Трећа слика
    :answer_d: Четврта слика
    :correct: b
    :feedback_a: Не.
    :feedback_b: Тачно!
    :feedback_c: Не.
    :feedback_d: Не.

    Која од понуђених слика одговара следећем *html* коду по распореду блокова:
    
    .. code-block:: html
    
        <div class="row">
          <div class="col">...</div>
        </div>
        <div class="row">
          <div class="col-1">...</div>
          <div class="col-10">
            <div class="row">
              <div class="col"><p>...</p>
              <div class="col">...</div>
              <div class="col">...</div>
            </div>
          </div>
          <div class="col-1">...</div>
        </div>
        <div class="row">
          <div class="col">...</div>
        </div>

    
    .. image:: ../../_images/bootstrap/layout51.png
        :width: 220px
    .. image:: ../../_images/bootstrap/layout52.png
        :width: 220px
    .. image:: ../../_images/bootstrap/layout53.png
        :width: 220px
    .. image:: ../../_images/bootstrap/layout54.png
        :width: 220px


.. Ускоро.

    col-1, col-2, col-3, col-4, col-6, col-8)
