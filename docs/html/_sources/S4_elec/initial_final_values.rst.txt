Limit values for 2nd order systems 
==================================

Introduction
------------

Lorsqu'un système est excité par une entrée :math:`e(t)` en :math:`t=0^+`, la sortie :math:`s(t)` peut
présenter différents comportements. Ces différents comportements permettent d'identifier le type de filtre (passe-bas, passe-haut, etc) et certains paramètres.

Dans ce tutorial, nous nous intéressons spécifiquement au comportement à l'excitation, c-à-d en :math:`t=0^+`, et au comportement final, c-à-d en :math:`t=\infty`. 
Pour analyser le comportement en :math:`t=0^+` et en :math:`t=\infty`, ce tutorial présente deux approches, l'une basée sur l'équation différentielle et l'autre sur la fonction de transfert.
Pour des raisons de simplicité, les approches présentées ci dessous se limitent au cas des systèmes de second ordre. De plus, ces approches sont développés sous l'hypothèse où les conditions initiales sont toutes nulles c-à-d 

.. math ::

    e(0^-)=s(0^-)=\frac{de(0^-)}{dt}=\frac{ds(0^-)}{dt}=0

Approche Temporelle
-------------------

Considérons un système de second ordre décrit par l'équation différentielle suivante

.. math ::

    a_2 \frac{d^2 s(t)}{dt^2}+a_1 \frac{d s(t)}{dt}+a_0 s(t)=b_2 \frac{d^2 e(t)}{dt^2}+b_1 \frac{d e(t)}{dt}+b_0 e(t)

Valeur Initiale
+++++++++++++++

Il est possible de trouver la valeur initiale en :math:`t=0^+`
en intégrant plusieurs fois l'équation différentielle entre :math:`0^-` et :math:`0^+`. Ainsi, nous obtenons

.. math ::

    a_2 \int\int_{0^-}^{0^+}\frac{d^2 s(t)}{dt^2}dt^2+a_1 \int\int_{0^-}^{0^+}\frac{d s(t)}{dt}dt^2 +a_0 \int\int_{0^-}^{0^+}s(t)dt^2\\
    =b_2 \int\int_{0^-}^{0^+}\frac{d^2 e(t)}{dt^2}dt^2+b_1 \int\int_{0^-}^{0^+}\frac{d e(t)}{dt}dt^2+b_0 \int\int_{0^-}^{0^+}e(t)dt^2

En supposant que l'entrée et la sortie ne contiennent pas d'impulsion, nous obtenons simplement

.. math ::

    a_2 \left[s(t)\right]_{0^-}^{0^+} =b_2 \left[e(t)\right]_{0^-}^{0^+}


En intégrant une fois l'équation différentielle entre :math:`0^-` et :math:`0^+`, nous obtenons également 

.. math ::

    a_2 \int_{0^-}^{0^+}\frac{d^2 s(t)}{dt^2}dt+a_1 \int_{0^-}^{0^+}\frac{d s(t)}{dt}dt +a_0 \int_{0^-}^{0^+}s(t)dt\\
    =b_2 \int_{0^-}^{0^+}\frac{d^2 e(t)}{dt^2}dt+b_1 \int_{0^-}^{0^+}\frac{d e(t)}{dt}dt+b_0 \int_{0^-}^{0^+}e(t)dt

Sous les mêmes hypothèses, nous trouvons alors :

.. math ::

    a_2  \left[\frac{d s(t)}{dt}\right]_{0^-}^{0^+}+a_1  \left[s(t)\right]_{0^-}^{0^+} =b_2 \left[\frac{d e(t)}{dt}\right]_{0^-}^{0^+}+b_1  \left[s(t)\right]_{0^-}^{0^+}

En utilisant le fait que les conditions initiales sont toutes nulles, nous obtenons :

.. math ::

    a_2s(0^+) &= b_2e(0^+)\\
    a_2 \dot{s}(0^+)+a_1 s(0^+) &=b_2 \dot{e}(0^+)+b_1 e(0^+)


où :math:`\dot{s}(0^+)=\left.\frac{ds(t)}{dt}\right|_{t=0^+}`. Finalement, la sortie et la dérivée de la sortie en :math:`0^+` s'expriment sous la forme

.. math ::

    s(0^+) = \frac{b_2}{a_2} e(0^+) \tag{1}

