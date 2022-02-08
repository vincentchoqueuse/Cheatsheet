Nombres Complexes
=================

Notons :math:`j` l'imaginaire pur tel que :math:`j^2=-1` et :math:`\mathbb{C}` le corps des complexes.

Forme algébrique
----------------

Tout nombre complexe :math:`z\in \mathbb{C}` s'écrit sous la forme :

.. math::

    z=a+jb


* :math:`a=\Re e(z)` correspond à la partie réelle,
* :math:`b=\Im m(z)`  correspond à la partie imaginaire.

Complexe Conjugué
++++++++++++++++++

On appelle conjugué de :math:`z` le nombre complexe 

.. math::

    z^*=a-jb


Exponentielle Complexe
++++++++++++++++++++++

L'exponentielle complexe est définie par 

.. math ::

    e^{j\theta}=\cos(\theta)+j\sin(\theta)



* Multiplication : La multiplication de deux exponentielles complexes donne : :math:`e^{j\theta_1}e^{j\theta_2}=e^{j(\theta_1+\theta_2)}`,
* Conjugaison :  Le conjugué d'une exponentielle complexe est égal à : :math:`\left(e^{j\theta}\right)^*=e^{-j\theta}`,
* Périodicité: L'exponentielle complexe est :math:`2\pi`-périodique,
* Formules d'Euler : Les formules d'Euler permettent d'exprimer le cosinus ou le sinus à partie de l'exponentielle complexe

.. math ::

    \cos(\theta)=\Re e(e^{j\theta})=\frac{1}{2}\left(e^{j\theta}+e^{-j\theta}\right)\\
    \sin(\theta)=\Im m(e^{j\theta})=\frac{1}{2j}\left(e^{j\theta}-e^{-j\theta}\right)



Forme Polaire
-------------


Tout nombre complexe :math:`z\in \mathbb{C}` non nul peut s'écrire sous la forme :

.. math ::

    z=|z|e^{j\theta}

* :math:`|z|` correspond au module,
* :math:`\theta=\arg[z]` correspond à l'argument (modulo :math:`2\pi`). 


Conversion
+++++++++++

Soit un nombre complexe :math:`z=a+jb`, alors

.. math ::

    |z|&=\sqrt{a^2+b^2}\\
    \theta&= \left\{\begin{array}{lc} \arctan(b/a) & \text{, si }a>0\\
        \pi +\arctan(b/a) & \text{, si }a<0\\
        \end{array}\right.


Propriétés
++++++++++

Soit deux complexes :math:`z_1` et :math:`z_2`. 

* Le module et l'argument de :math:`z=z_1z_2` sont donnés par :

.. math ::

    |z|&=|z_1| \times |z_2|\\
    \arg[z] &= \arg[z_1]+\arg[z_2]

* Le module et l'argument de :math:`z=z_1/ z_2` sont donnés par :


.. math ::

    |z|&=\frac{|z_1|}{|z_2|}\\
    \arg[z] &= \arg[z_1]-\arg[z_2]
