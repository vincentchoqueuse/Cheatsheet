Liste des correcteurs
=====================

Contexte
--------

Considérons un système en boucle fermée avec un retour unitaire 

.. figure:: img/closed_loop_2.svg
  :width: 300
  :align: center
  :alt: Boucle Fermée avec Retour unitaire

  Boucle Fermée avec Retour Unitaire

* :math:`E(p)`: Transformée de Laplace de la consigne,
* :math:`C(p)`: Fonction de transfert du correcteur,
* :math:`F(p)`: Fonction de transfert du système + capteur,
* :math:`C(p)F(p)`: Fonction de transfert en boucle ouverte (FTBO).

Correcteurs Usuels 
------------------

Pour respecter les contraintes du cahier des charges, nous pouvons utiliser différents types de correcteurs :math:`C(p)`.
Ces correcteurs possèdent un ou plusieurs paramètres de liberté que nous pouvons ajuster en fonction des performances souhaitées. 

Proportionnel
+++++++++++++

La fonction de transfert du correcteur P est donnée par:

.. math ::

    C(p) = K_c

* Paramètre du correcteur: :math:`K_c`

Proportionnel Intégral
++++++++++++++++++++++ 

La fonction de transfert du correcteur PI est donnée par:

.. math ::

    C(p) = K_c \left(1+ \frac{1}{T_ip}\right) = K_c \frac{T_i p+1}{T_ip}

* Paramètres du correcteur: :math:`K_c`, :math:`T_i`

Proportionnel Dérivé
++++++++++++++++++++

La fonction de transfert du correcteur PD est donnée par:

.. math ::

    C(p) = K_c (1+T_d p)

* Paramètres du correcteur: :math:`K_c`, :math:`T_d`

Proportionnel Intégral Dérivé
+++++++++++++++++++++++++++++

La fonction de transfert du correcteur PID est donnée par:

.. math ::

    C(p) = K_c\left(1+\frac{1}{T_ip}+T_d p\right) = K_c \frac{T_iT_d p^2+T_i p+1}{T_ip}

* Paramètres du correcteur: :math:`K_c`, :math:`T_i`, :math:`T_d`
