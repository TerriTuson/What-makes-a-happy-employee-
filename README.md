# What makes a Happy Employee?

Why do we choose to do the work we do? What makes a job fulfilling? Why are we satisfied and stay in a career?

This Capstone project aimed to discover whether there are certain factors that are important when it comes to job satisfaction - as we all spend a third of our lives at work, and a third of our waking day - and specifically, what these factors are. 

*Why?*

**Firstly**, for employers. 

Job satisfaction can improve productivity in one fell swoop. [Happy employees are 13% more productive,](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=3470734) while unhappy employees are a drain on a company’s finances - in 2019, almost [£92 billion and 38 working days per employee](https://www.uk.mercer.com/newsroom/britains-92-billion-pounds-productivity-loss-nations-first-productive-day-is-now-21st-february.html) was lost as a result of ill physical & mental health. 

Equally, employee satisfaction is a reliable predictor of employee retention. Employee satisfaction improves because workers tend to believe the company is using their skills and appreciating their service and commitment. In turn, high job satisfaction generally results in higher levels of employee retention which will reduce turnover, recruiting and training costs.

**Secondly**, for individuals, you or I, just trying to make a living.

With a third of our waking day and a third of our life working away, why shouldn’t we be able to choose a profession, career, day-to-day that suits us?

**Thirdly**, in the ever-changing landscape.

Post-COVID, a lot has changed. We’ve experienced alternative working practices and this has changed the way we believe we should be treated by employers. The great resignation is a sign of this. 

Industries have changed - when was the last time you went out to buy a pair of jeans? 

And technology is gaining more and more ground. AR, VR and the metaverse will soon be a reality. 


### The Skills Mismatch
Alongside job satisfaction and happiness and wellbeing in the workplace, I’m especially interested in the skills mismatch, and one of the aims of this project was to discover whether a skills mismatch directly impacted job satisfaction. 

A skills mismatch is defined as being over skilled, under skilled, over qualified, under qualified or working in a different field to one you trained in (often known as a horizontal mismatch). [How Useful is the Concept of Skills Mismatch?](https://www.ilo.org/wcmsp5/groups/public/---ed_emp/---ifp_skills/documents/publication/wcms_552798.pdf) is a great resource for better understanding the definition of a skills mismatch.


### Literature Review
During my research on job satisfaction there were few previous studies. My main information sources were three papers:
* Montt, G. (2015), "[The causes and consequences of field-of-study mismatch: An analysis using PIAAC](https://www.oecd-ilibrary.org/social-issues-migration-health/the-causes-and-consequences-of-field-of-study-mismatch_5jrxm4dhv9r2-en)", OECD Social, Employment and Migration Working Papers, No. 167, OECD Publishing, Paris.
* Müge Adalet McGowan & Dan Andrews (2015), “[Skill mismatch and public policy in OECD countries](https://www.oecd.org/economy/growth/Skill-mismatch-and-public-policy-in-OECD-countries.pdf)”, Economics Department Working Papers No 1210.
* Seamus McGuinness, Konstantinos Pouliakas, Paul Redmond (2017), "[How Useful is the Concept of Skills Mismatch?](https://www.ilo.org/wcmsp5/groups/public/---ed_emp/---ifp_skills/documents/publication/wcms_552798.pdf)" International Labour Office, Geneva.


### Research Steps
My project involved five separate steps taken consecutively:

* **Part 1:** Pitch & Problem Statement - Defined the research question, hypotheses, success metrics and data sources.
* **Part 2:** Data Acquisition & Cleaning - Sourced and formatted the required data for the project, performed preliminary data munging and cleaning of the data. Described the data, keeping my intended audience in mind.
* **Part 3:** EDA & Preliminary Analysis - Quantitatively described and visualised the data, and  maintained perspective on the goals and scope accordingly.
* **Part 4:** Data Modelling & Conclusion - Identified whether job satisfaction can be predicted better than baseline for my hypotheses.. Created models that accurately predicted job satisfaction and identified specific factors that impact the result. Evaluated model performance and discussed results.
* **Part 5:** Presentation - Prepared a presentation of my project for a non-technical audience. Covered goals, success criteria, data, approach, basic descriptions of the model, findings, risks/limitations, impact, next steps and conclusions.


### Dataset
Analysis was performed on [The European skills and jobs survey (ESJS)](https://www.cedefop.europa.eu/en/projects/european-skills-and-jobs-survey-esjs), by the European Centre for the Development of Vocational Training, and it is a periodic EU-wide survey aimed at collecting information on the skill requirements, skill mismatches and initial and continuing learning of adult workers in EU labour markets.

It came with a very informative questionnaire manual and could be easily interpreted across different countries. 

The survey was undertaken in all (28) EU member states in 2014 and aims to provide robust information from representative samples of adult workers on a set of core variables, including:

* sociodemographic characteristics;
* job characteristics;
* job-skill requirements (literacy, numeracy, digital, analytical, manual and interpersonal skills);
* skill mismatches (vertical; horizontal; mismatches in specific skills; skill gaps and deficits; skill mismatch transitions);
* initial and continuing vocational education and training participation;
* labour market outcomes (wages, job insecurity, job satisfaction).

Each row in my data represented an individual person’s responses to the questionnaire and there were 48676 rows. Each column represented a question, and questions could be split into more than one column through a similar system to dummying the data. There were 293 columns.


### Hypotheses
My first hypothesis asked whether I could predict job satisfaction better than baseline, and if so, what were the features that could predict this best.

My second hypothesis asked whether I could predict job satisfaction better than baseline based on factors that related to one of the five aspects of skills mismatch. Once again, if so, what were the features that could predict this best. 


### Data Cleaning
From the ESJS I dropped columns and rows where there were too many null values (over 75%) as well as columns that I felt weren't relevant to my question such as who the respondent lives with. 

I also changed 'don't know's  and 'not applicable’s to more suitable figures in line with the rest of the dataset for modelling. 

This left me with 96 columns (questions) and 16000 rows (individuals), with each value referring to one answer of a question by a respondent.


### Data Engineering
In order to have data in the right format for hypothesis 2, I needed to engineer some aspects of it. In this way, I ensured that either the data was categorised into one of five categories related to a skills mismatch - over skilled, under skilled, over qualified, under qualified or a horizontal mismatch - or it was disregarded. 

An example of this is below in the form of a density plot:

![qual match have](https://user-images.githubusercontent.com/93994809/157852451-ad38aed0-4d16-4ae8-8ed8-b3c8e72cf102.png)

Here the qualification difference is taken from two questions that ask what is your qualification level and what is the qualification level needed to enter into your career. Job satisfaction is plotted to the left and a value over one implies that an individual has more qualifications than are needed to enter into the career.


### Preliminary Findings based on EDA
My EDA focused on job satisfaction as this was going to be used as my target variable during modelling. Some quick insights showed me that:

* The happiest age is 64 (probably because everyone is looking forward to retiring!)
* The happiest country is Luxembourg
* The happiest career is a farmer with careers that involve the outdoors such as construction and farming, or people, such as teachers scoring highly
* 4/10 is the level at which people with the highest salary rate their job satisfaction implying that the money isn’t everything!

Using a correlation matrix, I looked at some elements that looked interesting in more detail.

Firstly, skills needed in the workplace. Violin plots showed me that teamwork, communication and problem solving seem to be needed the most whilst foreign languages and dealing with customers are needed the least. 

![skills needed](https://user-images.githubusercontent.com/93994809/157852658-52859337-2844-459c-9b9b-7d6686473b9b.png)

Secondly, how well the respondent's skill level is matched with what is needed. Apart from foreign languages, the matches are pretty evenly spread.

![skills you have](https://user-images.githubusercontent.com/93994809/157852714-1ac257a8-f36e-4a5f-b8a5-0ee3c14b299f.png)

Thirdly, why people choose their job in the first place. Interestingly, security was important, but less so pay, while the most important factors were that the job suited them and they found it interesting. 

![people choose job](https://user-images.githubusercontent.com/93994809/157852853-315897e6-cc1f-420d-9f46-2d1933624251.png)

It's interesting to note that these plots show that people primarily picked numbers in the 5-10 range. This finding fed into my assumption that in this project outliers should not be removed. People were much more likely to respond to a question in a certain range, but being outside that range implied either that they were someone that always marked surveys in that way, or they were outside the norm for that question, both of which were very relevant pieces of information that needed to be kept in.

![top correlations](https://user-images.githubusercontent.com/93994809/157852878-7f6f1bee-2e16-4087-ab53-cedd4a612771.png)

I also discovered with my correlation that there were little linear correlations between my top performing factors and job satisfaction (as shown below). The top performing correlation was between whether an individual chose the job because they found it interesting and this was correlated at 0.29. 

This means that when it comes to modelling the data, the success of the model might be constrained by the low correlations.


### Target Variable
People were asked how satisfied they were at work and asked to give an answer between 0 and 10. Instead of having 11 classes, I converted the data into three classes, ‘very satisfied’, ‘somewhat satisfied’ and ‘not at all satisfied’ with a baseline accuracy of 0.69 predicting class 2, ‘very satisfied’. 


### Success Metrics
As a classification problem, my modelling was evaluated primarily using accuracy, as I wanted to best determine whether I could correctly identify, and better predict, whether an individual would find their job ‘very satisfying’, ‘somewhat satisfying’, or ‘not at all satisfying’. I supplemented this using both precision-recall and AUC curves.


### Machine Learning Findings 
#### Hypothesis 1
I used a number of different models, focusing on either regression or tree based modelling with bagging and boosting.

XGBoost, where new models are created that predict the residuals or errors of prior models and then add together to make the final prediction, performed best with an accuracy score of 0.72, and AUC score of 0.7237 and a precision-recall score of 0.785.

And there were a number of trends throughout the models in what factors influenced the score:

* Firstly, whether you find the job interesting.
* Secondly, whether it's a good match for you in terms of skills.
* Thirdly, whether there's a chance of you losing your job in the next year or whether you have recently been demoted.
* Fourthly, working in specific sectors, especially outdoors and hands-on.
* Having the ability to learn new things.
* And having the ability to choose the way you want to work.

An interesting finding was that in the precision-recall curve class 2 always fared much better than 0 or 1 - the modelling works much better for class 2.

![Precision-Recall](https://user-images.githubusercontent.com/93994809/157853019-c3f95e57-17d0-4890-9b9c-80d8ac093757.png)

The precision-recall (PR) curve plots the precision versus the recall (=true positive rate) for all possible thresholds. Ideally, we want a high recall and a high precision. The area under the curve summarises this curve in a single number. The higher the AUPRC, the better. 

![Multiclass ROC](https://user-images.githubusercontent.com/93994809/157853061-b34431a5-926d-4930-b13d-8f4778f9af05.png)

The ROC curve plots the true positive rate versus the false positive rate for all possible thresholds. In this case, there was always less of a distinction between classes. 

One thing to investigate would be the class imbalance of the target variable and to find out whether oversampling or under sampling the classes might improve these scores. 

#### Hypothesis 2
Hypothesis two looked at whether we could predict job satisfaction due to the skills mismatch. Here the baseline is slightly higher at 0.70 due to the feature engineering we did. 

Once again I applied the same models, but this time the answer was no. So my hunch that a skills mismatch is a fundamental reason why people don't enjoy their careers is incorrect. 

The Grid Searched Gradient Boost performed best here but only due to the higher ROC and PRC scores of 0.612 and 0.709 respectively. 


### Shortfalls of the Project
There are a number of ways in which this project could be improved upon. 

Firstly, data engineering. I employed a fairly crude method of data engineering which could be improved upon. For example, if you trained as a teacher and now work in teaching that would be a match. However, you could have a biology degree and now work in teaching as a biology teacher and that would not be a match. But most people agree that it would.

Secondly, whether some of my data was overfitting. My test  scores and training scores for the most part weren't unaligned, but they could occasionally have been improved. 

Lastly, as mentioned before the target might have been imbalanced and balancing them might have affected the overall outcome. 


### Future Development 
There are a number of future roads I could go down in order to both improve my modelling and discover new trends in the data.

Firstly through Principal Component Analysis (PCA) to identify trends, clusters and outliers in the data. PCA might help to further uncover relationships between observations and variables, and among the variables themselves. 

A brief investigation using PCA didn't improve my score and I found the components difficult to interpret, but there might be a better model here through other unsupervised learning techniques. 

Secondly, using more than one dataset, incorporating other countries, especially non-western countries where satisfaction and wellbeing are viewed differently. Another way to look at this question would be to investigate COVID vs non-COVID years where work-life changed drastically.

Furthermore, linking these to specific wellbeing and productivity data and getting a better understanding of how they are all connected.

Lastly, using Natural Language Processing (NLP) to develop my data engineering and identify more specific careers to enhance both hypotheses and improve the skills mismatch data. In the original survey there was a question which asked specifically what job you had. I dropped this, but it would be interesting to explore further. It might take a while as the answers were in  a number of different languages, so I'd have to find a way to translate them into English before they'd be of much use. 


### Putting it into Action
As we now have the ability to better understand what factors make individuals satisfied in their employment, governments, companies and even individuals can use this to help ensure they or their employees can be happy in the workplace.

For employers, this might mean implementing ways that employees can choose how they work, for example, if possibly offering a hybrid method and increasing the learning curve of the employee so that they can develop skills more quickly.

Whilst, for employees this might mean choosing a role for reasons that will make them happy, for example one that offers an interesting day-to-day work life, doing a career that’s vocation, hands-on and possibly outside, picking a career that offers variety, choosing a role that is just beyond their skillset and preferably trying not to lose their job!
