---
# layout: post
layout: default
name:  "A brief introduction to RNA-seq"
title: null
# date:   2022-12-19 16:49:51 -0500
# categories: jekyll update
---
This post offers a high-level introduction to high-throughput RNA sequencing (RNA-seq). Topics discussed include:
1. [The central dogma and why we care about RNA](#dogma)
2. [A simple overview of how RNA-seq works ](#RNAseq)
3. [A discussion of the intuition behind interpreting RNA-seq data](#intuit)
4. [Brief discussion of differential expression analysis, a common application of RNA-seq](#DEA)
5. [A key limitation of differential expression analysis](#limited)
6. [Definitions of important jargon](#defn)

The final point will segue nicely into a discussion of time resolved RNA-seq methods, which attempt to address the limitation discussed in that sub-topic. 

Some things not covered in this post include:
1. How to perform RNA-seq in practice
2. The nitty gritty technical details of RNA-seq
3. The nitty gritty technical details of RNA-seq data analysis

This post assumes a basic knowledge of fundamental chemistry and biology, like what an atom is, or what cells are. Familiarity with some concepts from molecular biology, particularly DNA, RNA, proteins, and the central dogma will be very helpful, though the post starts with a crash course on these topics. If you are already well aware of what all these are, feel free to skip the first section. With all of that in mind, if you are still interested, read on!

## **The Central Dogma and the importance of RNA**<a name="dogma"></a>
In this day in age, the concept of DNA has become cemented into the public conscience. Most people have a vauge sense that DNA is the thing that makes each and every one of us unique. We think of it as responsible for our physical features (hair color, eye color, skin tone, height, etc.), our psychological disposition, and our individual health problems. DNA has even become a popular colloquialism synonomous with "things that make something what it is", like "the DNA of a company" or "the DNA of Relationships" (maybe a dated reference). But what IS DNA, and how has it become associated with all of these concepts?

The answer to the first question is simple: DNA is a molecule. Like water, carbon dioxide, caffeine, or any other popular moleculas, DNA is an entity composed of a certain combination of atoms. In particular, DNA typically consists of five different types of atoms: carbon, oxygen, hydrogen, nitrogen, and phosphorus atoms. DNA stands for deoxyribonucleic acid, and the molecular structure of a single DNA molecule is shown in Figure 1. 

![DNA](../assets/DNA.jpg)
**Figure 1:** *The chemical structure of DNA. DNA comes in four different varieities distinguished by the composition of their nitrogenous bases. These four varieties are typically denoted by the a single letter: A, G, C, and T*

DNA resides inside the nucleus of each and every one of your cells. Here, DNA is not a single molecule like that shown in Figure 1 though, but is rather a massive polymer (i.e., copies of this molecule stitched together in a particular way). In a typical cell in the human body, there are about 6 billion of these molecules in total. Rather than all being part of a single chain of DNA molecules though, in humans they are separated into 46 different polymers, two copies each of 23 unique polymers called chromosomes. Furthermore, each chromosome consists of not one but TWO polymers that weave together in a choreographed molecular dance known as the double helix. The discovery of this fact, published in 1953, kicked off modern molecular biology as we know it.

### What are all of these DNA molecules actually doing? 
Well, as shown in Figure 1, there isn't just one kind of DNA molecule, but rather there are four! Each of these flavors are typically associated with a single letter: A, G, C, and T. Each flavor is identical, except for the so-called nitrogenous base sticking out to the right in each of the depicted structures. Each of your chromosomes consist of a particular sequence of these four DNA flavors that can be read out much like a book. DNA isn't just any kind of book though, it's a **cook book**. Each chromosome consists of stretches of DNA that act as recipes, called genes. These genes are the key to building you from scratch, and they are the key for building almost every form of life on this planet. 

### What do cells do with these recipes? 
They use them to make RNA! RNA, as its name implies, is quite similar to DNA. A comparison of the two molecules is presented in Figure 2: see if you can spot the difference. RNA can play one of two roles in cells. For one, it can act as an intermediate message, that will once again be read like a recipe to make a new molecule: a protein. In this case, we refer to the RNA as messenger RNA, abbreviated mRNA. Proteins do most of the important work in cells. They make the energy cells need to stay alive, they transport things in and out of cells, they destroy harmful invaders, and so much more. The second role RNA can play though is to be like a protein and do something useful. These so-called non-coding RNA (because they don't **code** for a protein) are increasingly recognized as important factors involved in a number of different biological processes. A classic and well studied example are ribosomal RNA, which are a major component of ribosomes, the giant machines that make proteins. 

### Why bother making RNA?
It might seem kind of weird that cells use a molecule to make a molecule very similar to the first molecule. Isn't that redundant and unnecessary? No!! An amazing fact of multicellular life such as yourself is that each and every one of your cells should contain the **exact same** DNA. The cook book of recipes stored in your skin cells is exactly the same as the cook book in the heart cells, and eye cells, and liver cells, et cetera et cetera. How is it possible for cells with the exact same cook books to produce such vastly different "meals"? The solution is that each cell picks and chooses which recipes to use to make RNA. This process of choosing to use some genes and not others is known as **gene expression regulation**. Gene expression regulation is a hot topic in scientific research, and has been for a couple decades now. Therefore, it is of utmost importance that we have methods to study this process in exquisite detail. That is where RNA-seq comes in. 

## **Assaying RNA in cells**<a name="RNAseq"></a>

### <u>How can we study gene expression regulation?</u>
Studying gene expression regulation means using experimental methods to determine if a cell is using a particular gene to make an RNA/protein, and studying how its use changes as cells undergo important biological processes (e.g., the cell cycle, differentiation, stress responses, etc.). Therefore, we need an [assay](#assay) to determine the presence or absence of any RNA/protein of interest. Often, a researcher is interested in a single protein/RNA, or maybe a small handful of related proteins/RNAs. In that case, there are a number of [low-throughput](#low-throughput) methods that one can rely on. These include "blots", like [Western blots](#western) to detect proteins and Northern blots to detect RNA. These have been (and continue to be) workhorse methods in molecular biology used by countless scientists. 

What if you want to know the expression levels of every single gene that a cell could be using? Humans have about 20,000 protein coding genes, so good luck doing 20,000 Western blots! That's not to mention the myriad genes that code for functional RNA. An exciting development of the last 30 years has been the rise of methods for high-throughput investigations of gene expression. These have pushed us into the era of -omics, meaning the ability to assay the totality of particular classes of molecules. Many branches of -omics exist, such as [genomics](#genomics), [transcriptomics](#transcriptomics), [epigenomics](#epigenomics), [proteomics](#proteomics), [epitranscriptomics](#epitranscriptomics), etc. The rest of this post will focus specifically on transcriptomics, which is the high-throughput study RNA. 

### <u>Why focus on RNA?</u>
Some would vigorously answer: "You shouldn't, proteins are what matter!".

Here is my response to this common criticism of RNA-centric transcriptomics research:

1. If RNA levels change, so will protein levels. "But RNA levels and protein levels don't correlate!" It is true that our *high-thorughput estimates* of RNA levels and proteins levels often do not correlate. Many have used this as evidence that most gene expression regulation occurs at the level of protein synthesis and degradation. Do you know what else could cause estimates of RNA and protein levels to not correlate? Bad estimates. The accuracy of transcriptomics currently outpaces that of proteomics. Thus, while we should certainly not discount regulation of protein synthesis and degradation, we should not understate the extent to which RNA expression changes predict protein expression changes. See this [recent paper](https://www.sciencedirect.com/science/article/pii/S2667237522001709?via%3Dihub) for example. 
1. Even if RNA levels change and protein levels don't, cells are still clearly trying to achieve some end. Any time a cell decides that something is important enough to spend energy on, we should pay attention. 
1. Not all RNA codes for protein. These so-called non-coding RNAs (ncRNA) often have key biological roles.
1. Regulation of transcription (RNA synthesis) and RNA degradation is a common mechanism by which cells regulate the expression of their genes. We can't ignore the decades of research providing ample evidence that cellular regulation of RNA levels is key to many important biological processes. RNA matters!

### <u>RNA sequencing (RNA-seq)</u>
The current workhorse method in transcriptomics is RNA sequencing, or RNA-seq. RNA-seq allows us to quantify the relative abundances of all RNA species made by a population of cells. To help you understand how this incredibly important method works, I will walk through the major steps of an RNA-seq experiment and explain its importance.

End goal: determine the nucleotide sequence of fragments from every RNA present in your sample. We can use this information to determine which RNAs are present. It can also tell us about which RNAs are more abundant and which are less abundant. See [The intuition behind RNA-seq](#intuit) for more details.

### 1) RNA is extracted from cells
The importance of this step may be obvious: we want to assay RNA, so we must first obtain the RNA. 

### 2) Removal of unwanted RNA or enrichment for desired RNA
The most abundant RNA in almost any cell is ribosomal RNA (rRNA). This RNA is a key component of the ribosome. It is also often not the RNA we are interested in studying. If you keep it around, it will dominate most of the signal in our data. Therefore, it is common to specifically deplete rRNA in your sample, which can be achieved with a particular RNA exonuclease. 

Another solution is to enrich for a particular sub-species of RNA. For example, you can enrich for RNA with a polyA tail (a sequence of adenines at the 3-prime end of the RNA). polyA tails characterize transcripts synthesized by RNA Polymerase II, which includes all mRNA. 

### 3) Fragment the RNA
Sequencers can't sequence entire RNA molecules. Fragmenting the RNA ensures that the sequencer isn't forced to bite off more than it can chew. 

### 4) Reverse transcription and amplification with PCR
Much of early molecular biology was driven was the study of DNA, so a lot of awesome methods for working with and analyzing DNA have been developed over the years. This includes methods to amplify DNA (polymerase chain reaction, or PCR) and to determine the sequence of nucleotides that make up DNA (DNA sequencing). Thus, life is easier if we convert our RNA to DNA and then go forward with the well established DNA molecular biology infrastructure. 

The process of using RNA to make DNA is called reverse transcription, and viruses have kindly provided us with the enzymes necessary to perform this reaction. PCR amplification of the resulting DNA is important for a couple reasons. One, the sequencer will work better if provided more material. Two, the sequencer relies on their being specific nucleotide sequences at the ends of every RNA fragment. These nucleotide sequences are called adapters, and they will grab onto complementary sequences on the chips that the sequencing reaction is performed on. PCR is thus performed with specific primers and reagents that enable attachment of these adapters to each and every RNA fragment.

### 5) Sequence the cDNA
Your cDNA is now ready for sequencing! The data provided by sequencers is in what is known as the fastq file format. In a fastq file, each read is associated with four lines of data. The first line provides a unique identifier for that read. The second line is the sequence of As, Gs, Ts, and Cs that the sequencer identified as making up the fragment of RNA. The number of letters in this sequence is known as the read length, and typically varies anywhere between 50 and 300 nucleotides. The third line is a lone + sign. The final line is a sequence of characters that quantifies how confident the sequencer is in each of the nucleotide calls in line 2. 

## **The intuition underlying RNA-seq<a name="intuit"></a>**
Above is a very basic overview of what an RNA-seq experimental workflow might look like But why do we care about the sequences of RNA? And how does this tell us about the abundances of each RNA in our sample? In this section, I want to give you an intuition for how these experiments provide us with useful information and how we should go about interpreting it.

To understand RNA-seq, consider a simple analogy. Imagine you have a massive opaque jar filled with thousands of colored marbles. Let's say that there are 4 different colors of marble that could show up in this jar, and you want to know how abundant each color is. "Why not pour out the marbles and look"? Ah, because this is a magical jar, a jar that will allow this analogy to work. All you can do is remove one marble at a time, check its color, and return it to the jar. How can we go about determining how abundant each color of marble is?

{:refdef: style="text-align: center;"}
![Jar](../assets/Jar_analogy.jpg)
{: refdef}
**Figure 2:** *An analogy for how RNA-seq works. The different colors of marbles are analogous to different RNA species (e.g., different transcripts). Each RNA-seq read is like drawing a single marble from the jar and inspecting its color. If you sample a marble 100 times, the fraction of the time you draw a certain color may not perfectly reflect that color's true proportion. The more marbles you draw though, the better your estimate will become.*

If we keep sampling marbles from the jar, we can keep track of how many times we observed each color. More abundant marbles will show up more times, and less abundant marbles less times. This is a random process though, so only taking a couple samples won't give you much confidence as to the composition of the jar. Say you pull 5 marbles, 3 blues, 1 red, 1 yellow, and no purples. That implies that 60% of marbles are blue, 20% are red, 20% are yellow, and none are purple. Are you sure that all of those numbers are exactly accurate though? Pull another 5 and you might get 1 blue, 0 reds, 2 yellows, and 2 purples. Yet another 5 might give you something completely different. 

The solution is to collect LOTS of marble samples. Don't just pull out 5 marbles. Pull out 5,000 marbles! Or 5,000,000 marbles!! With enough samples, your estimate of the relative abundances of each marble color will be pretty good. Notice though, I keep saying *relative abundances* of each color. Saying "60% of marbles are blue" is a statement about relative abundance. It tells us that if yellow marbles make up 20% of the population, then the blue marbles are three times more abundant than the yellow marbles. This doesn't tell us anything about *absolute abundance* though. Unless I tell you how many total marbles are in the jar (which I didn't and won't), you won't be able to tell me how many blue marbles there are. 

Like in the marble analogy, RNA-seq is a strategy to measure *relative RNA abundances*. In RNA-seq, the jar is the population of RNA fragments that you got from your cells and processed in ways that make them sequencable. The different marble colors represent the different RNA species (e.g., RNA produced from different genes) present in your sample. A sequencing read is thus analogous to a sample from the marble jar. You can think of the sequencer as randomly choosing an RNA fragment, determining its nucleotide sequence, and throwing it back in the pool of RNA fragments. 

Something that makes RNA-seq trickier than pulling marbles from a jar though is that the information in a sequencing read does not automatically tell us which RNA species a particular fragment came from. It's not like looking at a marble and immediately discerning its color. Immense computational effort goes into **"mapping"** RNA-seq reads, which is the prcoess of figuring out the most likely RNA species of origin for each read in our fastq file. Once you do that though, you can begin to say something about the relative abundances of all RNA in your sample.



## **Differential expression analysis**<a name="DEA"></a>

## **Key limitation of differential expression analyses**<a name="limited"></a>
   
## **Definitions**<a name="defn"></a>

### <u>Assay<a name="assay"></a></u>
Definition: an assay is a fancy word for an experimental method. We also often use it as a verb. For example, you might say, "you did a Western blot to assay for protein X's presence in your cell". 

### <u>Low-throughput<a name="low-throughput"></a></u>:

Definition: a method is low-throughput if it is only able to provide information about one or a small number of molecules at a time. 

Example: Western blots provide information about the abundance of a single protein.

### <u>Western blot<a name = "western"></a></u>

Definition: a low-throughput method by which protein abundance can be quantified. In this method, protein is extracted from cells and then run on a gel. An antibody that targets your protein of interest is used to make it visible on the gel, if it is present.

### <u>Genomics<a name = "genomics"></a></u>

Definition: the high-throughput study of cellular DNA. DNA contains all of the genes that a cell could ever want to make use of. A major early accomplishment in the field of genomics was the sequencing of the human genome. 

### <u>Transcriptomics<a name = "transcriptomics"></a></u>

Definition: the high-throughput study of cellular RNA. Which genes a cell is using to make RNA plays a large part in determining the properties of the cell.

### <u>Epigenomics<a name = "epigenomics"></a></u>

Definition: the high-throughput study of the epigenome. The exact definition of the epigenome is sometimes [fiercely debated](https://twitter.com/z_chiang/status/1574455394482651136?lang=en). A literal interpretation would be that epigenomics is any non-DNA species that is inherited and affects how cells use their DNA. Studying the roles of chemical modifications found on histones, the proteins that DNA wrap around in eukaryotes, is a common example of what one might consider "epigenetics".

### <u>Proteomics<a name = "proteomics"></a></u>

Definition: the high-throughput study of cellular proteins. Proteins are the machines that do much of the work in cells. They have countless roles as structural components of the cell, key factors involved in inter/intracellular transport, enzymes that catalyze biochemical reactions, etc.

### <u>Epitranscriptomics<a name = "epitranscriptomics"></a></u>

Definition: the high-throughput study of chemical modifications of RNA. It is increasingly recognized that the nucleotides that make up RNA (A, G, C, and U) are often heavily modified in cells. These modifications have been shown to play a number of roles, though the function of many epitranscriptome marks is an area of active research.
