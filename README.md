# AI-Solutions-To-Bias-In-The-Criminal-Legal-System
Prediction algorithms are increasingly being used in criminal justice. In particular COMPAS software is used in courts across the US.
Even though the use of AI is undoubtedly effective and beneficial, it raises many technical, legal, and ethical questions.
A reverse model published by ProPublica was made to show that the tool is biased against African Americans in the US.

In this Report, we are going to question how a biased outcome affects human and constitutional rights, especially the defendant's rights. Then, we will discuss how affirmative action might solve the bias through 3 possible AI methods.

Our main question is, what are the possible solutions to assure fairness (applied in the case study of the ADM made by COMPAS)?
## Bias In The Data:
### Risk of Recidivism:
We can see that 26.6% of African American received a“HIGH” score whereas only 11% of Caucasian individuals received a similar score, meaning that the rate of receiving a  <b>“HIGH” score for African Americans is more 2.5 times that of Caucasians.</b><br>
![newplot (19)](https://user-images.githubusercontent.com/53708521/229221775-425cbf0f-6d95-465b-8724-2b0434ed2499.png)<br>

In addition, we can see that 67% of Caucasians received a "LOW" score whereas only 42.3% of African American individuals received a similar score, meaning that the rate of receiving a <b> "LOW" score for Caucasians is more 1.6 times that of African Americans.</b><br>

## Bias In The Algorithm:
We have trained a logistic Regression classifier on only the decile_score as a feature and then examine how the confusion matrices differ by race.<br>
![Capture](https://user-images.githubusercontent.com/53708521/229222596-e22d308b-f8c7-493b-8877-19319daf3624.JPG)

FNR - 𝑷(𝑳𝒐𝒘𝑹𝒊𝒔𝒌|𝑹𝒆𝒄𝒊𝒅) are higher for Caucasian than African American (0.663043 vs 0.36129), meaning we are more likely to misclassify Caucasian defendants who recidivated as a "LOW" risk than their African American counterparts. <br>

FPR - 𝑷(𝑯𝒊𝒈𝒉𝑹𝒊𝒔𝒌|𝑵𝒐𝑹𝒆𝒄𝒊𝒅) are higher for African American than Caucasian (0.31250 vs 0.159259), meaning we are more likely to misclassify African American defendants who did not recidivated as a "HIGH" risk than their Caucasian counterparts. <br>

# AI-Solutions

### Equalized Odds parity
Equalized Odds parity ensures parity between the subgroups of each race with label 1 in the training set, and parity between the subgroups of each race with label 0 in the training set.<br>
This means that the subgroups of each race who reoffended are equally likely to be predicted to reoffend. Similarly, there is parity between subgroups of each race without recidivism.<br>
In mathematical terms: $𝑇𝑃𝑅_{𝐴𝑓𝑟𝑖𝑐𝑎𝑛 𝐴𝑚𝑒𝑟𝑖𝑐𝑎𝑛}=𝑇𝑃𝑅_{𝐶𝑎𝑢𝑐𝑎𝑠𝑖𝑎𝑛}$ & $𝐹𝑃𝑅_{𝐴𝑓𝑟𝑖𝑐𝑎𝑛 𝐴𝑚𝑒𝑟𝑖𝑐𝑎𝑛}=𝐹𝑃𝑅_{𝐶𝑎𝑢𝑐𝑎𝑠𝑖𝑎𝑛}$
<br>
![newplot (18)](https://user-images.githubusercontent.com/53708521/229221191-b9badc03-08cc-44ea-a7e1-13b0bc4dab9d.png)

## Method 1 - Threshold-Moving 
Since we do not change the distribution of the risk of the defendants to re-offend in the model, we will not lower the accuracy of the model and/or the accuracy of the subgroups.<br> 
$𝑇𝑃𝑅_{𝐴𝑓𝑟𝑖𝑐𝑎𝑛 𝐴𝑚𝑒𝑟𝑖𝑐𝑎𝑛}=0.3226$ $𝑇𝑃𝑅_{𝐶𝑎𝑢𝑐𝑎𝑠𝑖𝑎𝑛}=0.2826$<br>
The diffrence:0.04<br>

$𝐹𝑃𝑅_{𝐴𝑓𝑟𝑖𝑐𝑎𝑛 𝐴𝑚𝑒𝑟𝑖𝑐𝑎𝑛}=0.1184$ $𝐹𝑃𝑅_{𝐶𝑎𝑢𝑐𝑎𝑠𝑖𝑎𝑛}=0.1037$ <br>
The diffrence:0.0147 <br>

##  Method 2-Normalizing the Predections
![newplot (20)](https://user-images.githubusercontent.com/53708521/229225223-378448b9-03b8-49f2-a3bf-3bfa4b43a83a.png)

## Method 3 - SGD With Weighted Samples
![newplot (21)](https://user-images.githubusercontent.com/53708521/229225350-58411d5e-e1fb-4349-ae31-ba651824ef2e.png)<br>

For more information see the 

