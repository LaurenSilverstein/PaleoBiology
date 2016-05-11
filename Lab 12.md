Paleobiology lab 12 answers

> 19/20

## Problem set 1:

1) 

TriassicSynapsids<-downloadPBDB("Synapsida","Triassic","Triassic")
TriassicDiapsids<-downloadPBDB("Diapsida","Triassic","Triassic")
JurassicDiapsids<-downloadPBDB("Diapsida","Jurassic","Neogene")
JurassicSynapsids<-downloadPBDB("Synapsida","Jurassic","Neogene")

2) 

TriassicSynapsids<-cleanRank(TriassicSynapsids,"genus")
TriassicDiapsids<-cleanRank(TriassicDiapsids,"genus")
 JurassicDiapsids<-cleanRank(JurassicDiapsids,"genus")
JurassicSynapsids<-cleanRank(JurassicSynapsids,"genus")


TriDiGenera<-subset(TriassicDiapsids[,28])
length(unique(TriDiGenera[,"genus"]))
[1] 430

TriSynGenera<-subset(TriassicSynapsids["genus"])
> length(unique(TriSynGenera[,"genus"]))
[1] 135

3)

JurSynGenera<-subset(JurassicSynapsids["genus"])
JurDiGenera<-subset(JurassicDiapsids["genus"])

 length(unique(JurSynGenera[,"genus"]))
[1] 146
length(unique(JurDiGenera[,"genus"]))
[1] 517
##(this is kinda pointless)

TriSynSurvivors<-intersect(TriassicSynapsids[,"genus"],JurassicSynapsids[,"genus"])

 [1] "Kuehneotherium" "Thomasia"       "Morganucodon"   "Pentasauropus" 
[5] "Ameghinichnus"  "Dicynodontipus" "Sinoconodon"    "Oligokyphus"   
[9] "Tritylodon"


TriSynVictims<-setdiff(TriassicSynapsids[,"genus"],JurassicSynapsids[,"genus"]) 

[1] "Therioherpeton"       "Adelobasileus"       
  [3] "Massetognathus"       "Ischigualastia"      
  [5] "Exaeretodon"          "Dinodontosaurus"     
  [7] "Jachaleria"           "Chiniquodon"         
  [9] "Probainognathus"      "Brachyzostrodon"     
 [11] "Lystrosaurus"         "Rhadiodromus"        

## 126 genera of synapsids did not cross the Triassic/Jurassic boundary
	
TriDiSurvivors<-intersect(TriassicDiapsids[,"genus"],JurassicDiapsids[,"genus"])

intersect(TriassicDiapsids[,"genus"],JurassicDiapsids[,"genus"])
 [1] "Clevosaurus"        "Grallator"          "Rhynchosauroides"  
 [4] "Rotodactylus"       "Brachychirotherium" "Coelurosaurichnus" 
 [7] "Synaptichnium"      "Chirotherium"       "Coelophysis"       
[10] "Euskelosaurus"      "Melanorosaurus"     "Kayentapus"        
[13] "Dilophosauripus"    "Anomoepus"          "Thecodontosaurus"  
[16] "Syntarsus"          "Gruipeda"           "Batrachopus"       
[19] "Otozoum"            "Tetrasauropus"      "Walteria"          
[22] "Platypterna"        "Massospondylus"     "Mystriosuchus"     
[25] "Mafatrisauropus"    "Megalosaurus"       "Steropoides"       
[28] "Sauropus"           "Argoides"           "Thalassiodracon"   
[31] "Rhomaleosaurus"     "Plesiosaurus"       "Shenmuichnus"      
[34] "Heterodontosaurus"  "Plesiornis"         "Moyenisauropus"    
[37] "Nihilichnus"

TriDiVictims<-setdiff(TriassicDiapsids[,"genus"],JurassicDiapsids[,"genus"]) 

[1] "Icarosaurus"         "Rutiodon"            "Kuehneosuchus"      
  [4] "Kuehneosaurus"       "Trilophosaurus"      "Diphydontosaurus"   
  [7] "Terrestrisuchus"     "Planocephalosaurus"  "Sigmala"            
 [10] "Pelecymala"          "Hyperodapedon"       "Lewisuchus"         
 [13] "Lagerpeton"          "Postosuchus"         "Desmatosuchus"      
 [16] "Malerisaurus"        "Efraasia"            "Neusticosaurus"     
 [19] "Plateosaurus"        "Aetosaurus"          "Saltoposuchus"      
 [22] "Liliensternus"       "Gresslyosaurus"      "Doswellia"


393 genera of diapsids did not cross the Triassic/Jurassic boundary.

4)

TriDiOdds<-(length(TriDiSurvivors)/length(TriDiGenera))/(length(TriDiVictims)/(length(TriDiGenera)))

