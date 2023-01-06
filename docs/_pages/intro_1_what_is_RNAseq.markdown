---
# layout: post
layout: default
name:  "A brief introduction to RNA-seq"
title: null
# date:   2022-12-19 16:49:51 -0500
# categories: jekyll update
---
# A brief introduction to RNA-seq

## What to expect, and what not to expect
This post offers a high-level introduction to high-throughput RNA sequencing (RNA-seq). Topics discussed include:
1. The central dogma and why we care about RNA
2. A simple overview of how RNA-seq works and how we interpret RNA-seq data
3. Brief discussion of differential expression analysis, a common application of RNA-seq
4. A key limitation of differential expression analysis

The final point will segue nicely into a discussion of time resolved RNA-seq methods, which attempt to address the limitation discussed in that sub-topic. 

Some things not covered in this post include:
1. How to perform RNA-seq in practice
2. The nitty gritty technical details of RNA-seq
3. The nitty gritty technical details of RNA-seq data analysis

This post assumes a basic knowledge of fundamental chemistry and biology, like what an atom is, or what cells are. Familiarity with some concepts from molecular biology, particularly DNA, RNA, proteins, and the central dogma will be very helpful, though the post starts with a crash course on these topics. If you are already well aware of what all these are, feel free to skip the first section. With all of that in mind, if you are still interested, read on!

## The Central Dogma and the importance of RNA
In this day in age, the concept of DNA has become cemented into the public conscience. Most people have a vauge sense that DNA is the thing that makes each and every one of us unique. We think of it as responsible for our physical features (hair color, eye color, skin tone, height, etc.), our psychological disposition, and our individual health problems. DNA has even become a popular colloquialism synonomous with "things that make something what it is", like "the DNA of a company" or "the DNA of Relationships" (maybe a dated reference). But what IS DNA, and how has it become associated with all of these concepts?

The answer to the first question is simple: DNA is a molecule. Like water, carbon dioxide, caffeine, or any other popular moleculas, DNA is an entity composed of a certain combination of atoms. In particular, DNA typically consists of five different types of atoms: carbon, oxygen, hydrogen, nitrogen, and phosphorus atoms. DNA stands for deoxyribonucleic acid, and the molecular structure of a single DNA molecule is shown in Figure 1. 

DNA resides inside the nucleus of each and every one of your cells. Here, DNA is not a single molecule like that shown in Figure 1 though, but is rather a massive polymer (i.e., copies of this molecule stitched together in a particular way). In a typical cell in the human body, there are about 6 billion of these molecules in total. Rather than all being part of a single chain of DNA molecules though, in humans they are separated into 46 different polymers, two copies each of 23 unique polymers called chromosomes. Furthermore, each chromosome consists of not one but TWO polymers that weave together in a choreographed molecular dance known as the double helix. The discovery of this fact, published in 1953, kicked off modern molecular biology as we know it.

### What are all of these DNA molecules actually doing? 
Well, as shown in Figure 1, there isn't just one kind of DNA molecule, but rather there are four! Each of these flavors are typically associated with a single letter: A, G, C, and U. Each flavor is identical, except for the so-called nitrogenous base sticking out to the right in each of the depicted structures. Each of your chromosomes consist of a particular sequence of these four DNA flavors that can be read out much like a book. DNA isn't just any kind of book though, it's a **cook book**. Each chromosome consists of stretches of DNA that act as recipes, called genes. These genes are the key to building you from scratch, and they are the key for building almost every form of life on this planet. 

### What do cells do with these recipes? 
They use them to make RNA! RNA, as its name implies, is quite similar to DNA. A comparison of the two molecules is presented in Figure 2: see if you can spot the difference. RNA can play one of two roles in cells. For one, it can act as an intermediate message, that will once again be read like a recipe to make a new molecule: a protein. In this case, we refer to the RNA as messenger RNA, abbreviated mRNA. Proteins do most of the important work in cells. They make the energy cells need to stay alive, they transport things in and out of cells, they destroy harmful invaders, and so much more. The second role RNA can play though is to be like a protein and do something useful. These so-called non-coding RNA (because they don't **code** for a protein) are increasingly recognized as important factors involved in a number of different biological processes. A classic and well studied example are ribosomal RNA, which are a major component of ribosomes, the giant machines that make proteins. 

### Why bother making RNA?
It might seem kind of weird that cells use a molecule to make a molecule very similar to the first molecule. Isn't that redundant and unnecessary? No!! An amazing fact of multicellular life such as yourself is that each and every one of your cells should contain the **exact same** DNA. The cook book of recipes stored in your skin cells is exactly the same as the cook book in the heart cells, and eye cells, and liver cells, et cetera et cetera. How is it possible for cells with the exact same cook books to produce such vastly different "meals"? The solution is that each cell picks and chooses which recipes to use to make RNA. This process of choosing to use some genes and not others is known as **gene expression regulation**. Gene expression regulation is a hot topic in scientific research, and has been for a couple decades now. Therefore, it is of utmost importance that we have methods to study this process in exquisite detail. That is where RNA-seq comes in. 

## Assaying RNA in cells

### How can we study gene expression regulation?
What we want is an experimental method that allows us determine which genes a group of cells is using, and which genes are going unused. The key insight when developing such a method is to realize that assaying RNA will give us the information we desire. If we know which RNAs are produced in our cells of interest, then we know which genes are being expressed. 

## Differential expression analysis

## Key limitation of differential expression analyses
   
