Filter Transformation
=====================

Introduction
------------

Pour synthétiser un filtre d'ordre N, la procédure classique consiste à d'abord synthétiser son équivalent "passe-bas" normalisé puis à réaliser une dénormalisation. 
Le plus souvent, cette dénormalisation est réalisée en modifiant la variable :math:`p` de la manière suivante 

.. math ::

    H(p) = \left.H_n(p)\right|_{p=f(p)}

* :math:`f(p)`: fonction de transformation,
* :math:`H_n(p)`: fonction de transfert du filtre normalisé,
* :math:`H(p)`: fonction de transfert du filtre dénormalisé.


Mapping Fréquentiel 
+++++++++++++++++++

En réalisant la substitution :math:`p=f(p)`, la pulsation :math:`\omega` rad/s du filtre normalisé est mappée à la pulsation :math:`\widehat{\omega}` rad/s où

.. math ::

    j\omega = f(j\widehat{\omega})

Mapping des pôles et zéros  
++++++++++++++++++++++++++

En réalisant la substitution :math:`p=f(p)`, le pôles :math:`p_n` du filtre normalisé est mappé vers le pôle  :math:`\widehat{p}_n` où 

.. math ::

    f(\widehat{p}_n) - p_n = 0


Dénormalisation Passe-Bas 
-------------------------

.. math ::

    f(p) = \frac{p}{\omega_c}


Mapping Fréquentiel 
+++++++++++++++++++

La pulsation :math:`\omega` rad/s du filtre normalisé est mappée à la pulsation 

.. math :: 

    \widehat{\omega}=\omega_c\omega 


.. plot ::
    :context: close-figs
    :include-source: false

    import numpy as np 
    from scipy.signal import lti, cheby1
    import matplotlib.pyplot as plt

    num, den = cheby1(5,3,1, analog=True)
    num2, den2 = cheby1(5,3,100, analog=True)
    sys = lti(num,den)
    sys2 = lti(num2,den2)
    w,Hjw = sys.freqresp()
    w2,Hjw2 = sys2.freqresp()

    fig, axs = plt.subplots(1, 2,figsize=(10,4))
    axs[0].loglog(w, np.abs(Hjw))
    axs[0].set_xlabel("w [rad/s]")
    axs[0].set_ylabel("Module")
    axs[0].grid()
    axs[0].set_xlim([0.1,10])
    axs[0].set_ylim([0.01,2])
    axs[0].set_title("Filtre Normalisée ")
    axs[1].loglog(w2, np.abs(Hjw2))
    axs[1].set_xlabel("w [rad/s]")
    axs[1].set_ylabel("Module")
    axs[1].set_title("Filtre Dénormalisée ")
    axs[1].set_xlim([10,1000])
    axs[1].set_ylim([0.01,2])
    axs[1].grid()
    fig.tight_layout()

Mapping des pôles et zéros  
++++++++++++++++++++++++++

Les pôles :math:`p_n` et zéros :math:`z_n` du filtre normalisé sont mappés aux pôles et zéros

.. math::     

    \widehat{p}_n&=\omega_c p_n\\
    \widehat{z}_n&=\omega_c z_n

.. plot ::
    :context: close-figs
    :include-source: false

    import numpy as np 
    from scipy.signal import lti, cheby1
    import matplotlib.pyplot as plt

    z,p,k = cheby1(5,3,1, analog=True,output='zpk')
    z2,p2,k2 = cheby1(5,3,100, analog=True,output='zpk')

    fig, axs = plt.subplots(1, 2,figsize=(10,4))
    axs[0].plot(np.real(p),np.imag(p),'x')
    axs[0].plot(np.real(z),np.imag(z),'o')
    axs[0].set_xlabel("Re (.)")
    axs[0].set_ylabel("Im (.)")
    axs[0].axis("equal")
    axs[0].grid()
    axs[0].set_title("Filtre Normalisée ")
    axs[1].plot(np.real(p2),np.imag(p2),'x')
    axs[1].plot(np.real(z2),np.imag(z2),'o')
    axs[1].set_xlabel("Re (.)")
    axs[1].set_ylabel("Im (.)")
    axs[1].axis("equal")
    axs[1].grid()
    axs[1].set_title("Filtre Dénormalisée ")
    fig.tight_layout()



Dénormalisation Passe-Haut 
--------------------------


.. math ::

    f(p) = \frac{\omega_c}{p}

Mapping Fréquentiel 
+++++++++++++++++++

La pulsation :math:`\omega` rad/s du filtre normalisé est mappée à la pulsation 

.. math :: 

    \widehat{\omega}=-\omega_c/\omega 