> TriDiOdds
[1] 0.09414758

TriSynOdds<-(length(TriSynSurvivors)/length(TriSynGenera))/(length(TriSynVictims)/(length(TriSynGenera)))

> TriSynOdds
[1] 0.07142857

FlippedOddsRatio<-TriDiOdds/TriSynOdds
> FlippedOddsRatio
[1] 1.318066
> log(FlippedOddsRatio)
[1] 0.2761656
>

5)

StandardError<-sqrt(1/length(TriDiSurvivors) + 1/length(TriDiVictims) + 1/length(TriSynSurvivors) + 1/length(TriSynVictims))

> StandardError
[1] 0.3855116

UpperLimit<-log(FlippedOddsRatio)+StandardError*1.96
> LowerLimit<-log(FlippedOddsRatio)-StandardError*1.96
> UpperLimit
[1] 1.031768
> LowerLimit
[1] -0.4794371

So, the 95% confidence interval is -0.479 to 1.0317. So, while Triassic diapsids were more likely than synapsids to cross the Triassic/Jurassic, this likelihood is not unusual enough to count as statistically significant. The lower limit intersects 0, indication that the confidence interval overlaps the perfect 1:1 odds.
(???????????)


## Problem set 2

1)
MidLateTri<-downloadPBDB(Taxa=c("Synapsida","Diapsida"),"Anisian","Rhaetian")
MidLateTri<-cleanRank(MidLateTri,"genus")

PostTri<-downloadPBDB(Taxa=c("Synapsida","Diapsida"),"Jurassic","Neogene")
PostTri<-cleanRank(PostTri,"genus")

2)

MeanTriLat<- tapply(MidLateTri[,"paleolat"],MidLateTri[,"genus"],mean)
 head(MeanTriLat)
 	Acaenasuchus  Acallosuchus Acompsosaurus 
     	  10.116        10.430        10.740 
  Actiosaurus Adamanasuchus Adelobasileus 
     	  32.120        10.145        10.170 



3)

TriSurvivors<-intersect(MidLateTri[,"genus"],PostTri[,"genus"])
TriVictims<-setdiff(MidLateTri[,"genus"],PostTri[,"genus"])

4)

TriSynapsids<-subset(MidLateTri,MidLateTri[,"genus"]%in%TriassicSynapsids[,"genus"]==TRUE)

TriDiapsids<-subset(MidLateTri,MidLateTri[,"genus"]%in%TriassicDiapsids[,"genus"]==TRUE)

5)

TriVictims<-array(0,dim=length(TriVictims),dimnames=list(TriVictims))
> head(TriVictims)
     Icarosaurus         Rutiodon    Kuehneosuchus 
               0                0                0 
   Kuehneosaurus   Trilophosaurus Diphydontosaurus 
               0                0                0 

TriMatrix<-merge(TriVictims,MeanTriLat,all=TRUE,by="row.names")
> head(TriMatrix)
      Row.names x      y
1  Acaenasuchus 0 10.116
2  Acallosuchus 0 10.430
3 Acompsosaurus 0 10.740
4   Actiosaurus 0 32.120
5 Adamanasuchus 0 10.145
6 Adelobasileus 0 10.170

colnames(TriMatrix)<-c("genus name","Survivor/Victim","Mean Latitude")
> head(TriMatrix)
     genus name Survivor/Victim Mean Latitude
1  Acaenasuchus               0        10.116
2  Acallosuchus               0        10.430
3 Acompsosaurus               0        10.740
4   Actiosaurus               0        32.120
5 Adamanasuchus               0        10.145
6 Adelobasileus               0        10.170

> Regression<-glm(TriMatrix[,"Survivor/Victim"]~TriMatrix[,"Mean Latitude"],family="binomial")

summary(Regression)

Call:
glm(formula = TriMatrix[, "Survivor/Victim"] ~ TriMatrix[, "Mean Latitude"], 
    family = "binomial")

Deviance Residuals: 
    Min       1Q   Median       3Q      Max  
-0.4474  -0.4411  -0.4385  -0.4308   2.1889  

Coefficients:
                               Estimate Std. Error
(Intercept)                  -2.3009122  0.1547326
TriMatrix[, "Mean Latitude"]  0.0007725  0.0051555
                             z value Pr(>|z|)    
(Intercept)                   -14.87   <2e-16 ***
TriMatrix[, "Mean Latitude"]    0.15    0.881    
---
Signif. codes:  
0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

(Dispersion parameter for binomial family taken to be 1)

    Null deviance: 308.10  on 504  degrees of freedom
Residual deviance: 308.08  on 503  degrees of freedom
AIC: 312.08

Number of Fisher Scoring iterations: 5

Was the mean latitude of a Triassic genus a good predictor of its survival across the T/J extinction?


> You didn't answer the question!
