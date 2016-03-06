## Problem Set 1

1)	There are 602 unique genera for the Miocene, 169 for the Early Jurassic, 375 in the Late Cretaceous (I’d have liked to know how many in the earliest Paleocene…) and 133 in the Pennsylvanian. I found this out by using the code apply(PresencePBDB,1,sum)

2)	
There are 29 epochs represented in this dataset:

````R
dim(PresencePBDB)
[1]  29 902
````

4) Mytilus is found throughout the Cenozoic (excluding the Holocene), the Mesozoic (excluding all epochs in the mid-Cretaceous) and sporadically during the Paleozoic (in the Cisuralian in the early Permian, and the Pridoli in the latest Silurian). 

5)	Based on the geologic timescale, this genus must have been present constantly since at least the Pridoli at the very top of the Silurian (including the mid-K). 

## Problem Set 2

1)	Jaccard Similarity for shelled marine invertebrates form the Miocene and Pliocene is 0.8276423. Yay!

````R
table(NeogeneMatrix)
NeogeneMatrix
  0   1   2 
287 106 509 
> 509/(509+106)
[1] 0.8276423
````

2)	This can be turned into a dissimilarity by simply subtracting the similarity value by subtracting it from 1 (i.e. fro total similarity). 

Dissimilarity is 0.1724.

3) 

````R
NEOGENE<-PresencePBDB[c("Miocene","Pleistocene"),]
> vegdist(NEOGENE,method="jaccard")
              Miocene
Pleistocene 0.1723577
# Same answer WOOOOOOOOOOOOOOOOO!!!!
````

5) neogene<-PresencePBDB[c("Paleocene","Eocene","Oligocene","Miocene","Pliocene","Pleistocene"),]

> That's not the Neogen! It's the Cenozoic!

````R
> vegdist(neogene,method="jaccard")
             Paleocene     Eocene  Oligocene    Miocene
Eocene      0.33280757                                 
Oligocene   0.40946166 0.19093851                      
Miocene     0.33228346 0.08598726 0.16091954           
Pliocene    0.37816456 0.13418530 0.19000000 0.08510638
Pleistocene 0.44356121 0.21904762 0.26955075 0.17235772
              Pliocene
Eocene                
Oligocene             
Miocene               
Pliocene              
Pleistocene 0.12714777

min(vegdist(neogene, method="jaccard"))
[1] 0.08510638
````

The most dissimilar epochs are the Miocene and Pliocene, oddly enough (given that they’re continuous). Himalayan conspiracy?

> What!? Nope, the most dissimilar are the Pleistocene and Paleocene with a distance of 0.443 -1 Points

## Problem Set 3

1) 

````R
RandomEpochs<-PresencePBDB[c("Paleocene","Late Jurassic","Oligocene","Middle Jurassic","Pliocene","Early Cretaceous"),]
````

2)  

````R
vegdist(RandomEpochs, method="jaccard")
                 Paleocene Late Jurassic Oligocene
Late Jurassic    0.7902622                        
Oligocene        0.4094617     0.8651685          
Middle Jurassic  0.7931689     0.2962963 0.8812199
Pliocene         0.3781646     0.8650675 0.1900000
Early Cretaceous 0.6400742     0.4703947 0.7476341
                 Middle Jurassic  Pliocene
Late Jurassic                             
Oligocene                                 
Middle Jurassic                           
Pliocene               0.8850746          
Early Cretaceous       0.4883721 0.7459138
````

3) 

````R
min(vegdist(RandomEpochs,method="jaccard"))
[1] 0.19 # for Oligocene/Pliocene, most similar
> max(vegdist(RandomEpochs,method="jaccard"))
[1] 0.8850746 # for Middle Jurassic/Oligocene, most dissimilar
````

> nope, look carefully the Middle Jurassic and Pliocene were the most dissimlar 0.885 vs 0.881, -1 points.

Ordination: first seven
Olig/plioc	M Jur/L Jur	Paleoc/Plioc	Paleoc/Olig	L Jur/EK	MJr/EK 	EK/Paleoc					
0.19	0.296	0.378	0.409	0.47	0.488	0.64					
											

Ordination: last eight
EK/Plioc	EK/Olig	LJur/Paleoc	MJur/Paleoc	LJur/Plioc	LJur/Olig	MJur/Olig	MJur/Plioc
0.7459	0.7476	0.7903	0.793	0.86507	0.8652	0.881	0.885