.. plot ::
    :context: close-figs
    :include-source: false

    import numpy as np 
    from scipy.signal import lti, cheby1
    import matplotlib.pyplot as plt

    num, den = cheby1(5,3,1, analog=True)
    num2, den2 = cheby1(5,3,100, btype="highpass", analog=True)
    sys = lti(num,den)
    sys2 = lti(num2,den2)
    w,Hjw = sys.freqresp()
    w2,Hjw2 = sys2.freqresp()

    fig, axs = plt.subplots(1, 2,figsize=(10,4))
    axs[0].loglog(w, np.abs(Hjw))
    axs[0].set_xlabel("w [rad/s]")
    axs[0].set_ylabel("Module")
    axs[0].grid()
    axs[0].set_xlim([0.1,10])
    axs[0].set_ylim([0.01,2])
    axs[0].set_title("Filtre Normalisée ")
    axs[1].loglog(w2, np.abs(Hjw2))
    axs[1].set_xlabel("w [rad/s]")
    axs[1].set_ylabel("Module")
    axs[1].set_title("Filtre Dénormalisée ")
    axs[1].set_xlim([10,1000])
    axs[1].set_ylim([0.01,2])
    axs[1].grid()
    fig.tight_layout()

Mapping des pôles et zéros  
++++++++++++++++++++++++++

Les pôles :math:`p_n` et zéros :math:`z_n` du filtre normalisé sont mappés aux pôles et zéros

.. math::     

    \widehat{p}_n&=\omega_c /p_n\\
    \widehat{z}_n&=\omega_c /z_n

.. plot ::
    :context: close-figs
    :include-source: false

    import numpy as np 
    from scipy.signal import lti, cheby1
    import matplotlib.pyplot as plt

    z,p,k = cheby1(5,3,1, analog=True,output='zpk')
    z2,p2,k2 = cheby1(5,3,100, btype="highpass", analog=True,output='zpk')

    fig, axs = plt.subplots(1, 2,figsize=(10,4))
    axs[0].plot(np.real(p),np.imag(p),'x')
    axs[0].plot(np.real(z),np.imag(z),'o')
    axs[0].set_xlabel("Re (.)")
    axs[0].set_ylabel("Im (.)")
    axs[0].axis("equal")
    axs[0].grid()
    axs[0].set_title("Filtre Normalisée ")
    axs[1].plot(np.real(p2),np.imag(p2),'x')
    axs[1].plot(np.real(z2),np.imag(z2),'o')
    axs[1].set_xlabel("Re (.)")
    axs[1].set_ylabel("Im (.)")
    axs[1].axis("equal")
    axs[1].grid()
    axs[1].set_title("Filtre Dénormalisée ")
    fig.tight_layout()


Dénormalisation Passe-Bande 
---------------------------

.. math ::

    f(p) = \frac{p^2+\omega_0^2}{p\Delta \omega}

où :math:`\omega_0=\sqrt{\omega_{c1}\omega_{c2}}` désigne la pulsation centrale et :math:`\Delta \omega=\omega_{c2}-\omega_{c1}` désigne la largeur de la bande passante.


Mapping Fréquentiel 
+++++++++++++++++++

La pulsation :math:`\omega` rad/s du filtre normalisé est mappée à la pulsation :math:`\widehat{\omega}` où 

.. math :: 

    \widehat{\omega}^2-\widehat{\omega}\omega \Delta \omega -\omega_0^2=0 

.. plot ::
    :context: close-figs
    :include-source: false

    import numpy as np 
    from scipy.signal import lti, cheby1
    import matplotlib.pyplot as plt

    num, den = cheby1(5,3,1, analog=True)
    num2, den2 = cheby1(5,3,[50,200], btype="bandpass", analog=True)
    sys = lti(num,den)
    sys2 = lti(num2,den2)
    w,Hjw = sys.freqresp()
    w2,Hjw2 = sys2.freqresp()

    fig, axs = plt.subplots(1, 2,figsize=(10,4))
    axs[0].loglog(w, np.abs(Hjw))
    axs[0].set_xlabel("w [rad/s]")
    axs[0].set_ylabel("Module")
    axs[0].grid()
    axs[0].set_xlim([0.1,10])
    axs[0].set_ylim([0.01,2])
    axs[0].set_title("Filtre Normalisée ")
    axs[1].loglog(w2, np.abs(Hjw2))
    axs[1].set_xlabel("w [rad/s]")
    axs[1].set_ylabel("Module")
    axs[1].set_title("Filtre Dénormalisée ")
    axs[1].set_xlim([10,1000])
    axs[1].set_ylim([0.01,2])
    axs[1].grid()
    fig.tight_layout()

Mapping des pôles et zéros  
++++++++++++++++++++++++++

Les pôles :math:`p_n` et zéros :math:`z_n` du filtre normalisé sont mappés aux pôles et zéros

.. math::     

    \widehat{p}_n&=\alpha p_n \pm \sqrt{\alpha^2p_n^2-\omega_0^2}\\
    \widehat{z}_n&=\alpha z_n \pm \sqrt{\alpha^2z_n^2-\omega_0^2}

où :math:`\alpha=\Delta \omega/2`. Pour obtenir un passe-bande, il est également nécessaire d'ajouter plusieurs zéros en 0.

