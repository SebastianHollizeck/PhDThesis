---
bibliography: MyBibLatex.bib
title: Development of new methods for accurate estimation of tumour
  heterogeneity
---

**DNA** & **D**eoxyribo**N**ucleic **A**cid\
**RNA** & **R**ibo**N**ucleic **A**cid\
**cfDNA** & **c**ell **f**ree **DNA**\
**ctDNA** & **c**irculating **t**umour **DNA**\
**bp** & **b**ase **p**air\
**ChIP** & **Ch**romatin **I**mmuno**P**recipitation\
**WGS** & **W**hole **G**enome **S**equencing\
**WES** & **W**hole **E**xome **S**equencing\
**SCLC** & **S**mall **C**ell **L**ung **C**ancer\
**NSCLC** & **N**on-**S**mall **C**ell **L**ung **C**ancer\
**RAID** & **R**edundant **A**rray of **I**ndependent **D**isks\
**SNP** & **S**ingle **N**ucleotide **P**olymorphism\
**InDel** & **In**sertion or **Del**etion\
**SV** & **S**tructural **V**ariant\
**PON** & **P**anel **O**f **N**ormals\
**GATK** & **G**enome **A**nalysis **T**ool**K**it\
**NJ** & **N**eighbour **J**oining\
**UPGMA** & **U**nweighted **P**air **G**roup **M**ethod with
**A**rithmetic mean\
**WPGMA** & **W**eighted **P**air **G**roup **M**ethod with
**A**rithmetic mean\
**F81** & **F**elsenstein 19**81** model\
**HKY85** & **H**asegawa, **K**ishino and **Y**ano 19**85** model\
**HPC** & **H**igh **P**erformance **C**omputing\

