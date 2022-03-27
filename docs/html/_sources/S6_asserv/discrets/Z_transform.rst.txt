Systèmes SLIT
=============

Transformée en Z 
----------------

Définition
++++++++++

La transformée en Z unilatérale d'une suite numérique :math:`x[n]` est définie par l'équation

.. math ::

    X(z)= \mathcal{Z}[x[n]] = \sum_{n=0}^{\infty}x[n]z^{-n}

où :math:`z` est une variable complexe. 


Il est important de noter que la transformée de Z d'un signal ne converge pas nécessairement pour tout :math:`z \in \mathbb{Z}`.
Il est alors nécessaire de préciser la région de convergence (ROC) pour laquelle la série converge c-a-d les valeurs de :math:`z` telles que :math:`|X(z)|<\infty`.

Exemple
+++++++

Soit :math:`x[n]=u[n]`, l'échelon unité défini par

.. math::

        u[n] =\left\{\begin{array}{cl} 1 & \text{ si }t\ge 0\\
        0&\text{ ailleurs}\\
        \end{array}\right.

La transformée en Z de :math:`x[n]=u[n]` est égale à 

.. math::

    X(z)&= \sum_{n=0}^{\infty}u[n]z^{-n}\\
    &=\sum_{n=0}^{\infty}z^{-n}\\
    &=\frac{1}{1-z^{-1}}\\
    &=\frac{z}{z-1}

où le passage de la deuxième à la troisième ligne s'obtient en remarquant le fait :math:`\sum_{n=0}^{\infty}z^{-n}` correspond à 
la somme des éléments d'une suite géométrique de raison :math:`z^{-1}`.


Propriétés
++++++++++

La transformée en Z possède les propriétés suivantes: 

* Linéarité: Si :math:`y[n]=\alpha x_1[n]+\beta x_2[n]` où :math:`\alpha` et :math:`\beta` sont des constantes, alors 

.. math ::

    Y(z)=\alpha X_1(z)+\beta X_2(z)

* Décalage temporel: Si :math:`y[n]=x[n-k]` (:math:`k \in \mathbb{N}^{+}`), alors 

.. math ::
    
    Y(z)=X(z)z^{-k}

* Multiplication par une fonction exponentielle: Si :math:`y[n]= a^n x[n]`, alors 

.. math ::

    Y(z)=X(a^{-1}z)

* Convolution: Si :math:`y[n]= h[n]*x[n]`, alors 

.. math ::
    Y(z)=H(z)X(z)

* Théorème de la valeur initiale: Si la limite :math:`\lim_{z\to \infty}X(z)` existe, alors la valeur initiale s'obtient via l'expression

.. math ::

    x[0]=\lim_{z\to \infty} X(z)

* Théorème de la valeur finale: Si tous les pôles de :math:`X(z)` sont compris dans le cercle unité, alors la valeur finale s'obtient via l'expression

.. math ::

    \lim_{n\to \infty} x[n]=\lim_{z\to 1}(z-1)X(z)

Equation aux différences
------------------------

Dans beaucoup de situation, le système peut être décrit par une équation aux différences liant l'entrée :math:e[n]` et la sortie :math:`s[n]`. Cette équation 
s'exprime sous la forme 

.. math ::

    a_L s[n+L] + \cdots + a_1s[n+1]+ a_0 s[n] = b_M e[n+M] + \cdots + b_1e[n+1] + b_0 e[n]

Lorsque le système est causal, :math:`M<L`. Sous l'hypothèse de causalité, l'équation aux différences peut également s'exprimer
sous la forme 

.. math ::

    a_L s[n]  &= b_M e[n+M-L] + \cdots + b_1e[n+1-L] + b_0 e[n-L]\\
    &~-a_{L-1} s[n-1] -  \cdots -a_1s[n-L+1]- a_0 s[n-L]


Fonction de transfert
---------------------

Lorsque les conditions initiales sont nulles, la transformée en Z de la sortie s'exprime sous la forme 
:math:`S(z)=H(z)E(z)` où :math:`H(z)` correspond à la fonction de transfert en Z du système.

.. figure:: img/representation_d.svg
  :width: 250
  :align: center
  :alt: schema bloc

  Schéma Bloc

Expression
++++++++++

Pour un système régit par une équation aux différences, l'utilisation des propriétés de la transformée en Z permet d'établir 
que :

.. math ::

    a_L z^{L}S(z) + \cdots + a_1zS(z)+ a_0 S(z) = b_M z^{M} E(z) + \cdots + b_1 z E(z) + b_0 E(z)

Après factorisation, nous obtenons alors

.. math ::

    H(z)=\frac{S(z)}{E(z)}=\frac{b_M z^{M} + \cdots + b_1 z + b_0}{a_L z^{L}+ \cdots + a_1z+ a_0}


Pôles et Zéros
++++++++++++++

Pour mettre en évidence les points singuliers de la fonction de transfert, il est possible de réexprimer la fonction de transfert sous une forme factorisée. 


.. math ::

    H(z)=K\frac{(z-z_1)(z-z_2)\cdots(z-z_M)}{(z-p_1)(z-p_2)\cdots(z-p_L)}

* Les valeurs :math:`z_m` correspondent aux zéros de la fonction de transfert,
* Les valeurs :math:`p_l` correspondent aux poles de la fonction de transfert).
* :math:`K=\frac{b_M}{a_L}` est un facteur d'amplification.

Propriétés
++++++++++

* Stabilité: Pour qu'un système à temps discret soit stable, il faut que tous les pôles de sa fonction de transfert sont inclus dans le cercle de rayon unité c-a-d si 

.. math ::

    |p_l|\le 1,~\forall l=1, \cdots, L

* Valeur Initiale : 

.. math ::

    s[0]=\lim_{z\to \infty}H(z)E(z)

* Valeur Finale : Si la sortie converge,  

.. math ::

    s(\infty)=\lim_{z\to 1}(z-1)H(z)E(z)
