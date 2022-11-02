# M.Tech-Project
Advisor : Prof. Pabitra Mitra (IIT Kharagpur)</br>

1. Business Problem :</br>
  1.1. Description :</br>
    Source: https://www.kaggle.com/c/msk-redefining-cancer-treatment</br>
    Data: Memorial Sloan Kettering Cancer Center (MSKCC)</br>
    Download training_variants.zip and training_text.zip from Kaggle.</br>
    
    Problem statement :</br>
    Classify the given genetic variations/mutations based on evidence from text-based clinical literature.</br>
  
  1.2. Real-world/Business objectives and constraints :</br>
    * No low-latency requirement.</br>
    * Interpretability is important.</br>
    * Errors can be very costly.</br>
    * Probability of a data-point belonging to each class is needed.</br>
    
2. Machine Learning Problem Formulation</br>
  2.1. Data :</br>
    2.1.1. Data Overview :</br>
      - Source: https://www.kaggle.com/c/msk-redefining-cancer-treatment/data</br>
      - We have two data files: one conatins the information about the genetic mutations and the other contains the clinical evidence (text) that human                     experts/pathologists use to classify the genetic mutations.</br>
      - Both these data files are have a common column called ID</br>
      - Data file's information :</br>
        training_variants (ID , Gene, Variations, Class)</br>
        training_text (ID, Text)</br>
      
    2.1.2. Example Data Point :</br>
      training_variants :</br>
        ID,Gene,Variation,Class</br>
        0,FAM58A,Truncating Mutations,1</br>
        1,CBL,W802*,2</br>
        2,CBL,Q249E,2</br>
        ...</br>
        
      training_text :</br>
        ID,Text</br>
        0||Cyclin-dependent kinases (CDKs) regulate a variety of fundamental cellular processes. CDK10 stands out as one of the last orphan CDKs for which no               activating cyclin has been identified and no kinase activity revealed. Previous work has shown that CDK10 silencing increases ETS2 (v-ets erythroblastosis           virus E26 oncogene homolog 2)-driven activation of the MAPK pathway, which confers tamoxifen resistance to breast cancer cells. The precise mechanisms by           which CDK10 modulates ETS2 activity, and more generally the functions of CDK10, remain elusive. Here we demonstrate that CDK10 is a cyclin-dependent kinase         by identifying cyclin M as an activating cyclin. Cyclin M, an orphan cyclin, is the product of FAM58A, whose mutations cause STAR syndrome, a human                 developmental anomaly whose features include toe syndactyly, telecanthus, and anogenital and renal malformations. ...</br>
        
  2.2. Mapping the real-world problem to an ML problem :</br>
    2.2.1. Type of Machine Learning Problem :</br>
      There are nine different classes a genetic mutation can be classified into => Multi class classification problem</br>
    
    2.2.2. Performance Metric :</br>
      Source: https://www.kaggle.com/c/msk-redefining-cancer-treatment#evaluation</br>
      Metric(s): </br>
      * Multi class log-loss </br>
      * Confusion matrix </br>
    2.2.3. Machine Learing Objectives and Constraints :</br>
      Objective: </br>
        * Predict the probability of each data-point belonging to each of the nine classes.</br>
      Constraints:</br>
        * Interpretability</br>
        * Class probabilities are needed.</br>
        * Penalize the errors in class probabilites => Metric is Log-loss.</br>
        * No Latency constraints.</br>
        
  2.3  Train, CV and Test Datasets</br>
    Split the dataset randomly into three parts train, cross validation and test with 64%,16%, 20% of data respectively</br>
   
