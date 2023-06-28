<a id="top"></a>
# Low-Code Tool for Automated Prediction of Students' Academic Performance

_This page provides additional material for the paper titled "Low-Code Tool for Automated Prediction of Students' Academic Performance"._


| _Table of contents_   |
|-----------------------|
| [Abstract](#abstract)   |
| [Software description](#software)   |
| [Case study REQ1_1](#csreq1_1): Predict mark (REQ1) - Educator advanced view |
| [Case study REQ1_2](#csreq1_2): Predict mark (REQ1) - Data expert view |
| [Case study REQ2_1](#csreq2_1): Predict passes and fails (REQ2) - Educator advanced view |
| [Case study REQ2_2](#csreq2_2): Predict passes and fails (REQ2) - Data expert view |
| [Case study REQ3_1](#csreq3_1): Early predict pass or fail (REQ3) - Educator advanced view |
| [Case study REQ3_2](#csreq3_2): Early predict pass or fail (REQ3) - Data expert view |

<a id="abstract"></a>
## Abstract 
The field of educational data mining (EDM) has benefited from the abundance of data generated by educational activities. However, the effective use of this data requires expertise in data preprocessing and machine learning techniques. To support educators in this aspect, we introduce LoCoAPe: a low-code tool for the application of EDM methods for predicting student performance. LoCoAPe employs a workflow architecture that integrates Weka algorithms, offering both pre-defined workflows while also allowing educators to visually construct their own. Our experiments illustrate the adaptability and potential of LoCoAPe in assisting educators and researchers with varying levels of expertise.

<a id="software"></a>
## Software description

LoCoAPe is a user-friendly low-code tool that grants teachers and educational administrators direct access to EDM methods focused on predicting student performance. It operates based on the concept of workflows, which are sequences of operations involving data preprocessing, ML methods, and outcome visualization. Users can combine and connect these operations in various ways, allowing for predefined workflows as well as user-defined ones.

### Download LoCoAPe

- Windows version (ZIP)
- Linux version (ZIP)
- MacOS version (ZIP)

### Installation and execution

__Requirements__: Java 8 or higher must be installed.

Unzip LoCoAPE and run LoCoAPE executable

[(top)](#top)

---

## Case studies

<a id="csreq1_1"></a>
### Predict mark (REQ1) - Educator advanced view

This case study shows how educators can use the ready-to-use "Predict Mark" and "Remove Attributes" elements to investigate the potential relationship between math, reading, and writing scores—three numerical attributes—in the Exam Performance dataset.

#### Datasets: 

[Historical](./case-studies/req1_1/data/exam_performance_historical.csv), [Target](./case-studies/req1_1/data/exam_performance_target.csv), [Original](https://www.kaggle.com/datasets/spscientist/students-performance-in-exams)

> J. Seshapanpu, “Dataset: Students Performance in Exams.” https://www.kaggle.com/datasets/spscientist/students-performance-in-exams, 2018

#### Operations:
- Predict Mark
  - Generate Numeric Predictor
    - Load Data
    - Simple Linear Regression
  - Make Prediction
    - Load Data
    - Load Predictor
    - Predict
- Remove Attributes
  - Load Data
  - Remove Properties

#### Demo

1. Create a high-level workflow consisting of the following elements: one Predict Marks, one Remove Attributes, two Dataset (Input), one Record (Input), and establish the necessary connections.


https://github.com/LoCoAPe/tool/assets/138053199/02d1c435-c813-4f2f-b030-01b85b96269a


2. Rename and configure the Dataset inputs and configure the Record input to remove the relevant dataset attributes.


https://github.com/LoCoAPe/tool/assets/138053199/726cc8be-8d1a-4f47-994d-723969f294b2


3. Add and connect the Dataset (Output) to store the resulting prediction.


https://github.com/LoCoAPe/tool/assets/138053199/49f0a207-9043-4a8a-b41c-fc97f771fb49


4. Execute the workflow, examine the sub-workflows, and display the outputs.


https://github.com/LoCoAPe/tool/assets/138053199/50110644-1760-453a-80ab-5896db60514b


__Results__: [ARFF](./case-studies/req1_1/predictions/exam_performance_prediction.arff)

[(top)](#top)

---

<a id="csreq1_2"></a>
### Predict mark (REQ1) - Data expert view

This case study illustrates how data experts can modify the configuration of the "Predict Marks" workflow to identify the most influential factors determining student success (positive weight) or failure (negative weight). The High School (Portuguese) dataset is used.

#### Datasets: 

[Historical](./case-studies/req1_2/data/student-por_historical.csv), [Target](./case-studies/req1_2/data/student-por_target.csv), [Original](https://archive.ics.uci.edu/ml/datasets/student+performance)

> P. Cortez and A. Silva, "Using Data Mining to Predict Secondary School Student Performance," in 5th Future Business Technology Conference (FUBUTEC), pp. 5–12, 2008. Retrieved from: https://archive.ics.uci.edu/ml/datasets/student+performance

#### Operations:

- Predict Mark
  - Generate Numeric Predictor
    - Load Data
    - Remove Attributes
    - Normalize in Range
    - SVR
  - Make Prediction
    - Load Data
    - Load Predictor
    - Predict
  - Evaluate Prediction


#### Demo

1. Add the Predict Mark element to the workflow and navigate to its source workflows. Then, navigate to the Generate Numeric Predictor sub-workflow to change the default behavior.


https://github.com/LoCoAPe/tool/assets/138053199/911dadd7-6392-4e38-bd29-732f2bce094d


2. Remove Simple Linear Regression and add the following elements: Normalize in Range (with ignoreClass to true) and SVR. Then, connect the corresponding elements to define the new behavior. Save the changes to confirm the new behavior and go to the parent workflow.


https://github.com/LoCoAPe/tool/assets/138053199/b33d3dde-af4b-45e2-81d1-0217b4ac8aab


3. Reconnect the modified element. Then add and connect Evaluate Prediction and Metrics (Output). Then, save the changes and go to the parent workflow. Now, Predict Mark provides a new output corresponding to the metrics.


https://github.com/LoCoAPe/tool/assets/138053199/e917f40c-bf40-4875-9b06-5e048f1fe3c7


4. Add a Dataset (Input), a Record (Input) and Remove Attributes. Then configure the input to the following value: 1,2,4-6,9-12,16-23,31,32. Then, connect the elements.


https://github.com/LoCoAPe/tool/assets/138053199/2b864244-9fc2-4a8e-94a8-8d9f29c3f896


5. Add, connect and configure a Dataset (Input), a Dataset (Output), and one Metrics (Output).


https://github.com/LoCoAPe/tool/assets/138053199/8b296cda-4329-4c56-bde3-c0675e8720c9


6. Configure inputs and outputs. Then execute the workflow, inspect the sub-workflows and display the outputs.


https://github.com/LoCoAPe/tool/assets/138053199/a510b0ca-38eb-4cb9-9acf-ff4709602621


__Results__: [ARFF](./case-studies/req1_2/predictions/student-por_predictions_svr.arff)

| Metric                         | Value      |
|--------------------------------|------------|
| Correlation coefficient       | 0.3332     |
| Mean absolute error           | 10         |
| Root mean squared error       | 10.3696    |
| Relative absolute error       | 424.1901%  |
| Root relative squared error   | 329.2245%  |
| Total Number of Instances     | 454        |

[(top)](#top)

---

<a id="csreq2_1"></a>
### Predict passes and fails (REQ2) - Educator advanced view

This case study aims to demonstrate how educators can easily predict passes and fails, but categorizing the student performance as “low” (L), “middle” (M) or “high” (H). To this end, the Kalboard 360 dataset is used without the need of changing the provided workflow.

#### Datasets: 

[Historical](./case-studies/req2_1/data/kalboard360_historical.csv), [Target](./case-studies/req2_1/data/kalboard360_target.csv)

> E. A. Amrieh, T. Hamtini, and I. Aljarah, “Mining educational data to predict student’s academic performance using ensemble methods,” International Journal of Database Theory and Application, vol. 9, no. 8, pp. 119–136, 2016

#### Operations:

- Predict Pass and Fails
  - Generate Predictor
    - Load Data
    - J48
  - Make Prediction
    - Load Data
    - Load Predictor
    - Predict

#### Demo

1. Create a high-level workflow with the following elements: one Predict Passes and Fails, two Dataset (Input), one Dataset (Output), and the corresponding connections.


https://github.com/LoCoAPe/tool/assets/138053199/040f4f4b-cc67-43ba-895f-8af5de108d3f


2. Configure the inputs and outputs to load the datasets and store the prediction.


https://github.com/LoCoAPe/tool/assets/138053199/d0aab834-129c-464a-8d47-79e941b9e55a


3. Execute the workflow, inspect the sub-workflows and display the outputs.


https://github.com/LoCoAPe/tool/assets/138053199/09fd7c2e-2189-4790-af96-0d35ea946e22


__Results__: [ARFF](./case-studies/req2_1/predictions/kalboard360_prediction.arff)

[(top)](#top)

---

<a id="csreq2_2"></a>
### Predict passes and fails (REQ2) - Data expert view

#### Datasets: 

[Historical/Student](./case-studies/req2_2/data/courseStudentInfo_historical.csv), [Historical/Assessment](./case-studies/req2_2/data/courseAssessmentInfo_historical.csv), [Target](./case-studies/req2_2/data/courseStudentAssessmentInfo_target.csv)

> J. Kuzilek, M. Hlosta, and Z. Zdrahal, “Open university learning analytics dataset,” Scientific Data, vol. 4, p. 170171, 2017

#### Operations:

- Predict Passes and Fails
- Generate Predictor
  - Integrate Datasets
    - Load Data
    - Link Datasets
  - Remove Attributes
    - Load Data
    - Remove Properties
  - Remove Missing Values
  - JRip
- Make Prediction
  - Load Data
  - Load Predictor
  - Predict

#### Demo

1. Add the Predict Passes and Fails element to the workflow and navigate to its source workflows. Then, navigate to the Generate Predictor sub-workflow to change the default behavior


https://github.com/LoCoAPe/tool/assets/138053199/bc6fd49b-7248-4545-993e-dc6c77e53c79


2. Remove J48 and add JRip. Then configure JRip with the attribute “prune” to false, save the changes to confirm the new behavior and go to the parent workflow. 


https://github.com/LoCoAPe/tool/assets/138053199/42768d6e-75d7-4a94-a785-baa2a3997da9


3. Reconnect the modified Generate Predictor and go to the parent workflow. 


https://github.com/LoCoAPe/tool/assets/138053199/e34c2271-04ef-4f4d-8d2d-e15dcb17d09f


4. Add the following elements: two Dataset (Input), one Dataset (Output), two Record (Input), Integrate Datasets, Remove Attributes, and Remove Missing Values. Then connect the corresponding elements. 


https://github.com/LoCoAPe/tool/assets/138053199/667561d4-ef2d-4fcd-8182-f8dbf75a2c6c


5. Configure the new inputs with the following values: id_student for the input of Integrate Datasets, and 1 for the input of Remove Attributes.


https://github.com/LoCoAPe/tool/assets/138053199/31a08a60-60d7-4702-919d-c741130d7750


6. Execute the workflow, inspect the sub-workflows and display the outputs.


https://github.com/LoCoAPe/tool/assets/138053199/757cc757-1787-4639-b7b8-989e0209f465


__Results__: [ARFF](./case-studies/req2_2/predictions/oulad_predictions.arff)

[(top)](#top)

---

<a id="csreq3_1"></a>
### Early predict pass or fail (REQ3) - Educator advanced view

The dataset Computer Programming contains information regarding the scores of students for six assignments from October to December 2021, as well as three exams. The objective of this case study is to allow the educator to predict the risk of each student at two moments of the course using the ready-to-use Predict Passes and Fails - Early workflow with additional data preprocessing.

#### Datasets: 

[Historical/Begin](./case-studies/req3_1/data/computer_programming_historical_begin.csv), [Historical/Middle](./case-studies/req3_1/data/computer_programming_historical_middle.csv), [Target/Begin](./case-studies/req3_1/data/computer_programming_target_begin.csv), [Target/Middle](./case-studies/req3_1/data/computer_programming_target_middle.csv)

> J. Edwards, “Dataset: 2021 CS1 Keystroke Data.” https://doi.org/10.7910/DVN/BVOF7S, 2022

#### Operations:

- Predict Passes and Fails - Early
  - Remove Attributes
  - Predict Pass and Fails
    - Generate Predictor
      - Load Data
      - Categorize Attribute
      - J48
    - Make Prediction
      - Load Data
      - Load Predictor
      - Predict


#### Demo

1. Add the Predict Passes and Fails - Early element to the workflow and navigate to its source workflows to change the default behavior. Then, navigate to each Predict Passes and Fails to change the ID3 element by J48. Finally, save, reconnect elements and go to the parent workflow.


https://github.com/LoCoAPe/tool/assets/138053199/f27c61d7-e61e-4b14-8af7-f155358ab598


2. Add the following set of preprocessing tasks to each Predict Passes and Fails task: Remove Attributes, Clean Data and Categorize Attribute, with the corresponding Record (Input). Then, connect all elements to define the new behavior.


https://github.com/LoCoAPe/tool/assets/138053199/731a678c-991a-47b5-bc04-9ad3bbddef41


3. Rename the inputs and save the changes. Then configure Categorize Attribute as follows:
  - Position=6 (attribute HighestACT)
  - Value=(1-17],low;(17-23],medium;(23-36],high
  + Finally go to the top workflow.


https://github.com/LoCoAPe/tool/assets/138053199/f1dd2441-e736-4ccc-85bd-4a1487870c28


4. Configure all Dataset inputs and outputs to load and store the datasets. Then, Configure the Record inputs with the value 1 (to remove the student ID). Execute the workflow, inspect the sub-workflows and display the outputs.


https://github.com/LoCoAPe/tool/assets/138053199/5455518c-5bb2-4f6d-adc8-60a46aa7848c


__Results__: [Begin/ARFF](./case-studies/req3_1/predictions/computer_programming_predictions_begin.arff), [Middle/ARFF](./case-studies/req3_1/predictions/computer_programming_predictions_middle.arff)

[(top)](#top)

---

<a id="csreq3_2"></a>
### Early predict pass or fail (REQ3) - Data expert view

In this case study, the data expert has to work with the Science Course dataset for academic performance prediction, according to the procedures outlined by Injadat et al. The authors define two prediction moments: the 20% stage, based on the scores of the first quiz and the first assignment, and the 50% stage, which includes an additional assignment and the midterm exam. The Predict Passes and Fails - Early workflow is used in combination with preprocessing operations to remove data and balance the dataset, and the classifier is modified to Naive Bayes, one of the algorithms analyzed in the original paper.

#### Datasets: 

[Historical/Begin](./case-studies/req3_2/data/science_course_historical_begin.csv), [Historical/Middle](./case-studies/req3_2/data/science_course_historical_middle.csv), [Target/Begin](./case-studies/req3_2/data/science_course_target_begin.csv), [Target/Middle](./case-studies/req3_2/data/science_course_target_middle.csv)

> M. Injadat, A. Moubayed, A. B. Nassif, and A. Shami, “Systematic ensemble model selection approach for educational data mining,” Knowledge-based Systems, vol. 200, p. 105992, 2020.

#### Operations:

- Remove Attributes
- Predict Passes and Fails - Early
  - Predict Pass and Fails
    - Generate Predictor
      - Load Data
      - Class Balancer
    - Naive Bayes
  - Make Prediction
    - Load Data
    - Load Predictor
    - Predict

#### Demo

1. Add the Predict Passes and Fails - Early element to the workflow and navigate to its source workflow to change the default behavior. Then, navigate to each Predict Passes and Fails to change the predictor, navigating to Generate Predictor. Then, add Class Balancer and Naive Bayer, and remove ID3 and Discretize Supervised. Finally, save, reconnect elements and go to the parent workflow.


https://github.com/LoCoAPe/tool/assets/138053199/c8336844-23d3-4216-b0a1-bc8aec78ed03


2. Add two Remove Attributes with the corresponding Record (Input) and Dataset (Input). Then add two Dataset (Input) and two Dataset (Output). Finally connect all elements.


https://github.com/LoCoAPe/tool/assets/138053199/ce6248e9-3567-4ce8-9853-138addb400cc


3. Configure all Record inputs, Dataset inputs and outputs to load and store the datasets. Then, execute the workflow, inspect the sub-workflows and display the outputs.


https://github.com/LoCoAPe/tool/assets/138053199/155f4e15-3c6b-4ec3-b819-c068b71b8ef9


__Results__: [Begin/ARFF](./case-studies/req3_2/predictions/science_course_predictions_begin.arff), [Middle/ARFF](./case-studies/req3_2/predictions/science_course_predictions_middle.arff)

[(top)](#top)


