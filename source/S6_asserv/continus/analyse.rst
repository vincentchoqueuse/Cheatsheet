Systèmes SLIT
=============

Equation Différentielle 
-----------------------

Dans ce cours, nous nous intéressons spécifiquement à l'analyse des SLITs modélisables par une équation différentielle linéaire d'ordre :math:`n`. 
Lorsqu'un système est modélisable par une équation différentielle linéaire d'ordre :math:`n`, le lien entre l'entrée :math:`e(t)`
et la sortie :math:`s(t)` est donné par:

.. math ::

    a_n \frac{d^n s(t)}{dt^n} + \cdots+a_1 \frac{d s(t)}{dt}  +a_0 s(t)=b_n \frac{d^n e(t)}{dt^n} +\cdots+b_0 e(t)

* La partie gauche de l'égalité est appelée second membre.
* L'équation homogène est donnée par:

.. math ::

    a_n \frac{d^n s(t)}{dt^n} + \cdots+a_1 \frac{d s(t)}{dt}  +a_0 s(t)=0

Un système SLIT peut être entièrement décrit par sa réponse impulsionnelle :math:`h(t)`. Lorsqu'un signal :math:`e(t)` 
est appliquée à l'entrée du système et lorsque les conditions initiales sont nulles, la sortie :math:`s(t)` s'obtient via un produit de convolution

.. math ::

    s(t)=h*e(t)=\int_{-\infty}^{\infty}h(\tau)e(t-\tau)d\tau 

* :math:`h(t)` : réponse impulsionnelle

Fonction de Transfert 
---------------------

Pour analyser un système SLIT, une approche très pratique consiste à utiliser la transformée de Laplace.
Soit :math:`E(p)` et :math:`S(p)` les transformées de Laplace de l'entrée et de la sortie. Lorsque les conditions 
initiales sont nulles, la transformée de Laplace de la sortie est donnée par :math:`S(p)=H(p)E(p)` où :math:`H(p)=\mathcal{L}[h(t)]` désigne la transformée
de Laplace de la réponse impulsionnelle du système et est appelée fonction de transfert.

.. figure:: img/representation.svg
  :width: 250
  :align: center
  :alt: schema bloc

  Schéma Bloc

Pour un système modélisable par une équation différentielle linéaire d'ordre :math:`n`, la fonction de transfert du système peut s'exprimer sous la forme polynomiale suivante

.. math ::

    H(p)=\frac{S(p)}{E(p)}=\frac{b_Np^N+\cdots+b_1p+b_0}{a_Np^N+\cdots+a_1p+a_0}

Pour faciliter l'analyse d'une fonction de transfert, il est très courant de recourir à sa forme factorisée

.. math ::

    H(p)=k\frac{(p-z_N)\cdots (p-z_1)}{(p-p_N)\cdots (p-p_1)}


* :math:`z_k` correspondent aux zéros de la fonction de transfert (:math:`H(z_k)=0`),
* :math:`p_k` correspondent aux pôles de la fonction de transfert (:math:`H(p_k)=\pm \infty`).
    
Exemples
++++++++

* Système de premier ordre :

.. math ::

    H(p) = \frac{K}{\tau p+1}

* Système de second ordre:

.. math ::

    H(p) = \frac{K}{\frac{1}{\omega_n^2}p^2+\frac{2m}{\omega_n}p+1}


Propriétés
++++++++++

* Stabilité: Un SLIT continu est stable si tous les pôles possède une partie réelle négative c-a-d :math:`\Re e(p_k)<0`.
* Valeur Initiale : 

.. math ::

    s(0^+)=\lim_{p\to \infty}pH(p)E(p)

* Valeur Finale : Si la sortie converge,  

.. math ::

    s(\infty)=\lim_{p\to 0}pH(p)E(p)



Type du système
+++++++++++++++

Le type de la fonction transfert :math:`H(p)` est le plus petit entier naturel :math:`\alpha` tel que :math:`H(p)` puisse s’écrire sous la forme :

.. math ::

    H(p) = \frac{G(p)}{p^{\alpha}}

* :math:`\alpha` : type du système,
* :math:`G(p)`: fonction de transfert telle que :math:`\lim_{p\to 0} G(p)` est finie et non nulle.

Réponse Temporelle
------------------

Principe
++++++++

Pour obtenir la réponse temporelle d'un système à une entrée :math:`e(t)`, une solution possible consiste à passer par le domaine de Laplace.

