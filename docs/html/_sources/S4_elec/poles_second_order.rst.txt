Poles/Zeros of 2nd order systems
================================

Introduction
------------

La localisation des pôles et des zéros permettent d'appréhender le comportement temporel et fréquentiel d'un système.
Dans ce tutorial, nous nous intéressons spécifiquement à la localisation des pôles et des zéros pour les systèmes d'ordre 2
décrit par la fonction de transfert

.. math ::

    H(p)=\frac{N(p)}{\frac{1}{\omega_0^2}p^2+\frac{2m}{\omega_0}p+1}

* :math:`N(p)` désigne le numérateur de la fonction de transfert, 
* :math:`\omega_0` désigne la pulsation propre,
* :math:`m` le coefficient d'amortissement.


Expressions des Pôles 
---------------------

Les systèmes d'ordre 2 possèdent deux pôles. Le regime libre d'un système d'ordre 2 s'exprime alors sous la forme:

.. math :: 

    s_l(t)=\lambda_1 e^{p_1t} + \lambda_2 e^{p_2t}

où :math:`\lambda_1` et :math:`\lambda_2` désignent les constantes d'intégration. Les deux pôles s'obtiennent en évaluant les racines du dénominateur
de la fonction de transfert c-a-d en déterminant les valeurs de :math:`p` telles que: 

.. math::

    \frac{1}{\omega_0^2}p^2+\frac{2m}{\omega_0}p+1 = 0

Cette équation est une équation du second degré. Le discriminant s'exprime sous la forme suivante:

.. math::

    \Delta = \left(\frac{2m}{\omega_0}\right)^2-\frac{4}{\omega_0^2} =\frac{4}{\omega_0^2}\left(m^2-1\right)


Cas où m>1
++++++++++

Lorsque :math:`m>1`, le système possède deux poles réels et distincts. Les pôles s'expriment sous la forme 

.. math::
    p_1 = -m\omega_0 +\omega_0 \sqrt{m^2-1}\\
    p_2 = -m\omega_0 -\omega_0 \sqrt{m^2-1}

Mathématiquement, nous obtenons les propriétés suivantes:

* le produit des deux pôles est égale à :math:`p_1p_2=m^2\omega_0^2-\omega_0^2(m^2-1)=\omega_0^2`
* la somme des deux pôle est égale à :math:`p_1+p_2=-2m\omega_0`.

Nous en déduisons alors que:

.. math::
    \omega_0 &= \sqrt{p_1p_2}\\
    m &= -\frac{p_1+p_2}{2\omega_0}

Géométriquement, les deux pôles sont placés sur un cercle de centre :math:`-m\omega_0` et de rayon :math:`\sqrt{m^2-1}`.

.. plot ::
    :context: close-figs
    :include-source: false

    import numpy as np 
    import matplotlib.pyplot as plt

    m = 2
    w0 = 1
    poles = np.sort(np.roots([1/(w0**2),2*m/w0,1]))
    center = -m*w0

    angle = np.arange(0,2*np.pi,0.05)
    radius = w0*np.sqrt(m**2-1)

    fig = plt.figure(figsize=[7,4.8])
    plt.plot(np.real(poles),np.imag(poles),'x')
    plt.plot(center-radius*np.cos(angle),radius*np.sin(angle),'k:')
    plt.xlabel("$\Re e(.)$")
    plt.ylabel("$\Im m(.)$")
    plt.grid()
    plt.xlim([-5,5])
    plt.xticks([poles[0],-m*w0,poles[1],0],["$p_2$","$-m\omega_0$","$p_1$","0"])
    plt.yticks([-w0*np.sqrt(m**2-1),0,w0*np.sqrt(m**2-1)],["$-\omega_0\sqrt{m^2-1}$","$0$","$\omega_0\sqrt{m^2-1}$"])
    plt.axis("equal")




Cas où m=1
++++++++++

Lorsque :math:`m=1`, le système possède un pole réel double. Le pole réel double s'exprime sous la forme

.. math::
    p_1 = p_2 = -m\omega_0

.. plot ::
    :context: close-figs
    :include-source: false

    import numpy as np 
    import matplotlib.pyplot as plt

    m = 1
    w0 = 1
    poles = np.sort(np.roots([1/(w0**2),2*m/w0,1]))

    fig = plt.figure(figsize=[7,4.8])
    plt.plot(np.real(poles),[0,0],'x')
    plt.xlabel("$\Re e(.)$")
    plt.ylabel("$\Im m(.)$")
    plt.grid()
    plt.xlim([-2.5,0.5])
    plt.xticks([-m*w0,0],["$-m\omega_0$","0"])
    plt.yticks([0],["0"])
    

Cas où m<1
++++++++++

Lorsque :math:`m<1`, le système possède une paire de pôles complex-conjugués. Les pôles s'expriment sous la forme 

.. math::
    p_1 = -m\omega_0 +j\omega_0 \sqrt{1-m^2}\\
    p_2 = -m\omega_0 -j\omega_0 \sqrt{1-m^2}

Mathématiquement, 

* le module de chaque pôle est égal à :math:`|p_1|=|p_2|=\sqrt{(m\omega_0)^2+\omega_0^2(1-m^2)}=\omega_0`.
* l'angle formé entre le pôle :math:`p_1` et l'axe des réels est donné par :math:`\cos(\theta)=-\Re e(p_1)/|p_1|=m`

Nous en déduisons alors que:

.. math::
    \omega_0 &= \sqrt{p_1p_1^*}=|p_1|\\
    m &= -\frac{\Re e(p_1)}{\omega_0 }

.. plot ::
    :context: close-figs
    :include-source: false

    import numpy as np 
    import matplotlib.pyplot as plt

    m = 0.6
    w0 = 1
    poles = np.sort(np.roots([1/(w0**2),2*m/w0,1]))
    center = -m*w0
    angle = np.arange(0,2*np.pi,0.05)
    radius = w0*np.sqrt(1-m**2)

    fig = plt.figure(figsize=[7,4.8])
    plt.plot(center-radius*np.cos(angle),radius*np.sin(angle),'k:')
    plt.plot(np.real(poles),np.imag(poles),'x')
    plt.xlabel("$\Re e(.)$")
    plt.ylabel("$\Im m(.)$")
    plt.grid()
    plt.xlim([-3,0.5])
    plt.xticks([-m*w0,0],["$-m\omega_0$","0"])
    plt.yticks([-w0*np.sqrt(1-m**2),0,w0*np.sqrt(1-m**2)],["$-\omega_0\sqrt{1-m^2}$","$0$","$\omega_0\sqrt{1-m^2}$"])
    plt.axis("equal")


