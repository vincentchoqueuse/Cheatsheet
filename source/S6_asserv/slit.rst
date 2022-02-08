Systèmes SLIT (Continus)
========================

Introduction
----------------------

Ce cours s'intéresse à l'analyse des systèmes linéaires et invariants dans le temps (SLIT).
Un système SLIT peut être entièrement décrit par sa réponse impulsionnelle :math:`h(t)`. Lorsqu'un signal :math:`e(t)` 
est appliquée à l'entrée du système, la sortie :math:`s(t)` s'obtient via un produit de convolution

.. math ::

    s(t)=h*e(t)=\int_{-\infty}^{\infty}h(\tau)e(t-\tau)d\tau 

Equation Différentielle 
+++++++++++++++++++++++

Dans ce cours, nous nous intéressons spécifiquement à l'analyse des SLITs modélisables par une équation différentielle linéaire d'ordre :math:`n`. 

Lorsqu'un système est modélisable par une équation différentielle linéaire d'ordre :math:`n`, le lien entre l'entrée :math:`e(t)`
et la sortie :math:`s(t)` est donné par:

.. math ::

    a_n \frac{d^n s(t)}{dt^n} + \cdots+a_1 \frac{d s(t)}{dt}  +a_0 s(t)=b_n \frac{d^n e(t)}{dt^n} +\cdots+b_0 e(t)


Fonction de Transfert 
+++++++++++++++++++++

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
    
Propriétés
++++++++++

* Stabilité: Un SLIT continu est stable si tous les pôles possède une partie réelle négative c-a-d :math:`\Re e(p_k)<0`.
* Valeur Finale : Si la sortie converge,  

.. math ::

    s(\infty)=\lim_{p\to 0}pH(p)E(p)

* Valeur Initiale : 

.. math ::

    s(0^+)=\lim_{p\to \infty}pH(p)E(p)

Comportement Fréquentiel
++++++++++++++++++++++++

Il est possible de montrer que si :math:`e(t)=e^{j\omega t}`, la sortie s'exprime sous la forme :math:`s(t)=H(j\omega)e^{j\omega t}`. La grandeur complexe 
:math:`H(j\omega)` est appelée réponse fréquentielle du système. 

Pour analyser la réponse fréquentielle :math:`H(j\omega)`, plusieurs représentations sont possibles :

* Diagramme de Bode: représentation du module :math:`|H(j\omega)|` en fonction de :math:`\omega`, et de l'argument :math:`\arg[H(j\omega)]` en fonction de :math:`\omega`.
* Diagramme de Black-Nichols: représentation du module :math:`|H(j\omega)|` en fonction de l'argument :math:`\arg[H(j\omega)]`.
* Diagramme de Nyquist: représentation de la partie imaginaire :math:`\Im m(H(j\omega))` en fonction de la partie réelle :math:`\Re e(H(j\omega))`.


Boucle Fermée
+++++++++++++

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

Correction
----------

Considérons un système en boucle fermée avec un retour unitaire 

.. figure:: img/closed_loop_2.svg
  :width: 400
  :align: center
  :alt: Boucle Fermée avec Retour unitaire

  Boucle Fermée avec Retour Unitaire

* :math:`E(p)`: Transformée de Laplace de la consigne,
* :math:`C(p)`: Fonction de transfert du correcteur,
* :math:`F(p)`: Fonction de transfert du système + capteur,
* :math:`C(p)F(p)`: Fonction de transfert en boucle ouverte (FTBO).

Critères de Performance
+++++++++++++++++++++++

Dans un système bouclé, notre objectif est de venir choisir un correcteur :math:`C(p)` de sorte à respecter un cahier des
charges. Ce cahier des charges peut specifier certaines contraintes portant sur la sortie du système. 


.. plot ::
    :context: close-figs
    :include-source: false

    import numpy as np
    from scipy.signal import lti
    

    w0 = 1
    m = 0.2
    t = np.arange(0,30,0.1)
    H = lti([0.8],[1/(w0**2),2*m/w0,1])
    t,s = H.step(T=t)
    t2 = np.insert(t,0,[-1,0])
    s2 = np.insert(s,0,[0,0])
    smax = max(s)
    tr = t[np.where((s>1.05*0.8) | (s<0.95*0.8))[-1]]

    plt.plot(t2,s2,label="s(t)")
    plt.plot([0,0,0,30],[0,0,1,1],color = 'r', label="Eu(t)")
    plt.xlabel("$t$ [rad/s]")
    plt.ylabel("$s(t)$")
    plt.xlim([-1,30])
    plt.ylim([0,1.25])
    plt.xticks([0,tr[-1]],["0","$t_r$"])
    plt.yticks([0,0.95*0.8,0.8,1.05*0.8,1,smax],["0","$0.95s(\infty)$","$s(\infty)$","$1.05s(\infty)$","$e(\infty)=E$","$\max(s(t))$"])
    plt.grid()
    plt.legend()


* Stabilité: BIBO stabilité. Le système est stable si et seulement si pour tout t

.. math ::

    |e(t)|<\infty ~\Rightarrow~|s(t)|<\infty


* Précision: Mesure de l'écart statique

.. math ::

    \epsilon_s = e(\infty)-s(\infty)

* Dépassement (réponse indicielle): Mesure du premier dépassement relatif 

.. math ::

    D_r(\%)=100 \times \frac{\max[s(t)]-s(\infty)}{s(\infty)}

* Rapidité (réponse indicielle): Mesure du temps de réponse :math:`t_r` à :math:`\pm 5\%`

.. math ::

    \forall t>t_r,~0.95 s(\infty) \le s(t) \le 1.05 s(\infty)


Correcteurs Usuels 
++++++++++++++++++

Pour respecter les contraintes du cahier des charges, nous pouvons utiliser différents types de correcteurs :math:`C(p)`.
Ces correcteurs possèdent un ou plusieurs paramètres de liberté que nous pouvons ajuster en fonction des performances souhaitées. 

* Proportionnel: 

.. math ::

    C(p) = K_c

* Proportionnel Intégral (PI): 

.. math ::

    C(p) = K_c \left(1+ \frac{1}{T_ip}\right) = K_c \frac{T_i p+1}{T_ip}

* Proportionnel Dérivé (PD): 

.. math ::

    C(p) = K_c (1+T_d p)

* Proportionnel Intégral Dérivé (PID): 

.. math ::

    C(p) = K_c\left(1+\frac{1}{T_ip}+T_d p\right) = K_c \frac{T_iT_d p^2+T_i p+1}{T_ip}



