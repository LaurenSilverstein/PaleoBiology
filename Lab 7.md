## PaleoBio lab 7

> 19.5/20

## Problem set 1:

1)	max_ma and min_ma list the time interval, in millions of years before present, of the taxon’s first and last occurrence? I.e. 45-43 Ma and 22-18 Ma?

2)	
````R
tapply(DataPBDB[,"max_ma"],DataPBDB[,"genus"],max)
                Abra          Abrachlamys        Acanthocardia                 Acar 
            56.0000              23.0300              66.0000              66.0000 
              Acesta              Acharax                Acila             Acorylus 
             66.0000              48.6000              66.0000              11.6200 
        Acrosterigma          Actinodonta          Acturellina           Acuticosta 
             23.0300              66.0000              15.9700              58.7000 
````	
	3) 
````R
tapply(DataPBDB[,"min_ma"],DataPBDB[,"genus"],min)
                Abra          Abrachlamys        Acanthocardia                 Acar 
              0.0000              15.9700               0.0000               0.0000 
              Acesta              Acharax                Acila             Acorylus 
              0.0117               2.5880               0.0117               0.1260 
        Acrosterigma          Actinodonta          Acturellina           Acuticosta 
              0.0117               5.3330              11.6080              55.8000 
          Acutostrea           Adamussium          Adansonella            Adipicola 
             23.0300               0.7810              61.6000              11.6080
````

4)
````R
table(DataPBDB[,"genus"])
max(table(DataPBDB[,"genus"]))
[1] 1916
which(table(DataPBDB[,"genus"]) == 1916)
Anadara 
     39
````

5) Anadara’ stratigraphic range extends form 66 million years ago to the present. So, from the End-Cretaceous to the modern.

````R
Anadara<-DataPBDB[which(DataPBDB[,26] == "Anadara"),]
max(Anadara[,15])
[1] 66
> min(Anadara[,16])
[1] 0
````

## Problem set 2

1) This line of code calculates the average paleolatitude for the Lucina subset, with replacement. It is part of the for() loop, so, at a counter of 1000 it will sample(sample())  1000 (repeat<-1:1000) potential means (mean()) from the column of the Lucina subset (Lucina[, “paleolat”]). 

> That's not what I was asking. -0.5 points

2) The distribution of the resampled mean Lucina paleolatitudes does indeed form a Gaussian profile:

`plot(density(ResampledMeans)) `

3)  the mean of the ResampledMeans array is greater than the actual mean paleolatitude of Lucina (at 22.84)
````R
mean(ResampledMeans)
[1] 24.16227
````

4) `sort(ResampledMeans)`

5)
````R
quantile(ResampledMeans, c(.025 , .975))
    2.5%         97.5% 
21.82094    26.28630 
````

6) These are the boundaries of our confidence interval. So, there is a 95% chance that the true average paleolatitude for Lucina lies between 21.8 and 26.3 N, and 5% chance that it lies outside our defined boundaries.

## Problem set 3:

1) Lucina is appears to be alive, since time is defined as positive going backwards and negative going forwards. So, Lucina will apparently go extinct sometime in the next 1.2 millions years.

2)
````R
Dallarca<-subset(DataPBDB,DataPBDB[,"genus"]=="Dallarca")
> estimateExtinction <- function(OccurrenceAges, ConfidenceLevel=.95)  {
+  NumOccurrences<-length(unique(OccurrenceAges))-1
+   Alpha<-((1-ConfidenceLevel)^(-1/NumOccurrences))-1
+   Lower<-min(OccurrenceAges)
+   Upper<-min(OccurrenceAges)-(Alpha*10)
+   return(setNames(c(Lower,Upper),c("Earliest","Latest")))
+   }
> estimateExtinction(Dallarca[,"min_ma"],0.95)
Earliest   Latest 
2.58800 -3.88749
````

3)	According to the function’s results, Dallarca’s earliest possible disappearance from the fossil record coincides roughly with the onset of the Pleistocene (which is apparently the case in the actual fossil record). However, the function also says that Dallarca “will” go extinct in another four million years. This odd result is probably due to the Upper component of the function, which subtracts the alpha vaue from the Lower component. If the Lower component is less than alpha, then the extinction date must then be sometime in the future. So, the upper limit is technically a mathematical fabrication in this case.

4)	We can’t trust the confidence interval in this case, because it overlaps with the modern. Also, due to the “pull of the modern”, we are more likely to know if it is indeed extant.  In addition, confidence intervals become less secure with decreasing amounts of data, so it is plausible that a scarce genus will be falsely extrapolated into the future!

## Problem set 4

1)	Ecologically speaking, random distribution up and down a column is unlikely because (geological reason) sea level can change up a strat sequence. This implies a change in the environmental conditions that each layer existed in, and so some layers may have been more or less hospitable to whatever organisms are of interest. So, a Dallarca may be perfectly happy in a shallow nearshore facies might simply not have existed in an earlier or later deeper facies. This is an example of a geologic (sedimentary) process permitting an ecological change in shelf environment and extent.
2)	Geologically speaking, random distribution is unlikely because subaerial exposure at some point in the strat column means that fossil destruction is all but guaranteed. Assuming we’re still thinking about Dallarca in the Pliocene, a Dallarca shell that is deposited nearshore may run the risk of exposure with falling sea levels due to the onset of glaciation.

