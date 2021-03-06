### grace-Cbairdi-transcriptome

# Effects of temperature and _Hematodinium sp._ - infection (Bitter Crab Syndrome) on Southeast Alaskan Tanner Crabs (_Chionoecetes bairdi_)

# The problem
Southeast Alaskan Tanner crabs support a $21 million fishery. However, warming temperatures and disease threaten stock numbers and marketability. The prevalence of Bitter Crab Disease caused by a parasitic dinoflagellate _Hematodinium sp._ ranges from 0-100% in SE Alaskan populations, and is projected to increase with increasing temperatures. The disease itself may not be directly fatal to the crabs, but it causes their meat to become chalky in texture and bitter in taste, rendering them unmarketable and negatively impacting the livelihoods of many. 

With temperatures projected to increase, it is thought that the increase in temperature will physiologically stress these naturally cold-water crabs, and also increase the prevalence of Bitter Crab Disease. 

## Design
_C. bairdi_ were collected from Juneau, AK by the ADF&G in the fall of 2017 (Day 0).    

An initical cPCR was performed on all crabs to determine initial infection status. 

Crabs were allowed to acclimate to the lab settings and tanks for a little over a week. 

On Day 9, crabs' hemolymph was sampled and stored in RNAlater. Then, the crabs were separated into 9 tanks, such that each tank had 10 infected and 10 uninfected crabs (n =180). The temperature in three tanks were lowered to 4˚C (cold treatment), three were brought up to 10˚C (warm treatment), and three were kept at 8˚C (ambient treatment).  

<p float="left">
  <img src="https://github.com/fish546-2018/grace-Cbairdi-transcriptome/blob/master/images/experimental-design/cold.jpeg" width="275" />
  <img src="https://github.com/fish546-2018/grace-Cbairdi-transcriptome/blob/master/images/experimental-design/warm.jpeg" width="275" /> 
  <img src="https://github.com/fish546-2018/grace-Cbairdi-transcriptome/blob/master/images/experimental-design/ambient.jpeg" width="275" />
</p>

The crabs' hemolymph was sampled again on Day 12 and Day 26, with Day 26 being the final sampling day after which all crabs had to be sacrificed. 

<p float="left">
  <img src="https://github.com/fish546-2018/grace-Cbairdi-transcriptome/blob/master/images/experimental-design/crabsintank.jpeg" width="250" />
  <img src="https://github.com/fish546-2018/grace-Cbairdi-transcriptome/blob/master/images/experimental-design/hemo-sample.jpeg" width="250" /> 
</p>

Upon receiving the hemolymph stored in RNAlater at -80˚C, I centrifuged the samples and saved the hemolymph pellet as well as the supernatant RNAlater. 

The pelleted hemolymph was processed using Qiagen RNeasy Micro Plus Kit to extract RNA. The extracted samples were run on the Roberts' Lab Qubit 3.0 using Qubit RNA High Sensitivity kit to quantify the RNA in each extracted sample. Additionally, the samples were run on the Bioanalyzer and NanoDop to confirm RNA purity. 

The samples were pooled such that each sample contributed equally to the pooled sample and given to the NWGC to be library prepped and sequenced. 

## Goals
This project aims to use bioinformatic tools to identify genes of SE Alaskan Tanner crabs (_Chionoecetes bairdi_) that are involved in immunity and temperature stress response in order to provide understanding of basic physiological mechanistic linkages of how climate change may impact the SE Tanner crab stocks. 

# Data and analysis
RNA sequence data from a pooled _C. bairdi_ hemolymph sample (Day 26, infected and uninfected, cold and ambient) was received from the Northwest Genomics Centeer (NWGC) at the University of Washington. The data came in the form of .fastq files with sequence reads for both the forward and reverse of the pooled sample. 

The sequence reads were assmebled into a transcriptome using Trinity. The assembled transcriptome was compared to uniprot/swissprot (database of known proteins) and a nucleotide database with taxonomy information using BLAST (Basic Local Alignment Search Tool). The BLAST output from the comparison with the protein database was annotated using GO (gene ontology) terms, which tells us what genes are present, and what their functions are. The BLAST output from the nucleotide taxonomy database was used to identify what was in the sample, and we found that _Hematodinium_ genetic material was present. 

