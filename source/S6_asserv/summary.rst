Summary
=======

Modélisation 
------------

Equation de récurrence
++++++++++++++++++++++

.. math ::

  s[n] = \sum_{k=0}^N b_k e[n-k] - \sum_{k=1}^N a_k s[n-k]

* :math:`b_k`: coefficient de la partie non recursive,
* :math:`a_k`: coefficient de la partie recursive. La valeur de :math:`a_0` est implicitement normalisée à 1.


Fonction de transfert
+++++++++++++++++++++

En exploitant le fait que la transformée en Z est linéaire et que :math:`\mathcal{Z}[e[n-1]]=z^{-1}E(z)`, la fonction
de transfert du système s'exprime sous la forme

.. math ::

  H(z)=\frac{S(z)}{E(z)} = \frac{\sum_{k=0}^N b_k z^{-k}}{1+\sum_{k=1}^N a_k z^{-k}}

Propriétés
++++++++++


* Stabilité: :math:`|p_k|\le 1` pour tout :math:`k`. Nous retiendrons alors que pour qu'un système soit stable, tous ses pôles doivent être compris dans le cercle de rayon unité. 
* Gain statique: :math:`K = H(1)`,
* Comportement fréquentiel: :math:`H\left(e^{j\omega T_e}\right)`.


Modélisation CNA/CAN avec BOZ
-----------------------------

Même si la correction se fait en numérique, en pratique, le système à contrôler reste
le plus souvent analogique. Pour pouvoir mettre en place une stratégie de correction, il 
est alors nécessaire de modéliser l'influence des convertisseurs A/N et N/A.

Soit un système comportant

* un CNA de période d'échantillonnage :math:`T_e`
* le système continu :math:`F(p)`
* un CAN de période d'échantillonnage :math:`T_e` modélisé par un bloqueur d'ordre 0,

.. figure:: img/boz.svg
  :width: 350
  :align: center
  :alt: schema bloc

  CNA avec BOZ

La chaîne peut être modélisée par la fonction de transfert suivante

.. math ::

    F(z)=\frac{z-1}{z}TZ\left[TL^{-1}\left[\frac{F(p)}{p}\right]\right]


Exemple
+++++++

Considérons un système continu de premier ordre de fonction de transfert 

.. math ::

    F(p)=\frac{K}{1+\tau p}


La Fonction de transfert discrete est égale à 

.. math ::

  F(z)=K\left(\frac{1-e^{-\frac{T_e}{\tau}}}{z-e^{-\frac{T_e}{\tau}}} \right)

où :math:`T_e` désigne la période d'échantillonnage. 

Correcteurs Numériques
----------------------

Proportionnel
+++++++++++++

.. math ::

  C(z)=K_p

* Paramètres du correcteur: :math:`\boldsymbol \theta=\{K_p\}`. 


PI
++

En "numérisant" l'intégration continue, la fonction de transfert d'un correcteur PI numérique est donnée par

.. math ::

  C(z)=K_p\left(1+\frac{T_e}{T_i}\frac{z}{z-1}\right)

* Paramètres du correcteur: :math:`\boldsymbol \theta=\{K_p,T_i\}`. 


PID
+++

.. math ::

  C(z)=K_p\left(1+\frac{T_e}{T_i}\frac{z}{z-1}+\frac{T_d}{T_e}\frac{z-1}{z}\right)

* Paramètres du correcteur: :math:`\boldsymbol \theta=\{K_p,T_i,T_d\}`. 