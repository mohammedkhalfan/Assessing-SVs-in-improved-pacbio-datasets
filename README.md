# Assessing-SVs-in-improved-pacbio-datasets

Datasets: 
PB New (2018): 10 kb, 15 kb. 99% correct with circular consensus filtered by QV20. 
PB Old: Not here yet. 25 kb. 85% correct pre-polishing. data > subreads > 2015. 
Depth is ~28X
Aligned to Hg2 (Adaptive gap penalty while mapping)
Truth set exists (GIAB) 

Tools (DL Y/N):
Alignment: minimap2 (Y), NGMLR (Y)
	Blasr not great for SVs. Doesn't do supplemental alignments
	The above two do supplemental alignments (multiple primaries)
PBSV can call translocations/inversions as well (Y)
	Came out a month ago
Sniffles (Y)
SMRT-SV (Y)
MetaSV (N)
TruVari- used to benchmark SV calls (Y)

Depth titration: Downsampling. Select a region. Re-align with a new aligner and use all callers.
Aligner: NGMLR vs. minimap. 
Caller: Quantify how those SV calls improve between old (sub-par reads) vs. new (new nicer reads) alignments. 

Figures:
Venn diagram OR bar-dot plot (upset plot) for concordance
Case studies: insertion, deletion, inversion, duplication
	Correct vs. incorrect 
	Called vs. uncalled

Project Flow:
- Select site: Chromosome 22
- Downsample to ?X

Workflow 1: Input is 1-2 BAMs vs. old, 1 BAM x NGMLR vs. minimap, 1-2 BAMs x ?X
B -> BAM stats -> variant caller -> TruVari

- IGV: Interesting gene to focus in on- MUC2 (~100KB gene, chromosome 11 p-arm)
- R

Analysis: 
How much better is the new vs. old BAM? 
How much better is one aligner?
How much better is increased coverage? 
