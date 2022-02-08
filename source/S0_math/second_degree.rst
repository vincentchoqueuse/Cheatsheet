Equations du Second Degré
=========================

Modèle Mathématique 
-------------------

Un polynôme du second degré peut s'écrire sous la forme

.. math ::

    p(x) = ax^2+bx+c

Exemple 
+++++++

.. plot ::

    import numpy as np
    import matplotlib.pyplot as plt

    a,b,c = 2,6,1

    x = np.arange(-5,5,0.001)
    p_x = a*(x**2)+b*x+c

    # plot figure
    plt.plot(x,p_x)
    plt.grid()
    plt.xlim([-5,5])
    plt.xlabel("x")


Expression des racines
----------------------

Les racines de :math:`p(x)` sont les valeurs de :math:`x` pour lesquelles 

.. math::
    
    p(x)=ax^2+bx+c=0

Les racines peuvent s'obtenir par identification avec la forme factorisée suivante 

.. math::
    
    p(x) &= a(x-x_1)(x - x_2)
    &=ax^2 - a(x_2 + x_1) +ax_1x_2
    
En particulier, nous 

Un polynôme de degré 2 possèdent 2 racines notées :math:`x_1`et :math:`x_2`. L'expression de ces 2 racines dépend de la valeur du discriminant 

.. math ::

    \Delta = b^2-4ac 


* :math:`\Delta > 0` : Le polynôme possède deux racines réelles 

.. math ::

    x_{1,2} = \frac{-b\pm \sqrt{\Delta}}{2a}\\

* :math:`\Delta = 0` : Le polynôme possède une racine double

.. math ::

    x_1 = x_2 = -\frac{b}{2a}


* :math:`\Delta < 0` : Le polynôme possède deux racines complexes-conjuguées

.. math ::

    x_{1,2} = \frac{-b\pm j\sqrt{|\Delta|}}{2a}\\
