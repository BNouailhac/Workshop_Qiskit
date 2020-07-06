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
> le "output = 'mpl'" nous sert juste 
