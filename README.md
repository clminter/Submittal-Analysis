# Submittal-Analysis

## Purpose
Analyze submittals to determine how many returned as 'revise & resubmit', 'rejected', or 'approved as noted, resubmit' were indeed resubmitted for design team approval.

## Analysis
Import and clean csv from NewForma log:

![image](https://user-images.githubusercontent.com/81878169/139930190-9dc7fd7b-d701-4c17-9d88-8d2d7000666b.png)

## Develop code for locating missing submittals:
rej = ['Revise and Resubmit','Approved as Noted/Resubmit','Rejected']

apv = ['Approved as Noted','Approved']

df2.loc[(df2['Final Response'].isin(rej)) & (df2[['Submittal_Number']] != df2[['Submittal_Number']].shift(-1)).any(axis=1),'Missing_Resubmittal']='Yes'

df2.loc[(df2['Final Response'].isin(rej)) & (df2[['Submittal_Number']] == df2[['Submittal_Number']].shift(-1)).any(axis=1),'Missing_Resubmittal']='No'

df2.loc[(df2['Final Response'].isin(apv)),'Missing_Resubmittal']='No'


df2.head(100)

#### Final dataframe:
![image](https://user-images.githubusercontent.com/81878169/139930684-498311a2-2867-4dc7-bc87-9d6233fd0a9d.png)


## Results

https://public.tableau.com/app/profile/chris.l.minter/viz/ProjectSubmittalAnalysis-CPA/Dashboard1

![image](https://user-images.githubusercontent.com/81878169/139931340-9a643d66-1ea7-4a52-9c4a-d9860a2cfad3.png)
