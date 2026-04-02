# EIC-DRICH PID analysis using IRTv2
- Analysis done by: 
    - Deepak Samuel, Christy Elsa Koshy and Meghna Majumdar, Central University of Karnataka
- EIC Version and details:  
    - ```./eic-shell -v 25.10.0-stable```
    - ```. EICrecon/irt-sandbox/environ.sh```

- Simulation details:
    - Used CUK GPU server with 50 cores, full analysis from hepmc generation to reco took about 4 days.
    - 4662 files of 1000 events each, phi smeared

    - Bins as in 
    https://docs.google.com/spreadsheets/d/1qNh3giwhRENJi25z45lgeh5d7QwIw5Uy3lepISHCv9Y/edit?gid=2032570815#gid=2032570815

        | Eta Bin | Eta Bins | Eta | bin begin | bin end |
        |:---|:---|:---|:---|:---|
        | 0 | 1.5 | 1.5 | 1.499 | 1.501 |
        | 1 | 1.6 | 1.6 | 1.599 | 1.601 |
        | 2 | 1.7 | 1.7 | 1.699 | 1.701 |
        | 3 | 1.8 | 1.8 | 1.799 | 1.801 |
        | 4 | 1.9 | 1.9 | 1.899 | 1.901 |
        | 5 | 2.0 | 2.0 | 1.999 | 2.001 |
        | 6 | 2.1 | 2.1 | 2.099 | 2.101 |
        | 7 | 2.2 | 2.2 | 2.199 | 2.201 |
        | 8 | 2.3 | 2.3 | 2.299 | 2.301 |
        | 9 | 2.4 | 2.4 | 2.399 | 2.401 |
        | 10 | 2.5 | 2.5 | 2.499 | 2.501 |
        | 11 | 2.6 | 2.6 | 2.599 | 2.601 |
        | 12 | 2.7 | 2.7 | 2.699 | 2.701 |
        | 13 | 2.8 | 2.8 | 2.799 | 2.801 |
        | 14 | 2.9 | 2.9 | 2.899 | 2.901 |
        | 15 | 3.0 | 3.0 | 2.999 | 3.001 |
        | 16 | 3.1 | 3.1 | 3.099 | 3.101 |
        | 17 | 3.2 | 3.2 | 3.199 | 3.201 |
        | 18 | 3.3 | 3.3 | 3.299 | 3.301 |
        | 19 | 3.4 | 3.4 | 3.399 | 3.401 |
        | 20 | 3.5 | 3.5 | 3.499 | 3.501 |

    - Phi: smeared randomly

    - Momentum (GeV):  
        - From 0.5 to 31.0: Increments by 0.5 
        - From 32.0 to 50.0: Increments by 2.0
        - From 55.0 to 60.0: Increments by 5.0

    - pid_range=[211,2212,321]

    
    - The `drich-reco.json` and `drich-calibration.json` were copied from the irt-sandbox folder and  the following flag was set to yes `"IntegratedReconstruction": "yes"` before running the simulation.

    Following changes were also made:

    - "CombinedEvaluationPlots": "display", changed to
        - "CombinedEvaluationPlots": "store",
    - "evaluation-plots": "display", changed to store

    Without these changes, on a ssh-session, the display is not shown and the programs is on an infinite loop

- The reco files are about 77 GB and so cannot be hosted online. 

- The analyze-reco.ipynb files reads the reco files and creates a csv file which contains the Cerenkov angles from the fit and the associated errors.

- 02 April 2026:
    - The reconstruction analysis skipped rows where the gas or aero histograms were not present which led to confusions. 
    - The updated file is in ```1k_fit_parameters_new.csv``` and the plots are in ```irtv2_interactive_1k_new.html```