Speed of Light & ![c](https://latex.codecogs.com/png.latex?c "c") &
![=](https://latex.codecogs.com/png.latex?%3D "=") &
![2.997\\ 924\\ 58\\times10\^{8}\\ \\mbox{ms}\^{-\\mbox{s}}](https://latex.codecogs.com/png.latex?2.997%5C%20924%5C%2058%5Ctimes10%5E%7B8%7D%5C%20%5Cmbox%7Bms%7D%5E%7B-%5Cmbox%7Bs%7D%7D "2.997\ 924\ 58\times10^{8}\ \mbox{ms}^{-\mbox{s}}")
(exact)\

![a](https://latex.codecogs.com/png.latex?a "a") & distance & m\
![P](https://latex.codecogs.com/png.latex?P "P") & power & W
(Js![\^{-1}](https://latex.codecogs.com/png.latex?%5E%7B-1%7D "^{-1}"))\
& &\
![\\omega](https://latex.codecogs.com/png.latex?%5Comega "\omega") &
angular frequency &
rads![\^{-1}](https://latex.codecogs.com/png.latex?%5E%7B-1%7D "^{-1}")\

::: savequote
"Begin at the beginning," the King said, very gravely, "and go on till
you come to the end: then stop."
:::

# Introduction {#ch:intro}

This first introduction chapter contains all the necessary background
information as well as an overview for the work discussed in this
thesis. It summarised basic biological properties of DNA and cell
biology as well as the respective technologies to read, analyse and
measure these biological concepts and then how to evaluate the output of
these methods. [Section [1.1](#intro-sec:DNA){reference-type="ref"
reference="intro-sec:DNA"}](#intro-sec:DNA) delineates the role DNA
plays for the cell and then
[section [1.2](#intro-sec:ctDNA){reference-type="ref"
reference="intro-sec:ctDNA"}](#intro-sec:ctDNA) shows how these
standards are changed in the tumour and cell free context.
[Section [1.3](#intro-sec:sequencing){reference-type="ref"
reference="intro-sec:sequencing"}](#intro-sec:sequencing) introduces the
current technologies used to measure and detect DNA and its variations.
With [section [1.4](#intro-sec:analysis){reference-type="ref"
reference="intro-sec:analysis"}](#intro-sec:analysis) covering the
computational analysis methods to read out changes in the DNA. Then
[section [1.5.1](#intro-sec:lungcancer){reference-type="ref"
reference="intro-sec:lungcancer"}](#intro-sec:lungcancer) relates how
these changes lead to cancer and what we can learn from them. The
introduction concludes with
[section [1.6](#intro-sec:overview){reference-type="ref"
reference="intro-sec:overview"}](#intro-sec:overview) as an overview
over the thesis aims and my work in addressing them in the following
chapters.

## DNA as a information storage unit {#intro-sec:DNA}

![Overview of DNA structure and the nucleobases, which form DNA strands.
Nucleotides are split into Purines and Pyrimidines by the structure of
the nitrogen ring; complementary pairing of bases is shown as shapes of
the bases as well as with 2D structures; Hyrdogen (H) bonds are shown as
dotted lines; Phosphates are shown as P; 3' and 5' ends are defined by
the internal number of the carbon atom of the sugar which is exposed;
Adapted from "DNA structure" by [`BioRender.com`](https://biorender.com)
(2021) Retrieved from
[`https://app.biorender.com/biorender-templates`](https://app.biorender.com/biorender-templates)](Figures/DNAStructure.png){#fig:DNAstructure
width="0.9\\linewidth"}

It is a widely accepted fact, that Deoxyribonucleic acid (DNA) serves as
the long term information storage molecule of our cells. This
information is protected and allows correction of simple errors through
its double helix structure [@Watson1953; @Liang1998]. The nucleotides,
which consist of a deoxyribose sugar (hence the name), a phosphate group
and the nitrogenous base, are joined together by phosphate groups. Even
though there are six common naturally occurring nitrogenous bases:
Adenine (A), Thymine (T), Guanine (G), Cytosine (C), Uracil (U) and
nicotinamide, only the first four are used to encode the genetic
information into DNA. Each of the strands mirrors the other, so that an
adenine will be paired up with a thymine forming two hydrogen bonds.
Similarly cytosine will pair with guanine forming an even stronger bond
with three hydrogen bonds. While other pairings which do not follow
those rules are chemically possible, they are mostly observed in
ribonucleic acid (RNA) [@Sinden1994]. These very strict bonding rules
enable the DNA to be similar to a hard drive with backup on a computer.
And as only one strand contains all the information, the DNA polymerase
enzyme does only need access to one strand, which allows parallel
replication during cell division, but also error corrections, by proof
reading the newly synthesised strand with the template. In order to be
able to distinguish the two strands, they were assigned the names 3' and
5' depending on the numbering of the carbon atom in the sugar, which is
exposed ().

The entirety of the DNA encoding the organism is commonly called "the
genome" with all genes, which consist of introns and exons are called
exome. Unicellular organisms usually only have a very small amount of
introns, which to current knowledge only provide limited information and
are only responsible for structure. In vertebrates introns as well as
intergeneic DNA (the DNA between genes) contribute most of the DNA in
the genome. For example in humans, only
![1\\%](https://latex.codecogs.com/png.latex?1%5C%25 "1\%") of the
genetic material is considered to be exonic, whereas introns contribute
![\\approx 24\\%](https://latex.codecogs.com/png.latex?%5Capprox%2024%5C%25 "\approx 24\%")
and the rest is intergeneic
(![\\approx 75\\%](https://latex.codecogs.com/png.latex?%5Capprox%2075%5C%25 "\approx 75\%"))[@Venter2001].

![Structural overview of the metaphase condensed chromosome: DNA is
first wrapped around Histones to form nucleosome, which then associate
with each other to form the chromatin fiber, which in the metaphase of
the cell cycle is condensed even more into the X-shaped
chromosome](Figures/ChromosomeStructure.png){#fig:chromsomestructure
width="0.9\\linewidth"}

The DNA in eukaryotes however is not free floating around in the nucleus
of a cell, but rather in most eukrayotic organisms, it is highly
condensed and structured, first wrapped around nucleosomes like thread
on a spool, then organised around histones, into either open
(accessible) or closed chromatin, which then can be even further
condensed into chromosomes, which have a X-like shape, with two shorter
and two longer arms (). This allows some of the DNA to be accessible
where the use of other areas can be restricted[@Hammond2017]. Through
this restriction, the availability of certain genes, which are the
sections of the DNA, which encode for short term storage molecules like
RNA. This restriction plays an important role in cell fate and cell
viability. Ultimately all information stored to create a new highly
complex organism is stored in just the DNA of one cell. Whichever parts
are used and how they are used decides the function and the identity of
the cell[@Bonev2016].

### Ploidy - its good to have a backup, if you do it right {#intro-sec:ploidy}

Similar to the already discussed RAID-like setup of the DNA in two
strands, another concept of data security, a spatial different storage
is also implemented. Most eukaryotic organisms have at least two of each
chromosome (diploid) with some species reaching up to
septaploid[@Tateoka1975]. However, this concept is not the only reason
for the ploidy of somatic cells. For sexually reproducing organisms, at
least a diploid set of chromosomes is necessary to enable information to
be joined from both parents. Germline cells (sperm and egg) are
generally monoploid, such that the resulting cell will be diploid, but
the ploidy of the somatic cells is not as uniform within a species,
where it can vary between organisms based on gender or rank
[@Trivers1976]. In most organisms, a change in ploidy is fatal
[@Otto2007] and only partial ploidy changes like extra copies of
chromosome 17 [@Gottlieb1962], chromosome 18 [@Cereda2012] and
chromosome 21 [@Hulten2008] are tolerated. These syndroms can occur when
the is an uneven split of chromosomes during cell division. The
additional advantage, apart from sexual reproduction, is that a second
almost identical copy of a chromosome allows repair of DNA, even when
both strands are damaged, for example in a double strand break. In this
case, the information from the sister chromosome will be used, by first
cutting the double strand break ends to have overhang (resection). This
overhang will then merge with the sister chromosome's mirrored strand.
In this state, the two chromosomes are fused together in a Holliday
junction, which allows the missing part from the resection and the
double strand break to be synthesised [@Lilley2000]. During this
process, which is part of the homology directed repair (HDR) machinery,
the sister chromosomes exchange parts of their DNA, when resolving the
Holliday junction. As these stretches of DNA do not need to be 100%
identical, this plays and important role in evolution and diversity
[@Hanage2006; @Kong2013].

![Individual chromosomes occupy a subspace in the nucleus called
chromosome territories. Chromosome territories can be further
partitioned to distinct A and B compartments, which are enriched for
active and repressed chromatin, respectively. Genomic regions within
topologically associating domains (TADs) display increased interactions,
while their interactions with neighbouring regions outside of the TADs
are rather
limited.](Figures/ChromosomeTerritories.png){#fig:chromosometerretories
width="0.9\\linewidth"}

Even though this X-like structure is the most commonly used and known
structure, the DNAs 3D structure is usually very different and only
takes this shape for the very short time of the cell cycle. Most of the
time, the chromosomes are unravelled into something resembling a ball of
yarn, where the "open" chromatin regions are on the outside and the
"closed" regions are "hidden" in the inside and each chromosome
establishes its own "territory" inside the nucleus (). This structure
allows another DNA cross over with non-sister chromsomes, which is
called a chiasma.

### Phantastical mutations and where to find them {#intro-sec:mutations}

However even though the DNA is highly stable and error correction
methods are constantly working to not introduce any changes in the DNA,
the source of evolution and adaptation of species is sourced in a steady
mutation rate [@Darwin2010; @Sprouffske2018]. These changes in normal
tissue are mostly irrelevant to the organism as a whole and will not be
passed on to the next generation. These changes are known as somatic
mutations. This type of mutation accumulates in a cell linearly over the
course of the lifespan of the cell and is not bound to just cell
divisions[@Alexandrov2015; @Moore2021]. In contrast, if one of those
mutations occurs in the germline cell, eg. sperm or egg producing cells,
these mutations will be propagated to all offspring and be present in
all cells of that organism and in term all its offspring. These
mutations are called germline mutations. These mutations are also called
germline variants, as they establish in the population and represent a
variation of the organism. Mutations can also be classified depending on
either their size ranging from single nucleotide polymorphisms (SNPs)
over small insertions or deletions (InDels) to large structural changes,
like the deletion of parts of or even a whole chromosome arm. like
previously described with ploidy changes, usually smaller changes have
less impact on the overall fitness of the organism, however even SNPs
can lead to changes which are not compatible with
life[@Shamseldin2015; @Frey2021].

## Cell free DNA is more than just bits and pieces {#intro-sec:ctDNA}

When a cell from a multicellular organism dies, through which ever
method, there will be many different enzymes involved, which clear the
debris and recycle material. This means that proteases digest proteins
into amino acids, which will later be used for either building new
proteins or possibly even digested further for energy production. The
same happens with the DNA in the cell. However as discussed in the
previous section [1.1](#intro-sec:DNA){reference-type="ref"
reference="intro-sec:DNA"} the DNA is wrapped around histones and
organised in structures called nuclesomes. These protect the DNA from
being cut by DNAases by hindering the access to the DNA, similar to how
they stopped the access for transcription into RNA. This then in turn
leads to the DNA being cut into pieces mainly in the length of 167 base
pairs (bp). These DNA fragments, which are called cell free DNA (cfDNA),
can then be detected in bodily fluids, like blood or even stool. By
analysing these fragments, non invasive tests for prenatal care have
been possible, as the DNA of the foetus is detectable in the mothers
blood [@Dan2012; @Nicolaides2013]. Similar to the process, a cancer also
sheds DNA, titled circulating tumour DNA (ctDNA), when its cells die,
either through intervention of the immune system or through other
forcefull processes. These ctDNA fragments can also be analysed and
molecular properties measured, without even knowing the exact location
of the tumour. As a blood test can be routinely performed in the clinic
or even a general practitioner, the monitoring of cancer progression is
significantly easier and safer than through other measures. Of course it
is, similar to the prenatal test, only a proxy for the cells which are
still alive, as these have not shed their DNA. Additionally the amount
of shedded DNA is highly variable between tumours, with a general higher
amount for later stages, so that sometimes there is almost no ctDNA
present, even though the cancer is fairly advanced
[@Diehl2008; @Schwarzenbach2011].

## DNA sequencing - when is next generation sequencing the current generation? {#intro-sec:sequencing}

As we know the building blocks, that make DNA as well as the process and
the enzymes responsible, we can synthesise DNA in vitro. By chemically
modifying the nucleotides supplied to the synthesis process, the
sequence of the copied strand can be analysed. The first method to make
use of this used the lambda phage to fuse known ends for the primers
needed for the reaction to the piece of DNA and supplied labelled
nucleotides [@Padmanabhan1974].This method was then superseded by
\"Sanger sequencing\" after Frederick Sanger who with colleagues
published this method in 1977, by adding **di**deoxynucleotides in a low
concentration, the polymerase chain reaction would terminate trying to
integrate these nucleotides and by labelling them radioactively or
flourecently, a gel can be used to determine the sequence of a piece of
DNA [@Sanger1975; @Sanger1977], which made the method better suited for
larger scale projects.

However this method has multiple issues for modern research questions.
Mostly, that it is fairly labour and time consuming to analyse multiple
pieces of DNA at the same time and it is very challenging to sequence
all the DNA of an organism. The human genome project, which was started
in 1990 used machines which automated the Sanger sequencing procedure
and it still took hundreds of researchers 13 years to complete the DNA
sequence of just one human [@Lander2001; @Venter2001]. Even though this
was a very long project, it laid the ground work for the usage of the
current sequencing technologies.

### Library preparation - what we learned from using phages {#intro-sec:libraryprep}

![Adapter ligation during library preparation. The adapters are added to
the DNA insert during library preparation. A. The DNA insert is prepared
by adding an A-tail and phosphorylation. B. The adapter complex which
includes the P5/P7 flow cell binding adapter is added to the DNA insert.
C. The DNA insert is ready for sequencing. D. The DNA insert binds to
the flow cell for sequencing. Primers bind to the DNA insert to generate
reads;\
Figure adapted from [\"How short inserts affect sequencing
performance\"](https://sapac.support.illumina.com/bulletins/2020/12/how-short-inserts-affect-sequencing-performance.html)[@Illumina2020]](Figures/LibraryPreparation.png){#fig:libraryprep
width=".9\\linewidth"}

Library preparation is the name of the preprocessing step, which is done
before it is sequenced with the current technologies. The first step to
sequence DNA is to obtain the DNA, which is done by lysing the cells of
interest, which disrupts the cell membrane and therefore spills all its
contents. The then spilled DNA is fragmented into smaller pieces, by
either restriction enzymes or sonication, to have a size of about
between 200-800bp. These steps are not necessary when preparing
sequencing of ctDNA, as discussed in , the DNA is unbound and already
digested into short fragments. Once the DNA is ready, it is both
phosphorelated as well as an A-tail is added, before the adapter complex
is ligated. This enabled the DNA to bind to the flow cell which is
covered with the reverse complement of the adapter ().

### Next generation sequencing {#intro-sec:ngs}

![The Illumina sequencing-by-synthesis approach. Cluster strands created
by bridge amplification are primed and all four fluorescently labeled,
3'-OH blocked nucleotides are added to the flow cell with DNA
polymerase. The cluster strands are extended by one nucleotide.
Following the incorporation step, the unused nucleotides and DNA
polymerase molecules are washed away, a scan buffer is added to the flow
cell, and the optics system scans each lane of the flow cell by imaging
units called tiles. Once imaging is completed, chemicals that effect
cleavage of the fluorescent labels and the 3'-OH blocking groups are
added to the flow cell, which prepares the cluster strands for another
round of fluorescent nucleotide incorporation; Figure adapted from
@Mardis2008[@Mardis2008]](Figures/SequencingBySynthesis.jpg){#fig:sequencingbysynthesis
width=".85\\linewidth"}

Next generation sequencing (NGS)is the coined term for basically any
standard high-throughput sequencing performed, which includes exome,
genome, transcriptome, protein-dna interactions (ChIP) and other
epigenome studies. The term NGS is still widely used, even though it has
been more than 10 years since the first NGS approach was commercially
available. While in the beginning of next generation sequencing there
were multiple approaches, the current lion share (80% of sequencing
data) of protocols use the Illumina short read sequencing by synthesis
approach ()[@Mardis2008; @Straiton2019], which is based on the concept
of alternating integration of florescently labelled nucleotides and
imaging with a microscope () as well as multiplexing, where a DNA
fragment is ligated to an index, which allows the sequencing of multiple
samples at once [@Church1984; @Church1988] as it is shown in . This
method allows highly accurate determination of the sequence of a DNA
fragment and depending on the flow cell and sequencing machine allows to
sequence a whole genome in just 24h.

### Long read sequencing - the \"third\" generation sequencing {#intro-sec:lrs}

By now, multiple methods which broke free of the size limitations of NGS
exist, which are commonly referred to as long read sequencing. Most of
the current methods trade the very high accuracy of the second
generation NGS methods for the capability of sequencing of sequencing
huge continous strands of DNA (current record 2.3 Million bp
[@Payne2018]) with normal library preparation ranging between 10-30 Kbp.
These methods are expected to revolutionise our understanding of the
highly repetitive elements that exist in the genome, such as the
centromeres of chromosomes. Methods such as the direct molecule
sequencing approach by Oxford Nanopore are even able to distinguish post
transcriptional modifications on RNA[@Pratanwanich2021]. So far, these
methods however are still very expensive and as this work is dealing
with ctDNA, which is highly fragmented, these methods offer only limited
advantages over the short read sequencing, while being much more
expensive.

## DNA analysis- what to do with the sequence {#intro-sec:analysis}

The types of analysis that can be done with the output from the
sequencing machine stretches far, however, all methods need to first
infer the location in the genome, the sequenced piece of DNA originated
from. As the current methods randomly fragment the DNA (), the genomic
location information is completely lost. This process is referred to as
mapping.

### Mapping - Ey man, where is my genomic location? {#intro-sec:mapping}

In this process, the fragments of DNA, which were sequenced, are
assigned a genomic coordinate on the reference genome. This is only
possible, due to the fact, that we have a resolved genome sequences ()
for a high number of species. The location a sequenced piece of DNA fits
to the reference genome might be unique, but it could also fit to
multiple locations, due to highly repetitive regions or due to the
existence of pseudo genes with almost 100% identify. In addition to
this, the reference genome might not accurately reflect the genome of
the organism that has been sequenced. Each mapping position is therefore
assigned a quality score, which reflects how likely it is the actual
position of the sequence. As Illumina sequencers have the ability to
sequence both ends of the DNA fragment, the position of the ends (read 1
and read 2) to each other can also be used to infer the quality, as they
should be within a reasonable distance to each other ()

As this process is time consuming and the exact location of the fragment
might not be as important, there exists a subset of tools called
pseudo-mapper, which are based on
![k](https://latex.codecogs.com/png.latex?k "k")-mers, which are
predefined DNA sequences of length
![k](https://latex.codecogs.com/png.latex?k "k"), which help to identify
certain regions of interest. These tools are especially common for
RNAseq, where the exact location of a read doesnt matter, only that the
read is within a gene [@Bray2016; @Patro2017], but also for methods that
estimate similarity between sequences (DNA, RNA or protein)
[@Ondov2016; @Luczak2017].

For this work however, the exact position of reads is important, so only
real mapping methods like BWA [@Li2013] or Bowtie 2 [@Langmead2018],
which are optimised for short reads from Illumina systems, provide the
necessary functions.

### Variant calling - spot the difference {#intro-sec:variantcalling}

As intra-species genetic variation is intended for adaptation and
evolution, there will be places where the DNA sequence of the subject
will differ from the sequence of the reference (see ). These variants
give insight into medical background as well as treatment options for
patients and can even be used to guide family planning. Depending on the
type of variation that is of interest, a different set of computational
methods are needed, as germline and somatic variants have different
properties.

### Germline variant calling - the cards you have been dealt at birth {#intro-sec:germlinecalling}

The most common source of DNA used for germline variant analysis is the
mono nuclear layer from the blood of the subject, but really almost any
cell can be used for this process, as all cells in the organism will
share all germline variants (). The only important input on top of the
DNA sequence from the sequencer are the reference genome of the organism
as all variant nomenclature is based on the reference and the ploidy of
the organism (). The ploidy is important to infer, at which ranges of
allele frequency a variant can biologically occur. For example in a
human diploid genome, germline variants can occur either in one or both
chromosomes, which mean we assume reads should show an allele frequency
of around 50% and 100%, where the hexaploid commercial wheat
[@Mayer2014] allele frequency for variants would be 16%, 33%, 50%, 66%,
0.83% and 100%. Due to the random sampling and possible sequencing
errors, however the observed allele frequencies will differ. Most state
of the art germline variant calling method will also use haplotype
reconstructions through de-Bruijn graphs, which features a remapping of
reads in relation to each other
[@Garrison2012; @Lai2016; @Kim2018; @Benjamin2019; @Cooke2021] where the
original mapping location assigned by the aligner () is only used as a
guideline. This allows to resolve even complex haplotypes of the sample
by not restricting the method to the linear setup of the reference
genome.

### Somatic variant calling - life is ever changing {#intro-sec:somaticcalling}

In contrast to germline variant calling, somatic variant calling methods
cannot rely on allele frequency, as not all cells sequenced are expected
to have the change in nucleotide. The allele frequency is instead a
measure of the sub clonal size. A subclone is here defined as the set of
cells, which were derived from the cell, which originally acquired the
somatic mutation. Depending on the selective advantage, just random
drift and also the time point when the variant was introduced, these
clones can be very variable in size and therefore their contribution to
the DNA in the sequencing. As not all cells have the variants, the
selection of the tissue for library preparation is very important,
unlike for germline calling. The main use of somatic variant calling is
the genetic diagnosis and research of cancer samples, where the main
question is, which changes are present in the tumour, which lead to the
disease.

The ideal scenario for tumour somatic variant calling is when a biopsy
of the tumour as well as a normal sample of the patient is available. In
most clinical cases, this will be the diagnostic biopsy as well as the
mono nuclear layer from blood, just like for germline calling (). This
needs to be adjusted depending on the type of malignancy, because if the
tumour is a leukemia, the mono nuclear layer of the blood might contain
tumour cells, but for solid tumours, the blood is a routine, minimally
invasive option. These two samples are then analysed together and only
changes that are only in the somatic tumour sample and not in the normal
sample are reported. Even though this concept sounds simple, there are
some pitfalls [@GATKTeam2021a]. First of all, there might be some tumour
contamination in the normal sample, which needs to be adjusted for
[@Kim2018; @TaylorWeiner2018]. Second, there might be normal
"contamination" in the tumour sample, this means that not all cells in
the tumour sample are actually tumour. This means that the signal of the
tumour changes is reduced and harder to find.

All of these issues are amplified in the case, when there is no "normal"
sample available, either because the patient didnt consent, due to other
medical issues, or because for diagnostic tests there usually is no need
for a germline sample. In this case, there is the option for "tumour
only" variant calling, which requires a database of germline variants in
the population, to distinguish between somatic and germline variants, as
the variant calling is very similar to just germline variant calling ()
without the restriction of the ploidy. However, even with an extensive
database like gnomAD [@Karczewski2020] it is unlikely that is possible
to remove all germline variants from the analysis and as there is no
direct comparison, the precision of the "tumour only" method is
significantly lower [@Karimnezhad2020].

## Cancer {#intro-sec:cancer}

While cancer is a massively heterogenous disease, as it can arise
through a multitude of ways in almost any tissue, there are a some
fundamental defining features, which most, if not all malignancies
acquire, before they are truly cancers . The original characteristics
comprise

::: enumerate*
Sustaining proliferative signaling

Evading growth suppressors

Activating invastion and metastasis

Enabling replicative immortality

Inducing angiogenesis

Resisting cell death
:::

(). These hallmarks were long considered the core of tumour development
and the authors themselves hypothesised, that these core mechanics allow
us to condense the complexity that cancer displays, both in the clinic
as well as in labs, with a small set of rules, which all cancers have to
obey [@Hanahan2000]. In their exact words: "We foresee cancer research
developing into a logical science, where the complexities of the
disease, described in the laboratory and clinic, will become
understandable in terms of a small number of underlying principles"

![Acquired capabilities of cancer; Functional capabilities acquired by
most cancers during their development; Figure adapted from
@Hanahan2000[@Hanahan2000]](Figures/oldHallmarksCancer.jpg){#fig:oldhallmarks
width=".95\\linewidth"}

However, with 11 years of additional research into the topic, more
hallmarks have been found and the original list was revised by the
authors to contain additional characteristics, namely

::: enumerate*
Avoiding immune destruction

Tumour-promoting inflamation

Genome instability and mutation

Deregulating cellular energetics
:::

() [@Hanahan2011]. And even then a few years later, even more hallmarks
e.g. metabolic rewiring are now considered a part of the characteristics
of cancer [@Fouad2017].

![Emerging hallmarks and enabling characteristics of cancer; updated
version of the hallmarks figure () with ; Figure adapted from
@Hanahan2011[@Hanahan2011]](Figures/newHallmarksCancer.jpg){#fig:newhallmarks
width=".95\\linewidth"}

So while the original set of the hallmarks was not sufficient or
complete, it offered a good attempt at abstraction of biological
concepts to describe cancers. In the following pages, I will outline
each of those hallmarks and how it influences my research.

#### Sustaining proliferative signaling - there are no breaks on the train

#### Evading growth suppressors

#### Activating invasion and metastasis - look at me\... I am the organism now

#### Enabling replicative immortality

#### Inducing angiogenesis

#### Resisting cell death

### Lungcancer {#intro-sec:lungcancer}

With around 1.6 million deaths world-wide each year, lung cancer is the
number one cause of cancer death [@Siegel2018]. Every year about twelve
thousand Australians get diagnosed with lung cancer. These cases can be
generally split into two groups: small cell lung cancers (SCLC) and
non-small cell lung cancers (NSCLC), which account for around 15% and
85% of cases, respectively. The majority of NSCLC are either lung
adenocarcinoma or lung squamous cell carcinoma [@Molina2008]. Even
though smoking is highly associated with lung cancers, there is a big
group of never smokers, with a high risk of lung cancers in East Asia,
especially women, which is correlated with outside influences like
pollution and occupational carcinogens and paired with genetic
susceptibility [@Sun2007]. This group usually shows *EGFR* (epidermal
growth factor receptor) driven tumours. EGFR is a transmembrane receptor
tyrosine kinase, which is usually only expressed in epithelial,
mesenchymal, and neurogenic tissue, but its overexpression in other
tissues is a hallmark of many human malignancies, not just NSCLC.

## Overview {#intro-sec:overview}

::: savequote
"It is the main source of our mistakes, when making making decision,
that we only look at life piece by piece and not as a whole."
:::

# Joint somatic variant calling - if germline can do it, so can we {#ch:variantcalling}

## Introduction {#variantcalling-sec:intro}

When I started exploring the somatic variant calling methods in the
beginning of my PhD in 2018, I was surprised about the stark difference
between germline and somatic variant calling methods. Where all
\"modern\" germline variant callers have the built-in capability to
joint call multiple samples, for example from family trios, virtually no
somatic variant caller had this function.

The joint analysis of smaller cohorts improves the performance of
germline variant calling methods significantly, by allowing to assess
technical artifacts, which might be unique for the individual sequencing
machine or the researcher handling the DNA [@Schirmer2016; @Stoler2021].
As certain parts of the genome are more problematic to sequence () and
map (), a "control" sample can help to distinguish if a certain observed
change occurs commonly, is a technical issue or in fact a real change.

For somatic variant calling, this concept has been adjusted in the
genome analysis toolkit (GATK) [@BrianOConnor2020] to allow the use of
panel of normals (PON), which contains frequently seen changes in
healthy ("normal") individuals analysed with the same sequencing
technology [@GATKTeam2021], but this is a post processing step of the
analysis rather than a more intricate model like it is for the germline
equivalent. Mutect2, which is the most recent somatic variant calling
algorithm provided by the Broad institute, however also provides a
multi-sample mode, for which all tumour samples need to be from the same
patient, either longitudinal or spatial different [@GATKTeam2020]. This
mode is hidden quite well and all tutorials published by the developers
state that "there is currently no way to perform joint calling for
somatic variant discovery" [@GATKTeam2021a], so while all methods in the
GATK are considered a beta feature, this seems, that development is not
a priority.

There are only two methods currently, which have documented and
published capabilities to jointly analyse tumour samples from the same
patient to call somatic variants. The first one is a specialised method
built on a joint bayesian model for SNVs to occur in multiple samples
called multiSNV [@Josephidou2015]. However it has multiple shortcomings,
which make it not useable for our data. First, as the name suggests, the
method can only jointly evaluate SNVs and completely ignores indels and
structural variants, which would be acceptable for the superior
performance shown. However, multiSNV was optimised only for WES and not
for the very deep WGS that is now available. This means exceptionally
high runtimes. Even with custom parallelisation that was attempted in
this work, the predicted runtime for just one multi sample patient would
have been longer than 3 years. This again shows, that while multiSNV was
a great step forward at the time, there is a real need for new methods
to stem the tide of sequencing data available at low cost.

multiSNV has been the only software available for multi sample analysis,
but only recently, during this work, superFreq [@Flensburg2020] was
published. It combines all standard analysis steps for tumour analysis,
like variant calling or clonal deconvolution, into one program and is
even able to jointly analyse samples. However similar to multiSNV, its
focus when optimising and developing was on WES and RNAseq data, so when
applied to our data, we could not find a server with enough memory to
execute the workflow.

This then prompted us to investigate possible workflows to enable the
analysis of high depth WGS, which we estimate to become more and more
normal, with the ever dropping prices of sequencing. The following
sections will first show the publication and then discusses additional
analysis done after the the publication of the manuscript () and the
impact of the joint analysis on downstream methods ().

## Publication

The publication about joint somatic variant calling can be found at
[`https://doi.org/10.1093/bioinformatics/btab606`](https://doi.org/10.1093/bioinformatics/btab606)
and non-journal formated version is also attached as .

## Effects on downstream analysis - not quite the missing link, but close {#variantcalling-sec:downstream}

The ability to find additional shared variants has significant impact on
our understanding of cancer evolution and the timing of initiation and
metastatic seeding. Recent work has shown, that similar to the well
known genetic heterogeneity, there is heterogeneity when it comes to
metastatic seeding. While traditionally it was thought that tumours only
metastesised after they reached a certain size, to escape the
restrictions of the niche, like reduced nutrition, recent publications
showed, there is also very early metastatic seeding [@Hu2019]. But all
those methods are ultimately based on the somatic variants found in the
data, so if we improve on the input of the downstream analysis methods,
we can expect a clearer and possibly more granular result.

In this section I will highlight for a few examples on how big the
effect can be for methods, like phylogenetic reconstruction and clonal
decomposition, which use somatic variants as input.

### Phylogenetic reconstruction {#variantcalling-sec:phylo}

As this work is not about the advantages and shortcomings of different
phylogenetic reconstruction tools, we will not show a comprehensive
amount of these tools, but rather focus on the results. For this reason,
we chose to use neighbour joining (NJ) [@Saitou1987], because it is
fast, readily available in most phylogenetic reconstruction tool kits
and if the input distance is correct, the output will be correct. And
even, if the distance is not 100% correct, if the distance is "nearly
additive" and the input distances are not far off the real distance, the
tree topology will still be reconstructed correctly [@Mihaescu2007].
Lastly, in contrast to many other methods like UPGMA and WPGMA
[@Sokal1958], NJ does not assume an equal mutation rate of each sample,
because we know, that the molecular clock hypothesis [@Zuckerkandl1962]
is not valid for different lineages of cancers [@Shibata2010].

While there are lots of distance measures for DNA sequences, which allow
accounting for different probabilities of transitions and transversions
as well as uneven base composition, models like F81 [@Felsenstein1981]
or HKY85 [@Hasegawa1985] are only really designed for germline mutations
and are not easily applicable for subclonal somatic mutations, which is
why we decided to first transform the variants present in all samples
into a binary occurrence vector and then calculating the Hamming
distance [@Hamming1950] between all samples. This generates a maximum
parsimony approach and the branch length of the trees will be directly
translatable to the amount of variants which are different between
samples.

shows both the reconstructed phylogenies when using the variants found
with the default tumour-normal method and our improved joint method and
using the exact same reconstruction method otherwise.

![Reconstructed phylogenies of a patient with multiple spatially
distinct samples; Reconstruction method is neighbour joining for both
cases, only the input of the called variants is different. Tip labels
describe the location of the sample in the patient. Trees are shown as
unrooted with germline as fixated origin point; black line ruler shows
the length of an edge with 5000
mutations](Figures/phyloCA99.pdf){#fig:ca99phylo width=".99\\linewidth"}

There are several obvious changes, first, the longer edge connecting the
the germline, which we consider as the state of no somatic variants, to
all other samples. This shows that there are many more shared mutations
in all samples, than what would have been anticipated with the default
method. As the accumulation of somatic variants is still used as a proxy
for timing and cell divisions, when assuming a high mutation rate for
lung cancer
(![5.3 \\cdot 10\^{-8}](https://latex.codecogs.com/png.latex?5.3%20%5Ccdot%2010%5E%7B-8%7D "5.3 \cdot 10^{-8}")
from @Werner2020 [@Werner2020]) this difference of
![\\approx 36000](https://latex.codecogs.com/png.latex?%5Capprox%2036000 "\approx 36000")
variants is equivalent to
![\\approx 2000](https://latex.codecogs.com/png.latex?%5Capprox%202000 "\approx 2000")
cell divisions. While the cell doubling rate of lung cancers is highly
dependent on the type [@Arai1994], this difference makes a huge
difference when assessing the timing of the tumour initiation and
further evolution.

Secondly, there have been topological changes, which generate a
bifuricating edge between the warm coloured pleura, occipital, l-liver-2
and l-liver-5 samples, which fits significantly better with the clinical
history and PET scans of the patient, as these are the sites of
progression, which lead to the death of the patient in contrast to the
earlier sites of disease.

shows a topology focused view of the two trees, which highlights the
breaks which are needed to morph one tree into the other with dotted
edges [@Vienne2018]. The common subtrees are coloured the same on both
sides and connecting lines show identical labels. This format shows that
while the trees look quite similar at first glance, they show vastly
different topologies.

![Side by side view of the reconstructed trees from ; internal edges,
which are distinct between trees are shown as dotted lines; common
subtrees are shown in red and green; Tree labels have been sorted to
minimise distance between labels; axis show the hamming distance between
two nodes. Visualisation generated with dendextend
[@Galili2015]](Figures/tanglePhyloCA99.pdf){#fig:tanglePhyloCa99
width=".99\\linewidth"}

One example of this is "l-liver-3" which was a singleton, almost an
outlier, in the pairwise reconstructed tree but is clustered together
with "r-liver-2" and "r-liver-3". Generally, there have been additional
changes, which make the topology more granular. Where all of the
"l-liver-\*" samples were shown as an almost linear branching off the
main stem, they are now further subdivided and each show distinct
mutations, like "l-liver-2" and "l-liver-5" ().

## Longitudinal analysis - something for the ages  {#variantcalling-sec:longitudinal}

While the initial motivation for the development of these workflows was
the analysis of multi-region, so spatial, samples from the same patient
coming from the CASCADE rapid autopsy program, a longitudinal
application of these methods for the joint analysis of diagnostic and
relapse sample, or even the repeated testing of ctDNA are quite worth
thinking about. In this part, I will present work using the published
workflows on a longitudinal datasets, which highlights the flexibility
and wide spread use of our new methods.

Specifically, I will show the analysis of longitudinal ctDNA WES of
patient "CA-F" from the manuscript (). in a study of late stage melanoma
patients, identified ctDNA sequencing as a way to stratify patients into
high and low risk of relapse and therefore inform adjuvant therapy
[@Tan2019]. In this analysis we aim to improve the quality of detection
of low allele frequency somatic variants. This would enable the
detection of variants from brains metastasis, as the blood brain barrier
decreases the availability of DNA fragments from lesions in the brains
in the normal blood stream [@2014], however it is detectable with
sensitive enough methods [@Yoon2019; @Ma2020].

### Clonal deconvolution {#variantcalling-sec:clonal}

Finally, the holy grail of analysis of multiple related samples from the
same patient is the clonal deconvolution, where subclonal reoccurring
patterns of mutations are detected. These can be linked to either
parallel evolution through positive selection pressure, like a targeted
drug or to the process of developing Metastases where a piece of the
cancer "breaks" off and grows at a different site. Surprisingly, as it
shares the same issues as the joint somatic variant calling of needing
deeply sequenced data from multiple samples of the same organism, there
is a plethora of algorithms and methods available for clonal
deconvolution. Since 2015 PhyloWGS [@Deshwar2015], Canopy [@Jiang2016],
CLOE [@Marass2016], CloneFinder [@Miura2018], Machina [@ElKebir2018] and
MOBSTER [@Caravagna2020]. Underlying these models is a form of
clustering variants with similar variant allele frequency together, to
reduce the combinatorial space and enhance the confidence in the signal
[@Tarabichi2021]. However even though there is a high number of tools,
the challenge to select the right tool is substantial, especially since
all of them have up and downsides [@Miura2020]. In this work we decided
to use PhylogicNDT [@Leshchiner2018] as it has been shown to work well
on clinical samples [@Gerstung2020] and does not have the restriction
for the input to be from copy number neutral areas which many of the
other tools have.

The analysis was conducted by transforming the variants called with the
joint workflows as well as the default pairwise analysis into the
required MAF file format without the cancer cell fraction part, in order
to let PhylogicNDT calculate those on the fly. The local copy numbers
for each variants are generated by intersecting the called segments from
sequenza with the position of the variants. Variants which could not be
assigned a local copy number change were discarded from the analysis.

![Reconstructed clonal trees from PhylogicNDT; Blue circle at top
depicts the germline/normal state. The coloured edges with the same
coloured circle represents a distinct subclone of the parent from which
the edge emerges; The number in braces next to the edge is the number of
mutations which define this subclone with an added gene symbol added, if
there is a cancer driver gene mutation. The left part shows the result
when using the default pairwise method of Strelka2 and the right side
uses the results from the Strelka2Pass
workflow](Figures/clonalDeconv.pdf){#fig:clonaldeconv
width=".99\\linewidth"}

shows the highest parsimony clonal tree reconstructed by PhylogicNDT for
the pairwise as well as the joint variant calling. As the copynumber
calling information is the same for both inputs, the only difference is
in the called variants. While there was no subclonal structure detected
at all for the pairwise analysis, there is a highly variable structure
detected using the jointly called variants.

## Usage - its not just me that thinks it is good

As published software is amazing, its real value is in the re-usability
and portability. Many published software packages are not maintained or
not even functional even though they are published. While I developed
these joint somatic variant calling workflows to deal with a challenge I
faced, many other people even just at the same institute have already
shown interest and some research groups are already using the software
to analyse their multi-sample data.

![Cumulative download numbers of the "dawsontoolkit" docker container
since publication of the manuscript; Actual counts are shown as dots,
with smoothed trajectory depicted as dotted line with the 95% confidence
interval shown as a grey background; confidence interval has been
adjusted with exponential decay of prediction accuracy with distance
from the last data point; Start date
7![\^{th}](https://latex.codecogs.com/png.latex?%5E%7Bth%7D "^{th}")
September 2021](Figures/dawsontoolkitDownloads.pdf){#fig:usageStats
width=".99\\linewidth"}

To have some proxy of the usage statistics of the workflows, I recorded
the download numbers of the "dawsontoolkit" docker container, which only
contains software for refiltering and joint analysis of the workflows
after the publication of the manuscript. Obviously, this is an imperfect
measurement, as people can reuse a downloaded container as often as they
want, which would not appear in the count and similarly, just because
the container was downloaded, the analysis might not have been used.
However it still shows an interaction and an interest in the methods.
The download numbers show a quick increase in numbers in the beginning,
just after the publication, followed by a short plateau but then another
increase (). This suggests, that there is a need in the methods, rather
than a simple curiosity after publication.

::: savequote
"Death is a release from and an end of all pains: beyond it our
sufferings cannot extend: it restores us to the peaceful rest in which
we lay before we were born"
:::

# CASCADE - Late stage lung cancer in the spotlight {#ch:cascade}

## Introduction {#cascade-sec:intro}

## Publication {#cascade-sec:publication}

This chapter includes the data analysis for two two publications. The
first publication features the resistance mechanism of small cell
transformation
([`https://doi.org/10.1016/j.ccell.2019.08.008`](https://doi.org/10.1016/j.ccell.2019.08.008)[@Burr2019])
and the second shows the discovery of resistance to a targeted
RET-fusion driven cancer
([`https://doi.org/10.1016/j.jtho.2020.01.006`](https://doi.org/10.1016/j.jtho.2020.01.006)[@Solomon2020])

## Cohort analysis {#cascade-sec:cohort}

## Mitochondrial phylogenetic reconstruction - the power house of the phylogenies {#cascade-sec:mitochondria}

## Outlook {#cascade-sec:outlook}

::: savequote
"Many a mickle makes a muckle."
:::

# MisMatchFinder - hope springs eternal {#ch:mmf}

## Introduction {#mmf-sec:intro}

::: savequote
"As you think, so you become. Our busy minds are forever jumping to
conclusions, manufacturing and interpreting signs that aren't there."
:::

# Conclusion {#ch:conclusion}

# Custom workflows to improve joint variant calling from multiple related tumour samples: FreeBayesSomatic and Strelka2Pass {#ch:appendixManuscript}

This appendix contains the manuscript published at *Bioinformatics* in
an non journal style format. It can also be found at
[10.1093/bioinformatics/btab606/6361543](https://doi.org/10.1093/bioinformatics/btab606/6361543)
for a paper style version.

------------------------------------------------------------------------

**Hollizeck
S.![\^{1,2}](https://latex.codecogs.com/png.latex?%5E%7B1%2C2%7D "^{1,2}"),
Wong
S.Q.![\^{1,2}](https://latex.codecogs.com/png.latex?%5E%7B1%2C2%7D "^{1,2}"),
Solomon
B.![\^{1,2}](https://latex.codecogs.com/png.latex?%5E%7B1%2C2%7D "^{1,2}"),
Chandrananda
D.![\^{1,2}](https://latex.codecogs.com/png.latex?%5E%7B1%2C2%7D "^{1,2}"),
and Dawson
S-J.![\^{1,2,3,\*}](https://latex.codecogs.com/png.latex?%5E%7B1%2C2%2C3%2C%2A%7D "^{1,2,3,*}")**

![\^1](https://latex.codecogs.com/png.latex?%5E1 "^1") Peter MacCallum
Cancer Centre, Melbourne 3000, Victoria, Australia\
![\^2](https://latex.codecogs.com/png.latex?%5E2 "^2") Sir Peter
MacCallum Department of Oncology, University of Melbourne, Melbourne
3000, Victoria, Australia\
![\^3](https://latex.codecogs.com/png.latex?%5E3 "^3") Centre for Cancer
Research, University of Melbourne, Melbourne 3000, Victoria, Australia\
![\^\*](https://latex.codecogs.com/png.latex?%5E%2A "^*") D.C and S.J.D
are co-senior authors and contributed equally to this article

Received on 27-Jan-2021; revised on 13-Jul-2021; accepted on 12-Aug-2021

**Abstract**

##### **Summary:**

This work describes two novel workflows for variant calling that extend
the widely used algorithms of Strelka2 and FreeBayes to call somatic
mutations from multiple related tumour samples and one matched normal
sample. We show that these workflows offer higher precision and recall
than their single tumour-normal pair equivalents in both simulated and
clinical sequencing data.

##### **Availability and Implementation:**

Source code freely available at the following link:
[`https://atlassian.petermac.org.au/bitbucket/projects/DAW/repos/multisamplevariantcalling`](https://atlassian.petermac.org.au/bitbucket/projects/DAW/repos/multisamplevariantcalling)
and executable through Janis
([`https://github.com/PMCC-BioinformaticsCore/janis`](https://github.com/PMCC-BioinformaticsCore/janis))
under the GPLv3 licence.

##### **Contact:**

[Dineika.Chandrananda\@petermac.org](Dineika.Chandrananda@petermac.org),
[Sarah-Jane.Dawson\@petermac.org](Sarah-Jane.Dawson@petermac.org)

##### **Supplementary information:**

Supplementary data are available at *Bioinformatics* online.

## Introduction {#introduction}

Joint variant calling methods are routinely used to call germline
variants by leveraging population-wide information across multiple
related samples [@DePristo2011; @Toptas2018]. This concept is also
advantageous for somatic variant calling to potentially overcome the
challenges of spatial heterogeneity and low tumour purity. However,
there is a critical lack of robust algorithms that allow multi-sample
somatic calling. Most studies still rely on variant calling of separate
tumour-normal pairs, subsequently combining the results across a sample
cohort [@Hu2019; @Leong2018; @Wang2018].

There are two major pitfalls for combining variants called from
individual tumour samples. First, it is very difficult to differentiate
between a false negative result due to \"missing data\" versus the true
absence of a variant. Second, there is limited sensitivity for low
allele frequency variants thus, decreasing the ability to detect minor
clones, particularly in samples with low tumour purity.

Currently, only three algorithms claim to have the functionality to
jointly analyse multiple samples: multiSNV [@Josephidou2015], SuperFreq
[@Flensburg2020], and Mutect2 [@Benjamin2019], each presenting different
limitations. For instance, multiSNV cannot call indels and along with
SuperFreq, is not optimised for analysis of deep coverage whole-genome
sequencing (WGS) data. Mutect2 has previously been shown to be
disadvantageously conservative as well as computationally inefficient
[@Chen2020a].

To enable highly sensitive, fast and accurate variant detection from
multiple related tumour samples, we have developed joint variant calling
extensions to two widely used single-sample algorithms, FreeBayes
[@Garrison2012] and Strelka2 [@Kim2018]. Using both simulated and
clinical sequencing data, we show that these workflows are highly
accurate and can detect variants at much lower variant allele
frequencies than commonly used methods.

## Materials and methods

### FreeBayesSomatic workflow

The original FreeBayes algorithm can jointly evaluate multiple samples
but routinely it does not perform somatic variant calling on
tumour-normal pairs. We introduce FreeBayesSomatic which allows
concurrent analysis of multiple tumour samples by adapting concepts from
SpeedSeq [@Chiang2015] which differentiates the likelihood of a variant
between tumour and normal samples instead of imposing an absolute filter
for all variants called in the normal. Hence, for each genotype (GT) at
SNV sites, FreeBayesSomatic first calculates the difference in
likelihoods (LOD) between the normal (Eq. 1) and the tumour (Eq. 2)
samples genotype likelihoods (GL) with
g![\_{0}](https://latex.codecogs.com/png.latex?_%7B0%7D "_{0}")
describing the reference genotype.

![\\begin{aligned}
\\text{LOD}\_{\\text{normal}} &= \\max\_{g_i \\in \\text{GT}} \\left( \\text{GL}(g_0) - \\text{GL}(g_i) \\right) \\label{eq:01}\\\\
\\text{LOD}\_{\\text{tumour}} &= \\min\_{s \\in \\text{Samples}} \\left( \\min\_{g_i \\in \\text{GT}} \\left( \\text{GL}\_s(g_i) - \\text{GL}\_s(g_0) \\right) \\right) \\label{eq:02}\\\\
\\text{somaticLOD} & := \\left( \\text{LOD}\_{\\text{normal}} \\geq 3.5 \\land \\text{LOD}\_{\\text{tumour}} \\geq 3.5 \\right) \\label{eq:03}\\end{aligned}](https://latex.codecogs.com/png.latex?%5Cbegin%7Baligned%7D%0A%5Ctext%7BLOD%7D_%7B%5Ctext%7Bnormal%7D%7D%20%26%3D%20%5Cmax_%7Bg_i%20%5Cin%20%5Ctext%7BGT%7D%7D%20%5Cleft%28%20%5Ctext%7BGL%7D%28g_0%29%20-%20%5Ctext%7BGL%7D%28g_i%29%20%5Cright%29%20%5Clabel%7Beq%3A01%7D%5C%5C%0A%5Ctext%7BLOD%7D_%7B%5Ctext%7Btumour%7D%7D%20%26%3D%20%5Cmin_%7Bs%20%5Cin%20%5Ctext%7BSamples%7D%7D%20%5Cleft%28%20%5Cmin_%7Bg_i%20%5Cin%20%5Ctext%7BGT%7D%7D%20%5Cleft%28%20%5Ctext%7BGL%7D_s%28g_i%29%20-%20%5Ctext%7BGL%7D_s%28g_0%29%20%5Cright%29%20%5Cright%29%20%5Clabel%7Beq%3A02%7D%5C%5C%0A%5Ctext%7BsomaticLOD%7D%20%26%20%3A%3D%20%5Cleft%28%20%5Ctext%7BLOD%7D_%7B%5Ctext%7Bnormal%7D%7D%20%5Cgeq%203.5%20%5Cland%20%5Ctext%7BLOD%7D_%7B%5Ctext%7Btumour%7D%7D%20%5Cgeq%203.5%20%5Cright%29%20%5Clabel%7Beq%3A03%7D%5Cend%7Baligned%7D "\begin{aligned}
\text{LOD}_{\text{normal}} &= \max_{g_i \in \text{GT}} \left( \text{GL}(g_0) - \text{GL}(g_i) \right) \label{eq:01}\\
\text{LOD}_{\text{tumour}} &= \min_{s \in \text{Samples}} \left( \min_{g_i \in \text{GT}} \left( \text{GL}_s(g_i) - \text{GL}_s(g_0) \right) \right) \label{eq:02}\\
\text{somaticLOD} & := \left( \text{LOD}_{\text{normal}} \geq 3.5 \land \text{LOD}_{\text{tumour}} \geq 3.5 \right) \label{eq:03}\end{aligned}")

Next, the variant allele frequencies (VAF) in both the tumour and the
normal samples are compared at each site.

![\\begin{aligned}
\\text{VAF}\_{\\text{tumour}} &= \\max\_{s \\in \\text{Samples}} ( \\text{VAF}\_s) \\label{eq:04}\\\\
\\text{somaticVAF} & := \\left( \\text{VAF}\_{\\text{normal}} \\leq 0.001 \~\\lor \\right. \\nonumber \\\\
 & \\left. ( \\text{VAF}\_{\\text{tumour}} \\geq 2.7 \\cdot \\text{VAF}\_{\\text{normal}}) \\right) \\label{eq:05}\\end{aligned}](https://latex.codecogs.com/png.latex?%5Cbegin%7Baligned%7D%0A%5Ctext%7BVAF%7D_%7B%5Ctext%7Btumour%7D%7D%20%26%3D%20%5Cmax_%7Bs%20%5Cin%20%5Ctext%7BSamples%7D%7D%20%28%20%5Ctext%7BVAF%7D_s%29%20%5Clabel%7Beq%3A04%7D%5C%5C%0A%5Ctext%7BsomaticVAF%7D%20%26%20%3A%3D%20%5Cleft%28%20%5Ctext%7BVAF%7D_%7B%5Ctext%7Bnormal%7D%7D%20%5Cleq%200.001%20~%5Clor%20%5Cright.%20%5Cnonumber%20%5C%5C%0A%20%26%20%5Cleft.%20%28%20%5Ctext%7BVAF%7D_%7B%5Ctext%7Btumour%7D%7D%20%5Cgeq%202.7%20%5Ccdot%20%5Ctext%7BVAF%7D_%7B%5Ctext%7Bnormal%7D%7D%29%20%5Cright%29%20%5Clabel%7Beq%3A05%7D%5Cend%7Baligned%7D "\begin{aligned}
\text{VAF}_{\text{tumour}} &= \max_{s \in \text{Samples}} ( \text{VAF}_s) \label{eq:04}\\
\text{somaticVAF} & := \left( \text{VAF}_{\text{normal}} \leq 0.001 ~\lor \right. \nonumber \\
 & \left. ( \text{VAF}_{\text{tumour}} \geq 2.7 \cdot \text{VAF}_{\text{normal}}) \right) \label{eq:05}\end{aligned}")

A variant is classified as somatic when both somaticLOD as well as
somatic VAF pass the criteria somaticLOD (Eq. 3) and somaticVAF (Eq. 5).

The thresholds chosen for both LOD and VAF calculations were previously
fitted by the blue-collar bioinformatics workflow for the DREAM
synthetic 3 dataset using the SpeedSeq likelihood difference approach
[@Chapman2020] and were selected to identify high confidence variants.

### Strelka2Pass workflow

In contrast to FreeBayes, whilst Strelka2 has a multiple-sample mode for
germline analysis and tumour-normal pair somatic variant calling
capabilities, it cannot jointly analyse multiple related tumour samples.
We enable this feature by adapting a two-pass strategy previously used
for RNA-seq data [@Veeneman2015]. First, somatic variants are called
from each tumour-normal pair. All detected variants across the cohort
are then used as input for the second pass of the analysis where we
re-iterate through each tumour-normal pair but assess allelic
information for all input genomic sites.

The method re-evaluates the likelihood of each variant, by integrating
every genotype from each tumour-normal pair. This step can \"call\" a
variant (![v](https://latex.codecogs.com/png.latex?v "v")) in a sample
that initially did not present enough evidence to pass the Strelka2
internal filtering using two conditions: 1) if this variant was called
as a proper \"PASS\" by Strelka2 in any other tumour sample, or 2) if
the integrated evidence for this variant across all tumour-normal pairs
reached a sufficiently high level. The second condition was based on the
somatic evidence score (SomEVS) reported by Strelka2, which is the
logarithm of the probability of the variant
![v](https://latex.codecogs.com/png.latex?v "v") being an artefact.

![p\_{error}(v) = 10\^{\\left( \\frac{-\\text{SomEVS}(v)}{10} \\right)} \\label{eq:06}](https://latex.codecogs.com/png.latex?p_%7Berror%7D%28v%29%20%3D%2010%5E%7B%5Cleft%28%20%5Cfrac%7B-%5Ctext%7BSomEVS%7D%28v%29%7D%7B10%7D%20%5Cright%29%7D%20%5Clabel%7Beq%3A06%7D "p_{error}(v) = 10^{\left( \frac{-\text{SomEVS}(v)}{10} \right)} \label{eq:06}")

While the germline sample is shared between all processes, we can
approximate these individual probabilities as being independent, since
one variant calling process is agnostic of the other. Hence, we derive
the following:

![p\_{error}(v\_{s_1},v\_{s_2},\\ldots,v\_{s_n}) = \\prod\_{s \\in \\text{Samples}} p\_{error}(v\_{s}) \\label{eq:07}](https://latex.codecogs.com/png.latex?p_%7Berror%7D%28v_%7Bs_1%7D%2Cv_%7Bs_2%7D%2C%5Cldots%2Cv_%7Bs_n%7D%29%20%3D%20%5Cprod_%7Bs%20%5Cin%20%5Ctext%7BSamples%7D%7D%20p_%7Berror%7D%28v_%7Bs%7D%29%20%5Clabel%7Beq%3A07%7D "p_{error}(v_{s_1},v_{s_2},\ldots,v_{s_n}) = \prod_{s \in \text{Samples}} p_{error}(v_{s}) \label{eq:07}")

And therefore:

![\\text{SomEVS}(v\_{s_1},v\_{s_2},\\ldots,v\_{s_n}) = \\sum\_{s \\in \\text{Samples}} \\text{SomEVS}(v\_{s}) \\label{eq:08}](https://latex.codecogs.com/png.latex?%5Ctext%7BSomEVS%7D%28v_%7Bs_1%7D%2Cv_%7Bs_2%7D%2C%5Cldots%2Cv_%7Bs_n%7D%29%20%3D%20%5Csum_%7Bs%20%5Cin%20%5Ctext%7BSamples%7D%7D%20%5Ctext%7BSomEVS%7D%28v_%7Bs%7D%29%20%5Clabel%7Beq%3A08%7D "\text{SomEVS}(v_{s_1},v_{s_2},\ldots,v_{s_n}) = \sum_{s \in \text{Samples}} \text{SomEVS}(v_{s}) \label{eq:08}")

This allows the summation (Eq. 8) of the SomEVS score across all
supporting variants to assign a \"PASS\" filter, if it reached a joint
SomEVS score threshold. This threshold can be set by the user and is 20
by default, which corresponds to an estimated error rate of 1%. These
\"recovered\" variants need to pass a set of additional quality metrics
related to depth of coverage, mapping quality and read position rank sum
score.

As an additional improvement, we also built multiallelic support into
Strelka2 which originally only reports the most prevalent variant at a
specific site. Within the two-pass analysis, we reconstruct the
available evidence for a multiallelic variant at a called site from the
allele-specific read counts and report the minor allele at this site, if
there is sufficient support from other samples. This method allows
recovery of minor alleles only if another sample has this variant called
by Strelka2, as SomEVS scores are not available for minor alleles.

## Validation

::: figure*
![image](Appendices/Variantcalling/Figure_1.pdf){width="\\textwidth"}
:::

### Simulated data

We first simulated a phylogeny with somatic and germline variants from
ten tumour samples and one normal (Fig. 1A, S1A, B) (Supplementary
methods). Germline variants were simulated at a uniform allele frequency
of ![0.5](https://latex.codecogs.com/png.latex?0.5 "0.5"). Somatic VAFs
were sampled from a custom distribution, modelled to favour low allele
frequency variants to closely represent real world data (min VAF:
![0.001](https://latex.codecogs.com/png.latex?0.001 "0.001"); max VAF:
![1](https://latex.codecogs.com/png.latex?1 "1"); Fig. S1C, D).
Paired-end sequencing reads with realistic error profiles were simulated
for WGS data at 160X average coverage using the ART-MountRainier
software [@Huang2011]. The simulated reads were aligned to GRCh38 and
both germline and somatic variants from the phylogeny were spiked into
the aligned reads using Bamsurgeon [@Ewing2015]. We compared the
workflows for FreeBayes and Strelka2 with and without our extensions for
joint variant calling on the simulated datasets. The performance of
Mutect2 joint variant calling was also assessed using its proposed best
practice workflow. As both Mutect2 and FreeBayes do not return a verdict
for each individual sample, we needed to assign each sample in the
multi-sample VCF its own FILTER value. We called a somatic variant as
present in a sample, if there were at least two reads supporting it for
this sample and the overall FILTER showed a "PASS", which was the same
cut-off used in the refiltering step in the Strelka2-pass workflow.

While the precision of each method without our extensions was greater
than
![99.8\\%](https://latex.codecogs.com/png.latex?99.8%5C%25 "99.8\%"),
they all missed at least 25% of all variants in the samples (i.e recall
![\\leq 75\\%](https://latex.codecogs.com/png.latex?%5Cleq%2075%5C%25 "\leq 75\%")).
In contrast, the recall of the modified workflows increased to
![\\approx 95\\%](https://latex.codecogs.com/png.latex?%5Capprox%2095%5C%25 "\approx 95\%")
with only a minute decrease in the precision for both FreeBayes and
Strelka2 (Fig. S2). Mutect2 however, had virtually no change in
precision, but the recall actually decreased from
![\\approx 75\\%](https://latex.codecogs.com/png.latex?%5Capprox%2075%5C%25 "\approx 75\%")
to
![\\approx 41\\%](https://latex.codecogs.com/png.latex?%5Capprox%2041%5C%25 "\approx 41\%")
when analysing the samples jointly (Fig. S2B). Additionally, with our
modified workflows, true positive variants were called with VAFs as low
as 0.008 (median detected VAF
![\\geq 0.14](https://latex.codecogs.com/png.latex?%5Cgeq%200.14 "\geq 0.14")
for joint sample analysis and
![\\geq 0.21](https://latex.codecogs.com/png.latex?%5Cgeq%200.21 "\geq 0.21")
for single tumour-normal pair analysis), enabling improved distinction
between true variants and technical errors (Fig. S3). This improvement
in performance for Strelka2 is only achieved after the refiltering step
and not just a result of the second pass (Fig. S4) (Supplementary
Methods).

The performance of joint variant calling in Mutect2 was inferior
compared to all other methods (Fig. S2A, B). This was primarily due to
the \"clustered_events\" filter in Mutect2, which excluded the majority
of false negative variants, with negligible contribution to the
exclusion of true negative variants (Fig. S5A, B). This result was
unexpected as the simulated variants were evenly distributed along the
genome and the corresponding allele frequencies were sampled randomly
(Fig. S1D).

Since the extent of the improvement in our joint calling workflows is
bound by the number of shared variants between samples, we sub-sampled
the simulated dataset, to show the effect of incomplete sampling on our
methods, which is more likely in clinical settings. Furthermore, the
evolutionary distance between the related samples in addition to the
number of samples, has a major impact on the number of shared variants,
as only variants acquired between the germline and the most recent
common ancestor (MRCA), will benefit from the joint analysis. Therefore,
we selected three sample subsets which included two, three and five
samples with high evolutionary distance to show the minimum expected
improvement (Fig. 1A, B). There was a clear linear improvement for both
FreeBayesSomatic and Strelka2Pass when increasing the number of samples
even if they had a distant evolutionary relationship. In contrast, when
using only two samples with a small evolutionary distance, the increase
in performance was almost as large as when jointly analysing all 10
available samples. This shows that samples with a high number of shared
variants will perform better in joint calling workflows (Fig. S6).

### Clinical data

To validate the performance of our new workflows, we then analysed WGS
and whole-exome sequencing (WES) data of multi-region tumour samples
from eight patients, with multiple tumour sites (average 7 samples per
patient; total number of samples 55), enrolled in a rapid autopsy
program conducted at the Peter MacCallum Cancer Centre (Table S1 and
Supplementary methods) [@Solomon2020; @Vergara2021]. The published
studies had multiple somatic variants from the clinical samples
orthogonally validated through targeted amplicon sequencing (TAS). We
used these TAS-validated variants as the gold standard to evaluate the
performance of different workflows, acknowledging that the technical
biases inherent to TAS data are different to those present in WGS and
WES (Fig. S7) and that there would be sampling biases depending on
different tumour cells analysed in each data type.

In concordance with the results of the simulated data, our improved
workflows found additional variants in all but one patient (Fig. 1D, S8)
(total additional variants Strelka2Pass:
![64](https://latex.codecogs.com/png.latex?64 "64"); FreeBayesSomatic:
![85](https://latex.codecogs.com/png.latex?85 "85")) with only a slight
drop in precision for FreeBayesSomatic (mean:
![0.94](https://latex.codecogs.com/png.latex?0.94 "0.94") vs.
![0.88](https://latex.codecogs.com/png.latex?0.88 "0.88")) and
Strelka2Pass (mean:
![0.97](https://latex.codecogs.com/png.latex?0.97 "0.97") vs.
![0.92](https://latex.codecogs.com/png.latex?0.92 "0.92")). Since the
panel of variants validated by TAS was limited
(![7108](https://latex.codecogs.com/png.latex?7108 "7108") bp for
patients CA-B through -H), this increase in detected variants suggests
that a high number of shared variants in samples are missed with current
approaches, which in turn leads to an overestimation of tumour
heterogeneity between samples, as these variants are thought to not be
present rather than undetected.

Even though the number of shared variants is a major influencing factor
when jointly calling variants, low cellularity samples benefit more from
the joint calling, as conventional methods cannot reliably distinguish
low allele frequency variants from noise. Through a joint analysis
approach, the number of recovered variants is higher in low cellularity
samples, which indicates, that especially for clinical samples with
variable tumour purity, joint analysis can have a major impact on
improving performance (Fig. 1E, S9).

Mutect2 in contrast, did not show significant improvement in any sample
in its joint calling configuration, but showed inferior performance
compared to the tumour-normal pairwise approach in two samples
(Fig. S8E), similar to its decreased performance in the simulated data
(Fig. S2). This was due to true variants being removed by the internal
filters of the tool (Fig. S5C, D). This is in stark contrast to our
novel workflows, where the joint analysis preserves all called sites
from the pairwise method and finds additional variants. Overall, Mutect2
found less validated variants in all patients than both Strelka2Pass
(mean: ![2.2](https://latex.codecogs.com/png.latex?2.2 "2.2")) and
FreeBayesSomatic (mean:
![2.5](https://latex.codecogs.com/png.latex?2.5 "2.5")) with comparable
levels of precision (Fig. S8, S10) but longer run times (Table S2).

Our improved workflow also enabled the discovery of multiallelic
variants with Strelka2, which led to the discovery of on average
![42](https://latex.codecogs.com/png.latex?42 "42") additional variants
(min: ![1](https://latex.codecogs.com/png.latex?1 "1"); max:
![535](https://latex.codecogs.com/png.latex?535 "535")) in the analysed
WES and ![987](https://latex.codecogs.com/png.latex?987 "987")
additional variants in the WGS (min:
![81](https://latex.codecogs.com/png.latex?81 "81"); max
![2329](https://latex.codecogs.com/png.latex?2329 "2329")). These
variants are strong indicators of sub clonal structure and could be
invaluable for the study of evolutionary trajectories in cancer.

## Discussion

Here we present an extension to two widely used variant callers,
enabling them to analyse multiple related tumour samples and improve the
sensitivity of detecting low allele frequency variants. This is highly
relevant in clinical settings where low tumour purities in samples is a
common occurrence. These workflows are an important step to satisfy the
current unmet need for multi-sample tumour variant calling. While we
have showcased their improvements in patient sequencing data, additional
validation on larger clinical datasets is warranted to ensure the
methodology performs robustly in real world settings. Importantly, these
workflows are fully containerised and can be run through Janis
[@Lupat2021] on almost any high-performance computing environment, as
well as cloud services. Each workflow is highly optimised and
parallelised to facilitate the analysis of the large amount of data
joint variant calling requires. The workflow specification also allows
the easy adjustment of parameters to enable customisation for the user's
needs and priorities, whereas building an ensemble workflow using
multiple callers is up to the discretion of the user (Fig. S11).

## Acknowledgements {#acknowledgements .unnumbered}

The authors would like to thank all patients who provided tissue samples
utilised in this study. The authors acknowledge Dr Lavinia Tan for
assistance provided with the collection of patient clinical samples.

## Funding {#funding .unnumbered}

This work was supported by the National Health and Medical Research
Council \[grant numbers 1196755 to S.J.D, 1158345 to S.J.D and B.J.S,
1194783 to S.Q.W, 1173450 to B.J.S\]; and CSL Centenary Fellowship to
S.J.D; Victorian Cancer Agency \[grant numbers 19008 to D.C, 19002 to
S.Q.W\]

## Conflicts of Interest {#conflicts-of-interest .unnumbered}

S.J.D has been a member of advisory boards for AstraZeneca and Inivata.
The S.J.D. lab has received funding from Cancer Therapeutics CRC and
Roche-Genentech. B.J.S. has been a member of advisory boards for
AstraZeneca, Roche-Genentech, Pfizer, Novartis, Amgen, Bristol Myers
Squibb and Merk

## Data availability {#data-availability .unnumbered}

The simulated data and the respective final variant calling files
underlying this article are available from Figshare at
[`https://melbourne.figshare.com`](https://melbourne.figshare.com), and
can be accessed with
[`https://doi.org/10.26188/13635186`](https://doi.org/10.26188/13635186)
for the dataset and
[`https://doi.org/10.26188/13635187`](https://doi.org/10.26188/13635187)
for the called variants.\
The biological data underlying this article are available at the
European Genome-Phenome Archive (EGA) at
[`https://ega-archive.org`](https://ega-archive.org), and can be
accessed with study id
[EGAS00001004023](https://ega-archive.org/studies/EGAS00001004023) and
[EGAS00001004950](https://ega-archive.org/studies/EGAS00001004950).

[\[Bibliography\]]{#Bibliography label="Bibliography"}