.. plot ::
    :context: close-figs
    :include-source: false

    import numpy as np 
    from scipy.signal import lti, cheby1
    import matplotlib.pyplot as plt

    z,p,k  = cheby1(5,3,1, analog=True,output='zpk')
    z2,p2,k2 = cheby1(5,3,[50,200], btype="bandpass", analog=True,output='zpk')

    fig, axs = plt.subplots(1, 2,figsize=(10,4))
    axs[0].plot(np.real(p),np.imag(p),'x')
    axs[0].plot(np.real(z),np.imag(z),'o')
    axs[0].set_xlabel("Re (.)")
    axs[0].set_ylabel("Im (.)")
    axs[0].axis("equal")
    axs[0].grid()
    axs[0].set_title("Filtre Normalisée ")
    axs[1].plot(np.real(p2),np.imag(p2),'x')
    axs[1].plot(np.real(z2),np.imag(z2),'o')
    axs[1].set_xlabel("Re (.)")
    axs[1].set_ylabel("Im (.)")
    axs[1].axis("equal")
    axs[1].grid()
    axs[1].set_title("Filtre Dénormalisée ")
    fig.tight_layout()


Dénormalisation Rejecteur 
-------------------------

.. math ::

    f(p) = \frac{p\Delta \omega}{p^2+\omega_0^2}

où :math:`\omega_0=\sqrt{\omega_{c1}\omega_{c2}}` désigne la pulsation centrale et :math:`\Delta \omega=\omega_{c2}-\omega_{c1}` désigne la largeur de la bande passante.

Mapping Fréquentiel 
+++++++++++++++++++

La pulsation :math:`\omega` rad/s du filtre normalisé est mappée à la pulsation :math:`\widehat{\omega}` où 

.. math :: 

    \widehat{\omega}^2+\widehat{\omega}(\Delta \omega/\omega ) -\omega_0^2=0 


.. plot ::
    :context: close-figs
    :include-source: false

    import numpy as np 
    from scipy.signal import lti, cheby1
    import matplotlib.pyplot as plt

    num, den = cheby1(5,3,1, analog=True)
    num2, den2 = cheby1(5,3,[50,200], btype="bandstop", analog=True)
    sys = lti(num,den)
    sys2 = lti(num2,den2)
    w,Hjw = sys.freqresp()
    w2,Hjw2 = sys2.freqresp()

    fig, axs = plt.subplots(1, 2,figsize=(10,4))
    axs[0].loglog(w, np.abs(Hjw))
    axs[0].set_xlabel("w [rad/s]")
    axs[0].set_ylabel("Module")
    axs[0].grid()
    axs[0].set_xlim([0.1,10])
    axs[0].set_ylim([0.01,2])
    axs[0].set_title("Filtre Normalisée ")
    axs[1].loglog(w2, np.abs(Hjw2))
    axs[1].set_xlabel("w [rad/s]")
    axs[1].set_ylabel("Module")
    axs[1].set_title("Filtre Dénormalisée ")
    axs[1].set_xlim([10,1000])
    axs[1].set_ylim([0.01,2])
    axs[1].grid()
    fig.tight_layout()

Mapping des pôles et zéros  
++++++++++++++++++++++++++

Les pôles :math:`p_n` et zéros :math:`z_n` du filtre normalisé sont mappés aux pôles et zéros

.. math::     

    \widehat{p}_n&=\alpha p_n^{-1} \pm \sqrt{\alpha^2p_n^{-2}-\omega_0^2}\\
    \widehat{z}_n&=\alpha z_n^{-1} \pm \sqrt{\alpha^2z_n^{-2}-\omega_0^2}

où :math:`\alpha=\Delta \omega/2`. Pour obtenir un rejecteur, il est également nécessaire d'ajouter plusieurs zéros en :math:`\pm j\omega_0`.

.. plot ::
    :context: close-figs
    :include-source: false

    import numpy as np 
    from scipy.signal import lti, cheby1
    import matplotlib.pyplot as plt

    z,p,k = cheby1(5,3,1, analog=True,output='zpk')
    z2,p2,k2 = cheby1(5,3,[50,200], btype="bandstop", analog=True,output='zpk')

    fig, axs = plt.subplots(1, 2,figsize=(10,4))
    axs[0].plot(np.real(p),np.imag(p),'x')
    axs[0].plot(np.real(z),np.imag(z),'o')
    axs[0].set_xlabel("Re (.)")
    axs[0].set_ylabel("Im (.)")
    axs[0].axis("equal")
    axs[0].grid()
    axs[0].set_title("Filtre Normalisée ")
    axs[1].plot(np.real(p2),np.imag(p2),'x')
    axs[1].plot(np.real(z2),np.imag(z2),'o')
    axs[1].set_xlabel("Re (.)")
    axs[1].set_ylabel("Im (.)")
    axs[1].axis("equal")
    axs[1].grid()
    axs[1].set_title("Filtre Dénormalisée ")
    fig.tight_layout()
