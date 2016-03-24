Lab 5: Biodiversity

> 12/20

## Problem set 1
1)  There were 93 unique genera of bivalves in the Miocene. 

````R
sum(table(BivalveAbundance["Miocene",]))
[1] 2334
2334-2241
[1] 93
````

> The correct number is 634, -1 Points

2) The Berger-Parker Index for brachiopods in the Pliocene was 0.58.
> table(BrachiopodAbundance["Pliocene",])

   0    1    2    3    4    7   14 
3256    7    1    1    1    1    1 
> sum(table(BrachiopodAbundance["Pliocene",]))
[1] 3268
> 3268-3256
[1] 12
> 7/12
[1] 0.5833333

{{{{{{0.22?

 sum(BrachAbundance["Pliocene",])
[1] 99
> max(BrachAbundance["Pliocene",])
[1] 22
> 22/99
[1] 0.2222222}}}}}}


3) The Gini Coefficient for Late Ordovician Brachiopods was 0.74.

````R
> table(BrachiopodAbundance["Late Ordovician",])
   0    1    2    3    4    5    6   11   12   17   18   19   23   31 
3205   30    9    4    1    2    1    1    1    1    1    1    1    1 
  35   38   48   51   54   58   61  107  322 
   1    1    1    1    1    1    1    1    1 
> 3268-3205
[1] 63
> Abundances<-c(30,9,2,4,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1)
> 1-sum((Abundances/63)^2)
[1] 0.7432603
````

> -1 Points

4) Shannon’s Entropy for Late Cretaceous bivalves is 1.35 (?)

````R
table(BivalveAbundance["Late Cretaceous",])
   0    1    2    3    6   11   16 
2320    8    2    1    1    1    1

5) Shannon’s Entropy for Paleocene is 1.73?  

````R   
table(BivalveAbundance["Paleocene",])
 0    1    2    3    4    5    6    7    8   10   11   12   13   16 
2222   50   16   20   10    3    2    1    1    1    1    2    1    1 
  18   21   29 
   1    1    1
length(which(BivalveAbundance["Paleocene",]!=0))
[1] 112
````

6) The percent change between the two is 22%. The drastic change in diversity can be attributed to alarming spikes in iridium worldwide, which probably indicates some sort of accelerated extraterrestrial flux. Or something.  

> -1 Points, I would have given partial credit if you'd given the formula for percentages.

7) 

exp(1.35)
[1] 3.857426
> exp(1.73)
[1] 5.640654
> exp(.22)
[1] 1.246077

> -1 Points

## Problem Set 2

1) 
````R
specnumber(BivalveAbundance["Miocene",])
[1] 634
````

> You didn't notice that this was very different from what you got in Problem Set 1?

2) 
````R
diversity(BrachiopodAbundance["Late Ordovician",], index="simpson")
[1] 0.9784588
````

3) 
````R
diversity(BivalveAbundance["Late Cretaceous",],index="shannon")
[1] 5.086512
````

4) 
````R
diversity(BivalveAbundance["Paleocene",],index="shannon")
[1] 4.511063
````

## Problem Set 3

````R
OrderedBiv<-array(c(42,48,87,56,66,81,51,111,88,70,99,104,160,191,156,101,151,242,217,202,270,393,573,304,512,355,634,534,498),dimnames=list(c("E Ord","M Ord","L Ord","Lland","Wenlock","Ludlow","Pridoli","E Dev","M Dev","L Dev","Miss","Penn","Cisur","Guad","Loping","E Tri","M Tri","L Tri","E Jur","M Jur","L Jur","E K", "L K","Paleoc","Eoc","Olig","Mio","Plio","Pleist"))
+ )
> OrderedBiv
  E Ord   M Ord   L Ord   Lland Wenlock  Ludlow Pridoli   E Dev   M Dev 
     42      48      87      56      66      81      51     111      88 
  L Dev    Miss    Penn   Cisur    Guad  Loping   E Tri   M Tri   L Tri 
     70      99     104     160     191     156     101     151     242 
  E Jur   M Jur   L Jur     E K     L K  Paleoc     Eoc    Olig     Mio 
    217     202     270     393     573     304     512     355     634 
   Plio  Pleist 
    534     498 
> OrderedBrachiopods
    E Ord     M Ord     L Ord     Lland   Wenlock    Ludlow   Pridoli 
      141       282       331       271       257       234       138 
    E Dev     M Dev     L Dev      Miss      Penn     Cisur      Guad 
      497       353       274       314       284       564       549 
   Loping     E Tri     M Tri     L Tri     E Jur     M Jur     L Jur 
      406        63       111       193       130       175       111 
       EK        LK Paleocene    Eocene      Olig   Miocene  Pliocene 
      125        96        29        57        38        45        23 
   Pleist 
       19
````

1) Bivalve and Brachiopod richnesses are negatively correlated.

````R
cor(OrderedBiv,OrderedBrachiopods)
[1] -0.5668888
````

> Yes! Great.

2) Bivalve and brachiopod Gini coefficients are also negatively correlated.

````R
Biv<-diversity(BivalveAbundance,index="simpson")
> Brach<-diversity(BrachiopodAbundance,index="simpson")
> cor(Biv,Brach)
[1] -0.2623969
````

3) The greatest drop in brachiopod richness occurred across the Lopingian-Early Triassic, no doubt in response to the Permo-Triassic extinction.

## Problem Set 4

1) 

````R
StandardizedRichness<-apply(BrachiopodAbundance,1,subsampleIndividuals,Quota=63)
> StandardizedRichness[1:6]
    Mississippian     Pennsylvanian  Early Ordovician Middle Ordovician 
            42.94             34.67             38.15             46.54 
  Late Ordovician        Llandovery 
            41.64             41.76
````

2) All StandardizedRichness values are all values between 10 and 51, while all OrderedBrachiopod values are between 19 and 564. 

````R
max(StandardizedRichness)
[1] 50.86
> min(OrderedBrachiopods)
[1] 19
> max(OrderedBrachiopods)
[1] 564
````

> I'm not sure what you were trying to say here. -1 Points

3) 
  
I neglected to do a decorana analysis due to time constraints, so I stuck with simple scatterplots that were also more intuitive. These two plots are functionally rotated mirror images of one another, so they show the same trend. There is a loosely linear relation between standardized richnesses and unstandardized brachiopods with low richness. However, high richness doesn’t seem to be compatible with standardization, indicating that high richness may not actually represent “richness”; hence, the need to standardize.

> Decorana would not have been appropriate for this lab anyway. A scatter plot and an ordination are two completely different things, we just visualize the output of an ordination with a scatterplot.
> -3 Points
