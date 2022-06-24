# PingPong
## Consigne
Nous avons repéré une communication bizarre provenant des serveurs de Hallebarde. On soupçonne qu'ils en aient profité pour s'échanger des informations vitales. Pouvez-vous investiguer ?
## Resolution
On dispose d'un fichier pcap qui contient seulement des trames ICMP.  

À première vue, il n'y a rien de très intéressant dans les Data.  
En se penchant sur le champ Lengt on commence à observer une structure intéressante :
  - Trame 1 : 9**4**
  - Trame 3 : 9**0**
  - Trame 5 : 9**4**  

Il est très facile de distinguer le 404 en supprimant le premier chiffre du nombre.

Pour la suite : 
  - Trame 7 : 109
  - Trame 9 : 126
  - Trame 11 : 112   

L'écart entre 09 et 26 est de 17 ce qui correspond à l'espace entre c et t. 
L'écart entre 26 et 12 est de 11 ce qui correspond à l'espace entre t et f.

On en déduit une table d'équivalence en se basant sur l'ordre des caractères Ascii :

107 : **A** ; 108 : **B** ; 109 : **C** ; 110 : **D** ; 111 : **E** ; 112 : **F** ; 113 : **G** ; 114 : **H** ; 115 : **I** ; 116 : **J** ; 117 : **K** ; 118 : **L** ; 119 : **M** ; 120 : **N** ; 121 : **O** ; 122 : **P** ; 123 : **Q** ;
124 : **R** ; 125 : **S** ; 126 : **T** ; 127 : **U** ; 128 : **V** ; 129 : **W** ; 130 : **X** ; 131 : **Y** ; 132 : **Z** ; 137 : **_** ;   
139 : **a** ; 140 : **b** ; 141 : **c** ; 142 : **d** ; 143 : **e** ; 144 : **f** ; 145 : **g** ; 146 : **h** ; 147 : **i** ; 148 : **j** ; 149 : **k** ; 150 : **l** ; 151 : **m** ; 152 : **n** ; 153 : **o** ; 154 : **p** ; 155 : **q** ;
156 : **r** ; 157 : **s** ; 158 : **t** ; 159 : **u** ; 160 : **v** ; 161 : **w** ; 162 : **x** ; 163 : **y** ; 164 : **z** ;  
165 : **{** ; 166 : **|** ; 167 : **}**

Il ne nous reste plus qu'à traduire chaque nombre :

94 90 94 109 126 112 165 127 152 137 154 91 152 145 137 154 90 152 145 137 154 94 157 137 157 147 137 91 152 152 90 141 93 152 158 167  
4  0  4   C   T   F   {   U   n   _   p   1  n   g   _   p   0   n  g   _   p   4   s  _   s   i   _   1  n   n   0  c   3  n   t   }  

Le flag est donc : _**404CTF{Un_p1ng_p0ng_p4s_si_1nn0c3nt}**_  
