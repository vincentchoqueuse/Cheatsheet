Systèmes Echantillonnés
=======================

Contexte
--------

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

Dans la plupart des cas, nous utiliserons par abus de notation la relation suivante :

.. math ::

    F(z)=\frac{z-1}{z}TZ\left[\frac{F(p)}{p}\right]


Exemple
+++++++

Considérons un système continu de premier ordre de fonction de transfert 

.. math ::

    F(p)=\frac{K}{1+\tau p}


La Fonction de transfert discrete est égale à 

.. math ::

  F(z)=K\left(\frac{1-e^{-\frac{T_e}{\tau}}}{z-e^{-\frac{T_e}{\tau}}} \right)

où :math:`T_e` désigne la période d'échantillonnage.