1. Dans le domaine de Laplace, la sortie du système s'exprime sous la forme : :math:`S(p) = H(p)E(p)` où :math:`E(p)` correspond à la transformée de Laplace de l'entrée. 
2. Décomposition en éléments simples de la sortie :math:`S(p)``
3. Retour à l'original en appliquant la transformée de Laplace inverse (utilisation des tables des transformées de Laplace).

Réponse Indicielle 
++++++++++++++++++

La réponse indicielle à un échelon d'amplitude :math:`E` correspond à la sortie du système :math:`s(t)` lorsque :

.. math ::

    e(t)= Eu(t)= \left\{\begin{array}{cc}
    E,&t\ge 0\\
    0,&t< 0
    \end{array}\right.

Dans le domaine de Laplace, la sortie s'exprime alors sous la forme :

.. math ::

    S(p)=\frac{H(p)}{p}E

L'expression de la décomposition en éléments simples dépend de :math:`H(p)`. Néanmoins, il est possible d'obtenir rapidement :math:`s(0^+)` et :math:`s(\infty)` en utilisant les théorèmes de la valeur initiale et de la valeur finale.

* Valeur Initiale : 

.. math ::

    s(0^+)=\lim_{p\to \infty}H(p)E

* Valeur Finale : Si la sortie converge,  

.. math ::

    s(\infty)=\lim_{p\to 0}H(p)E

En particulier, lorsque le système est un système de type :math:`\alpha=0`, la valeur finale s'exprime sous la forme :math:`s(\infty)=H(0)E`.


Exemple
+++++++

L'exemple suivant montre comment obtenir la réponse indicielle d'un système de premier ordre en utilisant la transformée de Laplace ainsi que 
la transformée de Laplace inverse. 

1. Transformée de Laplace de la sortie :

.. math ::

    S(p)=\frac{K}{p(\tau p +1)}E

2. Décomposition en éléments simples :

.. math ::

    S(p)=\frac{KE}{p}-\frac{KE\tau }{\tau p +1}

3. Transformée de Laplace Inverse en utilisant les tables des transformées :

.. math ::

    s(t) = KE u(t)-KE e^{-\frac{t}{\tau}}u(t)=KE(1-e^{-\frac{t}{\tau}})u(t).

Réponse Fréquentielle
---------------------

Il est possible de montrer que si :math:`e(t)=e^{j\omega t}`, la sortie s'exprime sous la forme :math:`s(t)=H(j\omega)e^{j\omega t}`. La grandeur complexe 
:math:`H(j\omega)` est appelée réponse fréquentielle du système. 

Pour analyser la réponse fréquentielle :math:`H(j\omega)`, plusieurs représentations sont possibles :

* Diagramme de Bode: représentation du module :math:`|H(j\omega)|` en fonction de :math:`\omega`, et de l'argument :math:`\arg[H(j\omega)]` en fonction de :math:`\omega`.
* Diagramme de Black-Nichols: représentation du module :math:`|H(j\omega)|` en fonction de l'argument :math:`\arg[H(j\omega)]`.
* Diagramme de Nyquist: représentation de la partie imaginaire :math:`\Im m(H(j\omega))` en fonction de la partie réelle :math:`\Re e(H(j\omega))`.


Boucle Fermée
-------------

Pour améliorer les performances d'un système, une technique couramment utilisée consiste à utiliser le principe de la boucle fermée. 
Considérons un système composé d'une comparateur, une chaîne directe de fonction de transfert :math:`A(p)` et une chaîne de retour de
fonction de transfert `B(p)`.

.. figure:: img/closed_loop.svg
  :width: 300
  :align: center
  :alt: Boucle Fermée

  Boucle Fermée 

Soit :math:`\epsilon(p)=E(p)-B(p)S(p)` la sortie du comparateur dans le domaine de Laplace. En remarquant que la sortie 
s'exprime sous la forme :math:`S(p)=A(p)\epsilon(p)`, il est possible d'établir que la fonction de transfert en boucle fermée (FTBF) s'exprime sous 
la forme

.. math ::

    H(p) =\frac{S(p)}{E(p)}= \frac{A(p)}{1+A(p)B(p)}
 
**Démonstration**

La sortie du comparateur s'exprime sous la forme 

.. math ::

    \epsilon(p) = E(p) - B(p)S(p)

De plus, la sortie du système s'exprime en fonction de la sortie 
du comparateur sous la forme 

.. math ::

    S(p) = A(p)\epsilon(p)

En manipulant ces deux équations nous obtenons 

.. math ::

     S(p) = A(p)E(p) - A(p)B(p)S(p) \Rightarrow H(p) = \frac{S(p)}{E(p)} = \frac{A(p)}{1+A(p)B(p)}

