This is the automated conversion from latex to markdown (mediawiki) with Pandoc, to get an idea what this is all about.

= Development of new methods for accurate estimation of tumour heterogeneity =
<div class="savequote">

“Begin at the beginning,“ the King said, very gravely, “and go on till you come to the end: then stop.“


</div>
= Introduction =

This first introduction chapter contains all the necessary background information as well as an overview for the work discussed in this thesis. It summarised basic biological properties of DNA and cell biology as well as the respective technologies to read, analyse and measure these biological concepts and then how to evaluate the output of these methods. [[#intro-sec:DNA|Section [[#intro-sec:DNA|1.1]]]] delineates the role DNA plays for the cell and then [[#intro-sec:ctDNA|section [[#intro-sec:ctDNA|1.2]]]] shows how these standards are changed in the tumour and cell free context. [[#intro-sec:sequencing|Section [[#intro-sec:sequencing|1.3]]]] introduces the current technologies used to measure and detect DNA and its variations. With [[#intro-sec:analysis|section [[#intro-sec:analysis|1.4]]]] covering the computational analysis methods to read out changes in the DNA. Then [[#intro-sec:lungcancer|section [[#intro-sec:lungcancer|1.5.1]]]] relates how these changes lead to cancer and what we can learn from them. The introduction concludes with [[#intro-sec:overview|section [[#intro-sec:overview|1.6]]]] as an overview over the thesis aims and my work in addressing them in the following chapters.

== DNA as a information storage unit ==

[[File:Figures/DNAStructure.png|thumb|none|alt=Overview of DNA structure and the nucleobases, which form DNA strands. Nucleotides are split into Purines and Pyrimidines by the structure of the nitrogen ring; complementary pairing of bases is shown as shapes of the bases as well as with 2D structures; Hyrdogen (H) bonds are shown as dotted lines; Phosphates are shown as P; 3’ and 5’ ends are defined by the internal number of the carbon atom of the sugar which is exposed; Adapted from “DNA structure“ by [https://biorender.com <code>BioRender.com</code>] (2021) Retrieved from [https://app.biorender.com/biorender-templates <code>https://app.biorender.com/biorender-templates</code>]|Overview of DNA structure and the nucleobases, which form DNA strands. Nucleotides are split into Purines and Pyrimidines by the structure of the nitrogen ring; complementary pairing of bases is shown as shapes of the bases as well as with 2D structures; Hyrdogen (H) bonds are shown as dotted lines; Phosphates are shown as P; 3’ and 5’ ends are defined by the internal number of the carbon atom of the sugar which is exposed; Adapted from “DNA structure“ by [https://biorender.com <code>BioRender.com</code>] (2021) Retrieved from [https://app.biorender.com/biorender-templates <code>https://app.biorender.com/biorender-templates</code>]]]

It is a widely accepted fact, that Deoxyribonucleic acid (DNA) serves as the long term information storage molecule of our cells. This information is protected and allows correction of simple errors through its double helix structure (Watson and Crick 1953; Liang et al. 1998). The nucleotides, which consist of a deoxyribose sugar (hence the name), a phosphate group and the nitrogenous base, are joined together by phosphate groups. Even though there are six common naturally occurring nitrogenous bases: Adenine (A), Thymine (T), Guanine (G), Cytosine (C), Uracil (U) and nicotinamide, only the first four are used to encode the genetic information into DNA. Each of the strands mirrors the other, so that an adenine will be paired up with a thymine forming two hydrogen bonds. Similarly cytosine will pair with guanine forming an even stronger bond with three hydrogen bonds. While other pairings which do not follow those rules are chemically possible, they are mostly observed in ribonucleic acid (RNA) (Sinden 1994). These very strict bonding rules enable the DNA to be similar to a hard drive with backup on a computer. And as only one strand contains all the information, the DNA polymerase enzyme does only need access to one strand, which allows parallel replication during cell division, but also error corrections, by proof reading the newly synthesised strand with the template. In order to be able to distinguish the two strands, they were assigned the names 3’ and 5’ depending on the numbering of the carbon atom in the sugar, which is exposed ().

The entirety of the DNA encoding the organism is commonly called “the genome“ with all genes, which consist of introns and exons are called exome. Unicellular organisms usually only have a very small amount of introns, which to current knowledge only provide limited information and are only responsible for structure. In vertebrates introns as well as intergeneic DNA (the DNA between genes) contribute most of the DNA in the genome. For example in humans, only <math display="inline">1\%</math> of the genetic material is considered to be exonic, whereas introns contribute <math display="inline">\approx 24\%</math> and the rest is intergeneic (<math display="inline">\approx 75\%</math>)(Venter et al. 2001).

[[File:Figures/ChromosomeStructure.png|thumb|none|alt=Structural overview of the metaphase condensed chromosome: DNA is first wrapped around Histones to form nucleosome, which then associate with each other to form the chromatin fiber, which in the metaphase of the cell cycle is condensed even more into the X-shaped chromosome|Structural overview of the metaphase condensed chromosome: DNA is first wrapped around Histones to form nucleosome, which then associate with each other to form the chromatin fiber, which in the metaphase of the cell cycle is condensed even more into the X-shaped chromosome]]

The DNA in eukaryotes however is not free floating around in the nucleus of a cell, but rather in most eukrayotic organisms, it is highly condensed and structured, first wrapped around nucleosomes like thread on a spool, then organised around histones, into either open (accessible) or closed chromatin, which then can be even further condensed into chromosomes, which have a X-like shape, with two shorter and two longer arms (). This allows some of the DNA to be accessible where the use of other areas can be restricted(Hammond et al. 2017). Through this restriction, the availability of certain genes, which are the sections of the DNA, which encode for short term storage molecules like RNA. This restriction plays an important role in cell fate and cell viability. Ultimately all information stored to create a new highly complex organism is stored in just the DNA of one cell. Whichever parts are used and how they are used decides the function and the identity of the cell(Bonev and Cavalli 2016).

=== Ploidy - its good to have a backup, if you do it right ===

Similar to the already discussed RAID-like setup of the DNA in two strands, another concept of data security, a spatial different storage is also implemented. Most eukaryotic organisms have at least two of each chromosome (diploid) with some species reaching up to septaploid(Tateoka 1975). However, this concept is not the only reason for the ploidy of somatic cells. For sexually reproducing organisms, at least a diploid set of chromosomes is necessary to enable information to be joined from both parents. Germline cells (sperm and egg) are generally monoploid, such that the resulting cell will be diploid, but the ploidy of the somatic cells is not as uniform within a species, where it can vary between organisms based on gender or rank (Trivers and Hare 1976). In most organisms, a change in ploidy is fatal (Otto 2007) and only partial ploidy changes like extra copies of chromosome 17 (Gottlieb et al. 1962), chromosome 18 (Cereda and Carey 2012) and chromosome 21 (Hultén et al. 2008) are tolerated. These syndroms can occur when the is an uneven split of chromosomes during cell division. The additional advantage, apart from sexual reproduction, is that a second almost identical copy of a chromosome allows repair of DNA, even when both strands are damaged, for example in a double strand break. In this case, the information from the sister chromosome will be used, by first cutting the double strand break ends to have overhang (resection). This overhang will then merge with the sister chromosome’s mirrored strand. In this state, the two chromosomes are fused together in a Holliday junction, which allows the missing part from the resection and the double strand break to be synthesised (Lilley 2000). During this process, which is part of the homology directed repair (HDR) machinery, the sister chromosomes exchange parts of their DNA, when resolving the Holliday junction. As these stretches of DNA do not need to be 100% identical, this plays and important role in evolution and diversity (Hanage, Fraser, and Spratt 2006; Kong et al. 2013).

[[File:Figures/ChromosomeTerritories.png|thumb|none|alt=Individual chromosomes occupy a subspace in the nucleus called chromosome territories. Chromosome territories can be further partitioned to distinct A and B compartments, which are enriched for active and repressed chromatin, respectively. Genomic regions within topologically associating domains (TADs) display increased interactions, while their interactions with neighbouring regions outside of the TADs are rather limited.|Individual chromosomes occupy a subspace in the nucleus called chromosome territories. Chromosome territories can be further partitioned to distinct A and B compartments, which are enriched for active and repressed chromatin, respectively. Genomic regions within topologically associating domains (TADs) display increased interactions, while their interactions with neighbouring regions outside of the TADs are rather limited.]]

Even though this X-like structure is the most commonly used and known structure, the DNAs 3D structure is usually very different and only takes this shape for the very short time of the cell cycle. Most of the time, the chromosomes are unravelled into something resembling a ball of yarn, where the “open“ chromatin regions are on the outside and the “closed“ regions are “hidden“ in the inside and each chromosome establishes its own “territory“ inside the nucleus (). This structure allows another DNA cross over with non-sister chromsomes, which is called a chiasma.

=== Phantastical mutations and where to find them ===

However even though the DNA is highly stable and error correction methods are constantly working to not introduce any changes in the DNA, the source of evolution and adaptation of species is sourced in a steady mutation rate (Darwin 2010; Sprouffske et al. 2018). These changes in normal tissue are mostly irrelevant to the organism as a whole and will not be passed on to the next generation. These changes are known as somatic mutations. This type of mutation accumulates in a cell linearly over the course of the lifespan of the cell and is not bound to just cell divisions(Alexandrov et al. 2015; Moore et al. 2021). In contrast, if one of those mutations occurs in the germline cell, eg. sperm or egg producing cells, these mutations will be propagated to all offspring and be present in all cells of that organism and in term all its offspring. These mutations are called germline mutations. These mutations are also called germline variants, as they establish in the population and represent a variation of the organism. Mutations can also be classified depending on either their size ranging from single nucleotide polymorphisms (SNPs) over small insertions or deletions (InDels) to large structural changes, like the deletion of parts of or even a whole chromosome arm. like previously described with ploidy changes, usually smaller changes have less impact on the overall fitness of the organism, however even SNPs can lead to changes which are not compatible with life(Shamseldin et al. 2015; Frey et al. 2021).

== Cell free DNA is more than just bits and pieces ==

When a cell from a multicellular organism dies, through which ever method, there will be many different enzymes involved, which clear the debris and recycle material. This means that proteases digest proteins into amino acids, which will later be used for either building new proteins or possibly even digested further for energy production. The same happens with the DNA in the cell. However as discussed in the previous section [[#intro-sec:DNA|1.1]] the DNA is wrapped around histones and organised in structures called nuclesomes. These protect the DNA from being cut by DNAases by hindering the access to the DNA, similar to how they stopped the access for transcription into RNA. This then in turn leads to the DNA being cut into pieces mainly in the length of 167 base pairs (bp). These DNA fragments, which are called cell free DNA (cfDNA), can then be detected in bodily fluids, like blood or even stool. By analysing these fragments, non invasive tests for prenatal care have been possible, as the DNA of the foetus is detectable in the mothers blood (Dan et al. 2012; Nicolaides et al. 2013). Similar to the process, a cancer also sheds DNA, titled circulating tumour DNA (ctDNA), when its cells die, either through intervention of the immune system or through other forcefull processes. These ctDNA fragments can also be analysed and molecular properties measured, without even knowing the exact location of the tumour. As a blood test can be routinely performed in the clinic or even a general practitioner, the monitoring of cancer progression is significantly easier and safer than through other measures. Of course it is, similar to the prenatal test, only a proxy for the cells which are still alive, as these have not shed their DNA. Additionally the amount of shedded DNA is highly variable between tumours, with a general higher amount for later stages, so that sometimes there is almost no ctDNA present, even though the cancer is fairly advanced (Diehl et al. 2008; Schwarzenbach, Hoon, and Pantel 2011).

== DNA sequencing - when is next generation sequencing the current generation? ==

As we know the building blocks, that make DNA as well as the process and the enzymes responsible, we can synthesise DNA in vitro. By chemically modifying the nucleotides supplied to the synthesis process, the sequence of the copied strand can be analysed. The first method to make use of this used the lambda phage to fuse known ends for the primers needed for the reaction to the piece of DNA and supplied labelled nucleotides (Padmanabhan, Jay, and Wu 1974).This method was then superseded by &quot;Sanger sequencing&quot; after Frederick Sanger who with colleagues published this method in 1977, by adding '''di'''deoxynucleotides in a low concentration, the polymerase chain reaction would terminate trying to integrate these nucleotides and by labelling them radioactively or flourecently, a gel can be used to determine the sequence of a piece of DNA (Sanger and Coulson 1975; Sanger, Nicklen, and Coulson 1977), which made the method better suited for larger scale projects.

However this method has multiple issues for modern research questions. Mostly, that it is fairly labour and time consuming to analyse multiple pieces of DNA at the same time and it is very challenging to sequence all the DNA of an organism. The human genome project, which was started in 1990 used machines which automated the Sanger sequencing procedure and it still took hundreds of researchers 13 years to complete the DNA sequence of just one human (Lander et al. 2001; Venter et al. 2001). Even though this was a very long project, it laid the ground work for the usage of the current sequencing technologies.

=== Library preparation - what we learned from using phages ===

[[File:Figures/LibraryPreparation.png|thumb|none|alt=Adapter ligation during library preparation. The adapters are added to the DNA insert during library preparation. A. The DNA insert is prepared by adding an A-tail and phosphorylation. B. The adapter complex which includes the P5/P7 flow cell binding adapter is added to the DNA insert. C. The DNA insert is ready for sequencing. D. The DNA insert binds to the flow cell for sequencing. Primers bind to the DNA insert to generate reads;<br />
Figure adapted from [https://sapac.support.illumina.com/bulletins/2020/12/how-short-inserts-affect-sequencing-performance.html &quot;How short inserts affect sequencing performance&quot;](Illumina 2020)|Adapter ligation during library preparation. The adapters are added to the DNA insert during library preparation. A. The DNA insert is prepared by adding an A-tail and phosphorylation. B. The adapter complex which includes the P5/P7 flow cell binding adapter is added to the DNA insert. C. The DNA insert is ready for sequencing. D. The DNA insert binds to the flow cell for sequencing. Primers bind to the DNA insert to generate reads;<br />
Figure adapted from [https://sapac.support.illumina.com/bulletins/2020/12/how-short-inserts-affect-sequencing-performance.html &quot;How short inserts affect sequencing performance&quot;](Illumina 2020)]]

Library preparation is the name of the preprocessing step, which is done before it is sequenced with the current technologies. The first step to sequence DNA is to obtain the DNA, which is done by lysing the cells of interest, which disrupts the cell membrane and therefore spills all its contents. The then spilled DNA is fragmented into smaller pieces, by either restriction enzymes or sonication, to have a size of about between 200-800bp. These steps are not necessary when preparing sequencing of ctDNA, as discussed in , the DNA is unbound and already digested into short fragments. Once the DNA is ready, it is both phosphorelated as well as an A-tail is added, before the adapter complex is ligated. This enabled the DNA to bind to the flow cell which is covered with the reverse complement of the adapter ().

=== Next generation sequencing ===

[[File:Figures/SequencingBySynthesis.jpg|thumb|none|alt=The Illumina sequencing-by-synthesis approach. Cluster strands created by bridge amplification are primed and all four fluorescently labeled, 3’-OH blocked nucleotides are added to the flow cell with DNA polymerase. The cluster strands are extended by one nucleotide. Following the incorporation step, the unused nucleotides and DNA polymerase molecules are washed away, a scan buffer is added to the flow cell, and the optics system scans each lane of the flow cell by imaging units called tiles. Once imaging is completed, chemicals that effect cleavage of the fluorescent labels and the 3’-OH blocking groups are added to the flow cell, which prepares the cluster strands for another round of fluorescent nucleotide incorporation; Figure adapted from Mardis (2008)(Mardis 2008)|The Illumina sequencing-by-synthesis approach. Cluster strands created by bridge amplification are primed and all four fluorescently labeled, 3’-OH blocked nucleotides are added to the flow cell with DNA polymerase. The cluster strands are extended by one nucleotide. Following the incorporation step, the unused nucleotides and DNA polymerase molecules are washed away, a scan buffer is added to the flow cell, and the optics system scans each lane of the flow cell by imaging units called tiles. Once imaging is completed, chemicals that effect cleavage of the fluorescent labels and the 3’-OH blocking groups are added to the flow cell, which prepares the cluster strands for another round of fluorescent nucleotide incorporation; Figure adapted from Mardis (2008)(Mardis 2008)]]

Next generation sequencing (NGS)is the coined term for basically any standard high-throughput sequencing performed, which includes exome, genome, transcriptome, protein-dna interactions (ChIP) and other epigenome studies. The term NGS is still widely used, even though it has been more than 10 years since the first NGS approach was commercially available. While in the beginning of next generation sequencing there were multiple approaches, the current lion share (80% of sequencing data) of protocols use the Illumina short read sequencing by synthesis approach ()(Mardis 2008; Straiton et al. 2019), which is based on the concept of alternating integration of florescently labelled nucleotides and imaging with a microscope () as well as multiplexing, where a DNA fragment is ligated to an index, which allows the sequencing of multiple samples at once (G. M. Church and Gilbert 1984; G. Church and Kieffer-Higgins 1988) as it is shown in . This method allows highly accurate determination of the sequence of a DNA fragment and depending on the flow cell and sequencing machine allows to sequence a whole genome in just 24h.

=== Long read sequencing - the &quot;third&quot; generation sequencing ===

By now, multiple methods which broke free of the size limitations of NGS exist, which are commonly referred to as long read sequencing. Most of the current methods trade the very high accuracy of the second generation NGS methods for the capability of sequencing of sequencing huge continous strands of DNA (current record 2.3 Million bp (Payne et al. 2018)) with normal library preparation ranging between 10-30 Kbp. These methods are expected to revolutionise our understanding of the highly repetitive elements that exist in the genome, such as the centromeres of chromosomes. Methods such as the direct molecule sequencing approach by Oxford Nanopore are even able to distinguish post transcriptional modifications on RNA(Pratanwanich et al. 2021). So far, these methods however are still very expensive and as this work is dealing with ctDNA, which is highly fragmented, these methods offer only limited advantages over the short read sequencing, while being much more expensive.

== DNA analysis- what to do with the sequence ==

The types of analysis that can be done with the output from the sequencing machine stretches far, however, all methods need to first infer the location in the genome, the sequenced piece of DNA originated from. As the current methods randomly fragment the DNA (), the genomic location information is completely lost. This process is referred to as mapping.

=== Mapping - Ey man, where is my genomic location? ===

In this process, the fragments of DNA, which were sequenced, are assigned a genomic coordinate on the reference genome. This is only possible, due to the fact, that we have a resolved genome sequences () for a high number of species. The location a sequenced piece of DNA fits to the reference genome might be unique, but it could also fit to multiple locations, due to highly repetitive regions or due to the existence of pseudo genes with almost 100% identify. In addition to this, the reference genome might not accurately reflect the genome of the organism that has been sequenced. Each mapping position is therefore assigned a quality score, which reflects how likely it is the actual position of the sequence. As Illumina sequencers have the ability to sequence both ends of the DNA fragment, the position of the ends (read 1 and read 2) to each other can also be used to infer the quality, as they should be within a reasonable distance to each other ()

As this process is time consuming and the exact location of the fragment might not be as important, there exists a subset of tools called pseudo-mapper, which are based on <math display="inline">k</math>-mers, which are predefined DNA sequences of length <math display="inline">k</math>, which help to identify certain regions of interest. These tools are especially common for RNAseq, where the exact location of a read doesnt matter, only that the read is within a gene (Bray et al. 2016; Patro et al. 2017), but also for methods that estimate similarity between sequences (DNA, RNA or protein) (Ondov et al. 2016; Luczak, James, and Girgis 2017).

For this work however, the exact position of reads is important, so only real mapping methods like BWA (Li 2013) or Bowtie 2 (Langmead et al. 2018), which are optimised for short reads from Illumina systems, provide the necessary functions.

=== Variant calling - spot the difference ===

As intra-species genetic variation is intended for adaptation and evolution, there will be places where the DNA sequence of the subject will differ from the sequence of the reference (see ). These variants give insight into medical background as well as treatment options for patients and can even be used to guide family planning. Depending on the type of variation that is of interest, a different set of computational methods are needed, as germline and somatic variants have different properties.

=== Germline variant calling - the cards you have been dealt at birth ===

The most common source of DNA used for germline variant analysis is the mono nuclear layer from the blood of the subject, but really almost any cell can be used for this process, as all cells in the organism will share all germline variants (). The only important input on top of the DNA sequence from the sequencer are the reference genome of the organism as all variant nomenclature is based on the reference and the ploidy of the organism (). The ploidy is important to infer, at which ranges of allele frequency a variant can biologically occur. For example in a human diploid genome, germline variants can occur either in one or both chromosomes, which mean we assume reads should show an allele frequency of around 50% and 100%, where the hexaploid commercial wheat (Mayer et al. 2014) allele frequency for variants would be 16%, 33%, 50%, 66%, 0.83% and 100%. Due to the random sampling and possible sequencing errors, however the observed allele frequencies will differ. Most state of the art germline variant calling method will also use haplotype reconstructions through de-Bruijn graphs, which features a remapping of reads in relation to each other (Garrison and Marth 2012; Lai et al. 2016; Kim et al. 2018; Benjamin et al. 2019; Cooke, Wedge, and Lunter 2021) where the original mapping location assigned by the aligner () is only used as a guideline. This allows to resolve even complex haplotypes of the sample by not restricting the method to the linear setup of the reference genome.

=== Somatic variant calling - life is ever changing ===

In contrast to germline variant calling, somatic variant calling methods cannot rely on allele frequency, as not all cells sequenced are expected to have the change in nucleotide. The allele frequency is instead a measure of the sub clonal size. A subclone is here defined as the set of cells, which were derived from the cell, which originally acquired the somatic mutation. Depending on the selective advantage, just random drift and also the time point when the variant was introduced, these clones can be very variable in size and therefore their contribution to the DNA in the sequencing. As not all cells have the variants, the selection of the tissue for library preparation is very important, unlike for germline calling. The main use of somatic variant calling is the genetic diagnosis and research of cancer samples, where the main question is, which changes are present in the tumour, which lead to the disease.

The ideal scenario for tumour somatic variant calling is when a biopsy of the tumour as well as a normal sample of the patient is available. In most clinical cases, this will be the diagnostic biopsy as well as the mono nuclear layer from blood, just like for germline calling (). This needs to be adjusted depending on the type of malignancy, because if the tumour is a leukemia, the mono nuclear layer of the blood might contain tumour cells, but for solid tumours, the blood is a routine, minimally invasive option. These two samples are then analysed together and only changes that are only in the somatic tumour sample and not in the normal sample are reported. Even though this concept sounds simple, there are some pitfalls (GATK Team 2021b). First of all, there might be some tumour contamination in the normal sample, which needs to be adjusted for (Kim et al. 2018; Taylor-Weiner et al. 2018). Second, there might be normal “contamination“ in the tumour sample, this means that not all cells in the tumour sample are actually tumour. This means that the signal of the tumour changes is reduced and harder to find.

All of these issues are amplified in the case, when there is no “normal“ sample available, either because the patient didnt consent, due to other medical issues, or because for diagnostic tests there usually is no need for a germline sample. In this case, there is the option for “tumour only“ variant calling, which requires a database of germline variants in the population, to distinguish between somatic and germline variants, as the variant calling is very similar to just germline variant calling () without the restriction of the ploidy. However, even with an extensive database like gnomAD (Karczewski et al. 2020) it is unlikely that is possible to remove all germline variants from the analysis and as there is no direct comparison, the precision of the “tumour only“ method is significantly lower (Karimnezhad et al. 2020).

== Cancer ==

While cancer is a massively heterogenous disease, as it can arise through a multitude of ways in almost any tissue, there are a some fundamental defining features, which most, if not all malignancies acquire, before they are truly cancers . The original characteristics comprise

<div class="enumerate*">

Sustaining proliferative signaling

Evading growth suppressors

Activating invastion and metastasis

Enabling replicative immortality

Inducing angiogenesis

Resisting cell death


</div>
(). These hallmarks were long considered the core of tumour development and the authors themselves hypothesised, that these core mechanics allow us to condense the complexity that cancer displays, both in the clinic as well as in labs, with a small set of rules, which all cancers have to obey (Hanahan and Weinberg 2000). In their exact words: “We foresee cancer research developing into a logical science, where the complexities of the disease, described in the laboratory and clinic, will become understandable in terms of a small number of underlying principles“

[[File:Figures/oldHallmarksCancer.jpg|thumb|none|alt=Acquired capabilities of cancer; Functional capabilities acquired by most cancers during their development; Figure adapted from Hanahan and Weinberg (2000)(Hanahan and Weinberg 2000)|Acquired capabilities of cancer; Functional capabilities acquired by most cancers during their development; Figure adapted from Hanahan and Weinberg (2000)(Hanahan and Weinberg 2000)]]

However, with 11 years of additional research into the topic, more hallmarks have been found and the original list was revised by the authors to contain additional characteristics, namely

<div class="enumerate*">

Avoiding immune destruction

Tumour-promoting inflamation

Genome instability and mutation

Deregulating cellular energetics


</div>
() (Hanahan and Weinberg 2011). And even then a few years later, even more hallmarks e.g. metabolic rewiring are now considered a part of the characteristics of cancer (Fouad and Aanei 2017).

[[File:Figures/newHallmarksCancer.jpg|thumb|none|alt=Emerging hallmarks and enabling characteristics of cancer; updated version of the hallmarks figure () with ; Figure adapted from Hanahan and Weinberg (2011)(Hanahan and Weinberg 2011)|Emerging hallmarks and enabling characteristics of cancer; updated version of the hallmarks figure () with ; Figure adapted from Hanahan and Weinberg (2011)(Hanahan and Weinberg 2011)]]

So while the original set of the hallmarks was not sufficient or complete, it offered a good attempt at abstraction of biological concepts to describe cancers. In the following pages, I will outline each of those hallmarks and how it influences my research.

==== Sustaining proliferative signaling - there are no breaks on the train ====

==== Evading growth suppressors ====

==== Activating invasion and metastasis - look at me... I am the organism now ====

==== Enabling replicative immortality ====

==== Inducing angiogenesis ====

==== Resisting cell death ====

=== Lungcancer ===

With around 1.6 million deaths world-wide each year, lung cancer is the number one cause of cancer death (Siegel, Miller, and Jemal 2018). Every year about twelve thousand Australians get diagnosed with lung cancer. These cases can be generally split into two groups: small cell lung cancers (SCLC) and non-small cell lung cancers (NSCLC), which account for around 15% and 85% of cases, respectively. The majority of NSCLC are either lung adenocarcinoma or lung squamous cell carcinoma (Molina et al. 2008). Even though smoking is highly associated with lung cancers, there is a big group of never smokers, with a high risk of lung cancers in East Asia, especially women, which is correlated with outside influences like pollution and occupational carcinogens and paired with genetic susceptibility (Sun, Schiller, and Gazdar 2007). This group usually shows ''EGFR'' (epidermal growth factor receptor) driven tumours. EGFR is a transmembrane receptor tyrosine kinase, which is usually only expressed in epithelial, mesenchymal, and neurogenic tissue, but its overexpression in other tissues is a hallmark of many human malignancies, not just NSCLC.

== Overview ==

<div class="savequote">

“It is the main source of our mistakes, when making making decision, that we only look at life piece by piece and not as a whole.“


</div>
= Joint somatic variant calling - if germline can do it, so can we =

== Introduction ==

When I started exploring the somatic variant calling methods in the beginning of my PhD in 2018, I was surprised about the stark difference between germline and somatic variant calling methods. Where all &quot;modern&quot; germline variant callers have the built-in capability to joint call multiple samples, for example from family trios, virtually no somatic variant caller had this function.

The joint analysis of smaller cohorts improves the performance of germline variant calling methods significantly, by allowing to assess technical artifacts, which might be unique for the individual sequencing machine or the researcher handling the DNA (Schirmer et al. 2016; Stoler and Nekrutenko 2021). As certain parts of the genome are more problematic to sequence () and map (), a “control“ sample can help to distinguish if a certain observed change occurs commonly, is a technical issue or in fact a real change.

For somatic variant calling, this concept has been adjusted in the genome analysis toolkit (GATK) (Brian O’Connor 2020) to allow the use of panel of normals (PON), which contains frequently seen changes in healthy (“normal“) individuals analysed with the same sequencing technology (GATK Team 2021a), but this is a post processing step of the analysis rather than a more intricate model like it is for the germline equivalent. Mutect2, which is the most recent somatic variant calling algorithm provided by the Broad institute, however also provides a multi-sample mode, for which all tumour samples need to be from the same patient, either longitudinal or spatial different (GATK Team 2020). This mode is hidden quite well and all tutorials published by the developers state that “there is currently no way to perform joint calling for somatic variant discovery“ (GATK Team 2021b), so while all methods in the GATK are considered a beta feature, this seems, that development is not a priority.

There are only two methods currently, which have documented and published capabilities to jointly analyse tumour samples from the same patient to call somatic variants. The first one is a specialised method built on a joint bayesian model for SNVs to occur in multiple samples called multiSNV (Josephidou, Lynch, and Tavaré 2015). However it has multiple shortcomings, which make it not useable for our data. First, as the name suggests, the method can only jointly evaluate SNVs and completely ignores indels and structural variants, which would be acceptable for the superior performance shown. However, multiSNV was optimised only for WES and not for the very deep WGS that is now available. This means exceptionally high runtimes. Even with custom parallelisation that was attempted in this work, the predicted runtime for just one multi sample patient would have been longer than 3 years. This again shows, that while multiSNV was a great step forward at the time, there is a real need for new methods to stem the tide of sequencing data available at low cost.

multiSNV has been the only software available for multi sample analysis, but only recently, during this work, superFreq (Flensburg et al. 2020) was published. It combines all standard analysis steps for tumour analysis, like variant calling or clonal deconvolution, into one program and is even able to jointly analyse samples. However similar to multiSNV, its focus when optimising and developing was on WES and RNAseq data, so when applied to our data, we could not find a server with enough memory to execute the workflow.

This then prompted us to investigate possible workflows to enable the analysis of high depth WGS, which we estimate to become more and more normal, with the ever dropping prices of sequencing. The following sections will first show the publication and then discusses additional analysis done after the the publication of the manuscript () and the impact of the joint analysis on downstream methods ().

== Publication ==

The publication about joint somatic variant calling can be found at [https://doi.org/10.1093/bioinformatics/btab606 <code>https://doi.org/10.1093/bioinformatics/btab606</code>] and non-journal formated version is also attached as .

== Effects on downstream analysis - not quite the missing link, but close ==

The ability to find additional shared variants has significant impact on our understanding of cancer evolution and the timing of initiation and metastatic seeding. Recent work has shown, that similar to the well known genetic heterogeneity, there is heterogeneity when it comes to metastatic seeding. While traditionally it was thought that tumours only metastesised after they reached a certain size, to escape the restrictions of the niche, like reduced nutrition, recent publications showed, there is also very early metastatic seeding (Hu et al. 2019). But all those methods are ultimately based on the somatic variants found in the data, so if we improve on the input of the downstream analysis methods, we can expect a clearer and possibly more granular result.

In this section I will highlight for a few examples on how big the effect can be for methods, like phylogenetic reconstruction and clonal decomposition, which use somatic variants as input.

=== Phylogenetic reconstruction ===

As this work is not about the advantages and shortcomings of different phylogenetic reconstruction tools, we will not show a comprehensive amount of these tools, but rather focus on the results. For this reason, we chose to use neighbour joining (NJ) (Saitou and Nei 1987), because it is fast, readily available in most phylogenetic reconstruction tool kits and if the input distance is correct, the output will be correct. And even, if the distance is not 100% correct, if the distance is “nearly additive“ and the input distances are not far off the real distance, the tree topology will still be reconstructed correctly (Mihaescu, Levy, and Pachter 2007). Lastly, in contrast to many other methods like UPGMA and WPGMA (Sokal and Michener 1958), NJ does not assume an equal mutation rate of each sample, because we know, that the molecular clock hypothesis (Zuckerkandl and Pauling 1962) is not valid for different lineages of cancers (Shibata 2010).

While there are lots of distance measures for DNA sequences, which allow accounting for different probabilities of transitions and transversions as well as uneven base composition, models like F81 (Felsenstein 1981) or HKY85 (Hasegawa, Kishino, and Yano 1985) are only really designed for germline mutations and are not easily applicable for subclonal somatic mutations, which is why we decided to first transform the variants present in all samples into a binary occurrence vector and then calculating the Hamming distance (Hamming 1950) between all samples. This generates a maximum parsimony approach and the branch length of the trees will be directly translatable to the amount of variants which are different between samples.

shows both the reconstructed phylogenies when using the variants found with the default tumour-normal method and our improved joint method and using the exact same reconstruction method otherwise.

[[File:Figures/phyloCA99.pdf|thumb|none|alt=Reconstructed phylogenies of a patient with multiple spatially distinct samples; Reconstruction method is neighbour joining for both cases, only the input of the called variants is different. Tip labels describe the location of the sample in the patient. Trees are shown as unrooted with germline as fixated origin point; black line ruler shows the length of an edge with 5000 mutations|Reconstructed phylogenies of a patient with multiple spatially distinct samples; Reconstruction method is neighbour joining for both cases, only the input of the called variants is different. Tip labels describe the location of the sample in the patient. Trees are shown as unrooted with germline as fixated origin point; black line ruler shows the length of an edge with 5000 mutations]]

There are several obvious changes, first, the longer edge connecting the the germline, which we consider as the state of no somatic variants, to all other samples. This shows that there are many more shared mutations in all samples, than what would have been anticipated with the default method. As the accumulation of somatic variants is still used as a proxy for timing and cell divisions, when assuming a high mutation rate for lung cancer (<math display="inline">5.3 \cdot 10^{-8}</math> from Werner et al. (2020) (Werner et al. 2020)) this difference of <math display="inline">\approx 36000</math> variants is equivalent to <math display="inline">\approx 2000</math> cell divisions. While the cell doubling rate of lung cancers is highly dependent on the type (Arai et al. 1994), this difference makes a huge difference when assessing the timing of the tumour initiation and further evolution.

Secondly, there have been topological changes, which generate a bifuricating edge between the warm coloured pleura, occipital, l-liver-2 and l-liver-5 samples, which fits significantly better with the clinical history and PET scans of the patient, as these are the sites of progression, which lead to the death of the patient in contrast to the earlier sites of disease.

shows a topology focused view of the two trees, which highlights the breaks which are needed to morph one tree into the other with dotted edges (Vienne 2018). The common subtrees are coloured the same on both sides and connecting lines show identical labels. This format shows that while the trees look quite similar at first glance, they show vastly different topologies.

[[File:Figures/tanglePhyloCA99.pdf|thumb|none|alt=Side by side view of the reconstructed trees from ; internal edges, which are distinct between trees are shown as dotted lines; common subtrees are shown in red and green; Tree labels have been sorted to minimise distance between labels; axis show the hamming distance between two nodes. Visualisation generated with dendextend (Galili 2015)|Side by side view of the reconstructed trees from ; internal edges, which are distinct between trees are shown as dotted lines; common subtrees are shown in red and green; Tree labels have been sorted to minimise distance between labels; axis show the hamming distance between two nodes. Visualisation generated with dendextend (Galili 2015)]]

One example of this is “l-liver-3“ which was a singleton, almost an outlier, in the pairwise reconstructed tree but is clustered together with “r-liver-2“ and “r-liver-3“. Generally, there have been additional changes, which make the topology more granular. Where all of the “l-liver-*“ samples were shown as an almost linear branching off the main stem, they are now further subdivided and each show distinct mutations, like “l-liver-2“ and “l-liver-5“ ().

== Longitudinal analysis - something for the ages  ==

While the initial motivation for the development of these workflows was the analysis of multi-region, so spatial, samples from the same patient coming from the CASCADE rapid autopsy program, a longitudinal application of these methods for the joint analysis of diagnostic and relapse sample, or even the repeated testing of ctDNA are quite worth thinking about. In this part, I will present work using the published workflows on a longitudinal datasets, which highlights the flexibility and wide spread use of our new methods.

Specifically, I will show the analysis of longitudinal ctDNA WES of patient “CA-F“ from the manuscript (). in a study of late stage melanoma patients, identified ctDNA sequencing as a way to stratify patients into high and low risk of relapse and therefore inform adjuvant therapy (Tan et al. 2019). In this analysis we aim to improve the quality of detection of low allele frequency somatic variants. This would enable the detection of variants from brains metastasis, as the blood brain barrier decreases the availability of DNA fragments from lesions in the brains in the normal blood stream (<span>“ctDNA Is a Specific and Sensitive Biomarker in Multiple Human Cancers.”</span> 2014), however it is detectable with sensitive enough methods (Yoon et al. 2019; Ma et al. 2020).

=== Clonal deconvolution ===

Finally, the holy grail of analysis of multiple related samples from the same patient is the clonal deconvolution, where subclonal reoccurring patterns of mutations are detected. These can be linked to either parallel evolution through positive selection pressure, like a targeted drug or to the process of developing Metastases where a piece of the cancer “breaks“ off and grows at a different site. Surprisingly, as it shares the same issues as the joint somatic variant calling of needing deeply sequenced data from multiple samples of the same organism, there is a plethora of algorithms and methods available for clonal deconvolution. Since 2015 PhyloWGS (Deshwar et al. 2015), Canopy (Jiang et al. 2016), CLOE (Marass et al. 2016), CloneFinder (Miura et al. 2018), Machina (El-Kebir, Satas, and Raphael 2018) and MOBSTER (Caravagna et al. 2020). Underlying these models is a form of clustering variants with similar variant allele frequency together, to reduce the combinatorial space and enhance the confidence in the signal (Tarabichi et al. 2021). However even though there is a high number of tools, the challenge to select the right tool is substantial, especially since all of them have up and downsides (Miura et al. 2020). In this work we decided to use PhylogicNDT (Leshchiner et al. 2018) as it has been shown to work well on clinical samples (Gerstung et al. 2020) and does not have the restriction for the input to be from copy number neutral areas which many of the other tools have.

The analysis was conducted by transforming the variants called with the joint workflows as well as the default pairwise analysis into the required MAF file format without the cancer cell fraction part, in order to let PhylogicNDT calculate those on the fly. The local copy numbers for each variants are generated by intersecting the called segments from sequenza with the position of the variants. Variants which could not be assigned a local copy number change were discarded from the analysis.

[[File:Figures/clonalDeconv.pdf|thumb|none|alt=Reconstructed clonal trees from PhylogicNDT; Blue circle at top depicts the germline/normal state. The coloured edges with the same coloured circle represents a distinct subclone of the parent from which the edge emerges; The number in braces next to the edge is the number of mutations which define this subclone with an added gene symbol added, if there is a cancer driver gene mutation. The left part shows the result when using the default pairwise method of Strelka2 and the right side uses the results from the Strelka2Pass workflow|Reconstructed clonal trees from PhylogicNDT; Blue circle at top depicts the germline/normal state. The coloured edges with the same coloured circle represents a distinct subclone of the parent from which the edge emerges; The number in braces next to the edge is the number of mutations which define this subclone with an added gene symbol added, if there is a cancer driver gene mutation. The left part shows the result when using the default pairwise method of Strelka2 and the right side uses the results from the Strelka2Pass workflow]]

shows the highest parsimony clonal tree reconstructed by PhylogicNDT for the pairwise as well as the joint variant calling. As the copynumber calling information is the same for both inputs, the only difference is in the called variants. While there was no subclonal structure detected at all for the pairwise analysis, there is a highly variable structure detected using the jointly called variants.

== Usage - its not just me that thinks it is good ==

As published software is amazing, its real value is in the re-usability and portability. Many published software packages are not maintained or not even functional even though they are published. While I developed these joint somatic variant calling workflows to deal with a challenge I faced, many other people even just at the same institute have already shown interest and some research groups are already using the software to analyse their multi-sample data.

[[File:Figures/dawsontoolkitDownloads.pdf|thumb|none|alt=Cumulative download numbers of the “dawsontoolkit“ docker container since publication of the manuscript; Actual counts are shown as dots, with smoothed trajectory depicted as dotted line with the 95% confidence interval shown as a grey background; confidence interval has been adjusted with exponential decay of prediction accuracy with distance from the last data point; Start date 7<math display="inline">^{th}</math> September 2021|Cumulative download numbers of the “dawsontoolkit“ docker container since publication of the manuscript; Actual counts are shown as dots, with smoothed trajectory depicted as dotted line with the 95% confidence interval shown as a grey background; confidence interval has been adjusted with exponential decay of prediction accuracy with distance from the last data point; Start date 7<math display="inline">^{th}</math> September 2021]]

To have some proxy of the usage statistics of the workflows, I recorded the download numbers of the “dawsontoolkit“ docker container, which only contains software for refiltering and joint analysis of the workflows after the publication of the manuscript. Obviously, this is an imperfect measurement, as people can reuse a downloaded container as often as they want, which would not appear in the count and similarly, just because the container was downloaded, the analysis might not have been used. However it still shows an interaction and an interest in the methods. The download numbers show a quick increase in numbers in the beginning, just after the publication, followed by a short plateau but then another increase (). This suggests, that there is a need in the methods, rather than a simple curiosity after publication.

<div class="savequote">

“Death is a release from and an end of all pains: beyond it our sufferings cannot extend: it restores us to the peaceful rest in which we lay before we were born“


</div>
= CASCADE - Late stage lung cancer in the spotlight =

== Introduction ==

== Publication ==

This chapter includes the data analysis for two two publications. The first publication features the resistance mechanism of small cell transformation ([https://doi.org/10.1016/j.ccell.2019.08.008 <code>https://doi.org/10.1016/j.ccell.2019.08.008</code>](Burr et al. 2019)) and the second shows the discovery of resistance to a targeted RET-fusion driven cancer ([https://doi.org/10.1016/j.jtho.2020.01.006 <code>https://doi.org/10.1016/j.jtho.2020.01.006</code>](Solomon et al. 2020))

== Cohort analysis ==

== Mitochondrial phylogenetic reconstruction - the power house of the phylogenies ==

== Outlook ==

<div class="savequote">

“Many a mickle makes a muckle.“


</div>
= MisMatchFinder - hope springs eternal =

== Introduction ==

<div class="savequote">

“As you think, so you become. Our busy minds are forever jumping to conclusions, manufacturing and interpreting signs that aren’t there.“


</div>
= Conclusion =

= Custom workflows to improve joint variant calling from multiple related tumour samples: FreeBayesSomatic and Strelka2Pass =

This appendix contains the manuscript published at ''Bioinformatics'' in an non journal style format. It can also be found at [https://doi.org/10.1093/bioinformatics/btab606/6361543 10.1093/bioinformatics/btab606/6361543] for a paper style version.


-----

<span>'''Hollizeck S.<math display="inline">^{1,2}</math>, Wong S.Q.<math display="inline">^{1,2}</math>, Solomon B.<math display="inline">^{1,2}</math>, Chandrananda D.<math display="inline">^{1,2}</math>, and Dawson S-J.<math display="inline">^{1,2,3,*}</math>'''</span>

<span> <math display="inline">^1</math> Peter MacCallum Cancer Centre, Melbourne 3000, Victoria, Australia<br />
<math display="inline">^2</math> Sir Peter MacCallum Department of Oncology, University of Melbourne, Melbourne 3000, Victoria, Australia<br />
<math display="inline">^3</math> Centre for Cancer Research, University of Melbourne, Melbourne 3000, Victoria, Australia<br />
<math display="inline">^*</math> D.C and S.J.D are co-senior authors and contributed equally to this article </span>

<span> Received on 27-Jan-2021; revised on 13-Jul-2021; accepted on 12-Aug-2021 </span>

<span>'''Abstract'''</span>

===== '''Summary:''' =====

This work describes two novel workflows for variant calling that extend the widely used algorithms of Strelka2 and FreeBayes to call somatic mutations from multiple related tumour samples and one matched normal sample. We show that these workflows offer higher precision and recall than their single tumour-normal pair equivalents in both simulated and clinical sequencing data.

===== '''Availability and Implementation:''' =====

Source code freely available at the following link: [https://atlassian.petermac.org.au/bitbucket/projects/DAW/repos/multisamplevariantcalling <code>https://atlassian.petermac.org.au/bitbucket/projects/DAW/repos/multisamplevariantcalling</code>] and executable through Janis ([https://github.com/PMCC-BioinformaticsCore/janis <code>https://github.com/PMCC-BioinformaticsCore/janis</code>]) under the GPLv3 licence.

===== '''Contact:''' =====

[[Dineika.Chandrananda@petermac.org|Dineika.Chandrananda@petermac.org]], [[Sarah-Jane.Dawson@petermac.org|Sarah-Jane.Dawson@petermac.org]]

===== '''Supplementary information:''' =====

Supplementary data are available at ''Bioinformatics'' online.

== Introduction ==

Joint variant calling methods are routinely used to call germline variants by leveraging population-wide information across multiple related samples (DePristo et al. 2011; Toptaş et al. 2018). This concept is also advantageous for somatic variant calling to potentially overcome the challenges of spatial heterogeneity and low tumour purity. However, there is a critical lack of robust algorithms that allow multi-sample somatic calling. Most studies still rely on variant calling of separate tumour-normal pairs, subsequently combining the results across a sample cohort (Hu et al. 2019; Leong et al. 2018; Wang et al. 2018).

There are two major pitfalls for combining variants called from individual tumour samples. First, it is very difficult to differentiate between a false negative result due to &quot;missing data&quot; versus the true absence of a variant. Second, there is limited sensitivity for low allele frequency variants thus, decreasing the ability to detect minor clones, particularly in samples with low tumour purity.

Currently, only three algorithms claim to have the functionality to jointly analyse multiple samples: multiSNV (Josephidou, Lynch, and Tavaré 2015), SuperFreq (Flensburg et al. 2020), and Mutect2 (Benjamin et al. 2019), each presenting different limitations. For instance, multiSNV cannot call indels and along with SuperFreq, is not optimised for analysis of deep coverage whole-genome sequencing (WGS) data. Mutect2 has previously been shown to be disadvantageously conservative as well as computationally inefficient (Chen et al. 2020).

To enable highly sensitive, fast and accurate variant detection from multiple related tumour samples, we have developed joint variant calling extensions to two widely used single-sample algorithms, FreeBayes (Garrison and Marth 2012) and Strelka2 (Kim et al. 2018). Using both simulated and clinical sequencing data, we show that these workflows are highly accurate and can detect variants at much lower variant allele frequencies than commonly used methods.

== Materials and methods ==

=== FreeBayesSomatic workflow ===

The original FreeBayes algorithm can jointly evaluate multiple samples but routinely it does not perform somatic variant calling on tumour-normal pairs. We introduce FreeBayesSomatic which allows concurrent analysis of multiple tumour samples by adapting concepts from SpeedSeq (Chiang et al. 2015) which differentiates the likelihood of a variant between tumour and normal samples instead of imposing an absolute filter for all variants called in the normal. Hence, for each genotype (GT) at SNV sites, FreeBayesSomatic first calculates the difference in likelihoods (LOD) between the normal (Eq. 1) and the tumour (Eq. 2) samples genotype likelihoods (GL) with g<math display="inline">_{0}</math> describing the reference genotype.

<math display="block">\begin{aligned}
\text{LOD}_{\text{normal}} &= \max_{g_i \in \text{GT}} \left( \text{GL}(g_0) - \text{GL}(g_i) \right) \label{eq:01}\\
\text{LOD}_{\text{tumour}} &= \min_{s \in \text{Samples}} \left( \min_{g_i \in \text{GT}} \left( \text{GL}_s(g_i) - \text{GL}_s(g_0) \right) \right) \label{eq:02}\\
\text{somaticLOD} & := \left( \text{LOD}_{\text{normal}} \geq 3.5 \land \text{LOD}_{\text{tumour}} \geq 3.5 \right) \label{eq:03}\end{aligned}</math>

Next, the variant allele frequencies (VAF) in both the tumour and the normal samples are compared at each site.

<math display="block">\begin{aligned}
\text{VAF}_{\text{tumour}} &= \max_{s \in \text{Samples}} ( \text{VAF}_s) \label{eq:04}\\
\text{somaticVAF} & := \left( \text{VAF}_{\text{normal}} \leq 0.001 ~\lor \right. \nonumber \\
 & \left. ( \text{VAF}_{\text{tumour}} \geq 2.7 \cdot \text{VAF}_{\text{normal}}) \right) \label{eq:05}\end{aligned}</math>

A variant is classified as somatic when both somaticLOD as well as somatic VAF pass the criteria somaticLOD (Eq. 3) and somaticVAF (Eq. 5).

The thresholds chosen for both LOD and VAF calculations were previously fitted by the blue-collar bioinformatics workflow for the DREAM synthetic 3 dataset using the SpeedSeq likelihood difference approach (Chapman et al. 2021) and were selected to identify high confidence variants.

=== Strelka2Pass workflow ===

In contrast to FreeBayes, whilst Strelka2 has a multiple-sample mode for germline analysis and tumour-normal pair somatic variant calling capabilities, it cannot jointly analyse multiple related tumour samples. We enable this feature by adapting a two-pass strategy previously used for RNA-seq data (Veeneman et al. 2015). First, somatic variants are called from each tumour-normal pair. All detected variants across the cohort are then used as input for the second pass of the analysis where we re-iterate through each tumour-normal pair but assess allelic information for all input genomic sites.

The method re-evaluates the likelihood of each variant, by integrating every genotype from each tumour-normal pair. This step can &quot;call&quot; a variant (<math display="inline">v</math>) in a sample that initially did not present enough evidence to pass the Strelka2 internal filtering using two conditions: 1) if this variant was called as a proper &quot;PASS&quot; by Strelka2 in any other tumour sample, or 2) if the integrated evidence for this variant across all tumour-normal pairs reached a sufficiently high level. The second condition was based on the somatic evidence score (SomEVS) reported by Strelka2, which is the logarithm of the probability of the variant <math display="inline">v</math> being an artefact.

<math display="block">p_{error}(v) = 10^{\left( \frac{-\text{SomEVS}(v)}{10} \right)} \label{eq:06}</math>

While the germline sample is shared between all processes, we can approximate these individual probabilities as being independent, since one variant calling process is agnostic of the other. Hence, we derive the following:

<math display="block">p_{error}(v_{s_1},v_{s_2},\ldots,v_{s_n}) = \prod_{s \in \text{Samples}} p_{error}(v_{s}) \label{eq:07}</math>

And therefore:

<math display="block">\text{SomEVS}(v_{s_1},v_{s_2},\ldots,v_{s_n}) = \sum_{s \in \text{Samples}} \text{SomEVS}(v_{s}) \label{eq:08}</math>

This allows the summation (Eq. 8) of the SomEVS score across all supporting variants to assign a &quot;PASS&quot; filter, if it reached a joint SomEVS score threshold. This threshold can be set by the user and is 20 by default, which corresponds to an estimated error rate of 1%. These &quot;recovered&quot; variants need to pass a set of additional quality metrics related to depth of coverage, mapping quality and read position rank sum score.

As an additional improvement, we also built multiallelic support into Strelka2 which originally only reports the most prevalent variant at a specific site. Within the two-pass analysis, we reconstruct the available evidence for a multiallelic variant at a called site from the allele-specific read counts and report the minor allele at this site, if there is sufficient support from other samples. This method allows recovery of minor alleles only if another sample has this variant called by Strelka2, as SomEVS scores are not available for minor alleles.

== Validation ==

<div class="figure*">

[[File:Appendices/Variantcalling/Figure_1.pdf|image]]


</div>
=== Simulated data ===

We first simulated a phylogeny with somatic and germline variants from ten tumour samples and one normal (Fig. 1A, S1A, B) (Supplementary methods). Germline variants were simulated at a uniform allele frequency of <math display="inline">0.5</math>. Somatic VAFs were sampled from a custom distribution, modelled to favour low allele frequency variants to closely represent real world data (min VAF: <math display="inline">0.001</math>; max VAF: <math display="inline">1</math>; Fig. S1C, D). Paired-end sequencing reads with realistic error profiles were simulated for WGS data at 160X average coverage using the ART-MountRainier software (Huang et al. 2011). The simulated reads were aligned to GRCh38 and both germline and somatic variants from the phylogeny were spiked into the aligned reads using Bamsurgeon (Ewing et al. 2015). We compared the workflows for FreeBayes and Strelka2 with and without our extensions for joint variant calling on the simulated datasets. The performance of Mutect2 joint variant calling was also assessed using its proposed best practice workflow. As both Mutect2 and FreeBayes do not return a verdict for each individual sample, we needed to assign each sample in the multi-sample VCF its own FILTER value. We called a somatic variant as present in a sample, if there were at least two reads supporting it for this sample and the overall FILTER showed a “PASS“, which was the same cut-off used in the refiltering step in the Strelka2-pass workflow.

While the precision of each method without our extensions was greater than <math display="inline">99.8\%</math>, they all missed at least 25% of all variants in the samples (i.e recall <math display="inline">\leq 75\%</math>). In contrast, the recall of the modified workflows increased to <math display="inline">\approx 95\%</math> with only a minute decrease in the precision for both FreeBayes and Strelka2 (Fig. S2). Mutect2 however, had virtually no change in precision, but the recall actually decreased from <math display="inline">\approx 75\%</math> to <math display="inline">\approx 41\%</math> when analysing the samples jointly (Fig. S2B). Additionally, with our modified workflows, true positive variants were called with VAFs as low as 0.008 (median detected VAF <math display="inline">\geq 0.14</math> for joint sample analysis and <math display="inline">\geq 0.21</math> for single tumour-normal pair analysis), enabling improved distinction between true variants and technical errors (Fig. S3). This improvement in performance for Strelka2 is only achieved after the refiltering step and not just a result of the second pass (Fig. S4) (Supplementary Methods).

The performance of joint variant calling in Mutect2 was inferior compared to all other methods (Fig. S2A, B). This was primarily due to the &quot;clustered_events&quot; filter in Mutect2, which excluded the majority of false negative variants, with negligible contribution to the exclusion of true negative variants (Fig. S5A, B). This result was unexpected as the simulated variants were evenly distributed along the genome and the corresponding allele frequencies were sampled randomly (Fig. S1D).

Since the extent of the improvement in our joint calling workflows is bound by the number of shared variants between samples, we sub-sampled the simulated dataset, to show the effect of incomplete sampling on our methods, which is more likely in clinical settings. Furthermore, the evolutionary distance between the related samples in addition to the number of samples, has a major impact on the number of shared variants, as only variants acquired between the germline and the most recent common ancestor (MRCA), will benefit from the joint analysis. Therefore, we selected three sample subsets which included two, three and five samples with high evolutionary distance to show the minimum expected improvement (Fig. 1A, B). There was a clear linear improvement for both FreeBayesSomatic and Strelka2Pass when increasing the number of samples even if they had a distant evolutionary relationship. In contrast, when using only two samples with a small evolutionary distance, the increase in performance was almost as large as when jointly analysing all 10 available samples. This shows that samples with a high number of shared variants will perform better in joint calling workflows (Fig. S6).

=== Clinical data ===

To validate the performance of our new workflows, we then analysed WGS and whole-exome sequencing (WES) data of multi-region tumour samples from eight patients, with multiple tumour sites (average 7 samples per patient; total number of samples 55), enrolled in a rapid autopsy program conducted at the Peter MacCallum Cancer Centre (Table S1 and Supplementary methods) (Solomon et al. 2020; Vergara et al. 2021). The published studies had multiple somatic variants from the clinical samples orthogonally validated through targeted amplicon sequencing (TAS). We used these TAS-validated variants as the gold standard to evaluate the performance of different workflows, acknowledging that the technical biases inherent to TAS data are different to those present in WGS and WES (Fig. S7) and that there would be sampling biases depending on different tumour cells analysed in each data type.

In concordance with the results of the simulated data, our improved workflows found additional variants in all but one patient (Fig. 1D, S8) (total additional variants Strelka2Pass: <math display="inline">64</math>; FreeBayesSomatic: <math display="inline">85</math>) with only a slight drop in precision for FreeBayesSomatic (mean: <math display="inline">0.94</math> vs. <math display="inline">0.88</math>) and Strelka2Pass (mean: <math display="inline">0.97</math> vs. <math display="inline">0.92</math>). Since the panel of variants validated by TAS was limited (<math display="inline">7108</math> bp for patients CA-B through -H), this increase in detected variants suggests that a high number of shared variants in samples are missed with current approaches, which in turn leads to an overestimation of tumour heterogeneity between samples, as these variants are thought to not be present rather than undetected.

Even though the number of shared variants is a major influencing factor when jointly calling variants, low cellularity samples benefit more from the joint calling, as conventional methods cannot reliably distinguish low allele frequency variants from noise. Through a joint analysis approach, the number of recovered variants is higher in low cellularity samples, which indicates, that especially for clinical samples with variable tumour purity, joint analysis can have a major impact on improving performance (Fig. 1E, S9).

Mutect2 in contrast, did not show significant improvement in any sample in its joint calling configuration, but showed inferior performance compared to the tumour-normal pairwise approach in two samples (Fig. S8E), similar to its decreased performance in the simulated data (Fig. S2). This was due to true variants being removed by the internal filters of the tool (Fig. S5C, D). This is in stark contrast to our novel workflows, where the joint analysis preserves all called sites from the pairwise method and finds additional variants. Overall, Mutect2 found less validated variants in all patients than both Strelka2Pass (mean: <math display="inline">2.2</math>) and FreeBayesSomatic (mean: <math display="inline">2.5</math>) with comparable levels of precision (Fig. S8, S10) but longer run times (Table S2).

Our improved workflow also enabled the discovery of multiallelic variants with Strelka2, which led to the discovery of on average <math display="inline">42</math> additional variants (min: <math display="inline">1</math>; max: <math display="inline">535</math>) in the analysed WES and <math display="inline">987</math> additional variants in the WGS (min: <math display="inline">81</math>; max <math display="inline">2329</math>). These variants are strong indicators of sub clonal structure and could be invaluable for the study of evolutionary trajectories in cancer.

== Discussion ==

Here we present an extension to two widely used variant callers, enabling them to analyse multiple related tumour samples and improve the sensitivity of detecting low allele frequency variants. This is highly relevant in clinical settings where low tumour purities in samples is a common occurrence. These workflows are an important step to satisfy the current unmet need for multi-sample tumour variant calling. While we have showcased their improvements in patient sequencing data, additional validation on larger clinical datasets is warranted to ensure the methodology performs robustly in real world settings. Importantly, these workflows are fully containerised and can be run through Janis (Lupat et al. 2021) on almost any high-performance computing environment, as well as cloud services. Each workflow is highly optimised and parallelised to facilitate the analysis of the large amount of data joint variant calling requires. The workflow specification also allows the easy adjustment of parameters to enable customisation for the user’s needs and priorities, whereas building an ensemble workflow using multiple callers is up to the discretion of the user (Fig. S11).

== Acknowledgements ==

The authors would like to thank all patients who provided tissue samples utilised in this study. The authors acknowledge Dr Lavinia Tan for assistance provided with the collection of patient clinical samples.

== Funding ==

This work was supported by the National Health and Medical Research Council [grant numbers 1196755 to S.J.D, 1158345 to S.J.D and B.J.S, 1194783 to S.Q.W, 1173450 to B.J.S]; and CSL Centenary Fellowship to S.J.D; Victorian Cancer Agency [grant numbers 19008 to D.C, 19002 to S.Q.W]

== Conflicts of Interest ==

S.J.D has been a member of advisory boards for AstraZeneca and Inivata. The S.J.D. lab has received funding from Cancer Therapeutics CRC and Roche-Genentech. B.J.S. has been a member of advisory boards for AstraZeneca, Roche-Genentech, Pfizer, Novartis, Amgen, Bristol Myers Squibb and Merk

== Data availability ==

The simulated data and the respective final variant calling files underlying this article are available from Figshare at [https://melbourne.figshare.com <code>https://melbourne.figshare.com</code>], and can be accessed with [https://doi.org/10.26188/13635186 <code>https://doi.org/10.26188/13635186</code>] for the dataset and [https://doi.org/10.26188/13635187 <code>https://doi.org/10.26188/13635187</code>] for the called variants.<br />
The biological data underlying this article are available at the European Genome-Phenome Archive (EGA) at [https://ega-archive.org <code>https://ega-archive.org</code>], and can be accessed with study id [https://ega-archive.org/studies/EGAS00001004023 EGAS00001004023] and [https://ega-archive.org/studies/EGAS00001004950 EGAS00001004950].

<span id="Bibliography" label="Bibliography">[Bibliography]</span>

<div id="refs" class="references csl-bib-body hanging-indent">

<div id="ref-Alexandrov2015" class="csl-entry">

Alexandrov, Ludmil B, Philip H Jones, David C Wedge, Julian E Sale, Peter J Campbell, Serena Nik-Zainal, and Michael R Stratton. 2015. <span>“Clock-Like Mutational Processes in Human Somatic Cells.”</span> ''Nature Genetics'' 47 (12): 1402–7. https://doi.org/10.1038/ng.3441.


</div>
<div id="ref-Arai1994" class="csl-entry">

Arai, T., T. Kuroishi, Y. Saito, Y. Kurita, T. Naruke, and M. Kaneko. 1994. <span>“[https://www.ncbi.nlm.nih.gov/pubmed/8072198 Tumor Doubling Time and Prognosis in Lung Cancer Patients: Evaluation from Chest Films and Clinical Follow-up Study].”</span> ''Japanese Journal of Clinical Oncology'' 24 (August): 199–204.


</div>
<div id="ref-Benjamin2019" class="csl-entry">

Benjamin, David, Takuto Sato, Kristian Cibulskis, Gad Getz, Chip Stewart, and Lee Lichtenstein. 2019. <span>“Calling Somatic <span>SNVs</span> and Indels with Mutect2.”</span> ''bioRxiv'', December. https://doi.org/10.1101/861054.


</div>
<div id="ref-Bonev2016" class="csl-entry">

Bonev, Boyan, and Giacomo Cavalli. 2016. <span>“Organization and Function of the 3d Genome.”</span> ''Nature Reviews Genetics'' 17 (11): 661–78. https://doi.org/10.1038/nrg.2016.112.


</div>
<div id="ref-Bray2016" class="csl-entry">

Bray, Nicolas L, Harold Pimentel, Páll Melsted, and Lior Pachter. 2016. <span>“Near-Optimal Probabilistic <span>RNA</span>-Seq Quantification.”</span> ''Nature Biotechnology'' 34 (5): 525–27. https://doi.org/10.1038/nbt.3519.


</div>
<div id="ref-BrianOConnor2020" class="csl-entry">

Brian O’Connor, Geraldine van der Auwera. 2020. ''Genomics in the Cloud''. O’Reilly UK Ltd. https://www.oreilly.com/library/view/genomics-in-the/9781491975183/.


</div>
<div id="ref-Burr2019" class="csl-entry">

Burr, Marian L., Christina E. Sparbier, Kah Lok Chan, Yih-Chih Chan, Ariena Kersbergen, Enid Y. N. Lam, Elizabeth Azidis-Yates, et al. 2019. <span>“An Evolutionarily Conserved Function of Polycomb Silences the <span>MHC</span> Class i Antigen Presentation Pathway and Enables Immune Evasion in Cancer.”</span> ''Cancer Cell'' 36 (4): 385–401.e8. https://doi.org/10.1016/j.ccell.2019.08.008.


</div>
<div id="ref-Caravagna2020" class="csl-entry">

Caravagna, Giulio, Guido Sanguinetti, Trevor A. Graham, and Andrea Sottoriva. 2020. <span>“The <span>MOBSTER</span> r Package for Tumour Subclonal Deconvolution from Bulk <span>DNA</span> Whole-Genome Sequencing Data.”</span> ''BMC Bioinformatics'' 21 (1). https://doi.org/10.1186/s12859-020-03863-1.


</div>
<div id="ref-Cereda2012" class="csl-entry">

Cereda, Anna, and John C Carey. 2012. <span>“Trisomy 18 Syndrome.”</span> In ''Atlas of Genetic Diagnosis and Counseling'', 7:990–96. 1. Humana Press. https://doi.org/10.1186/1750-1172-7-81.


</div>
<div id="ref-Chapman2020" class="csl-entry">

Chapman, Brad, Rory Kirchner, Lorena Pantano, Sergey Naumenko, Matthias De Smet, Luca Beltrame, Tetiana Khotiainsteva, et al. 2021. <span>“Bcbio/Bcbio-Nextgen: V1.2.4.”</span> Zenodo. https://doi.org/10.5281/ZENODO.3564938.


</div>
<div id="ref-Chen2020a" class="csl-entry">

Chen, Zixi, Yuchen Yuan, Xiaoshi Chen, Jiayun Chen, Shudai Lin, Xingsong Li, and Hongli Du. 2020. <span>“Systematic Comparison of Somatic Variant Calling Performance Among Different Sequencing Depth and Mutation Frequency.”</span> ''Scientific Reports'' 10 (1). https://doi.org/10.1038/s41598-020-60559-5.


</div>
<div id="ref-Chiang2015" class="csl-entry">

Chiang, Colby, Ryan M Layer, Gregory G Faust, Michael R Lindberg, David B Rose, Erik P Garrison, Gabor T Marth, Aaron R Quinlan, and Ira M Hall. 2015. <span>“<span>SpeedSeq</span>: Ultra-Fast Personal Genome Analysis and Interpretation.”</span> ''Nature Methods'' 12 (10): 966–68. https://doi.org/10.1038/nmeth.3505.


</div>
<div id="ref-Church1984" class="csl-entry">

Church, G. M., and W. Gilbert. 1984. <span>“Genomic Sequencing.”</span> ''Proceedings of the National Academy of Sciences'' 81 (7): 1991–95. https://doi.org/10.1073/pnas.81.7.1991.


</div>
<div id="ref-Church1988" class="csl-entry">

Church, G., and S Kieffer-Higgins. 1988. <span>“Multiplex <span>DNA</span> Sequencing.”</span> ''Science'' 240 (April): 185–88. https://doi.org/10.1126/science.3353714.


</div>
<div id="ref-Cooke2021" class="csl-entry">

Cooke, Daniel P., David C. Wedge, and Gerton Lunter. 2021. <span>“A Unified Haplotype-Based Method for Accurate and Comprehensive Variant Calling.”</span> ''Nature Biotechnology'' 39 (7): 885–92. https://doi.org/10.1038/s41587-021-00861-3.


</div>
<div id="ref-2014" class="csl-entry">

<span>“ctDNA Is a Specific and Sensitive Biomarker in Multiple Human Cancers.”</span> 2014. ''Cancer Discovery'' 4 (4, 4): OF8. https://doi.org/10.1158/2159-8290.CD-RW2014-051.


</div>
<div id="ref-Dan2012" class="csl-entry">

Dan, Shan, Wei Wang, Jinghui Ren, Yali Li, Hua Hu, Zhengfeng Xu, Tze Kin Lau, et al. 2012. <span>“Clinical Application of Massively Parallel Sequencing-Based Prenatal Noninvasive Fetal Trisomy Test for Trisomies 21 and 18 in 11<span></span>105 Pregnancies with Mixed Risk Factors.”</span> ''Prenatal Diagnosis'' 32 (13): 1225–32. https://doi.org/10.1002/pd.4002.


</div>
<div id="ref-Darwin2010" class="csl-entry">

Darwin, Charles. 2010. <span>“On the Origin of Species by Means of Natural Selection, or the Preservation of Favoured Races in the Struggle for Life.”</span> In ''Evolutionary Writings''. Oxford University Press. https://doi.org/10.1093/owc/9780199580149.003.0005.


</div>
<div id="ref-DePristo2011" class="csl-entry">

DePristo, Mark A, Eric Banks, Ryan Poplin, Kiran V Garimella, Jared R Maguire, Christopher Hartl, Anthony A Philippakis, et al. 2011. <span>“A Framework for Variation Discovery and Genotyping Using Next-Generation <span>DNA</span> Sequencing Data.”</span> ''Nature Genetics'' 43 (5): 491–98. https://doi.org/10.1038/ng.806.


</div>
<div id="ref-Deshwar2015" class="csl-entry">

Deshwar, Amit G, Shankar Vembu, Christina K Yung, Gun Ho Jang, Lincoln Stein, and Quaid Morris. 2015. <span>“<span>PhyloWGS</span>: Reconstructing Subclonal Composition and Evolution from Whole-Genome Sequencing of Tumors.”</span> ''Genome Biology'' 16 (1). https://doi.org/10.1186/s13059-015-0602-8.


</div>
<div id="ref-Diehl2008" class="csl-entry">

Diehl, Frank, Kerstin Schmidt, Michael A Choti, Katharine Romans, Steven Goodman, Meng Li, Katherine Thornton, et al. 2008. <span>“Circulating Mutant <span>DNA</span> to Assess Tumor Dynamics.”</span> ''Nature Medicine'' 14 (9): 985–90. https://doi.org/10.1038/nm.1789.


</div>
<div id="ref-ElKebir2018" class="csl-entry">

El-Kebir, Mohammed, Gryte Satas, and Benjamin J. Raphael. 2018. <span>“Inferring Parsimonious Migration Histories for Metastatic Cancers”</span> 50 (5): 718–26. https://doi.org/10.1038/s41588-018-0106-z.


</div>
<div id="ref-Ewing2015" class="csl-entry">

Ewing, Adam D, Kathleen E Houlahan, Yin Hu, Kyle Ellrott, Cristian Caloian, Takafumi N Yamaguchi, J Christopher Bare, et al. 2015. <span>“Combining Tumor Genome Simulation with Crowdsourcing to Benchmark Somatic Single-Nucleotide-Variant Detection.”</span> ''Nature Methods'' 12 (7): 623–30. https://doi.org/10.1038/nmeth.3407.


</div>
<div id="ref-Felsenstein1981" class="csl-entry">

Felsenstein, Joseph. 1981. <span>“Evolutionary Trees from <span>DNA</span> Sequences: A Maximum Likelihood Approach.”</span> ''Journal of Molecular Evolution'' 17 (6): 368–76. https://doi.org/10.1007/bf01734359.


</div>
<div id="ref-Flensburg2020" class="csl-entry">

Flensburg, Christoffer, Tobias Sargeant, Alicia Oshlack, and Ian J. Majewski. 2020. <span>“<span>SuperFreq</span>: Integrated Mutation Detection and Clonal Tracking in Cancer.”</span> Edited by Florian Markowetz. ''PLOS Computational Biology'' 16 (2): e1007603. https://doi.org/10.1371/journal.pcbi.1007603.


</div>
<div id="ref-Fouad2017" class="csl-entry">

Fouad, Yousef Ahmed, and Carmen Aanei. 2017. <span>“[https://www.ncbi.nlm.nih.gov/pubmed/28560055 Revisiting the Hallmarks of Cancer.]”</span> ''American Journal of Cancer Research'' 7: 1016–36.


</div>
<div id="ref-Frey2021" class="csl-entry">

Frey, Laura, Natalia Ziętara, Marcin Łyszkiewicz, Benjamin Marquardt, Yoko Mizoguchi, Monika I. Linder, Yanshan Liu, et al. 2021. <span>“Mammalian <span>VPS</span>45 Orchestrates Trafficking Through the Endosomal System.”</span> ''Blood'' 137 (14): 1932–44. https://doi.org/10.1182/blood.2020006871.


</div>
<div id="ref-Galili2015" class="csl-entry">

Galili, Tal. 2015. <span>“Dendextend: An r Package for Visualizing, Adjusting and Comparing Trees of Hierarchical Clustering”</span> 31 (22): 3718–20. https://doi.org/10.1093/bioinformatics/btv428.


</div>
<div id="ref-Garrison2012" class="csl-entry">

Garrison, Erik, and Gabor Marth. 2012. <span>“Haplotype-Based Variant Detection from Short-Read Sequencing.”</span> ''arXiv Preprint arXiv:1207.3907 [q-Bio.GN]'', July. https://arxiv.org/abs/http://arxiv.org/abs/1207.3907v2.


</div>
<div id="ref-GATKTeam2020" class="csl-entry">

GATK Team. 2020. <span>“Mutect2 Multi-Sample.”</span> September 25, 2020. https://gatk.broadinstitute.org/hc/en-us/community/posts/360062528691.


</div>
<div id="ref-GATKTeam2021" class="csl-entry">

———. 2021a. <span>“Panel of Normals (PON).”</span> July 23, 2021. https://gatk.broadinstitute.org/hc/en-us/articles/360035890631.


</div>
<div id="ref-GATKTeam2021a" class="csl-entry">

———. 2021b. <span>“Somatic Calling Is NOT Simply a Difference Between Two Callsets.”</span> September 15, 2021. https://gatk.broadinstitute.org/hc/en-us/articles/360035890491.


</div>
<div id="ref-Gerstung2020" class="csl-entry">

Gerstung, Moritz, Clemency Jolly, Ignaty Leshchiner, Stefan C. Dentro, Santiago Gonzalez, Daniel Rosebrock, Thomas J. Mitchell, et al. 2020. <span>“The Evolutionary History of 2,658 Cancers.”</span> ''Nature'' 578 (7793): 122–28. https://doi.org/10.1038/s41586-019-1907-7.


</div>
<div id="ref-Gottlieb1962" class="csl-entry">

Gottlieb, Marvin I., Kurt Hirschhorn, Herbert L. Cooper, Nevanka Lusskin, Ralph E. Moloshok, and Horace L. Hodes. 1962. <span>“Trisomy-17 Syndrome.”</span> ''The American Journal of Medicine'' 33 (5): 763–73. https://doi.org/10.1016/0002-9343(62)90253-x.


</div>
<div id="ref-Hamming1950" class="csl-entry">

Hamming, R. W. 1950. <span>“Error Detecting and Error Correcting Codes.”</span> ''Bell System Technical Journal'' 29 (2): 147–60. https://doi.org/10.1002/j.1538-7305.1950.tb00463.x.


</div>
<div id="ref-Hammond2017" class="csl-entry">

Hammond, Colin M., Caroline B. Strømme, Hongda Huang, Dinshaw J. Patel, and Anja Groth. 2017. <span>“Histone Chaperone Networks Shaping Chromatin Function.”</span> ''Nature Reviews Molecular Cell Biology'' 18 (3): 141–58. https://doi.org/10.1038/nrm.2016.159.


</div>
<div id="ref-Hanage2006" class="csl-entry">

Hanage, William P., Christophe Fraser, and Brian G. Spratt. 2006. <span>“The Impact of Homologous Recombination on the Generation of Diversity in Bacteria.”</span> ''Journal of Theoretical Biology'' 239 (2): 210–19. https://doi.org/10.1016/j.jtbi.2005.08.035.


</div>
<div id="ref-Hanahan2000" class="csl-entry">

Hanahan, Douglas, and Robert A Weinberg. 2000. <span>“The Hallmarks of Cancer.”</span> ''Cell'' 100 (1): 57–70. https://doi.org/10.1016/s0092-8674(00)81683-9.


</div>
<div id="ref-Hanahan2011" class="csl-entry">

Hanahan, Douglas, and Robert A. Weinberg. 2011. <span>“Hallmarks of Cancer: The Next Generation.”</span> ''Cell'' 144 (5): 646–74. https://doi.org/10.1016/j.cell.2011.02.013.


</div>
<div id="ref-Hasegawa1985" class="csl-entry">

Hasegawa, Masami, Hirohisa Kishino, and Taka-aki Yano. 1985. <span>“Dating of the Human-Ape Splitting by a Molecular Clock of Mitochondrial <span>DNA</span>.”</span> ''Journal of Molecular Evolution'' 22 (2): 160–74. https://doi.org/10.1007/bf02101694.


</div>
<div id="ref-Hu2019" class="csl-entry">

Hu, Zheng, Jie Ding, Zhicheng Ma, Ruping Sun, Jose A. Seoane, J. Scott Shaffer, Carlos J. Suarez, et al. 2019. <span>“Quantitative Evidence for Early Metastatic Seeding in Colorectal Cancer.”</span> ''Nature Genetics'' 51 (7): 1113–22. https://doi.org/10.1038/s41588-019-0423-x.


</div>
<div id="ref-Huang2011" class="csl-entry">

Huang, Weichun, Leping Li, Jason R. Myers, and Gabor T. Marth. 2011. <span>“<span>ART</span>: A Next-Generation Sequencing Read Simulator.”</span> ''Bioinformatics'' 28 (4): 593–94. https://doi.org/10.1093/bioinformatics/btr708.


</div>
<div id="ref-Hulten2008" class="csl-entry">

Hultén, Maj A, Suketu D Patel, Maira Tankimanova, Magnus Westgren, Nikos Papadogiannakis, Anna Jonsson, and Erik Iwarsson. 2008. <span>“On the Origin of Trisomy 21 down Syndrome.”</span> ''Molecular Cytogenetics'' 1 (1): 21. https://doi.org/10.1186/1755-8166-1-21.


</div>
<div id="ref-Illumina2020" class="csl-entry">

Illumina, Inc. 2020. <span>“How Short Inserts Affect Sequencing Performance.”</span> September 2020. https://sapac.support.illumina.com/bulletins/2020/12/how-short-inserts-affect-sequencing-performance.html.


</div>
<div id="ref-Jiang2016" class="csl-entry">

Jiang, Yuchao, Yu Qiu, Andy J. Minn, and Nancy R. Zhang. 2016. <span>“Assessing Intratumor Heterogeneity and Tracking Longitudinal and Spatial Clonal Evolutionary History by Next-Generation Sequencing”</span> 113 (37): E5528–37. https://doi.org/10.1073/pnas.1522203113.


</div>
<div id="ref-Josephidou2015" class="csl-entry">

Josephidou, Malvina, Andy G. Lynch, and Simon Tavaré. 2015. <span>“<span class="nocase">multiSNV</span>: A Probabilistic Approach for Improving Detection of Somatic Point Mutations from Multiple Related Tumour Samples.”</span> ''Nucleic Acids Research'' 43 (9): e61–61. https://doi.org/10.1093/nar/gkv135.


</div>
<div id="ref-Karczewski2020" class="csl-entry">

Karczewski, Konrad J., Laurent C. Francioli, Grace Tiao, Beryl B. Cummings, Jessica Alföldi, Qingbo Wang, Ryan L. Collins, et al. 2020. <span>“The Mutational Constraint Spectrum Quantified from Variation in 141,456 Humans.”</span> ''Nature'' 581 (7809): 434–43. https://doi.org/10.1038/s41586-020-2308-7.


</div>
<div id="ref-Karimnezhad2020" class="csl-entry">

Karimnezhad, Ali, Gareth A. Palidwor, Kednapa Thavorn, David J. Stewart, Pearl A. Campbell, Bryan Lo, and Theodore J. Perkins. 2020. <span>“Accuracy and Reproducibility of Somatic Point Mutation Calling in Clinical-Type Targeted Sequencing Data.”</span> ''BMC Med Genomics'' 13 (1). https://doi.org/10.1186/s12920-020-00803-z.


</div>
<div id="ref-Kim2018" class="csl-entry">

Kim, Sangtae, Konrad Scheffler, Aaron L. Halpern, Mitchell A. Bekritsky, Eunho Noh, Morten Källberg, Xiaoyu Chen, et al. 2018. <span>“Strelka2: Fast and Accurate Calling of Germline and Somatic Variants.”</span> ''Nature Methods'' 15 (8): 591–94. https://doi.org/10.1038/s41592-018-0051-x.


</div>
<div id="ref-Kong2013" class="csl-entry">

Kong, Ying, Jennifer H. Ma, Keisha Warren, Raymond S. W. Tsang, Donald E. Low, Frances B. Jamieson, David C. Alexander, and Weilong Hao. 2013. <span>“Homologous Recombination Drives Both Sequence Diversity and Gene Content Variation in Neisseria Meningitidis.”</span> ''Genome Biology and Evolution'' 5 (9): 1611–27. https://doi.org/10.1093/gbe/evt116.


</div>
<div id="ref-Lai2016" class="csl-entry">

Lai, Zhongwu, Aleksandra Markovets, Miika Ahdesmaki, Brad Chapman, Oliver Hofmann, Robert McEwen, Justin Johnson, Brian Dougherty, J. Carl Barrett, and Jonathan R. Dry. 2016. <span>“<span>VarDict</span>: A Novel and Versatile Variant Caller for Next-Generation Sequencing in Cancer Research.”</span> ''Nucleic Acids Research'' 44 (11): e108–8. https://doi.org/10.1093/nar/gkw227.


</div>
<div id="ref-Lander2001" class="csl-entry">

Lander, Eric S., Lauren M. Linton, Bruce Birren, Chad Nusbaum, Michael C. Zody, Jennifer Baldwin, Keri Devon, et al. 2001. <span>“Initial Sequencing and Analysis of the Human Genome.”</span> ''Nature'' 409 (6822): 860–921. https://doi.org/10.1038/35057062.


</div>
<div id="ref-Langmead2018" class="csl-entry">

Langmead, Ben, Christopher Wilks, Valentin Antonescu, and Rone Charles. 2018. <span>“Scaling Read Aligners to Hundreds of Threads on General-Purpose Processors.”</span> Edited by John Hancock. ''Bioinformatics'' 35 (3): 421–32. https://doi.org/10.1093/bioinformatics/bty648.


</div>
<div id="ref-Leong2018" class="csl-entry">

Leong, Tracy L., Velimir Gayevskiy, Daniel P. Steinfort, Marc R. De Massy, Alvaro Gonzalez-Rajal, Kieren D. Marini, Emily Stone, et al. 2018. <span>“Deep Multi-Region Whole-Genome Sequencing Reveals Heterogeneity and Gene-by-Environment Interactions in Treatment-Naive, Metastatic Lung Cancer.”</span> ''Oncogene'' 38 (10): 1661–75. https://doi.org/10.1038/s41388-018-0536-1.


</div>
<div id="ref-Leshchiner2018" class="csl-entry">

Leshchiner, Ignaty, Dimitri Livitz, Justin F. Gainor, Daniel Rosebrock, Oliver Spiro, Aina Martinez, Edmund Mroz, et al. 2018. <span>“Comprehensive Analysis of Tumour Initiation, Spatial and Temporal Progression Under Multiple Lines of Treatment.”</span> ''bioRxiv'', December. https://doi.org/10.1101/508127.


</div>
<div id="ref-Li2013" class="csl-entry">

Li, Heng. 2013. <span>“Aligning Sequence Reads, Clone Sequences and Assembly Contigs with BWA-MEM,”</span> March. https://arxiv.org/abs/1303.3997.


</div>
<div id="ref-Liang1998" class="csl-entry">

Liang, F., M. Han, P. J. Romanienko, and M. Jasin. 1998. <span>“Homology-Directed Repair Is a Major Double-Strand Break Repair Pathway in Mammalian Cells.”</span> ''Proceedings of the National Academy of Sciences'' 95 (9): 5172–77. https://doi.org/10.1073/pnas.95.9.5172.


</div>
<div id="ref-Lilley2000" class="csl-entry">

Lilley, David M. J. 2000. <span>“Structures of Helical Junctions in Nucleic Acids.”</span> ''Quarterly Reviews of Biophysics'' 33 (2): 109–59. https://doi.org/10.1017/s0033583500003590.


</div>
<div id="ref-Luczak2017" class="csl-entry">

Luczak, Brian B, Benjamin T James, and Hani Z Girgis. 2017. <span>“A Survey and Evaluations of Histogram-Based Statistics in Alignment-Free Sequence Comparison.”</span> ''Briefings in Bioinformatics'' 20 (4): 1222–37. https://doi.org/10.1093/bib/bbx161.


</div>
<div id="ref-Lupat2021" class="csl-entry">

Lupat, Richard, Michael Franklin, Evan Thomas, Juny Kesumadewi, Jiaan Yu, Mohammad Bhuyan, Tony Papenfuss, Daniel Park, Bernard Pope, and Jason Li. 2021. <span>“Janis: A Python Framework for Portable Pipelines.”</span> Zenodo. https://doi.org/10.5281/ZENODO.4427231.


</div>
<div id="ref-Ma2020" class="csl-entry">

Ma, Chunhua, Xueling Yang, Wenge Xing, Haipeng Yu, Tongguo Si, and Zhi Guo. 2020. <span>“Detection of Circulating Tumor <span>DNA</span> from Non-Small Cell Lung Cancer Brain Metastasis in Cerebrospinal Fluid Samples.”</span> ''Thoracic Cancer'' 11 (3): 588–93. https://doi.org/10.1111/1759-7714.13300.


</div>
<div id="ref-Marass2016" class="csl-entry">

Marass, Francesco, Florent Mouliere, Ke Yuan, Nitzan Rosenfeld, and Florian Markowetz. 2016. <span>“A Phylogenetic Latent Feature Model for Clonal Deconvolution.”</span> ''The Annals of Applied Statistics'' 10 (4). https://doi.org/10.1214/16-aoas986.


</div>
<div id="ref-Mardis2008" class="csl-entry">

Mardis, Elaine R. 2008. <span>“Next-Generation <span>DNA</span> Sequencing Methods.”</span> ''Annual Review of Genomics and Human Genetics'' 9 (1): 387–402. https://doi.org/10.1146/annurev.genom.9.081307.164359.


</div>
<div id="ref-Mayer2014" class="csl-entry">

Mayer, Klaus F. X., Jane Rogers, Jaroslav Doležel, Curtis Pozniak, Kellye Eversole, Catherine Feuillet, Bikram Gill, et al. 2014. <span>“A Chromosome-Based Draft Sequence of the Hexaploid Bread Wheat (Triticum Aestivum) Genome.”</span> ''Science'' 345 (6194): 1251788–88. https://doi.org/10.1126/science.1251788.


</div>
<div id="ref-Mihaescu2007" class="csl-entry">

Mihaescu, Radu, Dan Levy, and Lior Pachter. 2007. <span>“Why Neighbor-Joining Works.”</span> ''Algorithmica'' 54 (1): 1–24. https://doi.org/10.1007/s00453-007-9116-4.


</div>
<div id="ref-Miura2018" class="csl-entry">

Miura, Sayaka, Karen Gomez, Oscar Murillo, Louise A Huuki, Tracy Vu, Tiffany Buturla, and Sudhir Kumar. 2018. <span>“Predicting Clone Genotypes from Tumor Bulk Sequencing of Multiple Samples.”</span> Edited by John Hancock, June. https://doi.org/10.1093/bioinformatics/bty469.


</div>
<div id="ref-Miura2020" class="csl-entry">

Miura, Sayaka, Tracy Vu, Jiamin Deng, Tiffany Buturla, Olumide Oladeinde, Jiyeong Choi, and Sudhir Kumar. 2020. <span>“Power and Pitfalls of Computational Methods for Inferring Clone Phylogenies and Mutation Orders from Bulk Sequencing Data.”</span> ''Scientific Reports'' 10 (1). https://doi.org/10.1038/s41598-020-59006-2.


</div>
<div id="ref-Molina2008" class="csl-entry">

Molina, Julian R., Ping Yang, Stephen D. Cassivi, Steven E. Schild, and Alex A. Adjei. 2008. <span>“Non-Small Cell Lung Cancer: Epidemiology, Risk Factors, Treatment, and Survivorship.”</span> ''Mayo Clinic Proceedings'' 83 (5): 584–94. https://doi.org/10.4065/83.5.584.


</div>
<div id="ref-Moore2021" class="csl-entry">

Moore, Luiza, Alex Cagan, Tim H. H. Coorens, Matthew D. C. Neville, Rashesh Sanghvi, Mathijs A. Sanders, Thomas R. W. Oliver, et al. 2021. <span>“The Mutational Landscape of Human Somatic and Germline Cells.”</span> ''Nature'', August. https://doi.org/10.1038/s41586-021-03822-7.


</div>
<div id="ref-Nicolaides2013" class="csl-entry">

Nicolaides, Kypros H., Argyro Syngelaki, Ghalia Ashoor, Cahit Birdir, and Gisele Touzet. 2013. <span>“Noninvasive Prenatal Testing for Fetal Trisomies in a Routinely Screened First-Trimester Population.”</span> ''Obstetrical &amp; Gynecological Survey'' 68 (3): 173–75. https://doi.org/10.1097/ogx.0b013e318285bf66.


</div>
<div id="ref-Ondov2016" class="csl-entry">

Ondov, Brian D., Todd J. Treangen, Páll Melsted, Adam B. Mallonee, Nicholas H. Bergman, Sergey Koren, and Adam M. Phillippy. 2016. <span>“Mash: Fast Genome and Metagenome Distance Estimation Using <span>MinHash</span>.”</span> ''Genome Biology'' 17 (1). https://doi.org/10.1186/s13059-016-0997-x.


</div>
<div id="ref-Otto2007" class="csl-entry">

Otto, Sarah P. 2007. <span>“The Evolutionary Consequences of Polyploidy.”</span> ''Cell'' 131 (3): 452–62. https://doi.org/10.1016/j.cell.2007.10.022.


</div>
<div id="ref-Padmanabhan1974" class="csl-entry">

Padmanabhan, R., E. Jay, and R. Wu. 1974. <span>“Chemical Synthesis of a Primer and Its Use in the Sequence Analysis of the Lysozyme Gene of Bacteriophage T4.”</span> ''Proceedings of the National Academy of Sciences'' 71 (6): 2510–14. https://doi.org/10.1073/pnas.71.6.2510.


</div>
<div id="ref-Patro2017" class="csl-entry">

Patro, Rob, Geet Duggal, Michael I Love, Rafael A Irizarry, and Carl Kingsford. 2017. <span>“Salmon Provides Fast and Bias-Aware Quantification of Transcript Expression.”</span> ''Nature Methods'' 14 (4): 417–19. https://doi.org/10.1038/nmeth.4197.


</div>
<div id="ref-Payne2018" class="csl-entry">

Payne, Alexander, Nadine Holmes, Vardhman Rakyan, and Matthew Loose. 2018. <span>“<span>BulkVis</span>: A Graphical Viewer for Oxford Nanopore Bulk <span>FAST</span>5 Files.”</span> Edited by Inanc Birol. ''Bioinformatics'' 35 (13): 2193–98. https://doi.org/10.1093/bioinformatics/bty841.


</div>
<div id="ref-Pratanwanich2021" class="csl-entry">

Pratanwanich, Ploy N., Fei Yao, Ying Chen, Casslynn W. Q. Koh, Yuk Kei Wan, Christopher Hendra, Polly Poon, et al. 2021. <span>“Identification of Differential <span>RNA</span> Modifications from Nanopore Direct <span>RNA</span> Sequencing with <span class="nocase">xPore</span>.”</span> ''Nature Biotechnology'', July. https://doi.org/10.1038/s41587-021-00949-w.


</div>
<div id="ref-Saitou1987" class="csl-entry">

Saitou, N, and M Nei. 1987. <span>“The Neighbor-Joining Method: A New Method for Reconstructing Phylogenetic Trees.”</span> ''Molecular Biology and Evolution'', July. https://doi.org/10.1093/oxfordjournals.molbev.a040454.


</div>
<div id="ref-Sanger1975" class="csl-entry">

Sanger, F., and A. R. Coulson. 1975. <span>“A Rapid Method for Determining Sequences in <span>DNA</span> by Primed Synthesis with <span>DNA</span> Polymerase.”</span> ''Journal of Molecular Biology'' 94 (3): 441–48. https://doi.org/10.1016/0022-2836(75)90213-2.


</div>
<div id="ref-Sanger1977" class="csl-entry">

Sanger, F., S. Nicklen, and A. R. Coulson. 1977. <span>“<span>DNA</span> Sequencing with Chain-Terminating Inhibitors.”</span> ''Proceedings of the National Academy of Sciences'' 74 (12): 5463–67. https://doi.org/10.1073/pnas.74.12.5463.


</div>
<div id="ref-Schirmer2016" class="csl-entry">

Schirmer, Melanie, Rosalinda D’Amore, Umer Z. Ijaz, Neil Hall, and Christopher Quince. 2016. <span>“Illumina Error Profiles: Resolving Fine-Scale Variation in Metagenomic Sequencing Data.”</span> ''<span>BMC</span> Bioinformatics'' 17 (1). https://doi.org/10.1186/s12859-016-0976-y.


</div>
<div id="ref-Schwarzenbach2011" class="csl-entry">

Schwarzenbach, Heidi, Dave S. B. Hoon, and Klaus Pantel. 2011. <span>“Cell-Free Nucleic Acids as Biomarkers in Cancer Patients.”</span> ''Nature Reviews Cancer'' 11 (6): 426–37. https://doi.org/10.1038/nrc3066.


</div>
<div id="ref-Shamseldin2015" class="csl-entry">

Shamseldin, Hanan E., Maha Tulbah, Wesam Kurdi, Maha Nemer, Nada Alsahan, Elham Al Mardawi, Ola Khalifa, et al. 2015. <span>“Identification of Embryonic Lethal Genes in Humans by Autozygosity Mapping and Exome Sequencing in Consanguineous Families.”</span> ''Genome Biology'' 16 (1). https://doi.org/10.1186/s13059-015-0681-6.


</div>
<div id="ref-Shibata2010" class="csl-entry">

Shibata, D. 2010. <span>“Mutation and Epigenetic Molecular Clocks in Cancer.”</span> ''Carcinogenesis'' 32 (2): 123–28. https://doi.org/10.1093/carcin/bgq239.


</div>
<div id="ref-Siegel2018" class="csl-entry">

Siegel, Rebecca L., Kimberly D. Miller, and Ahmedin Jemal. 2018. <span>“Cancer Statistics, 2018.”</span> ''<span>CA</span>: A Cancer Journal for Clinicians'' 68 (1): 7–30. https://doi.org/10.3322/caac.21442.


</div>
<div id="ref-Sinden1994" class="csl-entry">

Sinden, Richard R. 1994. <span>“Introduction to the Structure, Properties, and Reactions of <span>DNA</span>.”</span> In ''<span>DNA</span> Structure and Function'', 1–57. Elsevier. https://doi.org/10.1016/b978-0-08-057173-7.50006-7.


</div>
<div id="ref-Sokal1958" class="csl-entry">

Sokal, Robert Reuven, and Charles Duncan Michener. 1958. ''A Statistical Method for Evaluating Systematic Relationships''. Vol. 38.2. University of Kansas Science Bulletin 22. University of Kansas.


</div>
<div id="ref-Solomon2020" class="csl-entry">

Solomon, Benjamin J., Lavinia Tan, Jessica J. Lin, Stephen Q. Wong, Sebastian Hollizeck, Kevin Ebata, Brian B. Tuch, et al. 2020. <span>“<span>RET</span> Solvent Front Mutations Mediate Acquired Resistance to Selective <span>RET</span> Inhibition in <span>RET</span>-Driven Malignancies.”</span> ''Journal of Thoracic Oncology'' 15 (4): 541–49. https://doi.org/10.1016/j.jtho.2020.01.006.


</div>
<div id="ref-Sprouffske2018" class="csl-entry">

Sprouffske, Kathleen, José Aguilar-Rodrı́guez, Paul Sniegowski, and Andreas Wagner. 2018. <span>“High Mutation Rates Limit Evolutionary Adaptation in Escherichia Coli.”</span> Edited by Ivan Matic. ''<span>PLOS</span> Genetics'' 14 (4): e1007324. https://doi.org/10.1371/journal.pgen.1007324.


</div>
<div id="ref-Stoler2021" class="csl-entry">

Stoler, Nicholas, and Anton Nekrutenko. 2021. <span>“Sequencing Error Profiles of Illumina Sequencing Instruments.”</span> ''<span>NAR</span> Genomics and Bioinformatics'' 3 (1). https://doi.org/10.1093/nargab/lqab019.


</div>
<div id="ref-Straiton2019" class="csl-entry">

Straiton, Jenny, Tristan Free, Abigail Sawyer, and Joseph Martin. 2019. <span>“From Sanger Sequencing to Genome Databases and Beyond.”</span> ''<span>BioTechniques</span>'' 66 (2): 60–63. https://doi.org/10.2144/btn-2019-0011.


</div>
<div id="ref-Sun2007" class="csl-entry">

Sun, Sophie, Joan H. Schiller, and Adi F. Gazdar. 2007. <span>“Lung Cancer in Never Smokers <span></span> a Different Disease.”</span> ''Nature Reviews Cancer'' 7 (10): 778–90. https://doi.org/10.1038/nrc2190.


</div>
<div id="ref-Tan2019" class="csl-entry">

Tan, L., S. Sandhu, R. J. Lee, J. Li, J. Callahan, S. Ftouni, N. Dhomen, et al. 2019. <span>“Prediction and Monitoring of Relapse in Stage <span>III</span> Melanoma Using Circulating Tumor <span>DNA</span>.”</span> ''Annals of Oncology'' 30 (5): 804–14. https://doi.org/10.1093/annonc/mdz048.


</div>
<div id="ref-Tarabichi2021" class="csl-entry">

Tarabichi, Maxime, Adriana Salcedo, Amit G. Deshwar, Máire Ni Leathlobhair, Jeff Wintersinger, David C. Wedge, Peter Van Loo, Quaid D. Morris, and Paul C. Boutros. 2021. <span>“A Practical Guide to Cancer Subclonal Reconstruction from DNA Sequencing.”</span> ''Nature Methods'' 18 (2, 2): 144–55. https://doi.org/10.1038/s41592-020-01013-2.


</div>
<div id="ref-Tateoka1975" class="csl-entry">

Tateoka, Tuguo. 1975. <span>“A Contribution to the Taxonomy of <span class="nocase">theAgrostis</span> Mertensii-Flaccida Complex (Poaceae) in Japan.”</span> ''The Botanical Magazine Tokyo'' 88 (2): 65–87. https://doi.org/10.1007/bf02491243.


</div>
<div id="ref-TaylorWeiner2018" class="csl-entry">

Taylor-Weiner, Amaro, Chip Stewart, Thomas Giordano, Mendy Miller, Mara Rosenberg, Alyssa Macbeth, Niall Lennon, et al. 2018. <span>“<span>DeTiN</span>: Overcoming Tumor-in-Normal Contamination.”</span> ''Nature Methods'' 15 (7): 531–34. https://doi.org/10.1038/s41592-018-0036-9.


</div>
<div id="ref-Toptas2018" class="csl-entry">

Toptaş, Berke Ç, Goran Rakocevic, Péter Kómár, and Deniz Kural. 2018. <span>“Comparing Complex Variants in Family Trios.”</span> Edited by Oliver Stegle. ''Bioinformatics'', June. https://doi.org/10.1093/bioinformatics/bty443.


</div>
<div id="ref-Trivers1976" class="csl-entry">

Trivers, R., and H Hare. 1976. <span>“Haploidploidy and the Evolution of the Social Insect.”</span> ''Science'' 191 (4224): 249–63. https://doi.org/10.1126/science.1108197.


</div>
<div id="ref-Veeneman2015" class="csl-entry">

Veeneman, Brendan A., Sudhanshu Shukla, Saravana M. Dhanasekaran, Arul M. Chinnaiyan, and Alexey I. Nesvizhskii. 2015. <span>“Two-Pass Alignment Improves Novel Splice Junction Quantification.”</span> ''Bioinformatics'' 32 (October): 43–49. https://doi.org/10.1093/bioinformatics/btv642.


</div>
<div id="ref-Venter2001" class="csl-entry">

Venter, J. Craig, Mark D. Adams, Eugene W. Myers, Peter W. Li, Richard J. Mural, Granger G. Sutton, Hamilton O. Smith, et al. 2001. <span>“The Sequence of the Human Genome.”</span> ''Science'' 291 (5507): 1304–51. https://doi.org/10.1126/science.1058040.


</div>
<div id="ref-Vergara2021" class="csl-entry">

Vergara, Ismael A., Christopher P. Mintoff, Shahneen Sandhu, Lachlan McIntosh, Richard J. Young, Stephen Q. Wong, Andrew Colebatch, et al. 2021. <span>“Evolution of Late-Stage Metastatic Melanoma Is Dominated by Aneuploidy and Whole Genome Doubling.”</span> ''Nature Communications'' 12 (1). https://doi.org/10.1038/s41467-021-21576-8.


</div>
<div id="ref-Vienne2018" class="csl-entry">

Vienne, Damien M de. 2018. <span>“Tanglegrams Are Misleading for Visual Evaluation of Tree Congruence.”</span> Edited by Jeffrey Townsend 36 (1): 174–76. https://doi.org/10.1093/molbev/msy196.


</div>
<div id="ref-Wang2018" class="csl-entry">

Wang, Di, Xiaohui Niu, Zhijie Wang, Cheng-Li Song, Zhen Huang, Ke-Neng Chen, Jianchun Duan, et al. 2018. <span>“Multiregion Sequencing Reveals the Genetic Heterogeneity and Evolutionary History of Osteosarcoma and Matched Pulmonary Metastases.”</span> ''Cancer Research'' 79 (1): 7–20. https://doi.org/10.1158/0008-5472.can-18-1086.


</div>
<div id="ref-Watson1953" class="csl-entry">

Watson, J. D., and F. H. C. Crick. 1953. <span>“Molecular Structure of Nucleic Acids: A Structure for Deoxyribose Nucleic Acid.”</span> ''Nature'' 171 (4356): 737–38. https://doi.org/10.1038/171737a0.


</div>
<div id="ref-Werner2020" class="csl-entry">

Werner, Benjamin, Jack Case, Marc J. Williams, Ketevan Chkhaidze, Daniel Temko, Javier Fernández-Mateos, George D. Cresswell, et al. 2020. <span>“Measuring Single Cell Divisions in Human Tissues from Multi-Region Sequencing Data.”</span> ''Nature Communications'' 11 (1). https://doi.org/10.1038/s41467-020-14844-6.


</div>
<div id="ref-Yoon2019" class="csl-entry">

Yoon, Sang Eun, Won Seog Kim, Seok Jin Kim, Young Hyeh Ko, Kim Yeon Jeong, and Park Donghyun. 2019. <span>“Clinical Application of Circulating Tumor <span>DNA</span> in Plasma of Patients with Primary Central Nervous System Lymphoma.”</span> ''Blood'' 134 (Supplement<span>_</span>1): 1491–91. https://doi.org/10.1182/blood-2019-130075.


</div>
<div id="ref-Zuckerkandl1962" class="csl-entry">

Zuckerkandl, Emile, and Linus Pauling. 1962. <span>“Molecular Disease, Evolution, and Genic Heterogeneity.”</span> ''Horizons in Biochemistry'', 189--225.


</div>

</div>
