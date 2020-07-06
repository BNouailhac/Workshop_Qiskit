# Workshop_Qiskit

L'objectif de ce Workshop est de vous initier au framework Quiskit pour python
----------------------------
## Qu'est-ce que Qiskit ?
Qiskit est un framework pour le language python qui permet de simuler des circuits quantique sur son ordinateur et même de les testers directements sur des ordinateur quantique grâce à IBM.

----------------------------
## 1. étape :
Commencons par installer les prérequis:
- Tout d'abord installer Anaconda prompt sur votre ordinateur: https://www.anaconda.com/products/individual

![Annaconda prompt](https://github.com/BNouailhac/Workshop_Quiskit/blob/master/git%20image/Capture2.PNG)

- ensuite lancez le et faite "pip install qiskit"
- maintenant faite "jupyter notebook"
cela devrait vous ouvrir cela dans votre navigateur:

![jupyter](https://github.com/BNouailhac/Workshop_Quiskit/blob/master/git%20image/Capture.PNG)

- maintenant cliquer sur "new" et créez un fichier python3.
> jupyter va nous servir à interpréter nos commandes qiskit lignes par lignes.

----------------------------
## 2. étape :
Ajoutons qiskit à notre code
```
from qiskit import *
```

----------------------------
## 3. étape :
teston si qiskit est bien installée sur votre ordinateur
```
qiskit.__qiskit_version__
```
----------------------------
## 4. étape :
maintenant nous allons créer des qbits et des bits qui nous serviront pour la suite
```
qr = QuantumRegister(2)

cr = ClassicalRegister(2)
```
> on peut mettre plusieurs arguments au QuantumRegister et ClassicalRegister pour les modifiers, ici le "(2)" permet de choisir le nombre de qbits et bits créaient.
----------------------------
## 5. étape :
maintenant nous allons créer un circuit informatique quantique qui va utiliser les 2 variables que nous venons de crer
```
circuit = QuantumCircuit(qr, cr)
```
----------------------------
## 6. étape :
Regardons ce à quoi ca ressemble:
```
circuit.draw()
```
> cela va vous montrer le circuit donc vous verrez juste les 2 qbits et bits.

----------------------------
## 7. étape :
Ajoutons maintenant une porte quantique qui va agir sur nos deux qbits et observont le résultat:
```
circuit.cx(qr[0], qr[1])

circuit.draw()
```
> cela va vous montrer le circuit donc vous verrez juste les 2 qbits et bits.

----------------------------
## 8. étape :
Ajoutons maintenant des portes quantique (H gate et CNOT gate) qui vont agir sur nos qbits et observont le résultat:
```
circuit.h(qr[0])

circuit.cx(qr[0], qr[1])

circuit.draw()
```
> pour connaitre les effets des portes quantique: https://quantum-computing.ibm.com/docs/circ-comp/q-gates#h-gate

----------------------------
## 9. étape :
maintenant nous allons écrire les résultats des deux portes d'avants sur les bits classiques:
```
circuit.measure(qr, cr)

circuit.draw(output = 'mpl')
```
> le "output = 'mpl'" nous sert juste à changer le type d'affichage.

----------------------------
## 10. étape :
maintenant nous allons écrire les résultats des deux portes d'avants sur les bits classiques:
```
circuit.measure(qr, cr)

circuit.draw(output = 'mpl')
```
> le "output = 'mpl'" nous sert juste à changer le type d'affichage.

----------------------------
## 11. étape :
et maintenant nous allons tester notre circuit en local:
```
simulator = Aer.get_backend('qasm_simulator') // on utiliser le simulateur 'qasm_simulator'

result = execute(circuit, backend = simulator).result() // on lance le test
```

----------------------------
## 12. étape :
et affichons les résultats dans un histogram:
```
from qiskit.tools.visualization import plot_histogram

plot_histogram(result.get_counts(circuit))
```
> Si cela à bien fonctionné vous avez maintenant un les différents résultats obtenue qui apparaisse  à l'écran.

----------------------------
## 13. étape :
Nous avons pu voir avant que notre code fonctionné sur notre ordianteur, donc éssayons maintenant de tester notre code sur un véritable ordinateur quantique:
Pour cela il va falloir créer un compte IBM et récupérer une clef d'accès: https://quantum-computing.ibm.com/

![IBM](https://github.com/BNouailhac/Workshop_Quiskit/blob/master/git%20image/Capture3.PNG)

Ensuite on l'utilise comme cela:
```
from qiskit import IBMQ

IBMQ.save_account('votre_token')

IBMQ.load_account()
```

----------------------------
## 14. étape :
Ensuite on paramètre le teste que l'on va executer:
```
provider = IBMQ.get_provider('ibm-q') // on dit que le fournisseur est ibm

qcomp = provider.get_backend('ibmq_16_melbourne') // on veut utiliser l'ordinateur quantique du nom de 'ibmq_16_melbourne'

job = execute(circuit, backend=qcomp) // on donne à job (la viariable qui va effectuer le test) notre circuit.
```

----------------------------
## 15. étape :
Lançons le test:
```
from qiskit.tools.monitor import job_monitor

job_monitor(job)
```
> Cela va prendre plusieurs minutes car vous allez devoir faire la queue avec les autres personnes souhaitant utiliser le même ordinateur quantique que vous.

----------------------------
## 16. étape :
Affichons les tests:
```
result = job.result()

plot_histogram(result.get_counts(circuit))
```
> Vous pouvez vous rendre compte que les résultats sont différends de ceux de tout a l'heure, cela est du au fait que même si qiskit peut simuler un ordinateur quantique, il ne le fait pas parfaitement ce qui explique la différence de résultat.

----------------------------
## 17. étape :
Merci d'avoir suivi ce Workshop, si vous souhaitez aller plus loin dans l'utilisation de qiskit, n'hésitez à continuez a apprendre sur ce framework directement sur le site de qiskit : https://qiskit.org/
