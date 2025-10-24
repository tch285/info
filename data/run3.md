# Run 3 data record

Information on the Run 3 data and MC stored on Perlmutter and Hiccup.

## Table of contents

- [Table of contents](#table-of-contents)
- [Contact](#contact)
- [Data](#data)
  - [Recommendations](#recommendations)
  - [Triggers](#triggers)
- [MC (central)](#mc-central)
- [MC (fast simulation)](#mc-fast-simulation)

## Contact

Author: Tucker Hwang  
Date: 19 October 2025  
Contact: [tucker_hwang@berkeley.edu](mailto:tucker_hwang@berkeley.edu) or Slack

## Data

Raw data converted to BerkeleyTree format.

1. All Perlmutter paths must be prepended by: `$CFS/alice/alicepro/hiccup/rstorage/alice` (no prepending needed for Hiccup)
2. If the Hiccup path column is empty, this means the dataset has not been transferred to Hiccup. Contact Irakli if you need a dataset transferred.
3. You will need your grid certificate installed in your browser to access the Hyperloop links. Check this [O2Physics documentation page](https://aliceo2group.github.io/analysis-framework/docs/gettingstarted/certificate.html) for more information.
4. See the [Triggers](#triggers) section for an explanation of the Trigger column.
5. A list of the BerkeleyTrees for each dataset can be found in `tree_list.txt` in the corresponding directory.

> [!CAUTION]
> The JE derived data format is still in flux, so the selection and trigger bits for tracks and events that you see in O2Physics **may not match the data you have.** Go to the dataset's train page on Hyperloop, find the Package tag, and look at the corresponding tag on the [O2Physics GitHub repository](https://github.com/AliceO2Group/O2Physics) to find exactly which bits were used during the derived data production.[^1]

| Dataset  | Pass | System | Trigger | JE dataset                                                                                       | Train                                                                   | Events  | Tracks  | Clusters | Perlmutter                                              | Hiccup                        | Notes               |
|----------|------|--------|---------|--------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|---------|---------|----------|---------------------------------------------------------|-------------------------------|---------------------|
| 22o      | 7    | pp     | 1       | [22o_pass7_minBias_small_CJ5_FJ5_C5_TT5](https://alimonitor.cern.ch/hyperloop/view-dataset/1611) | [309453](https://alimonitor.cern.ch/hyperloop/train-run/309453/general) | &check; | &check; | &check;  | `run3/data/LHC22o_small/BerkeleyTrees`                  |                               |                     |
| 22o      | 7    | pp     | 1       | [22o_pass7_CJ_R6_5_FJ_R6_5_CL_5_TT_5](https://alimonitor.cern.ch/hyperloop/view-dataset/1745)    | [346364](https://alimonitor.cern.ch/hyperloop/train-run/346364/general) | &check; | &check; | &check;  | `run3/data/LHC22o/BerkeleyTrees`                        | `/rstorage/alice/data/LHC22o` |                     |
| 23zzm    | 4    | PbPb   | 3       | [23zzm_pass4_Cl_8](https://alimonitor.cern.ch/hyperloop/view-dataset/1301)                       | [304817](https://alimonitor.cern.ch/hyperloop/train-run/304817/general) | &check; | &check; | &check;  | `run3/data/LHC23zzm/BerkeleyTrees`                      |                               |                     |
| 24aj     | 1    | pp     | 2       | [24aj_pass1_Triggered](https://alimonitor.cern.ch/hyperloop/view-dataset/1288)                   | [263284](https://alimonitor.cern.ch/hyperloop/train-run/263284/general) | &check; | &check; | &check;  | `run3/data/LHC24aj/BerkeleyTrees`                       |                               |                     |
| 24aj     | 1    | pp     | 2       | [24aj_pass1_Triggered](https://alimonitor.cern.ch/hyperloop/view-dataset/1288)                   | [263284](https://alimonitor.cern.ch/hyperloop/train-run/263284/general) | &check; | &check; | &check;  | `AnalysisResults/BerkeleyTrees/LHC24aj_pass1_Triggered` |                               |                     |
| 23       | 4    | pp     | 1*      | [LHC23_pass4_Thin](https://alimonitor.cern.ch/hyperloop/view-dataset/995) (full)                 |                                                                         |         |         |          |                                                         |                               | 7 pb-1 MB           |
| 24_ppref | 1    | pp     | 1*      | [LHC24_ppref_pass1](https://alimonitor.cern.ch/hyperloop/view-dataset/1728) (full)               |                                                                         |         |         |          |                                                         |                               | 5.36 TeV, 5 pb-1 MB |
| 24       | 1    | pp     | 2*      | [LHC24_pass1_skimmed](https://alimonitor.cern.ch/hyperloop/view-dataset/1661)(full)              |                                                                         |         |         |          |                                                         |                               | 60 pb-1             |

### Recommendations

For pp:

1. If your data is not particularly statistics-hungry, you will want MB data (no OTS skimming). In this case, use the 2024 pp reference data. The 2023 MB data is also available and is slightly larger, but the reconstruction is worse and it will remain on pass4 (no improvements possible).
2. If your data is statistics-hungry or needs a particular software trigger, use the 2024 skimmed data.

For Pb-Pb:

1. Use LHC23zzm. (only data we have)

### Triggers

The Trigger column denotes the filters, e.g. explicit ALICE JE software triggers or manually-applied filters, applied on the underlying JE derived data.

1. Minimum-bias data suitable for analyses looking at one or more of: charged jets with $R \leq 0.6$ above 5 GeV, full jets with $R \leq 0.6$ above 5 GeV, EMCal clusters over 5 GeV, trigger tracks above 5 GeV. 1* means MB but no other filtering applied.
2. Events with at least one JE software trigger fired. 2* means software triggers applied, but no specific JE selections.
3. EMCal clusters above 8 GeV.

## MC (central)

A list of central MC productions from ALICE that have been converted to the BerkeleyTree format.

1. If the path column is empty, this means the dataset has either not been converted or transferred from the other system. Please contact Tucker if you need a dataset.

| Name  | Pass | System | Generator | Type | Anchor | JE dataset | JIRA                                               | Events | Tracks | Clusters | Perlmutter | Hiccup | Notes                                            |
|-------|------|--------|-----------|------|--------|------------|----------------------------------------------------|--------|--------|----------|------------|--------|--------------------------------------------------|
| 25a2b | 7    | pp     | Pythia 8  | JJ   | 22o    | none yet   | [O2-5654](https://its.cern.ch/jira/browse/O2-5654) |        |        |          |            |        | continuous weighting with oversampling, MB gap 5 |

## MC (fast simulation)

Fast simulation events saved to disk. These events contain generated events and a parametrized version of the Run 3 detector response to approximate a corresponding reconstructed event.

There are currently no Run 3-based fast simulations available.

[^1]: Many of these derived datasets will be reproduced again in the future as the format is developed, so there many be a need for reconversion later.
