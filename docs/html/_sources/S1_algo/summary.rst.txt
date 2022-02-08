Summary 
=======

.. note::

    Documentation : https://docs.python.org/3/library/index.html


    
Affectation
-----------

Une variable informatique est un quadruplet (nom, adresse, valeur, type) qui caractérise une donnée informatique à un instant donné.


L'affectation se lit de droit à gauche. La valeur de droite est stockée dans la variable
spécifée par l'étiquette située à gauche.

.. code ::

    var_name = value


Mots Réservés 
+++++++++++++

Certaines etiquettes ne peuvent pas être utilisées car elles sont déjà utilisées
dans la syntaxe du langage.

.. code ::

    False      await      else       import     pass
    None       break      except     in         raise
    True       class      finally    is         return
    and        continue   for        lambda     try
    as         def        from       nonlocal   while
    assert     del        global     not        with
    async      elif       if         or         yield

.. note::

    Les étiquettes ci-dessus sont celles du language python qui est utilisé en S1. Si on change de language, les étiquettes réservées changent.

Alternative
-----------

Alternative simple
++++++++++++++++++

L'alternative simple est une instruction de contrôle du flux d'instructions qui permet de choisir entre deux instructions selon qu'une condition est vérifiée ou non.

.. code ::

    if condition:
        value = ...
    else:
        value = ...

La condition évaluée après l'instruction «if» est donc une expression booléenne qui prend soit la valeur False (faux) soit la valeur True (vrai).

Exemple
^^^^^^^

.. code ::

    test = 2
    if test >= 0:
        print("nombre positif ou nul")
    else:
        print("nombre strictement négatif")


Opérateurs de comparaison
^^^^^^^^^^^^^^^^^^^^^^^^^

.. code ::

    x == y      # x est égal à y 
    x != y      # x est différent de y
    x > y       # x est strictement supérieur à y 
    x < y       # x est strictement inférieur à y 
    x >= y      # x est plus grand que, ou égal à y
    x <= y      # x est plus petit que, ou égal à y

Opérateurs Booleens
^^^^^^^^^^^^^^^^^^^

Pour lier le résultat de plusieurs résultats booléens, il est possible d'utiliser 
des opérateurs specifiques

.. code ::

    not a       # négation de a 
    a and b     # a et b
    a or b      # a ou b


Alternatives Cascadées
++++++++++++++++++++++


.. code ::

    if condition1:
        value = ...
    elif condition2:
        value = ...
    else :
        value = ...

Itérations
----------


Boucle while
++++++++++++

L'instruction while (tant que) permet de répéter plusieurs fois une même instruction : le bloc d'instructions est exécuté tant que la condition est vérifiée. On arrête dès que la condition est fausse; on dit alors qu'on sort de la boucle.


.. code ::

    while condition:
        instruction

Boucle For
++++++++++

L'instruction For (pour ... faire) permet de répéter plusieurs fois la même instruction: le nombre d'itérations est connu à l'avance.

.. code ::

    for index in range(10):
        instruction
