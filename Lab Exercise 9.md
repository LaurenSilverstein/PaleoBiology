# Paleo Lab 

> Come see me some time if you want to learn how to put images up on GitHub.

> 19.5/20

## Problem set 1

1)	North America has moved progressively westward over the past 66 million years.

2)	`plot(ModernMap,col=rgb(1,0,0,0.33),lty=0,add=TRUE)`

plot () will___________, col= determines the color of the continents in each map (blue for the Cretaceous, red for the modern). “rgb” indicates the order of colors in the “col” component, so by putting a 1 in any of the three positions designates that color. lty= determines the type of lines that outline the shapes. And ADD=TRUE means that the _______.

3) AlbianMap<-downloadPaleogeography(Age=110)
	<strike>******Should actually be AptianMap, as the Aptian-Albian stage boundary was at 113 Ma according to the 2015 ICS timeline.</strike>
	
> Nope! The Albian comes after the Aptian, so 110, being younger than 113, is in the Albian.

4) 
````R
> plot(AlbianMap,col=rgb(0,1,0,0.33),lty=0)
> plot(CretaceousMap,col=rgb(0,0,1,0.33),lty=0,add=TRUE)
> plot(ModernMap,col=rgb(1,0,0,0.33),lty=0,add=TRUE)
````

5) There has been more North-South movement in the Eastern Hemisphere, due to Africa rotating into its present position from a more inclined orientation, and Australia and India’s detachment and northward movement from Antarctica.

6) There has been more East-West movement in the Western Hemisphere due to  the rifting of the present Atlantic and the near-latitudinal movement of North and South America westward.

## Problem set 2

1) 

````R
PETMMap<-downloadPaleogeography(Age=56)
plot(PETMMap,col=rgb(1,0,0,0.33),lty=0)
````
 

2)	

````R
source("https://raw.githubusercontent.com/aazaff/paleobiologyDatabase.R/master/communityMatrix.R")
Anthozoa<-downloadPBDB(Taxa=c("Anthozoa"),StartInterval="Paleocene",StopInterval="Eocene")
> Anthozoa<-cleanRank(Anthozoa)
````

3)	2721 occurrences?

> Where's your R Code? -0.5 Points

4)	Column names:

````R
[[2]]
 [1] "occurrence_no"   "record_type"    
 [3] "reid_no"         "flags"          
 [5] "collection_no"   "identified_name"
 [7] "identified_rank" "identified_no"  
 [9] "difference"      "accepted_name"  
[11] "accepted_rank"   "accepted_no"    
[13] "early_interval"  "late_interval"  
[15] "max_ma"          "min_ma"         
[17] "reference_no"    "paleomodel"     
[19] "paleolng"        "paleolat"       
[21] "geoplate"        "phylum"         
[23] "class"           "order"          
[25] "family"          "genus”

phylum, class, order, family and genus all refer to the taxonomic classifications of each Anthozoa occurrence. 

“Paleolng” and “paleolat” refer to the global coordinates of each fossil occurrence at the time when they were alive. 

“geoplate” applies to the ancient landmass on which each occurrence lived. “max_ma” and “min_ma” gives the earliest and latest possible ages of the occurrence.

 “early interval” and “late interval” is the StartInterval and StopInterval we coded for, to constrain the time period in which we’re interested. 

“occurrence_no” returns each occurrence’s ID number.

“reid_no” indicates whether or not the occurrence has been assigned to a new classification since its first description. 

“record_type” means that all the individual rows are fossil occurrences and not some other type. 

“flags” will only return a symbol if the occurrence has been re-identified. 

“collection_no” tells us what repository holds it, or what expedition or study first described it. 

“identified_name” and “accepted_name” return each occurrence’s taxonomic name, while “identified_rank” and “accepted_rank” yield the taxonomic rank of each occurrence. 

“identified_no” and “accepted_no” tell who first described it.

“difference” tell us, in the case of a reassigned taxonomic name, why the occurrence was re-identified.
````

5) 
PaleoLNG<-c(Anthozoa[,"paleolng"])
> PaleoLAT<-c(Anthozoa[,"paleolat"])
plot(PETMMap,col=rgb(1,0,0,0.33),lty=0.01)
> points(PaleoLNG,PaleoLAT,type="p",col=rgb(0,0,1))
 

5)	Eastern-hemisphere Anthozoa of the Paleocene and Eocene tended to cluster around the Mediterranean, inland off the coast of East Africa (which was then an epicontinental sea) and in general along continental margins. Anthozoa are scleractinian corals, sea anemones and sea pens, so they naturally live only in marine environments (especially warm, clear, shallow areas). From their broad extent, even into high latitudes and moern continental interiors, we can thus surmise that the Earth was in a greenhouse state and that sea level was high enough to flood continents. The abundance of Anthozoa around the Mediterranean suggests that it received the ideal amount of sunlight (for zooxanthellae), was the ideal salinity, temperature and water depth. As it happens, the Med at that time was part of the closing Tethys, and the center of a seaway that was fringed with mangrove swamps (in the present day Sahara) and even accommodated whales.

## Problem set 3

1) 

````R
Perissodactyla<-downloadPBDB(Taxa=c("Perissodactyla"),StartInterval="Paleogene",StopInterval="Paleogene")
Perissodactyla<-cleanRank(Perissodactyla)
````

2) Perissodactyla are ungulates (four-legged mammals) with an odd number of toes on each foot. Horses, zebras and donkeys all have one toe per foot (the hoof), while rhinos and tapirs have three toes per foot.  

