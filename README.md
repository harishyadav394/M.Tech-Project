# M.Tech-Project
Advisor: Prof. Pabitra Mitra (IIT Kharagpur)

1. Business Problem :
  1.1. Description :
    Source: https://www.kaggle.com/c/msk-redefining-cancer-treatment
    Data: Memorial Sloan Kettering Cancer Center (MSKCC)
    Download training_variants.zip and training_text.zip from Kaggle.
    
    Problem statement :
    Classify the given genetic variations/mutations based on evidence from text-based clinical literature.
  
  1.2. Real-world/Business objectives and constraints :
    * No low-latency requirement.
    * Interpretability is important.
    * Errors can be very costly.
    * Probability of a data-point belonging to each class is needed.
    
2. Machine Learning Problem Formulation
  2.1. Data :
    2.1.1. Data Overview :
      - Source: https://www.kaggle.com/c/msk-redefining-cancer-treatment/data
      - We have two data files: one conatins the information about the genetic mutations and the other contains the clinical evidence (text) that human                     experts/pathologists use to classify the genetic mutations. 
      - Both these data files are have a common column called ID
      - Data file's information :
        training_variants (ID , Gene, Variations, Class)
        training_text (ID, Text)
      
    2.1.2. Example Data Point :
      training_variants :
        ID,Gene,Variation,Class
        0,FAM58A,Truncating Mutations,1
        1,CBL,W802*,2
        2,CBL,Q249E,2
        ...
        
      training_text :
        ID,Text
        0||Cyclin-dependent kinases (CDKs) regulate a variety of fundamental cellular processes. CDK10 stands out as one of the last orphan CDKs for which no               activating cyclin has been identified and no kinase activity revealed. Previous work has shown that CDK10 silencing increases ETS2 (v-ets erythroblastosis           virus E26 oncogene homolog 2)-driven activation of the MAPK pathway, which confers tamoxifen resistance to breast cancer cells. The precise mechanisms by           which CDK10 modulates ETS2 activity, and more generally the functions of CDK10, remain elusive. Here we demonstrate that CDK10 is a cyclin-dependent kinase         by identifying cyclin M as an activating cyclin. Cyclin M, an orphan cyclin, is the product of FAM58A, whose mutations cause STAR syndrome, a human                 developmental anomaly whose features include toe syndactyly, telecanthus, and anogenital and renal malformations. ...
        
  2.2. Mapping the real-world problem to an ML problem :
    2.2.1. Type of Machine Learning Problem :
      There are nine different classes a genetic mutation can be classified into => Multi class classification problem
    
    2.2.2. Performance Metric :
      Source: https://www.kaggle.com/c/msk-redefining-cancer-treatment#evaluation
      Metric(s): 
      * Multi class log-loss 
      * Confusion matrix 
    2.2.3. Machine Learing Objectives and Constraints :
      Objective: 
        * Predict the probability of each data-point belonging to each of the nine classes.
      Constraints:
        * Interpretability
        * Class probabilities are needed.
        * Penalize the errors in class probabilites => Metric is Log-loss.
        * No Latency constraints.
        
  2.3  Train, CV and Test Datasets
    Split the dataset randomly into three parts train, cross validation and test with 64%,16%, 20% of data respectively
   
