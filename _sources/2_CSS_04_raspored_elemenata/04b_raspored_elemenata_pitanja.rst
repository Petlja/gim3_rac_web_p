Распоред елемената – питања
===========================

.. mchoice:: css_raspored_q1
    :answer_a: box-sizing: border-box;
    :answer_b: float: left;
    :answer_c: overflow: auto;
    :answer_d: margin: auto;.
    :correct: b
    :feedback_a: Не.
    :feedback_b: Тачно!
    :feedback_c: Не.
    :feedback_d: Не.

    Да би се *HTML* блокови надовезивали слева на десно, потребно је да сваки од тих блокова има ограничену ширину и дефинисано једно својство. Које?



.. mchoice:: css_raspored_q2
    :answer_a: Линије са леве и десне стране садржаја стране.
    :answer_b: Фиксирана оријентација екрана при његовом окретању.
    :answer_c: Садржај стране је фиксне ширине, позициониран по средини екрана.
    :answer_d: Садржај стране ће заузети сву расположиву ширину у прозору прегледача.
    :correct: c
    :feedback_a: Не.
    :feedback_b: Не.
    :feedback_c: Тачно!
    :feedback_d: Не.

    Шта се постиже следећим *CSS* кодом?
    
    .. code-block:: css

        body {
            margin: auto;
            width: 800px;
        }



.. mchoice:: css_raspored_q3
    :answer_a: За та два дугмета је постављено својство float: right; а за остала четири својство float: left;
    :answer_b: Довољно је за остала четири дугмета поставити својство float: left;
    :answer_c: Елементи се не могу овако позиционирати у истом блоку.
    :answer_d: Начин постоји, али није наведен међу понуђеним одговорима.
    :correct: a
    :feedback_a: Тачно!
    :feedback_b: Не.
    :feedback_c: Не.
    :feedback_d: Не.

    Дугмад са слике су елементи истог типа и налазе се у истом *HTML* блоку. На који начин су два дугмета са десне стране могла да буду одмакнута од остала четири?
    
    .. image:: ../../_images/css/raspored_test3.png
        :width: 550px
        :align: center



.. mchoice:: css_raspored_q4
    :answer_a: <br/>.prva.kolona {background-color:darkgray;}<br/>.druga.kolona {background-color:lightblue;}<br/>.treca.kolona {background-color:lightgreen;}
    :answer_b: <br/>.kolona {float:left; max-width:180px; padding:10px;}<br/>.prva {background-color:darkgray;}<br/>.druga {background-color:lightblue;}<br/>.treca {background-color:lightgreen;}
    :answer_c: <br/>.kolona {float:left; max-width:180px; padding:10px;}<br/>.prva kolona {background-color:darkgray;}<br/>.druga kolona {background-color:lightblue;}<br/>.treca kolona {background-color:lightgreen;}
    :correct: b
    :feedback_a: Не.
    :feedback_b: Тачно!
    :feedback_c: Не.

    Ово је део *HTML* кôда једне веб-стране.

    .. code-block:: html

        <body>
          <div class="prva kolona"> <h2> HTML </h2> <p> elementi, liste, tabele, hiperveze, multimedija </p> </div>
          <div class="druga kolona"> <h2> CSS </h2> <p> CSS stilovi, svojstva, selektori, raspored </p> </div>
          <div class="treca kolona"> <h2> Bootstrap </h2> <p> Biblioteka, klase, komponente, raspored </p> </div>
        </body>

    Који од понуђених стилова даје изглед у прегледачу као на следећој слици?
    
    .. image:: ../../_images/css/selektori_test5.png
        :width: 600px
        :align: center



.. mchoice:: css_raspored_q5
    :answer_a: Распоред као на првој слици.
    :answer_b: Распоред као на другој слици.
    :answer_c: Распоред као на трећој слици.
    :answer_d: Распоред као на четвртој слици.
    :correct: a
    :feedback_a: Тачно!
    :feedback_b: Не.
    :feedback_c: Не.
    :feedback_d: Не.

    За веб-страну која изгледа овако

    .. image:: ../../_images/css/raspored_test4_pitanje.png
        :width: 288px
        :align: center

    одредите распоред блокова који јој највише одговара:

    .. image:: ../../_images/css/raspored_test4_odg1.png
        :width: 240px
    .. image:: ../../_images/css/raspored_test4_odg2.png
        :width: 240px
    .. image:: ../../_images/css/raspored_test4_odg3.png
        :width: 240px
    .. image:: ../../_images/css/raspored_test4_odg4.png
        :width: 240px



.. mchoice:: css_raspored_q6
    :answer_a: Распоред као на првој слици.
    :answer_b: Распоред као на другој слици.
    :answer_c: Распоред као на трећој слици.
    :answer_d: Распоред као на четвртој слици.
    :correct: d
    :feedback_a: Не.
    :feedback_b: Не.
    :feedback_c: Не.
    :feedback_d: Тачно!

    На основу изгледа ове веб-стране...

    .. image:: ../../_images/css/raspored_test5_pitanje.png
        :width: 360px
        :align: center

    ...одредите који од понуђених распореда блокова јој одговара:

    .. image:: ../../_images/css/raspored_test5_odg1.png
        :width: 300px
    .. image:: ../../_images/css/raspored_test5_odg2.png
        :width: 300px
    .. image:: ../../_images/css/raspored_test5_odg3.png
        :width: 300px
    .. image:: ../../_images/css/raspored_test5_odg4.png
        :width: 300px

