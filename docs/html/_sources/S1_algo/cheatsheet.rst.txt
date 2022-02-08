Cheatsheet
==========


Turtle
-------

.. note::
    
    Documentation: https://docs.python.org/3/library/turtle.html


Importation
+++++++++++

.. code ::

    import turtle
    t = turtle.Turtle()


Usage
++++++++


.. code ::

    t.forward(100)      # deplacement rectiligne
    t.left(90)          # rotation à gauche de 90 degrés
    t.up()              # lever le crayon
    t.goto(10,10)       # se deplacer au point de coordonnées 10, 10
    t.down()            # baisser le crayon
    t.speed(10)         # changer la vitesse de deplacement
    t.pencolor("gray")  # changer la couleur du crayon


Math
----

.. note::
    
    Documentation: https://docs.python.org/3/library/math.html

Importation
+++++++++++

.. code ::

    import math


Random
-------

.. note::
    
    Documentation: https://docs.python.org/3/library/random.html

Importation
+++++++++++

.. code ::

    import random 


Usage
+++++

* Génération d'un nombre aléatoire entre 1 et 6

.. code ::

    random.randint(1,6)
