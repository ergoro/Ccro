# The need for corporate chief resilience officers

## 1. Project Overview
This research project has two research modules:
1. Estimation of total factor productivity
2. Distribution dynamics analysis

This research project is managed in the following platforms:
- [Google Docs](https://docs.google.com/document/d/1W1RfKarkPBdWVro2TD5QKg3dTj3GxVH9yQ9nsY9nvos/edit?usp=sharing) (for manuscript)
- [Zotero](https://www.zotero.org/groups/5969876/resilieceofficers) (for references)
- [Google Meet](https://duo.app.goo.gl/yrH6bq5cIBhPRk6mdnObT9) (for video meetings)

## 2. Data Sources and sample
The data source is the World Bank's Enterprise Survey (ES) dataset for Brazil corresponding to the years 2003 and 2009 (unbalanced panel data). ES provides an extensive array of data at the firm level. For instance, useful information for measuring firms' performance and aspects of the investment climate, among others, could be found. Data is collected from a representative sample of an economy's private sector. Through a stratified random sample process, firms in the manufacturing and services sectors in major cities and localities are selected (data does not include the agricultural sector). More info at Enterprise Surveys (http://www.enterprisesurveys.org), The World Bank.

An exploratory analysis was conducted. [Here](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/TFP-estimation/FPD_Brazil_2017_04_20_PI.pdf) is a summary about the number of observations by year, city and sector.

Based on the previous information, it was decided to estimate Total Factor Productivity (TFP) for the following sectors:
1. ISIC 18: Manufacture of wearing apparel; dressing and dyeing of fur
2. ISIC 36: Manufacture of furniture; manufacturing n.e.c.

## 3. Total Factor Productivity (TFP) Estimation

This module contains two sections

### Building the dataset and calculating variables
- Inputs
  - [Data (.dta file)](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/Build_database/Brazil_2003_2009_panel.dta)
- Code
  - [build_dataset_master](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/Build_database/pdf_brazil_build_dataset_main.do)
  - [code and sectors](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/Build_database/pdf_brazil_sectors_isic2.do)
  - [generate variables](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/Build_database/pdf_brazil_genvars.do)
  - [cleaning](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/Build_database/pdf_brazil_clean.do)
  - [descriptive stats](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/Build_database/pdf_brazil_describe.do)
  - [build dataset for TFP](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/Build_database/create_smaller_dataset.do)
- Outputs
  - [Dataset with required vars for TFP calculation (.dta file)](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/Estimating_TFP/brazil_smaller_dataset_ES.dta)

### Estimating TFP

#### Calculations based on ALL data available
- Inputs
  - [Data (.dta file)](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/Estimating_TFP/brazil_smaller_dataset_ES.dta)
- Code
  - [master](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/Estimating_TFP/pdf_brazil_tfp_main.do)
  - [estimation production function](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/Estimating_TFP/pdf_brazil_prodfunction.do)
  - [calculate tfp](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/Estimating_TFP/pdf_brazil_tfp.do)
  - [create balanced panel](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/Estimating_TFP/pdf_brazil_firm_tfp_year_data.do)
  - [reshape and relative productivity](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/Estimating_TFP/pdf_brazil_tfp_reshape_rel_prod.do)
- Outputs
  - [TFP for ISIC 18 (.csv file)](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/Estimating_TFP/Brazil_2003_2009_panel_TFP_ISIC18.csv)
  - [TFP for ISIC 18 only MSME (.csv file)](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/Estimating_TFP/Brazil_2003_2009_panel_TFP_ISIC18_MSME.csv) Cut-off of 250 employess based on this [study](https://smefinanceforum.org/data-sites/msme-country-indicators).
  - [TFP for ISIC 36 (.csv file)](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/Estimating_TFP/Brazil_2003_2009_panel_TFP_ISIC36.csv)
  - [TFP for ISIC 36 only MSME (.csv file)](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/Estimating_TFP/Brazil_2003_2009_panel_TFP_ISIC36_MSME.csv) Cut-off of 250 employess based on this [study](https://smefinanceforum.org/data-sites/msme-country-indicators).

#### Calculations based ONLY on firms with complete data for both years
- Inputs
  - [Data (.dta file)](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/Estimating_TFP/brazil_smaller_dataset_ES.dta)
- Code
  - [master](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/Estimating_TFP/pdf_brazil_tfp_main.do)
  - [calculate tfp_strict](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/Estimating_TFP/pdf_brazil_tfp_strict.do)
  - [create balanced panel_strict](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/Estimating_TFP/pdf_brazil_firm_tfp_year_data_strict.do)
  - [reshape and relative productivity_strict](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/Estimating_TFP/pdf_brazil_tfp_reshape_rel_prod_strict.do)
- Outputs
  - [TFP for ISIC 18_STRICT (.csv file)](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/Estimating_TFP/Brazil_2003_2009_panel_TFP_ISIC18_STRICT.csv)
  - [TFP for ISIC 36_STRICT (.csv file)](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/Estimating_TFP/Brazil_2003_2009_panel_TFP_ISIC36_STRICT.csv)

## 4. Distribution Dynamics Analysis

- [Basic Convergence and Mobility Facts for the Sector 18](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/journal-manuscript/figs/fig-sc-18.png)
- [Basic Convergence and Mobility Facts for the Sector 36](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/journal-manuscript/figs/fig-sc-36.png)

### 4.1 ACF approach for ISIC 18
- [Inputs](https://github.com/cmg777/firm-tfp-convergence-brazil/tree/master/distribution-dynamics-brazil/%20ISIC18LC-acf/inputs)
  - [Data for the distribution dynamics analysis](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/distribution-dynamics-brazil/%20ISIC18LC-acf/inputs/data.csv)
  - [Data for the mobility scatter plot](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/distribution-dynamics-brazil/%20ISIC18LC-acf/inputs/dataMobility.csv)
- Code:
  - [create distribution dynamics figures](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/distribution-dynamics-brazil/%20ISIC18LC-acf/RUN_convergence123.m)
  - [create simple mobility scatter plot](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/distribution-dynamics-brazil/%20ISIC18LC-acf/fig-mobility-scatter-plot.R)
- [Outputs](https://github.com/cmg777/firm-tfp-convergence-brazil/tree/master/distribution-dynamics-brazil/%20ISIC18LC-acf/outputs)
  - [Summary Figure](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/distribution-dynamics-brazil/%20ISIC18LC-acf/outputs/ACF-approach-for-SIC-18.png)

### 4.2 STCH approach for ISIC 18
- [Inputs](https://github.com/cmg777/firm-tfp-convergence-brazil/tree/master/distribution-dynamics-brazil/%20ISIC18LC-stch/inputs)
  - [Data for the distribution dynamics analysis](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/distribution-dynamics-brazil/%20ISIC18LC-stch/inputs/data.csv)
  - [Data for the mobility scatter plot](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/distribution-dynamics-brazil/%20ISIC18LC-stch/inputs/dataMobility.csv)
- Code:
  - [create distribution dynamics figures](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/distribution-dynamics-brazil/%20ISIC18LC-stch/RUN_convergence123.m)
  - [create simple mobility scatter plot](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/distribution-dynamics-brazil/%20ISIC18LC-stch/fig-mobility-scatter-plot.R)
- [Outputs](https://github.com/cmg777/firm-tfp-convergence-brazil/tree/master/distribution-dynamics-brazil/%20ISIC18LC-stch/outputs)
  - [Summary Figure](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/distribution-dynamics-brazil/%20ISIC18LC-stch/outputs/STCH-approach-for-SIC-18.png)

### 4.3 LP approach for ISIC 18
  - [Inputs](https://github.com/cmg777/firm-tfp-convergence-brazil/tree/master/distribution-dynamics-brazil/%20ISIC18LC-lp/inputs)
    - [Data for the distribution dynamics analysis](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/distribution-dynamics-brazil/%20ISIC18LC-lp/inputs/data.csv)
    - [Data for the mobility scatter plot](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/distribution-dynamics-brazil/%20ISIC18LC-lp/inputs/dataMobility.csv)
  - Code:
    - [create distribution dynamics figures](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/distribution-dynamics-brazil/%20ISIC18LC-lp/RUN_convergence123.m)
    - [create simple mobility scatter plot](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/distribution-dynamics-brazil/%20ISIC18LC-lp/fig-mobility-scatter-plot.R)
  - [Outputs](https://github.com/cmg777/firm-tfp-convergence-brazil/tree/master/distribution-dynamics-brazil/%20ISIC18LC-lp/outputs)
    - [Summary Figure](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/distribution-dynamics-brazil/%20ISIC18LC-lp/outputs/LP-approach-for-SIC-18.png)

### 4.4 ACF approach for ISIC 36
- [Inputs](https://github.com/cmg777/firm-tfp-convergence-brazil/tree/master/distribution-dynamics-brazil/%20ISIC36LC-acf/inputs)
  - [Data for the distribution dynamics analysis](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/distribution-dynamics-brazil/%20ISIC36LC-acf/inputs/data.csv)
  - [Data for the mobility scatter plot](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/distribution-dynamics-brazil/%20ISIC36LC-acf/inputs/dataMobility.csv)
- Code:
  - [create distribution dynamics figures](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/distribution-dynamics-brazil/%20ISIC36LC-acf/RUN_convergence123.m)
  - [create simple mobility scatter plot](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/distribution-dynamics-brazil/%20ISIC36LC-acf/fig-mobility-scatter-plot.R)
- [Outputs](https://github.com/cmg777/firm-tfp-convergence-brazil/tree/master/distribution-dynamics-brazil/%20ISIC36LC-acf/outputs)
  - [Summary Figure](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/distribution-dynamics-brazil/%20ISIC36LC-acf/outputs/ACF-approach-for-SIC-36.png)

### 4.5 STCH approach for ISIC 36
- [Inputs](https://github.com/cmg777/firm-tfp-convergence-brazil/tree/master/distribution-dynamics-brazil/%20ISIC36LC-stch/inputs)
  - [Data for the distribution dynamics analysis](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/distribution-dynamics-brazil/%20ISIC36LC-stch/inputs/data.csv)
  - [Data for the mobility scatter plot](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/distribution-dynamics-brazil/%20ISIC36LC-stch/inputs/dataMobility.csv)
- Code:
  - [create distribution dynamics figures](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/distribution-dynamics-brazil/%20ISIC36LC-stch/RUN_convergence123.m)
  - [create simple mobility scatter plot](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/distribution-dynamics-brazil/%20ISIC36LC-stch/fig-mobility-scatter-plot.R)
- [Outputs](https://github.com/cmg777/firm-tfp-convergence-brazil/tree/master/distribution-dynamics-brazil/%20ISIC36LC-stch/outputs)
  - [Summary Figure](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/distribution-dynamics-brazil/%20ISIC36LC-stch/outputs/STCH-approach-for-SIC-36.png)

### 4.6 LP approach for ISIC 36
  - [Inputs](https://github.com/cmg777/firm-tfp-convergence-brazil/tree/master/distribution-dynamics-brazil/%20ISIC36LC-lp/inputs)
    - [Data for the distribution dynamics analysis](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/distribution-dynamics-brazil/%20ISIC36LC-lp/inputs/data.csv)
    - [Data for the mobility scatter plot](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/distribution-dynamics-brazil/%20ISIC36LC-lp/inputs/dataMobility.csv)
  - Code:
    - [create distribution dynamics figures](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/distribution-dynamics-brazil/%20ISIC36LC-lp/RUN_convergence123.m)
    - [create simple mobility scatter plot](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/distribution-dynamics-brazil/%20ISIC36LC-lp/fig-mobility-scatter-plot.R)
  - [Outputs](https://github.com/cmg777/firm-tfp-convergence-brazil/tree/master/distribution-dynamics-brazil/%20ISIC36LC-lp/outputs)
    - [Summary Figure](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/distribution-dynamics-brazil/%20ISIC36LC-lp/outputs/LP-approach-for-SIC-36.png)


## 5. Working Paper Version

### Document in Overleaf
- [Link (read and edit)](https://www.overleaf.com/8268233vzwcbppkgzkr)

### Bibliography in Mendeley
- [Link (add and administer papers)](https://www.mendeley.com/community/fpp-1/)
- [References, updated 16 January 2018 (.bib file)](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/working-paper/FPD.bib)


## 6. Manuscript for the Economics Bulletin
- [Manuscript in LyX](https://github.com/cmg777/firm-tfp-convergence-brazil/blob/master/journal-manuscript/journal-manuscript.lyx)

### Journal Guidelines
- [Economics Bulletin (main page)](http://www.accessecon.com/pubs/eb/)
- [Economics Bulletin (authors' guidelines)](http://www.accessecon.com/Store/Economics%20Bulletin%20author%20guildlines-2012.pdf)
