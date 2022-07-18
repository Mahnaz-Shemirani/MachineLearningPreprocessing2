####Machine Learning Preprocessing of basic statistics and simple imputation of proteomics project

import numpy as np

import pandas as pd

from sklearn import preprocessing

#read data from excel file

PEA_biomine=pd.read_excel('D:\PhDproject\p1_2\protein data\PEA_biomine_unlock.xlsx', sheet_name='Sheet2')

#calculating mean, SD, count,for all groups

All_prot=PEA_biomine.describe()

#save in an excel file

All_prot.to_excel(r'D:\PhDproject\p1_2\tables\all_protein.xlsx')

#indexing reference proteins

IsRef=PEA_biomine['#Groups']==1

#extracting reference group

Ref=PEA_biomine[IsRef]

#calculating mean, SD,.. for reference group

Reference=Ref.describe()

#save it in an excel file

Reference.to_excel(r'D:\PhDproject\p1_2\tables\Ref.xlsx')

#Filling missing value by minimum in each column-1

PEA=PEA_biomine.fillna (PEA_biomine.min(axis=0)-1)

#eliminating 'DGKZ' protein with no expression value

PEA.drop('DGKZ', axis=1, inplace=True)

#save the data in a new variable

Ad_PEA=PEA

#save it in an excel file

Ad_PEA.to_excel(r'D:\PhDproject\p1_2\tables\ad_PEA.xlsx')
