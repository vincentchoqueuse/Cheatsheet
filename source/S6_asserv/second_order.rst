Systèmes de 2nd ordre (Continus)
================================

Modélisation
------------

Pour un système passe-bas linéaire d'ordre 2, le lien entre l'entrée et la sortie peut être régit par une équation différentielle de second ordre à coefficients constants.

.. math :: 

    \frac{1}{\omega_n^2}\frac{d^2 s(t)}{dt^2}+\frac{2m}{\omega_n}\frac{d s(t)}{dt}+s(t)=Ke(t)

* :math:`K\ge 0` : gain statique
* :math:`m \ge 0` : coefficient d'amortissement
* :math:`\omega_n` : pulsation propre (en rad/s)

La fonction de transfert d'un système passe-bas de second ordre est donnée par :

.. math :: 

    H(p)=\frac{K}{\frac{1}{\omega_n^2}p^2+\frac{2m}{\omega_n}p+1}

Pôles 
+++++

.. plot ::
    :context: close-figs
    :include-source: false

    import numpy as np 
    import matplotlib.pyplot as plt


    m_vect = [0.5,1,1.25]
    w0 = 1

    fig = plt.figure(figsize=[7,4.8])

    for m in m_vect:
        poles = np.sort(np.roots([1/(w0**2),2*m/w0,1]))
        plt.plot(np.real(poles),np.imag(poles),'x',label="m={}".format(m))

    plt.xlabel("$\Re e(.)$")
    plt.ylabel("$\Im m(.)$")
    plt.legend()
    plt.grid()
    plt.axis("equal")
    plt.xlim([-4,2])

- Cas où :math:`m>1`:
    - :math:`p_{1}=-\omega_n(m-\sqrt{m^2-1})`
    - :math:`p_{2}=-\omega_n(m+\sqrt{m^2-1})`
   
- Cas où :math:`m=1`: 
    - :math:`p_1 = p_2 = -m\omega_n`

- Cas où :math:`0\le m<1`:
    - :math:`p_{1}=-\omega_n(m-j\sqrt{1-m^2})`
    - :math:`p_{2}=-\omega_n(m+j\sqrt{1-m^2})`

.. note :: 

    Lorsque :math:`0\le m<1`, 
    
    * La pulsation propre est donnée par le module des pôles :math:`\omega_n=|p_{k}|`. 
    * Le coefficient d'amortissement est égal à :math:`m=-\Re e(p_{k})/|p_{k}|`.

Réponse Indicielle
-------------------

Cas où :math:`m>1`
++++++++++++++++++

**Expression**

La réponse indicielle s'exprime sous la forme :

.. math ::

    s(t)=KE\left(1-\frac{1}{2\omega_n\sqrt{m^2-1}}\left(p_1 e^{p_2 t}-p_2 e^{p_1 t} \right)\right)u(t)

**Exemple**

.. plot ::
    :context: close-figs
    :include-source: false

    from scipy.signal import lti
    import matplotlib.pyplot as plt

    K1, m1, wn1 = 10,2,100
    H1 = lti([K1],[1/(wn1**2),2*m1/wn1,1])
    E = 1
    t,s = H1.step(T=np.arange(0,0.25,0.001))  #E=1
    tr = 3/(-H1.poles[1])

    plt.plot(t,s)
    plt.plot([0,tr,tr],[0.95*K1*E,0.95*K1*E,0],'r--')
    plt.grid()
    plt.xticks([tr],["$t_r= -3/p_1$"])
    plt.yticks([K1*E,0.95*K1*E],["$s(\infty)=KE$","$0.95KE$"])
    plt.xlim([0,0.25])
    plt.ylim([0,11])
    plt.xlabel("temps [s]");

**Propriétés**

* Valeur initiale : :math:`s(0)=0`,
* Valeur finale : :math:`s(\infty)=KE`,
* Temps de réponse à :math:`\pm 5\%` : Pas de formule simple. Lorsque :math:`m\gg 1`, le temps de réponse est dicté par le pôle le plus lent c-a-d :math:`t_r\approx -\frac{3}{p_1}`
* Pas de dépassement : :math:`s(\infty)=\max(s(t))=KE`

Cas où :math:`m<1`
++++++++++++++++++

**Expression**

La réponse indicielle s'exprime sous la forme :

.. math ::

    s(t)=KE\left(1-\frac{1}{\sqrt{1-m^2}}e^{-m\omega_nt}\cos\left(\omega_n\sqrt{1-m^2}t-\arcsin(m)\right)\right)u(t)

**Exemple**

