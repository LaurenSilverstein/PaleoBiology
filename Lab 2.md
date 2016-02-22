> Great Job! Perfect score! 20/20

## Part 1

1)
+ Species A: 1,8,11,20
+ Species B: 5,7,14,16,19,23,24
+ Species C: 2,3,4,6,9,10,12,13,17,15,18,21,22,25

I based these groupings largely on visually-sorted morphological characteristics, and later tested them in R. Stratigraphic range was a key determining factor, given that ammonites define stratigraphic zones worldwide, but since there was a possibility for overlap I didn’t focus exclusively on it. In R, I subscripted each species and found the mean, median (to determine skewness), standard deviation and range of each column. Species B and C had a rather large stratigraphic range and standard deviation, which didn’t sit well with my intended sorting, but the means and medians didn’t overlap significantly. Therefore, I concluded that their stratigraphic “primes” were distinct. Mean and median UDs and WDs were very close as well, so I concluded that my species groupings were reasonable.

> Excellent, many students ignored the stratigraphic range aspects completely!

2) The shell textures were a key distinguishing feature for me. I noticed three general types; one with prominent, mainly straight ribs, one with a smooth shell texture, and one with more faint ribbing that appeared “wrinkly.” The shells with prominent ribs also appeared to share a common characteristic of having an evolute whorl structure, and a body chamber “lip” that was upright (when not broken off). Juveniles had body chamber lips that jutted forward, indicating faster growth(???).
> Bigger whorls mean more growth, yes.
The smooth shells had a body chamber lip that leaned slightly forward, while the wrinkly-shells were upright as well. Smooth shells were involute, giving them a tapered profile. Ribbed shells were slightly involute, and had a minimally-tapered profile, while wrinkly-shells were evolute and had very narrow profiles.

3) Ontogenetic change in ammonites was mainly a matter of size change. Since the mature shell builds upon previous whorls, juvenile features are preserved at the center. So, if a species with pronounced ribs has those ribs throughout its shell, it can be seen to have had the same ribs (only proportionally smaller) as a juvenile. Based on this, if we observe similar ribs on a much smaller shell that appears to be an infant, then we can reasonably assign it to the same species. Oddly, I noticed that the shape of the body chamber lip seemed to differ from those of adults. This was especially marked in the ribbed-shells, whose lips went from tilted forward to upright. I didn’t notice any marked differences in the other two groups.

4) Sexual dimorphism—apparently, sexual dimorphism in ammonites is expressed as size variation. Since the specimens here were seen only in pictures (with no scale bar, tsk tsk!) the size of each shell didn’t really impact my decisions. If ammonites varied in more apparent ways, like shell structures or whorl shape, then we’d have a problem. But the sources linked to the lab suggested that size was the main feature that varied.

## Part 2

1) in the plethodon list, the elements are

````R
names(plethodon)
[1] "land"    "links"   "species" "site"    "outline"
````

2)	Each object is a list:

> I meant each object in the ````plethodon```` list, but I guess this was not clear.

````R
class(plethodon)
[1] "list"
````

3) 

````R
dim(plethodon[[1]])
[1] 12  2 40
````

4) hummingbirds[[“land”]] gave the landmark data

5) ProcrustesHummingbirds<-gpagen(hummingbirds[["land"]])

6) plotTangentSpace(ProcrustesHummingbirds[["coords"]],warpgrids=FALSE,verbose=FALSE)

## Part 3

1)	The synapomorphy of the D,E clade is six-inch plus fangs.
2)	The plesiomorphy of the D,E clade is a sulfurous odor.
3)	The synapomorphy of the A,B clade is adorable eyelashes.
4)	Taxa C, D and E all have a sulfurous odor.
5)	Species E has evolved a laser death ray, while species D lacks this adaptation.
6)	Adorable eyelashes are a synapomorphy.
7)	Family 1 is monophyletic; Family 2 is polyphyletic; Family 3 is monophyletic.
8)	A clade containing species D and E would be a true clade, but the addition of species A would make it a polyphyletic, “false” clade. Hypothetically, including species B and C as well would make it a monophyletic clade again. It would include both B and A as descendants of a common ancestor with species C, D and E.
9)	Group 1: polyphyletic or paraphyletic: depends on if you start the clade at “adorable eyelashes” (in which case it would be polyphyletic) or at the base node (aka the one common ancestor, in which case it would be paraphyly).
Group 2: monophyletic
Group 3: paraphyletic 
Group 4: monophyletic
Group 5: polyphyletic


Part 4 Questions
	
1)	Gryphaea mccullochi evolved via peramorphosis (rounder profile and more compact growth lines) while Gryphaea gigantea evolved via paedomorphosis (a slender profile and fewer, more pread-out growth lines).
2)	Gryphaea gigantea underwent more heterochrony, because paedomorphosis would involve the most ontogenetic change over evolutionary time (the retention of juvenile characters).
3)	Olenellus underwent paedomorphosis over time.
