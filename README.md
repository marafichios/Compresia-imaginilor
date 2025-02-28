# Compresia-imaginilor
	
Task 1:

Aceasta functie reduce dimensiunea fotografiei primite ca input, creeand trei 
matrici prin intermediul algoritmului SVD; U e o matrice ce ofera informatii 
despre randurile fotografiei, S despre importanta valorilor singulare si V 
despre coloanele imaginii. Mai apoi fiecare din ele e redusa, la randul ei, 
in functie de numarul de componente principale (3 sau 30 in cazul nostru). 
Observam ca pentru 3 PC (componente principale), imaginea rezultata are o 
complexitate redusa, intrucat cele 3 PC sunt tratate ca niste 'axe', pe baza/
'in jurul' carora datele sunt modificate. In cazul in care avem 30 PC, 
aproximarea preciziei fotografiei este mai mare, intrucat acuratetea 
aproximarii datelor este mult mai ridicata.


Task 2:

Aceasta functie este asemanatoare cu cea anterioara. Algoritmul SVD imparte 
matricea Z in cele 3 matrici corespunzatoare, insa de data asta selectia 
componentelor principale alese e inmultita cu matricea initiala, dupa care
aproximam matricea new_X. Variabila pcs reprezinta nr de componente principale
cu care lucram, ideea principala fiind cea explicata mai sus. Pt pcs egal cu 
3, calitatea fotografiei e scazuta si detaliile vagi, iar pentru pcs egal cu 
30, precizia e mai mare.


Task 3:

In aceasta functie calculam vectorii si valorile proprii ale matricei de 
covarianta care reprezinta cum variaza pixelii in imagine. Stocam componentele
relevante pentru noi - in functie de cele pcs coloane ale matricei V de vectori
proprii in matricea W. Cream mai apoi proiectia pixelilor componentelor 
principale in matricea Y si reducem matricea la dimensiunile initiale cu 
ajutorul calculului de la penultimul pas si facem matricea valida. Ca mai sus,
in functie de nr de componente principale, adica pcs, conservam datele importante
pentru noi si obtinem o aproximare a acestora.


Task 4:

-visualise_image: citeste o anumita linie din train_mat pe care o transforma,
la randul ei, intr-o alta matrice pentru a obtine o orientare corecta a 
imaginii, dupa care e convertita pt a fi valida. Astfel, aceasta functie are 
scopul de a interpreta informatiile din imagini reprezentate de o linie in 
matricea data.

-prepare_data: datle de antrenament sunt incarcate dintr-un fisier dat in 
matricea train_mat, si etichetele respective in vectorul train_val 

-magic_with_pca: ca functiile anterioare, aceasta utilizeaza PCA pt a retine
informatia cea mai importamta din matrice. Asemanator cu ceea ce am facut 
anterior, calculam matricea de covarianta, vectorii si valorile proprii ale
acesteia. Sortam valorile proprii descrescator, iar matricea S e reordonata in
functie de indicii stocati in idxs. Calculam proiectia pe noile axe determinate
de PC dupa care obtinem o aproximare a matricei de antrenament prin inmultirea
cu transpusa matricei de vectori proprii.

-prepare_photo: vectorul sir e initializat drep un vector linie de 784 elemente,
adica 28 x 28 pixeli. Mai apoi, inversam pixelii imaginii im, scazand valoarea
255 adica val max dintr-un pixel intr-o fotografie grayscale, obtinand o imagine
negativa. Convertim transpusa intr-un vector de tip linie, cu un singur rand.

-KNN: in matricea distance retinem distantele euclidiene dintre imaginea de
antrenament si cea test. Calculam predictia valorilor celor mai apropiate
imagini din setul de antrenament fata de imaginea test prin intermediul medianei
etichetelor a k imagini, adica cele mai apropiate. 

-classify_image: functia reduce dimensiunea imaginii test - magic_with_pca si
face o predictie pe baza vecinilor cei mai apropiati din setul de antrenament - KNN

Consider ca functiile pe care le-am avut de implementat au fost explicate foarte
bine, fiecare TODO fiind detaliat. In acest document am incercat sa corelez
fiecare linie de cod cu modificarile aduse asupra imaginilor date si cum se
schimba specificatiile acestora. 
