# A l'aube d'un échange

## Contexte
>Nouvelle recrue ! Nous avons besoin de toi par ici. 
>Un de nos agents vient d'intercepter une courte conversation téléphonique entre deux agents de Hallebarde. 
>Un important échange de documents confidentiels doit avoir lieu et pour indiquer l'endroit du rendez-vous, l'un des agents ennemis à envoyé la photo ci-dessous à son collègue tout en précisant ceci :  
>>_Quel beau lever de soleil n'est-ce pas ? J'attendrai daans la rue qui sépare le bâtiment au premier plan de ceux au second plan. Rendez-vous ce soir, 22h00_.  
>
>Format du flag : 404CTF{md5 du nom complet de la rue}
>Le nom de la rue doit être en **minuscule**, inclure le **type de rue**(ex : avenue, rue, boulevard...),**sans accents,sans abréviation, et tous les espaces doivent être remplacés par des tirets.** Par exemple : si la rue est l'Avenue de Saint-Mandé à Paris, le flag correct est 404CTF{129af9edde5659143536427f9a5f659a}.  
>
>_**Auteur : Artamis**_

## Image

<p align='center'>

![Screenshot](aube-echange.photo.png)  

</p>

## Résolution

Sur cette image on aperçoit la fameuse "Tour Crayon" (**Tour Part-Dieu**) accompagné de la "Tour Gomme" (**Tour Incity**) situé à Lyon.  À gauche on y distingue une église avec ses deux clochés.

- On se rend sur [Google Earth](https://earth.google.com/web/) et on essaye de retrouver la direction dans laquelle a été prise la photo.  
[L'Église est à gauche et le Tour Part-Dieu est à droite.](https://earth.google.com/web/search/Lyon/@45.76387669,4.83123752,163.17996644a,642.32011573d,35y,87.32905318h,77.33211714t,0r/data=CigiJgokCSd2qHx-5kRAERaFaVIH_kLAGZ3-i0kMEhrAIVWmnWaL11_A) 

- On trouve le bâtiment situé devant nous (sur la photo) [ici](https://earth.google.com/web/search/Lyon/@45.76427305,4.82740149,183.99127317a,191.5291353d,35y,90.27344289h,62.56908916t,0r/data=CigiJgokCSd2qHx-5kRAERaFaVIH_kLAGZ3-i0kMEhrAIVWmnWaL11_A)

- La rue devant nous est [Mnt Saint-Barthélémy](https://earth.google.com/web/search/Lyon/@45.7641295,4.82634692,201.0004724a,0d,60y,18.42498196h,85t,0r/data=CigiJgokCSd2qHx-5kRAERaFaVIH_kLAGZ3-i0kMEhrAIVWmnWaL11_AIhoKFnZKMFZxX3g1ZHNxdFl0bFJqR0wtUFEQAg)

  - La rue complète est donc : montée-saint-barthélémy
  - Écriture correcte pour le flag : montee-saint-barthelemy
  - Chiffrement en [Md5](https://www.dcode.fr/hash-md5) : eb66c65861da9fe667f26667b3427d2c

**Le flag est :** `404CTF{eb66c65861da9fe667f26667b3427d2c} `
