# Usage Information:

## DSCI_train
### Description:
Takes training patient features as input and outputs trained model for privileged information prediction. Used ML model: KRVFL+ from the paper (P.-B. Zhang and Z.-X. Yang, “A new learning paradigm for random vector functional-link network: Rvfl+,” Neural Networks, vol. 122, pp. 94–105, 2020.)

### Requirements: 
- All four input .csv or .xlsx files must have the same number of rows (i.e. same number of patients).
- All four input .csv or .xlsx files must have column names indicating feature names.
- All four input .csv or .xlsx files must have "patientId" as the first column and "group" as the second column, indicating patient names and labels respectively.

### Inputs:
- [AF_path]: .csv or .xlsx file containing Articular Fossa features. Name of file must contain the substring "train_af".
- [BL_path]: .csv or .xlsx file containing Biological features. Name of file must contain the substring "train_bl".
- [CL_path]: .csv or .xlsx file containing Clinical features. Name of file must contain the substring "train_cl".
- [CT_path]: .csv or .xlsx file containing Condyle Trabecular features. Name of file must contain the substring "train_ct".
- [folder_path]: directory to output trained model to.

### Output:
- file named "TMJPI_train.mat" that contains the best performing ensemble of models trained from the input features.
  The file is output to the [folder path] directory

### Example usage:
./DSCI_train [AF_path] [BL_path] [CL_path] [CT_path] [folder path]

---

## DSCI_predict
### Description:
Takes testing patient features as input and outputs scores and predictions for each testing patient.

### Requirements: 
- All four input .csv or .xlsx files must have the same number of rows (i.e. same number of patients).
- All four input .csv or .xlsx files must have column names indicating feature names.
- All four input .csv or .xlsx files must have "patientId" as the first column indicating patient names. No "group" column or patient label column should be present.

### Inputs:
- [AF_path]: .csv or .xlsx file containing Articular Fossa features. Name of file must contain the substring "test_af".
- [BL_path]: .csv or .xlsx file containing Biological features. Name of file must contain the substring "test_bl".
- [CL_path]: .csv or .xlsx file containing Clinical features. Name of file must contain the substring "test_cl".
- [CT_path]: .csv or .xlsx file containing Condyle Trabecular features. Name of file must contain the substring "test_ct".
- [model path]: path to previously trained "TMJPI_train.mat" file.
- [folder_path]: directory to output prediction file to.

### Outputs:
Files output to [Folder path].
- .mat file named "TMJPI_pred.mat" that contains the model scores and prediction (either 1 or 0 for OA or non-OA) for each testing patient.
- .csv file named "TMJPI_pred.csv" that contains the model scores and prediction (either 1 or 0 for OA or non-OA) for each testing patient.

### Example usage:
./DSCI_predict [AF_path] [BL_path] [CL_path] [CT_path] [model path] [folder path]
