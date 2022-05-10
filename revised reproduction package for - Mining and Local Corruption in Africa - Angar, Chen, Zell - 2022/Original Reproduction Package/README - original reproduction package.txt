=======================================================
README file for "Mining and Local Corruption in Africa"
=======================================================



NOTE: We submit two ``replication packages": One that contains all the data used
to construct the dataset and run the analysis, which also includes restricted 
access information (and is not for public consumption) (NAME HERE), and one that 
contains the replication files that are intended for public consumption 
(NAME HERE). Hence, while both are submitted for review, only one will be posted 
on the dataverse page. We have informed the editor about this, and made the 
relevant arrangements.



-------------------------------------------------------------------------------
Ia) List of files included in full replication package (restricted access).
-------------------------------------------------------------------------------

1. Description of how to buy/access original source data from RMD and 
	Afrobarometer (Documentation/Access.pdf)
2. Codebook of variables (Documentation/CodebookMiningAJPS.pdf) 
3. Analysis datasets (Data/mininglocal.dta; Data/mininglocal_nw.dta)
4. Analysis code (master.do; mininglocal_data.do; Code/analysis.do)
5. Data construction code (
	Code/00_cleaning_afro.do;
	Code/01a_import_mines.do;
	Code/01b_append_mines.do;
	Code/02a_prenearstat.do;
	Code/02b_nearstat.do;
	Code/02c_postnearstat.do;
	Code/03_production_loop.do;
	Code/04_prices.do;
	Code/05_analysis_dataset.do
   )
