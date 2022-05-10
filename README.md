# Reproduction Project: Mining and Local Corruption in Africa (Knutsen et al. 2018).

Revised Reproducation Project Authors: Charlotte Zell, Jane Angar, Zejun Chen.

Paper Selected:
Knutsen, C. H., Kotsadam, A., Olsen, E. H., & Wig, T. (2017). Mining and local corruption in Africa. American Journal of Political Science, 61(2), 320-334.
DOI: 10.1111/ajps.12268 
Link: https://doi.org/10.1111/ajps.12268

Original Reproduction Package Link: https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/ZSYWHO

In the "revised reproduction package for - Mining and Local Corruption in Africa - Angar, Chen, Zell - 2022" folder, there are 2 sub-folders:
       
**1. Original Reproduction Package:** 
It contains the authors' original replication package, which can be downloaded directly from this link: 
https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/ZSYWHO. Files included in this folder are:

(a) Description of how to buy/access original source data from RMD and Afrobarometer (Access.pdf)

(b) Codebook of variables (CodebookMiningAJPS.pdf) 

(d) Analysis datasets (mininglocal.dta; mininglocal_nw.dta)

(e) Analysis code (analysis.do)

(f) Description of the geocoding procedure (Geocoding.pdf)

(g) Description of the construction of the night-time lights data (Creation of light dataset.pdf)

(h) Statetement on restricted data from Afrobarometer (Statement Afrobarometer.docx)

(i) Statement on restricted data from SNL Metals & Mining (Statement SNL.pdf)

(j) The original readme file (README - original reproduction package.txt)

**2. Revised Reproduction Package:** It contains our codes for improvements and additional robustness tests. 

(a) Improvement 1- Analysis code in R for Table 1-3 (MainReproductionCodeTables.dta)
- We sucessfully translated the majority of STATA codes to R for Table 1-3; however, we failed to reproduce the F-statistics and p-values for Table 1 and                 the F-statistics for Table 3. This remains an area of improvement for future reproducers. For replication of Table 1-3 presented in the main context of                 the paper, researchers can use "mininglocal.dta" or "mininglocal_nw.dta" datasets in the original reproduction package and run our codes.

(b) Improvement 2 - Analysis Code for Table 2 with Only Mine and Year Fixed Effects in R (Table 2 Improvement.dta)
- For Table 2, the authors' description of their regression analysis has some inconsistency. For the regression equation they present on page 328, the                   authors include all three sets of fixed effects: year, country, and mine fixed effects. However, in the description note provided at the bottom of                     Table 2 on page 330, they mention only two sets of fixed effects：year and mine fixed effects. Athough they include all three fixed effects in their                   original STATA codes. We suspect that in the case of Table 2, adding all three fixed effects may be theoretically inaccurate as it is designed to                       specifically estimate mine fixed effect. In addition, the variations of dependent variables explained by mine fixed effects alone should be largely                     the same as mine fixed effects plus country fixed effects, as variations are absorbed by lower level of locations. 
- We thus created this additional version of Table 2 (Table 2 Improvement), one with mine and year fixed effects but without country fixed effects. The results 
  do not differ much between the specification we used in (a)MainReproductionCodeTables and this additional version; however, like the authors we believe it is 
  preferable to only include mine fixed effects and year fixed effects.

(c) Additional Robustness Test - Analysis Code with Suspended Mines (SuspendedMinesRobustness.dta)
- We conducted analysis for Table 1-3 with suspended mines, which were excluded by the authors from the original analysis. This variation shows results                   with the full control group.

(d) Analytical Data (mininglocal)
- This is the same analytical dataset as the one in the original reproduction package. We have it here for the convenience of reproduction.
              