3) 

````R
head(Perissodactyla[which(Perissodactyla[,"collection_no"]==112723),])
     occurrence_no record_type reid_no flags
3949        961980         occ      NA    NA
3951        963172         occ      NA    NA
     collection_no          identified_name
3949        112723 Eotitanops pakistanensis
3951        112723     Balochititanops haqi
     identified_rank identified_no difference
3949         species        169823           
3951         species        192106           
                accepted_name accepted_rank
3949 Eotitanops pakistanensis       species
3951     Balochititanops haqi       species
     accepted_no early_interval late_interval max_ma
3949      169823       Ypresian                   56
3951      192106       Ypresian                   56
     min_ma reference_no paleomodel paleolng paleolat
3949   47.8        36699     gp_mid     70.7     2.76
3951   47.8        36699     gp_mid     70.7     2.76
     geoplate   phylum    class          order
3949      501 Chordata Mammalia Perissodactyla
3951      501 Chordata Mammalia Perissodactyla
              family           genus
3949 Brontotheriidae      Eotitanops
3951 Brontotheriidae Balochititanops
````

4) This occurrence was found on geoplate 501, which is presently found as part of the Indian subcontinent.

points(70.7,2.76,type="p",col=rgb(0,0,1))

> Collection, not occurrence. Never get them confused! 

5) 

````R
PerryinIndia<-c(Perissodactyla[,"geoplate"]==501)
> head(PerryinIndia)
[1] FALSE FALSE FALSE FALSE  TRUE FALSE
> table(PerryinIndia)
PerryinIndia
FALSE  TRUE 
 3838    75
````

There are 75 occurrences of Perrissodactyla on the Indian subcontinent.

> A really interesting approach!

6)	The Indian subcontinent detached from Gondwana (specifically, it was docked against Antarctica) in the Late Jurassic/Early Cretaceous.  Throughout the Cenozoic, it plowed northward, rotating very slightly until it collided with Asia around the late Eocene and began forming the Himalayas.

````R
AlbianMap<-downloadPaleogeography(Age=110)
MaastrichtianMap<-downloadPaleogeography(Age=66)
EoceneMap<-downloadPaleogeography(Age=57)
> OligoceneMap<-downloadPaleogeography(Age=36)
> MioceneMap<-downloadPaleogeography(Age=23)
> PlioceneMap<-downloadPaleogeography(Age=5)

> plot(MaastrichtianMap,col=rgb(0,1,0,0.33),lty=0)
> plot(AlbianMap,col=rgb(1,0,0,0.33),lty=0, add=TRUE)
> plot(EoceneMap,col=rgb(0,0,1,0.33),lty=0, add=TRUE)
> plot(OligoceneMap,col=rgb(0,0,1,0.33),lty=0, add=TRUE)
> plot(MioceneMap,col=rgb(0,1,0,0.33),lty=0, add=TRUE)
> plot(PlioceneMap,col=rgb(1,0,0,0.33),lty=0, add=TRUE)
````
 
7)	I decided to map all occurrences of Perissodactyla based on their earliest interval; so, I subset Perissodactyla that originated in the Paleocene(of which their were none), those that originated in the Eocene and those that originated in the Oligocene. I then mapped them on maps for each epoch.

PaleocenePerry<-subset(Perissodactyla,Perissodactyla[,"early_interval"]=="Paleocene")
> EocenePerry<-subset(Perissodactyla,Perissodactyla[,"early_interval"]=="Eocene")
> OligocenePerry<-subset(Perissodactyla,Perissodactyla[,"early_interval"]=="Oligocene")

PaleoPerryLNG<-c(PaleocenePerry[,"paleolng"])
PaleoPerryLAT<-c(PaleocenePerry[,"paleolat"])
plot(PaleoceneMap,col=rgb(0,0,1,0.33),lty=0)
points(PaleoPerryLNG,PaleoPerryLAT,type="p",col=rgb(0,1,0))

EoPerryLNG<-c(EocenePerry[,"paleolng"])
> EoPerryLAT<-c(EocenePerry[,"paleolat"])
> plot(EoceneMap,col=rgb(0,0,1,0.33),lty=0)
> points(EoPerryLNG,EoPerryLAT, type="p",col=rgb(0,1,0) 


> OligPerryLNG<-c(OligocenePerry[,"paleolng"])
> OligPerryLAT<-c(OligocenePerry[,"paleolat"])
> plot(OligoceneMap,col=rgb(0,0,1,0.33),lty=0)
> points(OligPerryLNG,OligPerryLAT,type="p",col=rgb(0,1,0))



Perissodactyla is found in the Oligocene throughout Asia and in the far west of India. In the Oligocene map, India appears to have made initial land-land contact with Asia via the eastern margin of India. In the Eocene, Perissodactyla are present throughout Asia and Europe but not on the then-still-isolated India. So:

Species of Perissodactyla did NOT migrate from isolated India through Asia after the two joined. There are no species present on India before the contact, and one occurrence after, while species were already widespread on Eurasia before and after.

Species of Perissodactyla probably migrated from China to region-X during the Paleogene. This is supported by the maps of the Eocene and Oligocene, in which Perissodactylids are present throughout China in both but only appear on India in the Oligocene. This indicates westward migration of Perissodactylids across China and Southeast Asia and into India via the eastern contact.

The species of Perissodactyla did NOT evolve separately on both landmasses. Not only does this contradict most (credible) models of speciation, it is also not supported by fossil evidence since species are simply not present on both landmasses contemporaneously.