So, more clearly, the inferred gradient(from least to most dissimilar)

Oligocene/Pliocene, Middle Jurassic/Late Jurassic, Paleocene/Pliocene, Paleocene/Oligocene, Late Jurassic/Early Cretaceous, Middle Jurassic/Early Cretaceous, Early Cretaceous/Paleocene, Early Cretaceous/Pliocene, Early Cretaceous/Oligocene, Late Jurassic/Paleocene, Middle Jurassic/Paleocene, Late Jurassic/Pliocene, Late Jurassic/Oligocene, Middle Jurassic/Oligocene, Middle Jurassic/Pliocene. 

> I don't quite understand what you were trying to do/say here? The inferred gradient is simply Pliocene->Oligocene->Paleocene->Early Cretaceous->Late Jurassic->Middle Jurassic. In other words, in simple time-order. -1 Points


4) The probable variable here may be sea level fall, as sea level was at a global highstand in the Cretaceous (and getting there in the Jurassic) and lowered over the course of the Cenozoic. This perhaps would have affected bivalves and gastropods that dwell on shallow continental shelf environments and epeiric seaways, as their geographic range would have been reduced or eliminated altogether (or, at the very least, their fundamental niche would have been downsized). The dissimilarity between the Mesozoic and Cenozoic is also partly attributable to the K-Pg imact event, which would have caused the extinctions of some genera and allowed for the origination of others.  I was kind of surprised that the Early Cretaceous was more similar to the Cenozoic, while the Jurassic/Cenozoic made up the six most dissimilar pairings. This does kind of throw a wrench in my theory…if sea level was the main determinant, then the Early Cretaceous should be the most dissimilar from the Cenozoic (since sea level was highest then).  Other plausible variables might be atmospheric pCO2 (as a primar productivity proxy?) or global temperature conditions, both of which declined over the course of the Cenozoic.  Knowing the Jaccard Dissimilarities for the Late Cretaceous and Eocene (in relation to the other fifteen combos) would definitely help here…

> I understand that this was a difficult question to answer because you got the previous questions slightly wrong. But also, think about this like a scientist. Did we have any direct data (or even indirect) data on sea-level? Does it make sense to invoke sea-level if we don't have any sea-level data. No points off, but think about what information you actually had - namely, the order of the epochs, which goes from oldest to youngest, which means that we have a *time* gradient.

5) The K-Pg global mass extinction significantly impacted marine invertebrate populations, and post-impact populations took much of the early Paleocene to recover (with significant species radiation). So, the dissimilarity between the two can be accounted for by that nasty business at Chixculub.

## Problem set 4

1)	To download the Ordovician animals, I used 

````R
Ordovician<-downloadPBDB(Taxa=c("Animalia"),StartInterval="Ordovician",StopInterval="Ordovician")
````

2)	To clean up the data, I used 

````R
> Ordovician<-cleanGenus(Ordovician)
> Epochs<-downloadTime(Timescale="international epochs")
> Ordovician<-constrainAges(Ordovician, Epochs)
````

3) OrdCoord<-presenceMatrix(Ordovician,SampleDefinition="geoplate")
OrdCoord<-cullMatrix(OrdCoord,minOccurrences=2,minDiversity=25)

4)	

````R
tapply(Ordovician[, “paleolat”], Ordovician[,"geoplate"],mean)

tapply(Ordovician[,"paleolng"], Ordovician[,"geoplate"],mean)

Mean paleocoordinates for each plate (put together manually)
0: 36 N, 17 W
101: 4 S, 110 W
103: 30 N, 89W
123: 25 N, 115 W
201: 32 S, 161 W
291: 28 S, 50 W 
302: 27 S, 64 W
304: 79 S, 16 W
305:68 S, 7 E
313: 11 S, 82 W
315: 44 S, 83 W
401:  9 N, 35 W
402: 15 S, 31 E
505: 49 S, 80 E
602: 33 N, 112 E
604: 27 N, 93 E
611: 11 S, 82 E
714: 82 S, 74 W
801: 9 N, 118 E
806: 9 N, 137 E
````

Each geoplate on the plot can be compared to another (in terms of faunal similarity) in terms of the spatial distance between them. So, plates 505 and 806 are very dissimilar, but plates 305 and 304 are very similar.
