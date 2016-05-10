## PART 1

> 20/20

## Problem set 1

1) 

`TriassicUnits<-read.csv("https://macrostrat.org/api/units?interval_name=Triassic&format=csv")`

2) 

```R
dim(TriassicUnits)
[1] 838  17
````

3)

The first ten units returned are primarily igneous, with some metamorphic complexes and metasedimentary rocks (the Bedford Canyon is interpreted as metamorphosed turbidites)

````R
TriassicUnits[1:10,1:10]
unit_name
1                                                      Metamorphic Igneous Complex
2                                                                       Sur Series
3  Southern California Batholith and Santiago Peak Volcanics and Bedford Canyon Fm
4  Southern California Batholith and Santiago Peak Volcanics and Bedford Canyon Fm
5  Southern California Batholith and Santiago Peak Volcanics and Bedford Canyon Fm
6  Southern California Batholith and Santiago Peak Volcanics and Bedford Canyon Fm
7                                                                 Bonsall Tonolite
8  Southern California Batholith and Santiago Peak Volcanics and Bedford Canyon Fm
9                                                                          Unnamed
10                                                          Central Gneiss Complex
Fm Gp
1                                  
2                                  
3  Southern California Batholith   
4  Southern California Batholith   
5  Southern California Batholith   
6  Southern California Batholith   
7               Bonsall Tonolite   
8  Southern California Batholith   
9                                  
10        Central Gneiss Complex  
 ````
 
4) t_age and b_age yield top ages and bottom ages, respectively. 

````R
t_age    b_age 
1       67.037 259.9000         
2       74.975 396.8750         
3       92.875 203.1000         
4       92.875 203.1000         
5       92.875 203.1000         
6       92.875 203.1000         
7       93.900 261.9667         
8       95.550 203.1000         
9      100.500 396.8750         
10     103.625 249.1750
````

5) The Triassic ran from 252 Ma to 201 Ma, but four of the top ten units have bottom ages older than this, and all ten continue past the Triassic/Jurassic boundary. Five exceed the bounds of the Triassic in both temporal directions. This makes sense, since we have included everything from the formation level up through the supergroup, so any unit that contains rock that existed in the Triassic will be included. But is not very helpful from a searching standpoint.

## Problem Set 2

1)

`TriassicUnits<-read.csv("https://macrostrat.org/api/units?lith_class=sedimentary&interval_name=Triassic&format=csv")`

2)  

`JustTriassic<-TriassicUnits[which(TriassicUnits[,"t_age"]>=201& TriassicUnits[,"b_age"]<=252),]`

3)
````R
CretaceousUnits<-read.csv("https://macrostrat.org/api/units?lith_class=sedimentary&interval_name=Cretaceous&format=csv")
JustK<-CretaceousUnits[which(CretaceousUnits[,"t_age"]>=66& CretaceousUnits[,"b_age"]<=145),]

JurassicUnits<-read.csv("https://macrostrat.org/api/units?lith_class=sedimentary&interval_name=Jurassic&format=csv")
JustJur<-JurassicUnits[which(CretaceousUnits[,"t_age"]>=145& CretaceousUnits[,"b_age"]<=201),]


PermianUnits<-read.csv("https://macrostrat.org/api/units?lith_class=sedimentary&interval_name=Permian&format=csv")
JustPerm<-PermianUnits[which(PermianUnits[,"t_age"]>=252& PermianUnits[,"b_age"]<=298.9),]

CarboniferousUnits<-read.csv("https://macrostrat.org/api/units?lith_class=sedimentary&interval_name=Carboniferous&format=csv")
JustCarb<-CarboniferousUnits[which(CarboniferousUnits[,"t_age"]>=298.9& CarboniferousUnits[,"b_age"]<=358.9),]

DevonianUnits<-read.csv("https://macrostrat.org/api/units?lith_class=sedimentary&interval_name=Devonian&format=csv")
JustDev<-DevonianUnits[which(DevonianUnits[,"t_age"]>=358.9& DevonianUnits[,"b_age"]<=419.2),]

SilurianUnits<-read.csv("https://macrostrat.org/api/units?lith_class=sedimentary&interval_name=Silurian&format=csv")
JustSil<-SilurianUnits[which(SilurianUnits[,"t_age"]>=419.2& SilurianUnits[,"b_age"]<=443.8),]

OrdovicianUnits<-read.csv("https://macrostrat.org/api/units?lith_class=sedimentary&interval_name=Ordovician&format=csv")
JustOrd<-OrdovicianUnits[which(OrdovicianUnits[,"t_age"]>=443.8& OrdovicianUnits[,"b_age"]<=485.4),]
````

4) 

`UnitFreqs<-c(2161,1205,2059,3020,903,527,13,4588)`

5)

````R
UnitFreqsminusTri<-c(2161,1205,2059,3020,903,13,4588)
> mean(UnitFreqsminusTri)
[1] 1992.714
````

[UnitFreqsminusTri mean – number of units in Triassic ]/ standard deviation of UnitFreqsminusTri---→ [1992.714-527]/1502.818= 0.975 standard deviations below the mean.

So, the number of Triassic units falls just under one standard deviation below the average number of units in a period over the Paleozoic and Mesozoic.

6) 

The Triassic does feature fewer unique beds than most other periods, but we cannot consider this difference to be statistically significant; it is still among the bulk of the data and is not an outlier. 

7) 

````R
FreqsminusTriJur<-c(2161,1205,2059,3020,903,4588)
> mean(FreqsminusTriJur)
[1] 2322.667
> sd(FreqsminusTriJur)
[1] 1340.022
````

[2322.667 – (527+13)]/1340.022 = 1.33 standard deviations. The Triassic and Jurassic together fall further from the mean but do not surpass the two-standard-deviation cutoff that would make them significant outliers.

## Part 2

## Problem set 3

1) 

````R
URL<-"https://macrostrat.org/api/columns?format=geojson_bare&project_id=1"
> GotURL<-getURL(URL)
> AllNAmap<-readOGR(GotURL,"OGRGeoJSON",verbose=FALSE)
> plot(AllNAmap,main="All North American Units")
````

2)

````R
URL<-"https://macrostrat.org/api/columns?format=geojson_bare&age_top=252.17&age_bottom=242&project_id=1"
> GotURL<-getURL(URL)

> EarlyTriMap<-readOGR(GotURL,"OGRGeoJSON",verbose=FALSE)
> plot(AllNAmap,main="Induan-Anisian Units in Purple")
> plot(EarlyTriMap,col="#B051A5",add=TRUE)
 ````

3)

`EarlyTriTaxa<-downloadPBDB(Taxa=c("Animalia"),StartInterval="Induan",StopInterval="Anisian")`

````R
TriTaxaLAT<-c(EarlyTriTaxa[,"lat"])
> TriTaxaLNG<-c(EarlyTriTaxa[,"lng"])
> plot(AllNAmap,main="Induan-Anisian Units in Purple")
> plot(EarlyTriMap,col="#B051A5",add=TRUE)
> points(TriTaxaLNG,TriTaxaLAT,type="p",col=rgb(0,1,0),pch=19)
````


 

4)
````R
URL<-"https://macrostrat.org/api/columns?format=geojson_bare&project_id=1"
GotURL<-getURL(URL)
AllNAmap<-readOGR(GotURL,"OGRGeoJSON",verbose=FALSE)
> URL<-"https://macrostrat.org/api/columns?format=geojson_bare&age_top=259.8&age_bottom=252.17&project_id=1"
> GotURL<-getURL(URL)
> EndPermMap<-readOGR(GotURL,"OGRGeoJSON",verbose=FALSE)
plot(AllNAmap,main="Lopingian-age units shaded")
plot(EndPermMap,col="#FBA794",add=TRUE)
 ````

5)
````R
LatePermTaxa<-downloadPBDB(Taxa=c("Animalia"),StartInterval="Lopingian",StopInterval="Lopingian")
PermTaxaLAT<-c(LatePermTaxa[,"lat"])
> PermTaxaLNG<-c(LatePermTaxa[,"lng"])
> plot(AllNAmap,main="Lopingian-age units shaded")
> plot(EndPermMap,col="#FBA794",add=TRUE)
> points(PermTaxaLNG,PermTaxaLAT,type="p",col=rgb(0,1,0),pch=19)
````
 

  

6)  

•	There was a substantial drop in the areal extent of North American sedimentary units across the P/T boundary?
	
This is worded kind of strangely. A substantial drop in areal extent would imply that there was less exposed crust, as in sea level rise, which we know to be untrue during the formation of Pangaea. I’m assuming you’re asking if we have evidence for decreased deposition across the P/T (more or fewer beds contained in the latest P and earliest T). Based on these maps, we do see a decrease across the PT in terms of beds being deposited, particularly in the continental interior.
  
•	There was a substantial drop in the percentage of sedimentary units with reported fossils in them across the P/T boundary?
	
	This is also worded in a somewhat confusing manner… are you asking if there were fewer fossiliferous units out of the total in the early Triassic, or fewer occurrences in general in the Triassic?

In either case, we see more fossil occurrences in the Triassic than in the Permian, although the proportion of fossiliferous beds is hard to determine. The long and short is that there are more points plotted in the Triassic. 

(However, and this has been bothering me: in both maps, not all the points plot in the colored units. Did I do something wrong, or is coelophysis popping up in Paleozoic age sediments??).

> Presumably you did something wrong.

Overall, do you think there is sufficient evidence from these maps to reject or accept the hypothesis that lower diversity in the Early Triassic is an artefact of either poor fossil sampling of the available sedimentary rock or a low availablility of sedimentary rock.

The issue at hand is clearly not one of poor fossil sampling, as our mapping showed a marked increase in the number of fossils found in beds of early Triassic age. In fact, the poor sampling may run in the opposite direction, with the Permian being less well-sampled compared to the famously rich fossil deposits of the US Southwest. Regardless, the low diversity of the early Triassic is not the result of being poorly sampled, as that would imply an equal or lesser number of known fossil sites in the Triassic as in the Late Permian. 

	Based on occurrence data alone, we can’t make any assumptions about diversity (all we know is that the Triassic is not being neglected by science). Since decreased deposition exerts a strong control on preservation, this interval of time represents a period of lower preservation that saw an increase in fossil occurrences. Whether this upswing records more and more varied fauna, or just more of the same, is unknowable from the maps. However, we can assume based on this odd inverse response that the low diversity is not due exclusively to rock record contros like the Signor-Lipps effect. If the Signor-Lipps effect was, well, fully in effect, we would expect to see more occurrences in the Late Permian than in the Triassic, since higher deposition would equal higher preservation if the SLE was the only control. However, we see the opposite: lower deposition in the Triassic coincides with better preservation (or more zealous sampling?). So, Early Triassic diversity was probably suppressed by the continued climatic stress from the Permo-Triassic and had still to rebound from the extinction. The decline in sedimentation may have led to poor preservation of certain taxa, which appears in the rock record as lower diversity, but the overall spike in fossil occurrences during a time of low deposition indicates that poor preservation is not the primary control.

<strike>This may not be entirely attributable to the Signor-Lipps effect, since this is not a problem of origination—there just appear to simply be more Triassic fossils than Permian. If the Signor-Lipps effect were the only control (due to a downswing in</strike>
