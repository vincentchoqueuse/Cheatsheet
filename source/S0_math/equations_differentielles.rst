Equations Differentielles
=========================

Modèle Mathématique 
-------------------

Une équation différentielle linéaire d'ordre n s'exprime sous la forme 

.. math ::

    a_n \frac{d^n s(t)}{dt^n} + \cdots+a_1 \frac{d s(t)}{dt}  +a_0 s(t)=b_m \frac{d^m e(t)}{dt^m} +\cdots+b_0 e(t)

Solution
--------

La solution de l'équation différentielle s'exprime sous la forme :

.. math ::

    s(t)=s_l(t)+s_p(t)

Solution libre
++++++++++++++

Le terme :math:`s_L(t)` désigne la solution libre de l'équation sans second membre :

.. math ::

    s_l(t)=\sum_{k=1}^{n}\lambda_k e^{p_kt}

* :math:`\lambda_k` désigne des constantes d'intégration. Ces constantes peuvent être déterminées à partir de la connaissance des conditions initiales.
* :math:`p_k \in \mathbb{C}` désigne les racines de l'équation caractéristique :

.. math ::

    a_n p^n+a_{n-1}p^{n-1}+\cdots+a_1 p+a_0=0


Solution particulière
+++++++++++++++++++++

Le terme :math:`s_P(t)` désigne la solution particulière de l'équation avec second membre.

Exemple
-------

Considérons l'équation différentielle suivante de premier ordre

.. math ::

    \tau \frac{d s(t)}{dt} + s(t)= Ku(t)

où :math:`u(t)` désigne l'échelon unité (:math:`u(t)=0` si :math:`t<0` et :math:`u(t)=1` si :math:`t\ge 0`) et :math:`s(0)=0`. 

La solution s'exprime sous la forme :math:`s(t)=s_l(t)+s_p(t)`

* Solution libre: :math:`s_l(t)=\lambda e^{p_0t}` avec :math:`\tau p_0+1=0 \Rightarrow p_0=-\frac{1}{\tau}`.
* Solution particulière: :math:`s_p(t)=\beta` avec :math:`\tau \times 0 +\beta = K\times 1 \Rightarrow \beta=K`.
* Condition initiale: :math:`s(0)=0` c-a-d :math:`s_l(0) + s_p(0) = 0 \Rightarrow \lambda=-K` 

Pour :math:`t>0`, nous obtenons finalement 

.. math ::

    s(t) = K(1-e^{-\frac{1}{\tau}t})