6.
7. Source files for mininglocal.dta (
	*Data/Afrobarometer/rX_merged_geocoded.dta; 
	*Data/Afrobarometer/all_rounds_small.dta;
	*Data/Afrobarometer/r3_nunn.dta; 
	*Data/Afrobarometer/r4_deconinck.dta;
	Data/Afrobarometer/WP_All_Base_ACFcorrect_MeanC.xlsx;
	*Data/Mines/RMD/`country'.xlsx;
	*Data/Mines/SNL/latlon_snl.dta;
	Data/Mines/dia_analysis.dta;
	Data/Mines/usgs_analysis.dta;
	Data/Oil/SJ_AB_oil.txt;
	Data/qog_std_ts_jan15.dta;
	Data/NTL_collapsed.dta;
	*Data/Prices/coal_price.xlsx;
	Data/Prices/ds140-MINERAL.xlsx
   )
8. Description of geocoding procedure (Documentation/Geocoding.pdf)
9. Description of nighttime lights (Documentation/Creation of light dataset.pdf)
10. Statetement on restricted data from Afrobarometer 
	(Documentation/Statement Afrobarometer.docx)
11. Statement on restricted data from SNL Metals & Mining 
	(Documentation/Statement SNL.pdf)
12. This readme file (README.txt)

*******Various original datasets, source files etc,)

Please note that all files marked with * will be made available from the authors
provided that  
	A) Data are bought from SNL and/or 
	B) Permission for usage is granted from Afrobarometer (see elaboration in 
		document 1.)
	C) Permission is granted by Koen Deconinck and Nathan Nunn 
		for the coordinates from their respective papers

-------------------------------------------------------------------------------
Ib) List of files included in the table replication package (public access).
-------------------------------------------------------------------------------

1. Description of how to buy/access original source data from RMD and 
	Afrobarometer (Access.pdf)
2. Codebook of variables (CodebookMiningAJPS.pdf) 
3. Analysis datasets (mininglocal.dta; mininglocal_nw.dta)
4. Analysis code (analysis.do)
5. Description of the geocoding procedure (Geocoding.pdf)
6. Description of the construction of the nighttime lights data 
	(Creation of light dataset.pdf)
7. Statetement on restricted data from Afrobarometer 
	(Statement Afrobarometer.docx)
8. Statement on restricted data from SNL Metals & Mining (Statement SNL.pdf)
9. This readme file (README.txt)

----------------------------------------------------------------------------
II) Information on how to replicate findings, including on sequence in which 
	files need to be run
----------------------------------------------------------------------------

1. Automated replication procedure
----------------------------------
The findings can be replicated from their source files by running the file 
"master.do", after replacing the path to the replication package in line 10. 
This file automatically executes "mininglocal_data.do", which in turn executes 
the necessary do-files for constructing the data from the original source 
(or as close to the original source as we can get). All tables in the paper
and online appendix are produced by "analysis.do" (the file path must be edited).

The replication package is organized as a project, using project.ado, 
which among other things requires that the folder structure is preserved
and that individual files cannot, without slight modifications, be run separately.
Users who wish to run a single do-file in the list under I.5. above, should comment 
out lines beginning with "project, " and add the following line to the preamble:

local master "LOCATION OF MASTER.DO"

For replication of the tables in the paper and online appendix, researchers
can download the public access replication package, and run "analysis.do". 
The analysis datasets needed forthis procedure are included in this package.


2. Do-files and code not included in replication procedure
----------------------------------------------------------
There are some do-files and GIS programs that are not included in the automated 
replication sequence in "mininglocal_data.do", because they are somewhat auxiliary 
to the main analysis, or running them is not feasible at this time.

"usgs_nearstat.do" and "dia_nearstat.do" connects the Afrobarometer respondents
to the USGS mine-data and PRIO diamond deposit data, respectively,
using "nearstat.ado" (as in "02b_nearstat.do"). These do-files produce
"usgs_analysis.dta" and "dia_analysis.dta", which are merged in with the rest of 
the data in "05_analysis_dataset.do". "latlon_snl.do" imports coordinate data
from an xlsx file, in which we manually filled in coordinates for RMD mines
from another database from SNL based on different spellings of mine names, using
their Excel add-in.

The do-files for the geocoding procedure are included for reference in 
"Data/Afrobarometer/Geocoding". The algorithm sending requests to the Google API
seems to be not working at the moment, and so manual search is required. This is
labor intensive and therefore not feasible for most replication purposes.

There are also some do-files that perform the match between EA codes in the
Afrobarometer with the shapefiles from Statistics South Africa. These are
"rX_match.do", "import_from_gis.do" and "Append_AP_EAs.do". These files ultimately
generate "all_rounds_small.dta", which is merged in with the main data in
"02a_prenearstat.do".

--------------------------------------------------------------
III) Information on software and version used for the analysis 
--------------------------------------------------------------

The analysis and data construction code is written in Stata 13 SE, so users
should have some version of Stata 13 or higher.

All necessary user written programs are automatically installed by the dofiles,
if not already present:
	1. project.ado
	2. fs.ado
	3. carryforward.ado
	4. kountry.ado
	5. nearstat.ado
	6. ivreg2.ado

----------------------------------
IV) References for source datasets
----------------------------------

Raw Materials Data. Copyright: SNL Metals & Mining, Stockholm, 2014

SNL Excel add-in. Copyright: SNL Metals & Mining, 2014.

Afrobarometer Data, [Algeria, Benin, Botswana, Burkina Faso, Burundi, Cameroon, 
	Cape Verde, Cote d'Ivoire, Egypt, Ghana, Guinea, Kenya, Lesotho, Liberia, 
	Madagascar, Malawi, Mali, Mauritius, Morocco, Mozambique, Namibia, Niger, 
	Nigeria, Senegal, Sierra Leone, South Africa, Swaziland, Tanzania, Togo, 
	Tunisia, Uganda, Zambia, Zimbabwe], [Round 2, 2.5, 3, 4, 5], 
	[2002, 2003, 2004, 2005, 2006, 2008, 2009, 2011, 2012, 2013],
	available at http://www.afrobarometer.org.

Teorell, Jan, Stefan Dahlberg, Sören Holmberg, Bo Rothstein, Felix Hartmann &
	Richard Svensson. 2015. The Quality of Government Standard Dataset, 
	version Jan15. University of Gothenburg: The Quality of Government Institute,
	http://www.qog.pol.gu.se.
	
Marshall, M. G., Jaggers, K., & Gurr, T. R. (2014). 
	Polity iv project, political regime characteristics and transitions, 
	1800-2014.

Kaufmann, Daniel, Aart Kraay and Massimo Mastruzzi. 2010.
	The Worldwide Governance Indicators: Methodology and Analytical Issues.
	World Bank Policy Research Working Paper No. 5430

World Bank. 2015. World Development Indicators.

NOAA. 2014.DMSP-OLS Nighttime Lights Time Series
	Image and Data processing by NOAA's National Geophysical Data Center. 
	DMSP data collected by the US Air Force Weather Agency.

Lujala, Päivi; Jan Ketil Rød & Nadja Thieme, 2007. ’Fighting over Oil: Introducing
	a New Dataset’, Conflict Management and Peace Science. 24(3): 239–256. 

Statistics South Africa. 2012. Digital Census Atlas.

Ministry of Energy and Water Resources. 2012. Sierra Leone Waterpoint Report.
	accessed 09.09.2014, at http://www.sl-wash.org/.

U.S. Geological Survey, 2014, MINERAL statistics, 
	in Kelly, T.D., and Matos, G.R., comps., 
	Historical statistics for mineral and material commodities in the 
	United States: U.S. Geological Survey Data Series 140, accessed 10.08.2015, 
	at http://minerals.usgs.gov/minerals/pubs/historical-statistics/.

	(where MINERAL is one of aluminum, antimony, chromium, cobalt, copper,
	iron ore, gold, lead, manganese, nickel, phosphate, platinum, silver,
	titanium, tin, vandium, zinc, zirconium.)


