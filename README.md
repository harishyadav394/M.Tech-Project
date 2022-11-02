# M.Tech-Project
Advisor : <b>Prof. Pabitra Mitra</b> <i>(IIT Kharagpur)</i>

<h2>1. Business Problem</h2>
<h3>1.1. Description</h3>
<p> Source: https://www.kaggle.com/c/msk-redefining-cancer-treatment/ </p>
<p> Data : Memorial Sloan Kettering Cancer Center (MSKCC)</p>
<p> Download training_variants.zip and training_text.zip from Kaggle.</p> 

<h6> Context :</h6>
<p> Source: https://www.kaggle.com/c/msk-redefining-cancer-treatment/discussion/35336#198462</p>

<h6> Problem statement :</h6>
<p> Classify the given genetic variations/mutations based on evidence from text-based clinical literature. </p>

<h3>1.2. Real-world/Business objectives and constraints</h3>
<p>
    <ul>
        <li>No low-latency requirement.</li>
        <li>Interpretability is important.</li>
        <li>Errors can be very costly.</li>
        <li>Probability of a data-point belonging to each class is needed.</li>
     </ul>
</p>

<h2>2. Machine Learning Problem Formulation</h2>
<h3>2.1. Data</h3>
<h4>2.1.1. Data Overview</h4>
<p>
  <ul>
    <li>Source: https://www.kaggle.com/c/msk-redefining-cancer-treatment/data</li>
    <li>We have two data files: one conatins the information about the genetic mutations and the other contains the clinical evidence (text) that  human experts/pathologists use to classify the genetic mutations.</li>
    <li>Both these data files are have a common column called : ID</li>
   </ul>
</p>
<p> 
   Data file's information :
    <ul> 
        <li>
        training_variants (ID , Gene, Variations, Class)
        </li>
        <li>
        training_text (ID, Text)
        </li>
    </ul>
</p>

<h4>2.1.2. Example Data Point</h4>
<h6>training_variants</h6>
<hr>
ID,Gene,Variation,Class<br>
0,FAM58A,Truncating Mutations,1 <br>
1,CBL,W802*,2 <br>
2,CBL,Q249E,2 <br>
...

<h6> training_text</h6>
<hr>
ID,Text <br>
0||Cyclin-dependent kinases (CDKs) regulate a variety of fundamental cellular processes. CDK10 stands out as one of the last orphan CDKs for which no activating cyclin has been identified and no kinase activity revealed. Previous work has shown that CDK10 silencing increases ETS2 (v-ets erythroblastosis virus E26 oncogene homolog 2)-driven activation of the MAPK pathway, which confers tamoxifen resistance to breast cancer cells. The precise mechanisms by which CDK10 modulates ETS2 activity, and more generally the functions of CDK10, remain elusive. Here we demonstrate that CDK10 is a cyclin-dependent kinase by identifying cyclin M as an activating cyclin. Cyclin M, an orphan cyclin, is the product of FAM58A, whose mutations cause STAR syndrome, a human developmental anomaly whose features include toe syndactyly, telecanthus, and anogenital and renal malformations. We show that STAR syndrome-associated cyclin M mutants are unable to interact with CDK10. Cyclin M silencing phenocopies CDK10 silencing in increasing c-Raf and in conferring tamoxifen resistance to breast cancer cells. CDK10/cyclin M phosphorylates ETS2 in vitro, and in cells it positively controls ETS2 degradation by the proteasome. ETS2 protein levels are increased in cells derived from a STAR patient, and this increase is attributable to decreased cyclin M levels. Altogether, our results reveal an additional regulatory mechanism for ETS2, which plays key roles in cancer and development. They also shed light on the molecular mechanisms underlying STAR syndrome.Cyclin-dependent kinases (CDKs) play a pivotal role in the control of a number of fundamental cellular processes (1). The human genome contains 21 genes encoding proteins that can be considered as members of the CDK family owing to their sequence similarity with bona fide CDKs, those known to be activated by cyclins (2). Although discovered almost 20 y ago (3, 4), CDK10 remains one of the two CDKs without an identified cyclin partner. This knowledge gap has largely impeded the exploration of its biological functions. CDK10 can act as a positive cell cycle regulator in some cells (5, 6) or as a tumor suppressor in others (7, 8). CDK10 interacts with the ETS2 (v-ets erythroblastosis virus E26 oncogene homolog 2) transcription factor and inhibits its transcriptional activity through an unknown mechanism (9). CDK10 knockdown derepresses ETS2, which increases the expression of the c-Raf protein kinase, activates the MAPK pathway, and induces resistance of MCF7 cells to tamoxifen (6). ... 

<h3>2.2. Mapping the real-world problem to an ML problem</h3>
<h4>2.2.1. Type of Machine Learning Problem</h4>
<p>
  There are nine different classes a genetic mutation can be classified into => Multi class classification problem
</p>
<h4>2.2.2. Performance Metric</h4>
Source: https://www.kaggle.com/c/msk-redefining-cancer-treatment#evaluation

Metric(s): 
* Multi class log-loss 
* Confusion matrix 

<h4>2.2.3. Machine Learing Objectives and Constraints</h4>
<p> Objective : 
    <ul>
        <li>Predict the probability of each data-point belonging to each of the nine classes.</li>
     </ul>
</p>
<p> Constraints :
    <ul>
        <li>Interpretability</li>
        <li>Class probabilities are needed.</li>
        <li>Penalize the errors in class probabilites => Metric is Log-loss.</li>
        <li>No Latency constraints.</li>
     </ul>
</p>

<h3>2.3. Train, CV and Test Datasets</h3>

 Split the dataset randomly into three parts train, cross validation and test with 64%,16%, 20% of data respectively