![img](https://github.com/fish546-2018/grace-Cbairdi-transcriptome/blob/master/images/F546-flowchart.png)

# Visualizations
### Figure 1. Pie Chart of Library 01 GOslim term composition
![img](https://github.com/fish546-2018/grace-Cbairdi-transcriptome/blob/master/images/GOslim-pie-lib01.png)

**Fig. 1** The composition of genes expressed categorized by their function. 

This pie chart was made in [excel](http://owl.fish.washington.edu/scaphapoda/grace/Blastquery-GOslim-sep.xlsx) based on the number of proteins counted for each GOslim category with this file: [Blastquery-GOslim-sep.csv](https://github.com/fish546-2018/grace-Cbairdi-transcriptome/blob/master/analyses/Blastquery-GOslim-sep.csv), which is the output file with columns tab delimited [using R](https://github.com/fish546-2018/grace-Cbairdi-transcriptome/blob/master/scripts/plots.R) from this python notebook: [11052018-C_bairdi-blastn.ipynb](https://github.com/fish546-2018/grace-Cbairdi-transcriptome/blob/master/notebooks/11052018-C_bairdi-blastn.ipynb).

### Figure 2. Pie chart of Library 01 Taxa proportions
<p align="center">
  <img width="460" height="425" src="https://github.com/fish546-2018/grace-Cbairdi-transcriptome/blob/master/images/taxa-proportions.png">
</p>

**Fig. 2** Taxonomy proportions highlighting crab and _Hematodinium_ relative composition. 

This pie chart was made using the [output](http://gannet.fish.washington.edu/seashell/bu-mox/analyses/1114b/cg-trinity-nt.tab) from the BLAST of the assembled crab transcriptome with a ```nt``` database that includes taxonomy data. The "crab-related" proportion was found by using ```grep("crab", tax$common_name)``` in the column with the animal common names. The "Hematodinium sp." proportion was found in the same way. The "other" category lumps all the other taxonomy groups, since we are interested in the composition of _Hematodinium sp._ and crab-related proteins. (Made using this script: [taxa_breakdown.R](https://github.com/fish546-2018/grace-Cbairdi-transcriptome/blob/master/scripts/taxa_breakdown.R)). 

### Figure 3. WORD CLOUD
<p align="center">
  <img width="460" height="300" src="https://github.com/fish546-2018/grace-Cbairdi-transcriptome/blob/master/images/taxa-wordcloud.png">
</p>

**Fig. 3** Word cloud showing the taxonomy groups that resulted from the ```nt``` taxonomy database BLAST with the assembled _C. bairdi_ transcriptome. The more frequently the term appears in the output file, the larger the text size. Made by Steven. 

### Table 1. Trinity Assembly Output
| Trinity           | Assembly | Summary               | Stats    |
|:------------------|:---------|:----------------------|:---------|
| Number of Contigs:| 143,172  | Average contig length:| 873.95	  |
| Contig N50:       | 1539     | Assembled bases:      | 69687682 |

**Table 1** Summary statistics from the Trinity _de novo_ transcriptome assembly. Contig N50 value means that at least half of the assembled bases are found in contigs that are at least 1539 in length. 

Made using [Cbairdi_01_transrate-trinitystats.ipynb](https://github.com/fish546-2018/grace-Cbairdi-transcriptome/blob/master/notebooks/Cbairdi_01_transrate-trinitystats.ipynb)


# Next Steps
- Create RNAseq libraries that are specific to infection-status and temperature regime
- Assemble and analyze transcriptomes to identify crab response genes
- Identify target host and parasite genes to perform qPCR

## Repository structure and Contents
[analyses](https://github.com/fish546-2018/grace-Cbairdi-transcriptome/tree/master/analyses)
- output files from R, FastQC, trinity, transrate
- Pie charts from taxonomy analyses
- Word cloud from taxonomy analysis

[data](https://github.com/fish546-2018/grace-Cbairdi-transcriptome/tree/master/data)
- .fastq files from the _C. bairdi_ pooled RNA sample that was library-prepped and sequenced at the NWGC. 
These files are a small subset of the total data because my laptop downloaded unzipped, severely shortened versions of the RNAseq data. 
- query.fa
For practice, I assembled the short .fastq files into a transcriptome and renamed as query.fa for BLAST
- 1031-cbairdiblast-sprot.tab
For practice, I used BLAST to compare the short query.fa with uniprot-sprot

[images](https://github.com/fish546-2018/grace-Cbairdi-transcriptome/tree/master/images)    
- figures from analyses (pie charts and word cloud) 
- flow chart of RNAseq analysis

[notebooks](https://github.com/fish546-2018/grace-Cbairdi-transcriptome/tree/master/notebooks)
- Jupyter notebooks used for analyses

[scripts](https://github.com/fish546-2018/grace-Cbairdi-transcriptome/tree/master/scripts)
- R scripts used for analyses
- .sh scripts for running jobs on Mox

## Project Timeline (FISH 546 Fall Quarter 2018)
- Week 4: FastQC files and assemble using Trinity on Mox; set up script for running BLAST once assembly is complete
- Week 5: Run BLAST with protein database, and classify according to biological function using GO terms and GO Slim terms 
