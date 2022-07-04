CSS селектори - вежбе
=====================

Следећи задаци су осмишљени да бисте вежбали писање селектора. Исправним решењем задатка се сматра само оно решење којим се у коду мења једино текст "_уписати_селектор_".


.. questionnote::

    **Задатак 2.3.1**

    У следећем коду упишите одговарајући селектор на место текста "_уписати_селектор_", тако да свако појављивање речи "црвено" постане црвено.
    
    .. activecode:: selektor_elementa_html
       :language: html
       :nocodelens:

       <html>
       <body>
         <style>
           _уписати_селектор_ {
             color: red;
           }
         </style>

         <h2><span>Црвено</span>-црни наслов </h2>
         <p>Црно црно црно <span>црвено</span> црно</p>
         <p>Црно црно црно <span>црвено</span> црно</p>
       </body>
       </html>

|

.. questionnote::

    **Задатак 2.3.2**

    У следећем коду упишите одговарајући селектор на место текста "_уписати_селектор_", тако да текст "Црвено" постане црвен.
    
    .. activecode:: selektori_id_html
       :language: html
       :nocodelens:

       <html>
       <body>
         <style>
           _уписати_селектор_ {
             color: red;
           }
         </style>

         <h2>Наслов</h2>
         <p>Црно</p>
         <p id="crveno">Црвено</p>
         <p>Црно</p>
       </body>
       </html>

|

.. questionnote::

    **Задатак 2.3.3**

    У следећем коду упишите одговарајући селектор на место текста "_уписати_селектор_", тако да свако појављивање речи "црвено" постане црвено.
    
    .. activecode:: selektor_klase_html
       :language: html
       :nocodelens:

       <html>
       <body>
         <style>
           _уписати_селектор_ {
             color: red;
           }
         </style>
         <h2>Наслов</h2>
         <p>Црно</p>
         <p class="crveno">Црвено</p>
         <p>Црно</p>
         <p class="crveno">Црвено</p>
         <p class="crveno">Црвено</p>
         <p>Црно</p>
       </body>
       </html>

|

.. questionnote::

    **Задатак 2.3.4**

    У следећем коду упишите одговарајући селектор на место текста "_уписати_селектор_", тако да свако појављивање речи "црвено" постане црвено, осим у наслову.
    
    .. activecode:: selektor_elementa_sa_klasom_html
       :language: html
       :nocodelens:

       <html>
       <body>
         <style>
           _уписати_селектор_ {
             color: red;
           }
         </style>
         <h2 class="neki_poseban_stil">У наслову ништа не треба да буде црвено</h2>
         <p>Црно</p>
         <p class="neki_poseban_stil">Црвено</p>
         <p>Црно</p>
         <p class="neki_poseban_stil">Црвено</p>
         <p class="neki_poseban_stil">Црвено</p>
         <p>Црно</p>
       </body>
       </html>

|

.. questionnote::

    **Задатак 2.3.5**

    У следећем коду упишите одговарајући селектор на место текста "_уписати_селектор_", тако да свако појављивање речи "црвено" постане црвено.
    
    .. activecode:: selektor_elementa_sa_nasledjenom_klasom_html
       :language: html
       :nocodelens:

       <html>
       <body>
         <style>
           _уписати_селектор_ {
             color: red;
           }
         </style>

         <h2>Наслов</h2>
         <div class="prvi_omot">
           <p>Црно</p>
           <p>Црно</p>
         </div>
         <div class="drugi_omot">
           <h4>Поднаслов</h4>
           <p>Црвено</p>
           <p>Црвено</p>
           <p>Црвено</p>
         </div>
         <div class="treci_omot">
           <p>Црно</p>
           <p>Црно</p>
         </div>
       </body>
       </html>

|

.. questionnote::

    **Задатак 2.3.6**

    У следећем коду упишите одговарајући селектор на место текста "_уписати_селектор_", тако да свако појављивање речи "црвено" постане црвено.
    
    .. activecode:: selektor_elementa_sa_sopstvenom_i_nasledjenom_klasom_html
       :language: html
       :nocodelens:

       <html>
       <body>
         <style>
           _уписати_селектор_ {
             color: red;
           }
         </style>

         <h2 class="neki_poseban_stil">Наслов</h2>
         <div class="prvi_omot">
           <p class="neki_poseban_stil">Црно</p>
           <p class="neki_poseban_stil">Црно</p>
         </div>
         <div class="drugi_omot">
           <p class="neki_poseban_stil">Црвено</p>
           <p>Црно</p>
           <p class="neki_poseban_stil">Црвено</p>
         </div>
         <div class="treci_omot">
           <p>Црно</p>
           <p>Црно</p>
         </div>
       </body>
       </html>
