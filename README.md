# capstone
Flatiron Phase 5 Capstone project

### Business Understanding


Mental health disorders are often difficult to diagnose, sometimes taking months and years of assessment and treatment depending on the emerging disorder. It is a time intensive process for the individuals who need care and for their families. With that added time comes increased out of pocket costs for doctor’s visits - potentially from multiple providers - and loss of income from having to take time off of work. Psychiatrists and clinical psychologists are often booked out months in advance for appointments. It may take an acute mental health crisis that leads to hospitalization to speed up treatment and diagnosis of the suffering individual. Earlier diagnosis is needed.

Routine tests such as Electroencephalograms (EEG), which detect abnormalities in brain waves, traditionally have been used to diagnose epilepsy, Alzheimer's disease, sleep disorders, and brain tumors. EEGs have also been helpful to identify underlying causes of psychosis, a condition marked by a loss of some contact with reality. EEG data is being explored further to identify a broader range of psychiatric conditions - schizophrenia, addictive disorders, anxiety disorders, traumatic stress disorders, and obsessive compulsive disorders. EEGs may offer a path to earlier diagnosis for some psychiatric conditions.

### Data source 

The data for this modeling project comes from recent work conducted by researchers in South Korea who gathered resting state EEG data from nearly 1000 patients. These adult patients suffer from six major psychiatric disorders.

The raw data is accessible through the Center for Open Science’s data portal located at https://osf.io/. The dataset size is 10.5 MB in csv format making it easy to download and use locally. There are over 1000 features making this a rather large dataset. The features consist of some basic patient data such as sex, age, education level and psychiatric diagnosis. The remaining features consists of multiple brain wavelength readings at 19 different contact points on the skull. 

### Predicting Classes of Psychiatric conditions

There are six classes and one healthy control:

  Condition:                          Number of patients: 

Mood disorder                         266
Addictive disorder                    186
Trauma and stress related disorder    128
Schizophrenia                         117
Anxiety disorder                      107
Healthy control                        95
Obsessive compulsive disorder          46

### First simple model results


The initial simple model did not do well predicting each class, but it was moderately successful in predicting mood disorder based on recall score of 81%, which includes major depressive and bipolar disorders. The model appears to be confusing 'mood disorder' class with the other disorders. Mood disorder is also the majority class making it possibly easier to predict. It may be necessary to turn this into a binary classification problem: 'mood disorder' v. 'not mood disorder'.