.. plot ::
    :context: close-figs
    :include-source: false

    K3, m3, wn3 = 10,0.05,100
    H3 = lti([K3],[1/(wn3**2),2*m3/wn3,1])
    E = 1
    t,s = H3.step(T=np.arange(0,0.7,0.001))  #E=1
    Dr = np.exp(-np.pi*m3/np.sqrt(1-m3**2))

    plt.plot(t,s)
    plt.plot(t,K3*E*(1+(1/np.sqrt(1-m3**2))*np.exp(-m3*wn3*t)),'r--')
    plt.plot(t,K3*E*(1-(1/np.sqrt(1-m3**2))*np.exp(-m3*wn3*t)),'r--')
    plt.plot([0,0.7],[K3*E,K3*E],'r--')
    plt.plot([0,0.7],[K3*E*(1+Dr),K3*E*(1+Dr)],'r--')
    plt.yticks([K3*E,K3*E*(1+Dr)],["$s(\infty)$","$\max[s(t)]$"])
    plt.grid()
    plt.xlim([0,0.7])
    plt.xlabel("temps [s]")


**Propriétés**

* Valeur initiale : :math:`s(0)=0`,
* Valeur finale : :math:`s(\infty)=KE`,
* Temps de réponse à :math:`\pm 5\%` : Pas de formule simple, nous utiliserons des abaques. Lorsque :math:`m\to 0`, le temps de réponse est approximativement imposé par l'enveloppe c-a-d :math:`t_r\approx \frac{3}{\omega_n m}`,
* Présence d'oscillations à la pseudo-pulsation (rad/s):

.. math ::

    \omega_p = \omega_n\sqrt{1-m^2}

* Premier Dépassement relatif : 

.. math ::

    D_r(\%)=\frac{\max[s(\infty)]-s(\infty)}{s(\infty)} =e^{\frac{-\pi m}{\sqrt{1-m^2}}}

.. note ::

    En pratique, nous utiliserons des abaques pour déterminer le temps de réponse et le premier dépassement relatif : https://vincentchoqueuse.github.io/ENIB_tools/control_settling_time.html


Réponse Fréquentielle
---------------------

La réponse fréquentielle s'obtient en posant :math:`p=j\omega` où :math:`\omega` désigne la pulsation (en rad/s). La réponse fréquentielle d'un système passe-bas de premier ordre est donnée par :

.. math ::

    H(j\omega)=\frac{K}{1-\frac{\omega^2}{\omega_n^2}+j\frac{2m\omega }{\omega_n}}

* Comportement à la pulsation propre :math:`\omega_n` (rad/s) : :math:`H(j\omega_n)=\frac{K}{2jm}`.

Module
++++++

**Expression**

Pour :math:`K>0`, le module s'exprime sous la forme

.. math ::

    |H(j\omega)|=\frac{K}{\sqrt{\left(1-\frac{\omega^2}{\omega_n^2}\right)^2+\frac{4m^2\omega^2}{\omega_n^2}}}


**Exemple**

.. plot ::
    :context: close-figs
    :include-source: false

    w,H3jw = H3.freqresp(w=np.logspace(0,4,200))
    K3, m3, wn3 = 10,0.05,100
    H3 = lti([K3],[1/(wn3**2),2*m3/wn3,1])
    wr = wn3*np.sqrt(1-2*m3**2)
    Gm = K3/(2*m3*np.sqrt(1-m3**2))
    ax = plt.loglog(w,np.abs(H3jw))
    plt.plot([0,wr,wr],[K3/(2*m3*np.sqrt(1-m3**2)),K3/(2*m3*np.sqrt(1-m3**2)),0],'r--')
    plt.plot([1,100],[K3,K3],'r--')
    plt.plot([1,10000],[K3*(wn3/1)**2,K3*(wn3/10000)**2],'r--')
    plt.grid()
    plt.ylim([0.001,200])
    plt.xlim([1,10000])
    plt.yticks([K3,Gm],["$G_0$", "$G_m$"])
    plt.xticks([wr],["$\omega_r$"])
    plt.xlabel("$w$ [rad/s]")
    plt.ylabel("$|H(j\omega)|_{dB}$")


**Propriétés**

* Amplification basse-fréquence : :math:`\lim_{\omega\to 0}|H(j\omega)|=K`,
* Amplification haute-fréquence : :math:`\lim_{\omega\to \infty}|H(j\omega)|=0`.
* Comportement asymptotique : Pour :math:`\omega \gg \omega_n`, :math:`|H(j\omega)|\approx K \left(\frac{\omega_n}{\omega}\right)^2`
* Si :math:`m<\frac{1}{\sqrt{2}}`, la module présente un extremum à la pulsation de résonance: :math:`\omega_r = \omega_n \sqrt{1-2m^2}`. A la pulsation de résonance, le module est égal à :math:`|H(j\omega_r)|=\frac{K}{2m\sqrt{1-m^2}}`. En pratique, nous utiliserons essentiellement le facteur de resonance :math:`M` qui est égal en valeur naturelle à 

.. math ::

    M=\frac{|H(j\omega_r)|}{K}=\frac{1}{2m\sqrt{1-m^2}}

.. note ::

    En dB, le facteur de résonance s'exprime sous la forme :math:`M_{dB} = G_m - G_0`.

.. note ::

    En pratique, nous utiliserons des abaques pour déterminer le facteur de résonance en dB : https://vincentchoqueuse.github.io/ENIB_tools/control_resonance.html

