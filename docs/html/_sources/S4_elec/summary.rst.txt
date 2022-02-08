Summary 
=======

Système SLIT
-------------

Un système linéaire et invariant dans le temps (SLIT) d'ordre n peut être modélisé par une équation différentielle linéaire d'ordre n 

.. math ::

    a_n \frac{d^n s(t)}{dt^n} + \cdots+a_1 \frac{d s(t)}{dt}  +a_0 s(t)=b_m \frac{d^m e(t)}{dt^m} +\cdots+b_0 e(t)


* Résolution: voir :doc:`/S0_math/equations_differentielles`
* Equation caractéristique :

.. math ::

    a_n p^n+a_{n-1}p^{n-1}+\cdots+a_1 p+a_0=0



Fonction de Transfert 
---------------------

La passage à la fonction de transfert s'obtient en utilisant les propriétés de
linéarité et de dérivation de la :doc:`/S0_math/transformee_laplace`.

Forme Polynomiale (ba)
++++++++++++++++++++++

.. math ::

    H(p)=\frac{S(p)}{E(p)}=\frac{b_Np^N+\cdots+b_1p+b_0}{a_Np^N+\cdots+a_1p+a_0}


Forme Factorisée (zpk)
++++++++++++++++++++++

.. math ::
        H(p)=\frac{S(p)}{E(p)}=\alpha \frac{\prod_{k=0}^{m}(p-z_k)}{\prod_{k=0}^{N}(p-p_k)}

* Zéros :math:`z_k`: les zéros correspondent aux valeurs de :math:`p` annulant le numérateur de la fonction de transfert.
* Pôles :math:`p_k`: les pôles correspondent aux valeurs de :math:`p` annulant le dénominateur de la fonction de transfert.
    

.. note ::

    Un SLIT est stable si tous les pôles possède une partie réelle négative c-a-d :math:`\Re e(p_k)<0`.


Réponse Fréquentielle
---------------------

Exponentielle Complexe
++++++++++++++++++++++

Lorsque l'entrée est une exponentielle complexe de pulsation :math:`\omega`, c-à-d :math:`e(t)=e^{j\omega t}`, il est possible d'établir 
que la sortie s'exprime sous la forme :math:`s(t)=H(j\omega)e^{j\omega t}`. Le terme :math:`H(j\omega)` correspond à la réponse fréquentielle du système.

.. note ::

   La réponse fréquentielle d'un SLIT s'obtient en évaluant la fonction de transfert :math:`H(p)` en :math:`p=j\omega`.


La réponse fréquentielle est une grandeur généralement complexe. Pour la représenter, il est courant de représenter en fonction de :math:`\omega` :

* son module: :math:`|H(j\omega)|`, 
* son argument: :math:`\arg[H(j\omega)]` [deg].

Sinusoide 
+++++++++

Lorsque l'entrée est une sinusoïde de pulsation :math:`\omega`, c-à-d :math:`e(t)=\cos(\omega t)`, il est possible d'établir que la sortie s'exprime sous la forme 

.. math :: 

    s(t)=|H(j\omega)|\cos(\omega t+\arg[H(j\omega)])

* Le module de la réponse fréquentielle agit sur l'amplitude crète en sortie,
* l'argument de la réponse fréquentielle agit sur le déphasage. 

