[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.14024548.svg)](https://doi.org/10.5281/zenodo.14024548)

# The Archaeoriddle

If you don't know where to start, you may want to have a look at [thearchaeoriddle.org](https://thearchaeoriddle.org/)!

## Preamble

The Archaeoriddle Project has been implemented and developed by the [Computational and Digital Archaeology Lab](https://www.arch.cam.ac.uk/research/laboratories/cdal) at the McDonald Institute, University of Cambridge, based on ideas from Enrico Crema and Xavier Rubio-Campillo. It is primarily funded by a grant from the British Academy (SRG2223\230262) and the Marie Skłodowska-Curie Actions (H2020-MSCA-IF No. 101020631/ArchBiMod), but would not have been possible without support from the ENCOUNTER project (ERC grant agreement No. 801953).

This repository compiles all elements developed throughout this project. They can be divided in three main components, detailed in this README:

1. [The Bookdown](#the-bookdown): a compiled version is available online [here](https://www.thearchaeoriddle.org). This standalone document details every aspect of the project. It allows the reproduction and exploration of every aspect of the project ( :file_folder: [./doc/bookdown/](./doc/bookdown/)).
2. [The Original Challenge](#the-original-challenge): one instance of archaeoriddle's simulation, including the website, data and the contributions from five participants ( :file_folder: [./doc/shinyapp/](./doc/shinyapp/) & [./doc/bookdown/data_original/](./doc/bookdown/data_original/)).
2. [The R package](#the-r-package) : contains all of the above and the underlying R functions, tests and associated documentation ( :file_folder: [./](./)).


This repository has the structure of an R package. This allows each sub-component to easily use and call all available functions and data included in the project. It also greatly simplifies the use of the different functions throughout the bookdown for anyone who would like to recreate and explore their own Archaeoriddle world.


*Note:* Version v0.1.2  of this repository is the last version that has been shared with reviewers during the revision process of the paper "Assessing the inferential power of quantitative methods in archaeology via simulated datasets: the archaeoriddle challenge", by:
Cortell-Nicolau, A., Carrignon, S., Rodríguez-Palomo, I., Hromada, D., Kahlenberg, R., Mes, A., Priss, D., Yaworsky, P., Zhang, X., Brainerd, L., Lewis, J., Redhouse, D., Simmons, C., Coto-Sarmiento, M., Daems, D., Deb, A., Lawrence D., O’Brien, M., Riede, F., Rubio-Campillo, X., Crema, E.

This version includes the modifications requested by the reviewers, archived on zenodo ([ DOI: 10.5281/zenodo.14024548](https://doi.org/10.5281/zenodo.14024547)), as well as [:file_folder: doc/figures_paper/](./doc/figures_paper/), that stores the scripts to generate the figures in the paper.

## The Bookdown

This is the main outcome of the Archaeoriddle project, detailing the sub-components. An online version is available at [www.thearchaeoriddle.org](https://www.thearchaeoriddle.org). It is associated with [forum](https://www.thearchaeoriddle.org/forum), intended as a place to discuss the and explore the project, issues encountered while using the package or to exchange ideas about inference in archaeology in general.

The Archaeoriddle bookdown guides you through the Archaeoriddle project, allowing you to follow every step and decision taken, e.g. which models have been chosen and why. Coupled with the functions provided by [the R package](#the-r-package), you will be able to use code chunks to reproduce elements of interest and create your own world, with its unique mountains, seas, and islands. You will be able to generate settlements, distribute populations that fluctuate based on parameters you will choose. The bookdown also facilitates recreating your own [challenge](#the-original-challenge). It will take you through the steps to generate your own radiocarbon deposits and create output files to share with students or colleagues to infer your original parameters.

The source for the bookdown is stored in ( :file_folder: [./doc/bookdown/](./doc/bookdown/)). This folder contains the files and documents required to compile Archaeoriddle's bookdown. It also houses the output and original files shared for the original Archaeoriddle challenge.

If you want to compile the bookdown yourself, we invite you to read [this chapter](https://thearchaeoriddle.org/index.html#compiling-the-book).

### Files & Folders for the Bookdown:

- [:file_folder: doc/bookdown/](./doc/bookdown/) : main folder.
    - [:file_folder: data_original/](./doc/bookdown/data_original/) : folder with data of the original challenge ([cf section original challenge](#the-original-challenge)).
    - [📄 01_Introduction.Rmd](./doc/bookdown/01_Introduction.Rmd) to [09_thearchaeoriddle.Rmd](./doc/bookdown/09_thearchaeoriddle.Rmd): R Markdown file with chapters of the bookdown.
    - [📄 README.md](./doc/bookdown/README.md) : README specific for the bookdown.
    - [📄 dateGeneration.R](./doc/bookdown/dateGeneration.R) : R script to automatically generate dates from the record of population size through time.
    - [📄 exploreDate.R](./doc/bookdown/exploreDate.R) : R script for exploring and analyzing date-related data.
    - [📄 index.Rmd](./doc/bookdown/index.Rmd) : Preface of the bookdown to initialise the setup, load required package etc.
    - [📄 packages.bib](./doc/bookdown/packages.bib) : bibliography listing references and packages used for the bookdown.
    - [📄 scriptmini.R](./doc/bookdown/scriptmini.R) : minimal example to run one simulation and save the results.
    - [📄 smallscript.md](./doc/bookdown/smallscript.md) : how to run multiple simulations to explore them.
    - [💾 testsites.RDS](./doc/bookdown/testsites.RDS) : not used.
    - [📄 tools.R](./doc/bookdown/tools.R) : series of functions, to be deleted as they should be all in `./R/`

If you compile the bookdown, some folders will be generated (`data_tmp` and `data_toshare`) that will be used to store the files generated during the compilation (the new world, csv outputs, etc.). Here a quick overview of what they will look like (⚠️ note that they are not tracked and stored in the git repository):

- :file_folder: doc/bookdown/data_tmp/ : data generated during the compilation of the bookdown.
    - 🌐 allsites.shp : shapefile with site locations.
    - 📄 square_1.csv to square_65.csv: list of the occupation dates generated for the squares (exact number may vary).
    - 💾 popSizeMatrix.RDS: matrix with population size for the sites at all time steps for one simulation.
    - 💾 popStructList.RDS: list representing the population structure for the sites at all time steps for one simulation.
    - 💾 wardeath.RDS: vector storing the total deaths per time step in the example simulation.
    - 💾 exn_dates.RDS: occupation dates generated in the simulations.
    - 💾 exp1_all.RDS to [exp8_all.RDS](./doc/bookdown/data_tmp/exp8_all.RDS)  : results of eight different runs in your new world.
    - 💾 exp1_sitesRast.RDS to exp8_sitesRast.RDS : site locations from eight different runs in your new world.
- :file_folder: data_toshare : data that will be shares with participants. 
    - 🌐 costline.shp: shapefile defining the coastline of the world.
    - 🗺️ dem_raster.tiff: DEM raster with elevation of your new world. 
    - 🗺️ resources.tiff: raster with the ecological fitness of the environment.
    - 📄 square_1.csv to square_5.csv: randomly selected squares shared publicly.
(reminder: these file _are not_ tracked by git, they appear _only_ if you decide to compile the bookdown)


## The Original Challenge 

The Original Challenge corresponds to a specific instance of Archaeoriddle, called 'Rabbithole'. This includes: 
- a landscape
- an 'ecological map'
- a set of parameters that have been used to conduct a set of simulations from which _one_ has been chosen

Radiocarbon deposit have been generated from this simulation and a `CSV` with a list of <sup>14</sup>C dates has been created. The map of the landscape and the ecological fitness raster, together with a selection of `CSV` files, were shared publicly with archaeologists on our website. The website is still available [here](https://theia.arch.cam.ac.uk/archaeoriddle/) as of now (01.11.2024), but will be shut down soon. However, the source to generate the website is provided [here](./doc/shinyapp/).

The participants were asked to answer three research questions:

- RQ1. What was the relationship between the two groups? Was it peaceful or hostile?
- RQ2. What was the population trajectory of each group?
- RQ3. What was the rate of dispersal of poppy chewers?

On the website, four squares representing four zones of 'Rabbithole' were available, for which data about occupation was available. Participants were able to request five additional zones to be 'excavated' and received the respective data for those zones. 

<div style="font-size: 8pt;text-align: center;">
  <figure>
    <img src="doc/bookdown/data_original/map_rh.png" alt="Map of rabbithole with square" width="40%">
    <img src="doc/bookdown/data_original/map_ex.png" alt="Map of rabbithole" width="40%">
  </figure>
<br>
<sub>Map of publicly available sites of Rabbithole: On the left, the squares available; on the right, the names and cultures of the settlements.</sub>
</div>


### Proposals

The original challenge received five proposals that can be explore via the links below. A snapshot of the proposals as submitted by the authors after the revision process is provided at [zenodo repository](https://doi.org/10.5281/zenodo.14024548). We here briefly summarize the proposals.

#### P1 by Deborah Priß and Raphael Kahlenberg

> The authors used agent-based modeling combined with exploratory data analysis to study dispersal and site preference in Rabbithole, using ArcGIS Pro and R for calibration and trajectory computation, resulting in an ABM built with NetLogo that correctly predicted group interactions and movements but revealed discrepancies in expansion rates due to differing population trajectories.

**Source:** https://github.com/dpriss/Archaeoriddle_Kahlenberg_Priss

**Citation:** Priß, D., & Kahlenberg, R. (2024). _dpriss/Archaeoriddle_Kahlenberg_Priss: Archaeoriddle Kahlenberg and Priß (v1_Archaeoriddle)._ Zenodo. https://doi.org/10.5281/zenodo.14062675


#### P2 by Xuan Zhang

> The author employed point-process modeling to predict potential occupation and assess conflict between groups, finding increased hostility and mortality over time due to growing populations and settlements, despite non-time-dependent hostility rules.

**Source:** https://github.com/Xuan-Zhang-arc/Archaeoriddle_PPM_HG_F_relationship/

**Citation:** Xuan Zhang. (2024). _Using Point Process Modelling to detect cooperation vs competition (Archaeoriddle RQ1) (Archaeoriddle)._ Zenodo. https://doi.org/10.5281/zenodo.12803445

#### P3 by Peter Yaworsky

> The author utilized species-distribution modeling in R to develop a four-stage approach that successfully modeled historical population distributions and dispersal patterns of farmers and foragers, highlighting a south-north farming dispersal and a decline in hunter-gatherer populations.

**Source:** https://doi.org/10.5281/zenodo.8260754

**Citation:** Yaworsky, P. (2023). _Archeo-Riddle Submission 2023._ Zenodo. https://doi.org/10.5281/zenodo.8260754


#### P4 by Alexes Mes:

> The author employed a friction-based strategy and hierarchical Bayesian phase modeling in R to analyze and successfully predict the complex dispersal patterns and expansion rates of Poppy-chewers in Rabbithole, incorporating spatial and environmental factors.

**Source:** https://github.com/AlexesMes/Archeaoriddle_RabbitWorld

**Citation:** Alexes, M. (2024). _Archeaoriddle RabbitWorld._ Zenodo. https://doi.org/10.5281/zenodo.14218979


#### P5 by Daniel Hromada

> The author used a qualitative analysis to infer hostility between Poppy-chewers and Rabbit-skinners by comparing the shorter settlement persistence of Rabbit-skinners in the region where Poppy-chewers exist to its persistence in other regions under equal conditions.

**Source:** [here](https://zenodo.org/records/14207474) and [here](http://dx.doi.org/10.13140/RG.2.2.10753.47207)

**Citation:** Hromada, D. (2024). _Exploring the 'Hostile vs. Peaceful' Archaeoriddle Dilemma Using the NALANA Method._ 10.13140/RG.2.2.10753.47207. 

The original challenge is detailed in [this chapter](https://thearchaeoriddle.org/original-challenge.html) of the bookdown.

### Files & Folders for the Original Challenge:

- [:file_folder: doc/shinyapp/](./doc/shinyapp/) : the code of the shiny app for the website can be accessed [here](https://theia.arch.cam.ac.uk/archaeoriddle).
    - [📄 README.md](./doc/shinyapp/README.m) : README explaining how to recreate the shiny app and detailing the files available in the folder.
- [:file_folder: doc/fake_papers/](./doc/fake_papers/) :  LaTex code for fake papers and posters to advertise the original challenge at conferences.
- [:file_folder: doc/survey_archaeoriddle/](./doc/survey_archaeoriddle/) : results and analysis of a survey to gauge interest in the project. A quick analysis is available [here](file:///home/simon/projects/archaeoriddle/doc/survey_archaeoriddle/survey_analysis.html).
- [:file_folder: doc/bookdown/data_original/](./doc/bookdown/data_original/) : orignal data
    - [:file_folder: all_squares/](./doc/bookdown/data_original/all_squares/): `CSV`s of the original challenge
		- [📄 square_1.csv](./doc/bookdown/data_original/all_squares/square_1.csv) to [square_100.csv](./doc/bookdown/data_original/all_squares/square_100.csv) : dates available for the squares of the original challenge.
    - [:file_folder: general_results_selected_simu/](./doc/bookdown/data_original/general_results_selected_simu/) :
        - [💾 buffattack300_K110_PSU065_3_all.RDS](./doc/bookdown/data_original/general_results_selected_simu/buffattack300_K110_PSU065_3_all.RDS) : results of the selected simulation.
        - [💾 buffattack300_K110_PSU065_3_sitesRast.RDS](./doc/bookdown/data_original/general_results_selected_simu/buffattack300_K110_PSU065_3_sitesRast.RDS) : raster with site locations.
        - [💾 buffattack300_K110_PSU065_3_dates.RDS](./doc/bookdown/data_original/general_results_selected_simu/buffattack300_K110_PSU065_3_dates.RDS) : occupation dates generated for the sites generated.
    - [:file_folder: sitesinitialposition/](./doc/bookdown/data_original/sitesinitialposition/) : file required to read shapefile.
        - [🌐 sitesinitialposition.shp](./doc/bookdown/data_original/sitesinitialposition/sitesinitialposition.shp) : shapefile with initial site locations.
    - [🌐 costline.shp ](./doc/bookdown/data_original/coastline.shp) : shapefile defining the coastline of Rabbithole.
    - [🗺️ east_narnia4x.tiff](./doc/bookdown/data_original/east_narnia4x.tif) : DEM raster with elevation of Rabbithole.
    - [🗺️ resources.tiff](./doc/bookdown/data_original/resources.tiff/) : raster with the ecological fitness of the environment.


## The R-Package 

The overall structure of this repository is in the format of an R package. 

The easisest way to install it is by using the `devtools` function `github_install()`: `devtools::install_github("acortell3/archaeoriddle")`.

Most of the functions defined in the package are described in detail in [the bookdown](https://www.thearchaeoriddle.org).

The purpose of the package is to follow the bookdown or recompile it. It also allow you to easily re-use the functions defined in the package to assess the proposal of the original challenge, create your own model of interaction and explore and modify the underlying model of the Archaeoriddle project.


## Files & Folders for the R Package:

- [:file_folder: doc/](./doc/): documents, websites, etc. (cf below)
- [:file_folder: div/](./div/): scripts
    - [📄 post-receive-hook](./div/post-receive-hook): script to automatically deploy the bookdown when pushes are made to the git repository.
- [:file_folder: .github/](./.github/): github-specific files
    - [📄 .github/workflows/deploy_bookdown.yml](./.github/workflows/deploy_bookdown.yml): `YML` file to automatically deploy the bookdown via github.
- [:file_folder: man/](./man/): R documentation (cf below)
- [:file_folder: R/](./R/): source file of R package (cf below)
- [📄 DESCRIPTION](./DESCRIPTION): R-package-related file
- [📄 archaeoriddle.Rproj](./archaeoriddle.Rproj): R-package-related file
- [📄 NAMESPACE](./NAMESPACE): R-package-related file
- [📄 README.md](./README.md): R-package-related file



### `doc/`

- [:file_folder: doc/bookdown/](./doc/bookdown/): cf section [The Bookdown](#the-bookdown)
- [:file_folder: doc/shinyapp/](./doc/shinyapp/): cf section [The Original Challenge](#the-original-challenge)
- [:file_folder: doc/tex_files/](./doc/tex_files//): `tex` files to lay out ideas.
- [:file_folder: doc/figures_paper/](./doc/figures_paper/): scripts to generate the figures in the paper and output of the scripts. 
    - [:file_folder: doc/figures_paper/Figure1/](./doc/figures_paper/Figure1/): layers used in Figure 1. Layers have been manually grouped together using [Inkscape version 1.2.2 (b0a8486541, 2022-12-01)](http://inkscape.org)).
- [🖼️  brain_map_colabm.png](./doc/brain_map_colabm.png) : image representing early reflections about the project.
- [📄 Explanation_of_ideas_brain_map.md](./doc/Explanation_of_ideas_brain_map.md): Markdown detailing programming languages, world options, and more.
- [📄 interactive_brain_map.md](./doc/interactive_brain_map.md): Markdown guide for using Markmap visualization; contains programming language options, and more.
- [📄 pop_id.Rmd](./doc/pop_id.Rmd): R Markdown specifying population ideas and environmental qualities for hunting/farming.

### `man/`
- [📄 A_rates.Rd](./man/A_rates.Rd),[📄 Gpd.Rd](./man/Gpd.Rd) and all other `Rd` files: files automatically generated by `ROxygen` to generate `R` documentation (shown when using `?Gpd` when the package is loaded`).

### `R/`

- [📄 anthropogenic_deposition.R](./R/anthropogenic_deposition.R): simulates anthropogenic bone deposition rates at a site.
- [📄 climate.R](./R/climate.R): generates power-law noise and simulates environmental fluctuations.
- [📄 init_simulation.R](./R/init_simulation.R): initializes carrying capacities, population matrices, and site lists for simulations.
- [📄 logistic_decay.R](./R/logistic_decay.R): applies logistic decay to resources around points in a raster.
- [📄 natural_deposition.R](./R/natural_deposition.R): models deposition and post-deposition effects of archaeological materials.
- [📄 perlin_noise.R](./R/perlin_noise.R): creates Perlin noise for 2-D slope and elevation autocorrelation.
- [📄 population.R](./R/population.R): manages stochastic population dynamics, growth, and mortality.
- [📄 record_loss.R](./R/record_loss.R): simulates taphonomic losses in archaeological records.
- [📄 run_simulation.R](./R/run_simulation.R): runs a simulation of cultural interactions, migration, and conflicts.
- [📄 tools.R](./R/tools.R): utility functions for visualization, data extraction, and map plotting.