.. math ::

    \dot{s}(0^+) =\frac{b_2}{ a_2 } \dot{e}(0^+)+\frac{a_2b_1-a_1b_2}{ a_2^2 } e(0^+)\tag{2}

Valeur Finale
+++++++++++++

Considérons une entrée de type échelon c-à-d :math:`e(t)=E` pour :math:`t\ge 0`. Pour :math:`t\ge 0`, la solution particulière s'exprime 
sous la forme :math:`s_P(t)=\alpha`. En exploitant l'équation différentielle, nous obtenons alors :

.. math ::

    0+0+a_0 \alpha = 0+0+b_0 E

Dans le contexte, la valeur finale, également appelée regime permanent, est égale à:

.. math ::

    s(\infty)=s_P(\infty)=\alpha=\frac{b_0}{a_0}E

Approche basée sur Laplace 
--------------------------

Propriétés
++++++++++

Soit :math:`s(t)` un signal et :math:`S(p)` sa transformée de Laplace. 
Pour déterminer les comportements temporels en :math:`t=0^+` et en :math:`t=\infty`, il est possible d'utiliser les théorèmes de la valeur initiale et de la valeur finale.

.. math ::

    s(0^+)&=\lim_{t\to 0^+} s(t)= \lim_{p\to \infty} p S(p)\\
    s(\infty)&=\lim_{t\to \infty} s(t)= \lim_{p\to 0} p S(p)

En supposant également les conditions initiales nulles, il est possible d'établir que :math:`\mathcal{L}\left[\frac{ds(t)}{dt}\right]=pS(p)`. Il en vient que 

.. math ::

    \dot{s}(0^+)&=\lim_{t\to 0^+} \frac{ds(t)}{dt}= \lim_{p\to \infty} p^2 S(p)\\

Pour le cas des systèmes d'ordre deux, la transformée de Laplace de la sortie s'exprime sous la forme :math:`S(p)=H(p)E(p)` avec

.. math ::

    H(p)=\frac{b_2p^2+b_1p+b_0}{a_2p^2+a_1p+a_0}

.. note ::

    Lorsque les conditions initiales ne sont pas nulles, il est possible de raisonner en variation. Par exemple, pour le filtre passe-haut, nous obtenons 




Valeur Initiale
+++++++++++++++

Concernant la sortie, nous obtenons la limite suivante 

.. math ::

    s(0^+)=\lim_{p\to \infty} p H(p)E(p)= H(\infty)\left(\lim_{p\to \infty} pE(p)\right)=H(\infty)e(0^+)
    
Dans le cas spécifique des systèmes d'ordre 2, nous obtenons

.. math ::

    s(0^+)= \frac{b_2}{a_2}e(0^+)\tag{1bis}

Pour la dérivée de la sortie, il est nécessaire de décomposer la fonction de transfert sous la forme :math:`H(p)=H_1+H_2(p)` avant d'évaluer la limite. En utilisant
la décomposition. Nous obtenons alors la limite

.. math ::

    \dot{s}(0^+)&=\lim_{p\to \infty} p^2 H(p)E(p)= H_1\left(\lim_{p\to \infty} p^2E(p)\right)+\left(\lim_{p\to \infty} pH_2(p)\right) \left(\lim_{p\to \infty}pE(p)\right)\\
    &=H_1\dot{e}(0^+)+\left(\lim_{p\to \infty} pH_2(p)\right)e(0^+)\\
    
Notons que lorsque le degré du numérateur est inférieur au degré du numérateur, :math:`H_1=0` et le premier terme est nécessairement nul.

Concernant les systèmes de second ordre, nous obtenons

.. math ::

    H(p)=H_1+H_2(p)=\frac{b_2}{a_2}+\frac{a_2b_1p+a_2b_0-(a_1b_2p+a_0b_2)}{a_2(a_2p^2+a_1p+a_0)}

La limite est alors égale à 

.. math ::

    \dot{s}(0^+)=\frac{b_2}{a_2} \dot{e}(0^+)+ \frac{a_2b_1-a_1b_2}{a_2^2}e(0^+) \tag{2bis}


Valeur Finale
+++++++++++++

Pour une entrée de type échelon c-à-d :math:`e(t)=E` pour :math:`t\ge 0`, la valeur finale est égale à 

.. math ::

    s(\infty)=\lim_{p\to 0} p H(p)E(p)= H(0)\left(\lim_{p\to 0} pE(p)\right)=\frac{b_0}{a_0}E


