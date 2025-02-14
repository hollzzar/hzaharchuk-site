---
title: 'From EEG to ERP: Processing pipeline with MATLAB and R'
date: 2021-03-11
permalink: /posts/2011/03/Southern-dialect/
tags:
	- MATLAB
	- R
	- ANOVA
	- ERP
	- Visualization
---

[My lab](https://sites.psu.edu/bildlab/) uses a combined NeuroScan and Brain Vision system with 31 active Ag/AgCl electrodes and two bipolar channels. I developed the processing pipeline presented here for my first EEG/ERP experiment on dialectal variation in syntax (double modal [DM] versus single modal [SM] constructions) in two groups of participants (Unmarked [MAE] and Southern [SUSE]).

1. I adapted a MATLAB script from my former labmate [Carla Fernandez](https://www.linkedin.com/in/carla-fernandez-5ab404bb/), currently a post-doc at Duke University, to [pre-process CNT files](https://github.com/hollzzar/eeg-data-scripts/blob/master/DM_process.m) for analysis. I also developed [this MATLAB script](https://github.com/hollzzar/eeg-data-scripts/blob/master/DM_process_half.m) to separate the first and second halves of the experiment for an analysis of adaptation effects.
2. I wrote [this MATLAB script](https://github.com/hollzzar/eeg-data-scripts/blob/master/DM_analysis.m) to calculate average ERPs in each time window for each subject, both for the main analysis and first/second half analysis, and  grand averages for plotting. The script exports the processed data as TXT files for use in R.
3. [This R script](https://github.com/hollzzar/erp-data-scripts/blob/main/1a_group_analysis.R) uses the processed data from MATLAB to run a series of within- and between-group ANOVAs, format the results according to APA guidelines, and create data tables that can be passed onto the plotting scripts, output to CSV files, and joined with the cleaned behavioral data for correlation analyses. [This R script](https://github.com/hollzzar/erp-data-scripts/blob/main/1b_group_analysis_halves.R) compares the first and second halves of the experiment. The ANOVAs were run in two time windows, corresponding to the early anterior negativity (EAN) and P600 components, and in two sets of electrodes: midline (Fz, Cz, Pz) and lateral (LP, RP, LF, RF).
4. Two additional scripts work together to [set up plotting parameters](https://github.com/hollzzar/erp-data-scripts/blob/main/2_plot_format.R) and [generate butterfly plots](https://github.com/hollzzar/erp-data-scripts/blob/main/3_erp_plots.R). These scripts pull the significance levels of the analyses in each time window and group and adds them to the ERP plots automatically. Here is an example of the final plot from my Southern participant group: ![Southern group butterfly plot](/images/SUSE_erp.png)
5. Contrary to my primary hypothesis, the Unmarked and Southern groups did not display any differences in their ERP effects. After a reviewer asked whether I had sufficient power to detect a difference, I learned how to calculate Bayes factors, and thought I would share what I learned! You can find one of my examples with descriptions [here](https://htmlpreview.github.io/?https://github.com/hollzzar/erp-data-scripts/blob/main/4_bayes_example.html).