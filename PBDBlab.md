> Good Job even with the R trip up, 18.8/20

## Paleobio lab 3 answers

1) There are 704 references associated with this paper by Holland and Patzowsky.

2) The reference ID for this paper is 24429.

3) This is the first published description of the taxon.

4) Strophomenata - Strophomenida - Strophomenidae Strophomena planumbona

5) Union county, Indiana

6) Late/Upper Ordovician

7) Liberty formation

8) The dot color indicated the relative age of the fossil: orange corresponds to Palaeogene-age samples and yellow designates Neogene samples. If the mollusks are in a section of known stratigraphy, a rectangle around the eon, era, period, epoch or age will pop up.

8) The *Abra* genus of clams appear in the Ypresian only in Alabama and southern England and Belgium.

9) Cincinnati has the highest density of Ambonychia in the US.

10) Ambonychia's range in the fossil record is limited to the Ordovician, although some samples appear to reference the entire Paleozoic.

11) During the Ordovician, the paleolatitude of North America was indeed equatorial, and the pre-orogenic (future East) coast was orientied E-W along the equator.

12)Ambonychia is in the order Myalinida. 

13) https://training.paleobiodb.org/data1.2/occs/list.json?datainfo&rowcount&base_name=Ambonychia&strat=Lexington Limestone

https://training.paleobiodb.org/data1.2/occs/list.csv?datainfo&rowcount&base_name=Mammal&interval=Paleocene,Oligocene

https://training.paleobiodb.org/data1.2/taxa/opinions.csv?datainfo&rowcount&base_name=Testudines&interval=Triassic,Cretaceous

https://training.paleobiodb.org/data1.2/colls/list.csv?datainfo&rowcount&base_name=Aves, Marsupialia, Sirenia&cc=US

https://training.paleobiodb.org/data1.2/occs/list.csv?datainfo&rowcount&base_name=Gastropoda:Ficus

14) Gastrocoptidae

15) The Portuguese occurrence of Isoetes is Aptian in age.

16) The oldest occurrence of Gastrocopta is in the Eocene.

17) Tiktaalik lived when North American was at the paleoequator.

18) Kotodzha and Raiga Formations

19) Mastodons<-read.csv(URL,row.names=1)
> Mastodons

20) dim(Mastodons)
[1] 39 12

21) The route used here was ÒcollsÓ for Òcollections.Ó

22)  Mammut is the genus name being called for. This taxon is better known as the mastodon, and the time interval referenced is the Pliocene.
	 
23)  URL<"https://paleobiodb.org/data1.2/colls/list.csv?base_name=Mammut&interval=Miocene,Pleistocene"
````R
> Mastodons<-read.csv(URL)
> Mastodons
````

24) https://paleobiodb.org/data1.2/occs/list.csv?datainfo&rowcount&base_name=Mammut&interval=Miocene,Pliocene&show=paleoloc

URL for Mammut paleolatitudes throughout Neogene.


https://paleobiodb.org/data1.1/occs/list.json?limit=all&interval_id=25&base_id=43274&show=coords,attr,loc,prot,time,strat,stratext,lith,lithext,geo,rem,ent,entname,crmod&showsource
> I'm not sure what this bit is for?

25) Glyptophiceras sinuatum corresponds to Species A in Lab 2. I reasoned this based on process of elimination (I had identified the other two first).

Average measurements (in mm): shell width 9.62, shell diameter 40.8 average W/D: 0.24
Xenoceltites variocostatus matches up with Species A in Lab 2. (see explanation below).

Average measurements (in mm): shell width 6.12, shell diameter 23.5 average W/D: 026

Submeekoceras mushbachanum aligns with Species B from Lab 2. Both are involute with a strongly-tapered profile. In Lab 2, these shells has a smooth texture, while in the book there is some minor ribbing at the most recent whorl (the remainder of the whorls are smooth).

Average measurements (in mm): shell width 11.0, shell diameter 42.4, average W/D: 0.26

Xenoceltites variocostatus was first described in a 2008 paper by Brayard and Bucher, called Smithian (Early Triassic) ammonoid faunas from northwestern Guangxi (South China): taxonomy and biochronology. 

Xenoceltites variocostatus appears to be Species A from Lab 2: shell textures were similar (ridged as opposed to smooth or tightly ribbed). Like Species A, this species of ammonite has a thin, minimally-tapered profile and an involute whorl structure. The lip of the living chamber is upright in both series of images, as opposed to tilted forward in Species B. 

My general reasoning was based mainly on sorting characteristics visually. The PaleoDB data did not permit us to control for size cariations, instead giving only averaged shell morphological data. This meant that ontogenetic change and sexual dimorphism were not accounted for in the raw data. So, since these three ammonite species apparently only differ in size and shell proportions, but not in other regards, I decided to mainly exclude the PaleobioDB data and rely instead on the plates from the article. 

26) IÕm afraid I wasnÕt able to make this workÉworked on it for hours, for what itÕs worth. 

> Don't worry you weren't the only one. I've put in a copy of the answer below.. -2 Points

````R
DownloadData<-function(taxon,interval) {
    URL<-paste("https://training.paleobiodb.org/data1.2/occs/list.csv?datainfo&rowcount&base_name=",taxon,"&interval=",interval,sep="")
    return(read.csv(URL))
    }
````

Abra=all Pleistocene Abra data from PBDB. (so far as IÕve gotten on R)


Taxon, Ò&intervalÓ interval, ÒsepÓÓ<
Data info row count

