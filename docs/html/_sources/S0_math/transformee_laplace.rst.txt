Transformée de Laplace
======================

Définition
----------

.. math ::

    X(p) = \mathcal{L}[x(t)]=\int_{0}^{\infty} x(t)e^{-pt}dt


Propriétés
----------

* Linéarité :

.. math ::

    \mathcal{L}\left[\alpha_1 x_1(t)+\alpha_2 x_2(t)\right]=\alpha_1 X_1(p)+\alpha_2 X_2(p)

* Dérivation :

.. math ::

    \mathcal{L}\left[\frac{dx(t)}{dt}\right]=pX(p)-x(0^-)

* Théorème de la Valeur Initiale :

.. math ::

    x(0^+)=\lim_{p\to \infty} p X(p)

* Théorème de la Valeur Finale :

.. math ::

    x(\infty)=\lim_{p\to 0} p X(p)


Signaux Usuels
--------------

Impulsion de Dirac
++++++++++++++++++

* Définition : 

.. math :: 

    x(t) = \delta(t)=\left\{\begin{array}{cc}
    \infty,&t=0\\
    0,&t\ne 0
    \end{array}\right.~\text{s.t.}\int_{-\infty}^{\infty} \delta(t)dt = 1


* Transformée de Laplace : 

.. math :: 

    X(p) = 1


Echelon Unitaire 
++++++++++++++++

* Définition : 

.. math :: 

    u(t)=\left\{\begin{array}{cc}
    1,&t\ge 0\\
    0,&t< 0
    \end{array}\right.


* Transformée de Laplace : 

.. math :: 

    U(p) = \frac{1}{p}


Exponentielle Décroissante
+++++++++++++++++++++++++++

* Définition : 

.. math :: 

    x(t)=e^{-\alpha t}u(t)


* Transformée de Laplace : 

.. math :: 

    X(p) = \frac{1}{p+\alpha}


Sinusoide Amortie (Part 1)
++++++++++++++++++++++++++

* Définition : 

.. math :: 

    x(t)=e^{-\alpha t}\sin(\omega t) u(t)


* Transformée de Laplace : 

.. math :: 

    X(p) = \frac{\omega}{(p+\alpha)^2+\omega^2}

Sinusoide Amortie (Part 2)
++++++++++++++++++++++++++

* Définition : 

.. math :: 

    x(t)=e^{-\alpha t}\cos(\omega t) u(t)


* Transformée de Laplace : 

.. math :: 

    X(p) = \frac{p+\alpha}{(p+\alpha)^2+\omega^2}


Exemple
-------

Considérons l'équation différentielle suivante de premier ordre

.. math ::

    \tau \frac{d s(t)}{dt} + s(t)= Ke(t)

Nous souhaitons obtenir la réponse indicielle (entrée=échelon) du système.

* Partie 1: Transformée de Laplace de la sortie

.. math ::

    S(p)=\frac{K}{p(\tau p +1)}

* Partie 2: Décomposition en éléments simples

.. math ::

    S(p)=\frac{K}{p}-\frac{K\tau }{\tau p +1}

* Partie 3 : Transformée de Laplace Inverse

.. math ::

    s(t) = K u(t)-K e^{-\frac{t}{\tau}}u(t)=K(1-e^{-\frac{t}{\tau}})u(t)
