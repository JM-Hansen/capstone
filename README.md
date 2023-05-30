# capstone
Flatiron Phase 5 Capstone project

### Business Understanding


Mental health disorders are often difficult to diagnose, sometimes taking months and years of assessment and treatment depending on the emerging disorder. It is a time intensive process for the individuals who need care and for their families. With that added time comes increased out of pocket costs for doctor’s visits - potentially from multiple providers - and loss of income from having to take time off of work. Psychiatrists and clinical psychologists are often booked out months in advance for appointments. It may take an acute mental health crisis that leads to hospitalization to speed up treatment and diagnosis of the suffering individual. Earlier diagnosis is needed.

Routine tests such as Electroencephalograms (EEG), which detect abnormalities in brain waves, traditionally have been used to diagnose epilepsy, Alzheimer's disease, sleep disorders, and brain tumors. EEGs have also been helpful to identify underlying causes of psychosis, a condition marked by a loss of some contact with reality. EEG data is being explored further to identify a broader range of psychiatric conditions - schizophrenia, addictive disorders, anxiety disorders, traumatic stress disorders, and obsessive compulsive disorders. EEGs may offer a path to earlier diagnosis for some psychiatric conditions.

### Business stakeholder - Huntsman Mental Health Institute

The business client for this project is Huntsman Mental Health Institute (HMHI), a research and care-driven psychiatric hospital affiliated with University of Utah health. HMHI serves individuals in Utah, the Intermountain West, and their long term assessment program serves teens and young adults across the United States. The primary stakeholder are the treatment teams made up of a psychiatrist, clinical psychologist, and social worker who are charged with assessment and diagnosis. 


### Data source 

The data for this modeling project comes from recent work conducted by researchers in South Korea who gathered resting state EEG data from nearly 1000 patients. These adult patients suffer from six major psychiatric disorders.

The raw data is accessible through the Center for Open Science’s data portal located at https://osf.io/. Or from kaggle at https://www.kaggle.com/datasets/shashwatwork/eeg-psychiatric-disorders-dataset. 

The dataset size is 10.5 MB in csv format making it easy to download and use locally. There are over 1000 features making this a rather large dataset. The features consist of some basic patient data such as sex, age, education level and psychiatric diagnosis. The remaining features consists of multiple brain wavelength readings at 19 different contact points on the skull. 

Two different brainwave readings were conducted while the patients were in a resting state. The first was absolute conductance at each node placement for six different brain wavelengths. The second, and the major bulk of the data, were brain wavelength readings across the 19 nodes. 

### Predicting Classes of Psychiatric conditions

Patients were previously diagnosed under the umbrella of six major psychiatric diagnoses. A health control was also included in the data. 

There are six classes and one healthy control:

    Condition:                          Number of patients: 

    Mood disorder                         266
    Addictive disorder                    186
    Trauma and stress related disorder    128
    Schizophrenia                         117
    Anxiety disorder                      107
    Healthy control                        95
    Obsessive compulsive disorder          46
    
![Psychiatric_Classes](https://github.com/JM-Hansen/capstone/assets/104652254/80352161-d959-4e1d-a04a-bfe332a71ea7)


### Modeling process

1. Load modeling packages --> 2. Access and download the data --> 3. Exploratory Data Analysis --> 4. Preprocessing data for modeling --> 5. Multiclassification modeling --> 6. Binary Classification modeling --> 7. Model Summary and Accuracy Scores -->
8. Recommendations 


### Model Summary 

#### Findings for Multiclassification 

   Multiclassification models using both random forest and XGBoost models consistently improved in overall accuracy but not to the points where the model could be useful. The models consistently scored Mood disorder higher. Addictive disorder was often confused with mood disorder, about one out of every three predictions for mood was misclassified as addictive. Addictive disorder was dropped from the entire dataset and multiclassification modeling was run again. This improved scores somewhat but not to the point where the model could be used in a clinical or medical research setting. Greater quantity and greater diversity of EEG data is needed for further multiclassification modeling. 
    
   Schizophrenia, anxiety, and trauma were difficult to tease out, likely given that they looked so much  like other disorders. We do not have data on whether the patients in our data suffered from more than one disorder such as a mood disorder along with trauma disorder. Given that mental health conditions often overlap in the same individual this makes for more noise in the data. 
    
    Final multiclassification results using XGBoost:
    
                                        precision    recall  f1-score   support

                      Anxiety disorder       0.10      0.05      0.06        21
                       Healthy control       0.68      0.68      0.68        19
                         Mood disorder       0.43      0.57      0.49        53
         Obsessive compulsive disorder       0.50      0.33      0.40         9
                         Schizophrenia       0.18      0.12      0.15        24
    Trauma and stress related disorder       0.16      0.19      0.18        26

                              accuracy                           0.36       152
    
#### Findings for Binary Classification 

   Binary classification modeling proved more fruitful in teasing out mood disorder. Mood disorder was first  compared against all other disorders and healthy control using a one versus rest approach. The results showed increased mood precision scores to 62% but very poor mood recall scores. When just mood disorder was compared against healthy control overall scores improved to the point that we have a useful model. The need for greater quantity and more diverse data still exists. 
    
    Final Binary Classification results using XGBoost:
    
                                         precision    recall  f1-score   support

                        Healthy control       0.60      0.32      0.41        19
                          Mood disorder       0.79      0.93      0.85        54

                               accuracy                           0.77        73
    


### Recommendations


1.The binary model comparing mood disorder against healthy control can be useful as an added datapoint in the diagnosis process, particularly for those who may be suffering from psychosis as a result of their mood disorder. Because addictive disorder looks like mood disorder it will be necessary to screen out those who are suffering from addictive disorder using other diagnosis methods. 

2 For individuals and their doctors who may be considering electroconvulsive therapy (ECT), the binary model can be used as another datapoint to inform their choice. 

3 Clinicians can use this model for individuals who may be non-verbal or who struggle to communicate their inner state to others -- those who face nonverbal autism or those who face increased non-verbalness as a result of depression). Because an EEG analysis is non-invasive and takes 30-60 minutes and can be administered by a medical technician, this could be a useful quick datapoint for diagnosis.

### Repository Architecture

* eeg-psychiatric-disorders-dataset  (data source from kaggle)
* images                             (images from exploratory data analysis)
* saved_models                       (saved simple, multiclassification, and binary models)
* eeg_model.ipynb                    (Jupyter notebook code)
* environment.yml                    (modeling environment for reproducible results)
* LICENSE                            (Apache license version 2.0)
* README.md                          (Readme document)