## Problem set 5
1) 
```R
dim(DataPBDB)
[1] 67617    26
> dim(ExtantData)
[1] 59096    26
> 67617-59096
[1] 8521
````
2.)	There are 1018 unique genera in DataPBDB, and 532 unique genera in ExtantData. So, 52.3% of Cenozoic bivalves are present today. 

3)	
````R
tapply(ExtantData[,"max_ma"],ExtantData[,"genus"],max)
          Abra  Acanthocardia           Acar 
       56.0000        66.0000        66.0000 
        Acesta        Acharax          Acila 
     66.0000        48.6000        66.0000 
      Acorylus   Acrosterigma     Adamussium 
       11.6200        23.0300        11.6200 
    Adipicola         Adrana          Adula 

tapply(ExtantData[,"min_ma"],ExtantData[,"genus"],min)
          Abra  Acanthocardia           Acar 
        0.0000         0.0000         0.0000 
        Acesta        Acharax          Acila 
        0.0117         2.5880         0.0117 
      Acorylus   Acrosterigma     Adamussium 
        0.1260         0.0117         0.7810 
     Adipicola         Adrana          Adula 
       11.6080         0.0000         0.0117
````

4) There appear to be 306 genera that have minimum stratigraphic ages before the present, i.e. aren’t extant according to the PBDB. 
````R
ZeroOrNot<-tapply(ExtantData[,"min_ma"],ExtantData[,"genus"],min) 
	which(ZeroOrNot > 0)
	ZeroOrNot[which(ZeroOrNot > 0)]
	length(ZeroOrNot[which(ZeroOrNot > 0)])
[1] 306
````

5)	Whoo, boy.
````R
Scrobicularia<-subset(DataPBDB,DataPBDB[,"genus"]=="Scrobicularia")
> Meiocardia<-subset(DataPBDB,DataPBDB[,"genus"]=="Meiocardia")
> Dimya<-subset(DataPBDB,DataPBDB[,"genus"]=="Dimya")
> Digitaria<-subset(DataPBDB,DataPBDB[,"genus"]=="Digitaria")
> Cuspidaria<-subset(DataPBDB,DataPBDB[,"genus"]=="Cuspidaria")
> Arctica<-subset(DataPBDB,DataPBDB[,"genus"]=="Arctica")
Aloides<-subset(DataPBDB,DataPBDB[,"genus"]=="Aloides")
> Kurtiella<-subset(DataPBDB,DataPBDB[,"genus"]=="Kurtiella")
> Gouldia<-subset(DataPBDB,DataPBDB[,"genus"]=="Gouldia")
> Acrosterigma<-subset(DataPBDB,DataPBDB[,"genus"]=="Acrosterigma")
> estimateExtinction <- function(OccurrenceAges, ConfidenceLevel=.95)  {
+   NumOccurrences<-length(unique(OccurrenceAges))-1
+   Alpha<-((1-ConfidenceLevel)^(-1/NumOccurrences))-1
+   Lower<-min(OccurrenceAges)
+   Upper<-min(OccurrenceAges)-(Alpha*10)
+   return(setNames(c(Lower,Upper),c("Earliest","Latest")))
+   }

> estimateExtinction(Scrobicularia[,"min_ma"],0.95)
 Earliest    Latest 
  0.01170 -34.70966 
> estimateExtinction(Meiocardia[,"min_ma"],0.95)
 Earliest    Latest 
 0.011700 -4.530454 
> estimateExtinction(Dimya[,"min_ma"],0.95)
 Earliest    Latest 
 0.781000 -1.810551 
> estimateExtinction(Digitaria[,"min_ma"],0.95)
 Earliest    Latest 
 0.781000 -3.761154 
> estimateExtinction(Cuspidaria[,"min_ma"],0.95)
Earliest   Latest 
2.588000 1.606613 
> estimateExtinction(Arctica[,"min_ma"],0.95)
  Earliest     Latest 
 0.0117000 -0.7867083 
> estimateExtinction(Aloides[,"min_ma"],0.95)
Earliest   Latest 	
   5.333     -Inf 							
> estimateExtinction(Kurtiella[,"min_ma"],0.95)
 Earliest    Latest 
  0.01170 -34.70966 
estimateExtinction(Gouldia[,"min_ma"],0.95)
 Earliest    Latest 
 0.011700 -1.696099 
> estimateExtinction(Acrosterigma[,"min_ma"],0.95)
 Earliest    Latest 
 0.011700 -3.481128 
>
````

It appears that eight of the ten genera have confidence intervals that extend into the future (negative time).  So, 80% of these taxa have confidence intervals indicating that they are still around.
