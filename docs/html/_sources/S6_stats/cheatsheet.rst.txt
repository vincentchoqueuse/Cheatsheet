Cheatsheet
==========

Les labos de statistiques reposent essentiellement sur l'utilisation de `numpy`, `scipy`, `matplotlib` et `seaborn`.

.. plot ::
    :context: close-figs

    import numpy as np
    import matplotlib.pyplot as plt
    import seaborn as sns
    from scipy.stats import norm, randint

    sns.set_theme()
    
Distributions Continues
-----------------------

* Liste des lois continues : https://docs.scipy.org/doc/scipy/reference/stats.html#continuous-distributions 

Exemple
+++++++

La classe `norm` permet de générer des réalisations suivant une loi Gaussienne (normale)

.. note ::

    Documentation: https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.norm.html

.. plot ::
    :context:

    N = 10000
    rv = norm(loc=1,scale=3)
    x = rv.rvs(size=N)  # realisation de la va

Statistiques Empiriques
+++++++++++++++++++++++

Les statistiques empiriques peuvent s'obtenir en utilisant les fonctionnalités de `numpy`.

.. plot ::
    :context:
    
    mean_est = np.mean(x)  # moyenne empirique
    std_est = np.std(x)    # écart type 
    var_est = np.var(x)    # variance empirique

Histogramme
+++++++++++

.. note ::

    Documentation : https://seaborn.pydata.org/generated/seaborn.histplot.html

.. plot ::
    :context:

    ax = sns.histplot(data=x,stat="density")

Il est également possible de superposer la densité de probabilité théorique en utilisant la méthode `pdf` de l'objet
`norm`.

.. plot ::
    :context:

    vect = np.arange(-10,10,0.1)
    ax.plot(vect,rv.pdf(vect),"r",label="pdf")
    ax.set(xlabel="x");
    ax.legend()

Fonction de répartition
+++++++++++++++++++++++

.. plot ::
    :context: close-figs

    plt.figure()
    ax = sns.histplot(data=x,stat="density",cumulative=True,label="exp")
    vect = np.arange(-10,10,0.1)
    ax.plot(vect,rv.cdf(vect),"r",label="cdf")
    ax.set(xlabel="x");
    ax.legend()


Distributions Discrètes
-----------------------

* Liste des lois discrètes : https://docs.scipy.org/doc/scipy/reference/stats.html#discrete-distributions 

Exemple
+++++++


Le classe `randint` permet de générer une loi uniforme discrète.

.. note ::

    Documentation: https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.randint.html

.. plot ::
    :context: close-figs

    N = 1000
    rv = randint(low=1,high=7)
    x = rv.rvs(size=N)

Histogramme
+++++++++++

.. note ::

    Documentation : https://seaborn.pydata.org/generated/seaborn.histplot.html

.. plot ::
    :context: 

    sns.histplot(data=x,stat="density",discrete=True)