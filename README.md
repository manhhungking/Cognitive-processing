# Cognitive-processing

This guide outlines the steps required to replicate the project.

## Preprocessing Steps

We start with preprocessed EEG data, excluding the removal of eye blinks and saccades. This data is located in the `filt0p1_CL_ICs(1)` folder, provided by Evan. The following steps describe how to continue:

### Step-by-Step Process

1. **Remove eye blinks and saccades components.**
2. **Bandpass filtering**: Apply bandpass filtering from 0.1 Hz to 50 Hz.
3. **Relabel events**: This step results in the folder `N300 1/EEG_event_relabel(4)`.
4. **Assign bins.**
5. **Extract bin-based epochs.**
6. **Detect artifacts from epochs**: Results are stored in the folder `N300 1/EEG_artifact_epochs_detected(7)`.
7. **Compute averaged ERP**: Compute averaged ERP for each candidate, then perform a grand average across candidates. This is saved in the folder `N300 1/ERP(8)`.

> **Note**: You may need to modify some file paths in certain MATLAB scripts if necessary.

## Deep Neural Network Training

We train a deep neural network (DNN) model to categorize 12 image categories located in `Stimulus/scenes_all_1` using the notebook `Final_version.ipynb`. The trained model is saved as `model.keras`. More details are available in that file.

## Grand-Averaged ERP and RSA Analysis

From this point, we will use files located in the `N300 1/Grand_averaged_ERP(9)_Spearman` folder.

1. **Time-course RSM computation**: Compute the time-course RSM from grand-averaged ERP by running the `RSM_Spearman.m` script.
2. **Permutation test for whole ERP**: Run `RSM_Whole_ERP.m` to compute the permutation test for the entire ERP as one time point (instead of 200 time points).
3. **Run Permutation Test**: Execute the `Permutation_test.m` script.
4. **Run RSA**: Finally, run the `RSA.m` script. The results are saved in the `RSA_Figures` folder.

---

Follow these steps to replicate the analysis and obtain the final RSA results.
