Getting Started
===============

Ce site comporte plusieurs résumés de plusieurs cours. 
Ces cours sont illustrés au moyen du langage de programmation Python et des libraires `numpy`, `scipy`, `matplotlib`, `control`, `seaborn` et `jupyter`.

Distribution Python
-------------------

.. note ::

    Pour des raisons de sobriété numérique, je vous recommande d'utiliser `miniconda` au lieu d'`anaconda`.


Pour gérer différentes distributions Python, la solution la plus simple consiste à utiliser `conda`. 

* Miniconda: https://docs.conda.io/en/latest/miniconda.html
* Tutorial d'installation: https://www.youtube.com/watch?v=XCvgyvBFjyM
* Cheatsheet: https://docs.conda.io/projects/conda/en/4.6.0/_downloads/52a95608c49671267e40c689e0bc00ca/conda-cheatsheet.pdf

Pour vérifier que l'installation fonctionne bien, lancez un terminal ou l'`anaconda prompt` sous windows, puis tapez la commande `python`.


Gestion des paquets
+++++++++++++++++++

Pour connaître la liste des paquets python installés, il suffit de lancer via le terminal ou l'`anaconda prompt` la commande 

.. code ::

    pip list

Pour installer de nouveaux paquets, il suffit de lancer la commande `conda install`.

.. code ::

    conda install scipy matplotlib seaborn pandas jupyter 

Notons qu'il est préférable d'installer les paquets avec `conda` plutôt que `pip` (https://www.anaconda.com/blog/understanding-conda-and-pip).

Gestion des environnements
++++++++++++++++++++++++++

Lorsque vous utilisez Python pour des projets très différents (calculs numériques, machine learning, développement web), il est préférable de travailler avec différents environnements Python. 
En isolant vos environnements, il est ainsi possible de faire cohabiter des projets utilisant différentes versions de paquets Python.

Conda permet de gérer très facilement plusieurs environnements avec des versions de Python et des paquets différents. La liste
des environnements disponibles s'obtient via la commande 

.. code ::  
    
    conda env list


**Création** 

Pour créer un nouvel environnement `conda`, il suffit de lancer la commande

.. code ::

    conda create --name myenv_py39 python=3.9

**Activation**

L'activation de l'environnement s'obtient en lançant la commande

.. code ::

    conda activate myenv_py39

**Désactivation**

La désactivation de l'environnement courant s'obtient en lançant la commande

.. code ::

    conda deactivate myenv_py39

