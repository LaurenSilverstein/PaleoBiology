> 20/20

## Problem set 1

1) 26,001 occurrences were emitted from the MacroStrat database.

````R
nrow(DataPBDB)
[1] 35419
> nrow(MacroPBDB)
[1] 9418

35419-9418
[1] 26001
````

2) The data were not included here because not every continent is North America, and North America is not the only continent. Not all of North America is even on North America*, so the MacroStrat database is limited to the present-day political boundaries that define “North America” and the fossils found therein. 

## Problem Set 2

1)	
````R
sort(specnumber(OrderMatrix))
length(sort(specnumber(OrderMatrix)))
Lagers<-c(sort(specnumber(OrderMatrix)))
Lagers[149:158]
Parker Slate   Snowy Range Fm      Weymouth Fm      Langston Fm       Forteau Fm 
              16               16               16               17               17 
   Wheeler Shale Marjum Limestone       Kinzers Fm       Stephen Fm       
Chancellor 
              18               22               24               24               27
CandidateUnits<-c("Parker Slate","Snowy Range Fm","Weymouth Fm","Langston Fm","Forteau Fm","Wheeler Shale","Marjum Lm","Kinzers Fm","Stephen Fm","Chancellor")
CandidateUnits
 [1] "Parker Slate"   "Snowy Range Fm" "Weymouth Fm"    "Langston Fm"    "Forteau Fm"    
 [6] "Wheeler Shale"  "Marjum Lm"      "Kinzers Fm"     "Stephen Fm"     "Chancellor"
````

2)
````R
apply(GenusMatrix,2,sum)
sort(apply(GenusMatrix,2,sum))
 GenusFrequencies<-sort(apply(GenusMatrix,2,sum))
````

3) 
````R
barplot(table(GenusFrequencies))
````
 
4) This type of curve is called a hollow curve.

5) 
````R
> Rare<-c(which((GenusFrequencies)==2))
> Genera<-c(which((GenusFrequencies)<2))
> RareGenera<-c(Rare,Genera)
> length(RareGenera)
[1] 565
>
````

## Problem Set 3

1) 
````R
GenusMatrix[CandidateUnits,]
````

2) The four most likely Lagerstatten candidates are the four that have the highest amount of rare genera AND the highest richness of orders: 

````R
  sort(PercentShared)
     Langston Fm   Snowy Range Fm    Wheeler Shale       Kinzers Fm     Parker Slate 
       0.1632653        0.1951220        0.2307692        0.2586207        0.2812500 
      Stephen Fm Marjum Limestone       Forteau Fm       Chancellor      Weymouth Fm 
       0.3055556        0.3559322        0.5652174        0.5714286        0.6764706
````

These top four are the Weymouth, Chancellor Group, Forteau Fm, and Marjum lm. 

3) The Chancellor Group includes the Burgess Shale, which is the type locality for the Cambrian Explosion and the locality where it was first described. The elaborate soft-body configurations, many not analogous to modern organisms, made paleontologists rethink the paradigm that complexity had evolved slowly over time. 











