# Par Câble

## Consigne
Un de nos agents a réussi à acquérir les tensions qui passaient à travers un câble de communication de Hallebarde. Pouvez-vous interpréter le signal ?

## Resolution
Par analyse de ces tensions, on observe qu'il s'agit d'un codage par NRZ (Non-retour à Zéro). En effet, la tension passe de 1 à -1 (ou l'inverse) sans jamais revenir à 0.  
On sait que pour décoder ce message : 
  - Si la tension change entre n et n+1 on doit noter la valeur 1
  - Sinon c'est un 0

Par exemple prenons le début du signal :
1 1 1 -1 1 1 -1 -1 -1 -1 -1 1 -1  
On obtient :
0 0 1 1 0 1 0 0  
Ce qui nous donne la valeur 4 (conversion binaire to ascii) et correspond bien au format du flag **4**04CTF{flag}

Il ne nous reste plus qu'à faire un petit script en python pour trouver le flag.

```python
tension = '1 1 1 -1 1 1 -1 -1 -1 -1 -1 1 -1 -1 -1 -1 -1 -1 -1 1 -1 -1 1 1 1 1 -1 -1 -1 -1 -1 1 -1 -1 1 1 -1 -1 1 1 1 1 -1 -1 -1 -1 1 -1 -1 -1 1 -1 1 -1 -1 1 -1 -1 1 1 1 -1 1 -1 -1 -1 -1 1 -1 -1 -1 -1 -1 -1 1 -1 -1 1 -1 1 1 1 1 -1 1 1 1 -1 1 1 -1 -1 1 -1 1 -1 1 1 -1 -1 1 1 1 -1 -1 -1 -1 1 -1 -1 -1 1 -1 -1 1 -1 1 1 -1 -1 -1 -1 1 1 -1 -1 1 1 -1 -1 1 -1 1 1 1 -1 -1 -1 1 -1 -1 1 -1 1 1 1 -1 -1 1 -1 1 -1 1 1 -1 -1 1 -1 -1 1 1 1 1 -1 1 1 1 -1 1 1 -1 1 -1 -1 -1 1 1 1 1 -1 1 1 1 1 1 1 -1 -1 1 -1 1 -1 1 1 -1 -1 -1 1 1 1 -1 -1 1 -1 -1 1 -1 1 1 1 -1 -1 1 1 -1 1 1 1 1 -1 1 1 1 -1 1 1 -1 1 -1 -1 -1 1 1 1 -1 1 -1 -1 1 1 1 1 -1 -1 -1 -1 1 1 -1 -1 1 -1 -1 -1 1 1 1 1 -1 -1 1 -1 1 -1 1 1 -1 1 1 1 -1 1 1 1 1 -1 1 1 1 1 1 1 -1 1 -1 -1 -1 1 1 1 1 -1 1 1 1 -1 1 1 -1 1 -1 -1 1 -1 -1 -1 -1 1 -1 -1 -1 1 -1 -1 1 -1 1 1 1 -1 -1 -1 1 -1 1 -1 1 1 -1'
binaire = ''
flag = ''

# Transformer la chaine de caractère en tableau pour pouvoir comparer les valeurs
binaire = binaire + tension.replace(' ',',') 
binaire = binaire.split(',') 

# Si les deux valeurs sont les mêmes on note 0 sinon 1
for i in range (0,len(binaire)-1) :
    if binaire[i] == binaire[i+1] :
        flag +='0'
    else :
        flag +='1'
print(flag)
```
En sortie de ce programme nous obtenons :  
0011010000110000001101000100001101010100010001100111101101001110001100000110111000110011010111110101001000110011011101000101010101110010011011100101111101011010001100110111001000110000010111110100100101101110010101100011001101110010011101000100010101100100010111110110011000110000011100100011001101110110001100110111001001111101  

En utilisant l'outil cyberchef 
[CyberChef Tool](https://gchq.github.io/CyberChef/#recipe=From_Binary('Space',8)&input=ICDigIIKMDAxMTAxMDAwMDExMDAwMDAwMTEwMTAwMDEwMDAwMTEwMTAxMDEwMDAxMDAwMTEwMDExMTEwMTEwMTAwMTExMDAwMTEwMDAwMDExMDExMTAwMDExMDAxMTAxMDExMTExMDEwMTAwMTAwMDExMDAxMTAxMTEwMTAwMDEwMTAxMDEwMTExMDAxMDAxMTAxMTEwMDEwMTExMTEwMTAxMTAxMDAwMTEwMDExMDExMTAwMTAwMDExMDAwMDAxMDExMTExMDEwMDEwMDEwMTEwMTExMDAxMDEwMTEwMDAxMTAwMTEwMTExMDAxMDAxMTEwMTAwMDEwMDAxMDEwMTEwMDEwMDAxMDExMTExMDExMDAxMTAwMDExMDAwMDAxMTEwMDEwMDAxMTAwMTEwMTExMDExMDAwMTEwMDExMDExMTAwMTAwMTExMTEwMQo)

Le flag est donc : **_404CTF{N0n3_R3tUrn_Z3r0_InV3rtEd_f0r3v3r}_**