Exemples
--------

Dans cette partie, nous nous intéressons aux comportements des filtres de second ordre de type passe-bas, passe-bande, passe-haut et rejecteur (voir :doc:`/S4_elec/transfer_function_list`).

La figure suivante présente la réponse indicielle pour un filtre passe-bas, passe-bande, passe-haut et rejecteur ayant la même pulsation propre :math:`\omega_0=1` rad/s, le même coefficient d'amortissement :math:`m=0.5` et le même 
coefficient d'amplification :math:`T_0=T_\infty=T_m=2`.

.. plot ::
    :context: close-figs
    :include-source: false

    import numpy as np 
    from scipy.signal import lti
    import matplotlib.pyplot as plt

    m = 0.5
    w0 = 1
    T = 2

    den = [(1/(w0**2)),2*m/w0,1]
    sys1 = lti([T],den)
    sys2 = lti([2*m*T/w0,0],den)
    sys3 = lti([T/(w0**2),0,0],den)
    sys4 = lti([T/(w0**2),0,T],den)
    
    t = np.arange(0,10,0.05)
    name_list = ["Passe-Bas","Passe-Bande","Passe-Haut","Rejecteur"]
    plt.plot(t,t>=0,label="u(t)")
    for indice, sys in enumerate([sys1,sys2,sys3,sys4]):
        t,s = sys.step(T=t)
        t_2 = np.insert(t, 0, [-1,0], axis=0)
        s_2 = np.insert(s, 0, [0,0], axis=0)
        plt.plot(t_2,s_2,label=name_list[indice])
    plt.xlim([-1,10])
    plt.xlabel("temps [s]")
    plt.ylabel("s(t)")
    plt.legend(loc=4)

Nous observons rapidement que :

    * Seuls les filtres passe-haut et rejecteur laissent passer les discontinuités en entrée.
    * Seuls les filtres passe-bas et rejecteur possèdent un regime permanent non nul.


Valeur Initiale 
+++++++++++++++

En utilisant les relations (1) et (2), il est possible d'obtenir le comportement en présence de discontinuités.
La tableau suivant présente ce comportement lorsque les conditions initiales sont nulles c-a-d
:math:`e(0^-)=s(0^-)=0`.

.. table:: Comportement en présence de discontinuités
    :widths: 100 100 100 100 100
    :align: center

    +--------------------------+------------------+-------------------------------+------------------------------------------------------------+------------------------------------------------------------+
    | Sortie                   |    Passe-Bas     |  Passe-Bande                  |   Passe-Haut                                               |   Rejecteur                                                |
    +==========================+==================+===============================+============================================================+============================================================+
    | :math:`s(0^+)`           |   :math:`0`      |    :math:`0`                  |    :math:`T_{\infty}e(0^+)`                                |    :math:`T_{0}e(0^+)`                                     |
    +--------------------------+------------------+-------------------------------+------------------------------------------------------------+------------------------------------------------------------+
    | :math:`\dot{s}(0^+)`     |   :math:`0`      |  :math:`2mT_m\omega_0 e(0^+)` |  :math:`T_{\infty}\dot{e}(0^+)- 2mT_\infty\omega_0 e(0^+)` |  :math:`T_{0}\dot{e}(0^+)- 2mT_0\omega_0 e(0^+)`           |
    +--------------------------+------------------+-------------------------------+------------------------------------------------------------+------------------------------------------------------------+



Valeur Finale
++++++++++++++

La tableau suivant présente la valeur du regime permanent lorsque l'entrée est un échelon d'amplitude E et lorsque les conditions initiales sont nulles.


.. table:: Comportement en regime permanent (entrée: echelon d'amplitude E)
    :widths: 100 100 100 100
    :align: center

    +--------------------------+------------------+-------------------------------+------------------------------------------------------------+------------------------------------------------------------+
    | Sortie                   |    Passe-Bas     |  Passe-Bande                  |   Passe-Haut                                               |   Rejecteur                                                |
    +==========================+==================+===============================+============================================================+============================================================+
    | :math:`s(\infty)`        |   :math:`T_0E`   |    :math:`0`                  |    :math:`0`                                               |     :math:`T_0E`                                           |
    +--------------------------+------------------+-------------------------------+------------------------------------------------------------+------------------------------------------------------------+

