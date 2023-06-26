## Denials Management Analysis


### Introduction
Healthcare is business and as such Denials Management is critical to ensure the business profits aren't spent unnecessarily  on appeals and claim. resubmission. Claim Denials are pain point, and the overall aim of denial management is to identify and mitigate potential denials. Appeals and resubmission of claims cost the practice money that could have been reinvested into the practice. In this project, I worked as the revenue cycle analyst to a small clinic and was charged with the responsibility of identifying current issues behind denials whilst also suggesting ways to reduce and possibly prevent future occurrence of same.



### Data

The dataset used in this article was a part of the RCM Analyst Career Accelerator Program at Parable Academy. The dataset is for transactions posted between Jan 17, 2021, and March 15, 2023. Although the data is from a system outside the patient accounting system, it can still be tied to the transaction data from the patient accounting system. There are three different type of adjustment transactions in the data:

·      835 Adjustments

·      Balance Transfers

·      Write-offs.

 

### Business Questions

·      How big is the denial problem by volume and by Dollars? 

·      How quickly are denials resolved? Is the clinic successful at overturning denials. Resolution means zero balance or with payment.

·      I wanted to see the overall denial trends of the clinic and the effectiveness of the claims process.

i.  What were the reasons for the initial denials?

ii.  Is the clinic doing well at submitting claims to meet the payer’s specification?



### Analysis and Insights 

My first task was to find out the magnitude of the denial problem by volume and by dollars. 

Claim denial rate is a key metric when it comes to healthcare revenue cycle management. It shows us the percentage of claims denied by insurance payers compared to the total number of claims submitted over a given period. This can be expressed as a percentage of total volume and dollars. A low denial rate shows the effectiveness of the organization; however, a high denial rate is an indication of issues related to billing, documentation, authorization etc. and this can result in revenue loss for the clinic.  For this clinic, the analysis showed a denial rate of 4.8% by volume and 4.1% by dollars. Industry standard rate is typically around 5-10% which tells us that the clinic is doing well in this regard.

<img width="706" alt="denial kpi" src="https://github.com/Tolulope-Akinmoju/Tolulope-Akinmoju.Github.io/assets/114532273/b2a271bd-18c0-4bac-9c65-9a15b878ce73">


My other goal in the analysis was to find out how quickly denials are resolved.

An important KPI for this is the percentage of initial denials overturned with reference to volume or dollars. To calculate this, 

% of initial denials overturned = Initials denials overturned & paid/ total initial denials paid & adjusted.

The closer this value is to 100% the better for the clinic because it gives an idea of how successful the team is at overturning denials to revenue. For this clinic, the rate is 35.4% of the total volume. I would expect that the initial denials overturned is closer to 1000% or at best 80%. This suggests to me that the clinic can do better at overturning their claims so that it does not lead to lost revenue.

<img width="239" alt="overturned rate" src="https://github.com/Tolulope-Akinmoju/Tolulope-Akinmoju.Github.io/assets/114532273/ebaa5ce5-88cd-4b43-ba8d-444e43b51605">

Next, I wanted to see the overall denial trends of the clinic. Looking at in a variety of ways, Denial reason, by payer type, by CPT procedure, and by provider. Going by the first chart that shows the denials by category, the top 3 categories for denials were Non-covered, Duplicates and Info Request. Interestingly, when this chart by category was compared to the chart that shows the denials by provider, we saw that the same type of denials was consistent across board. This tells us that denials observed are not necessarily a provider problem. The suspicion here by denial category was more of a process problem. 

<img width="848" alt="denials by variety" src="https://github.com/Tolulope-Akinmoju/Tolulope-Akinmoju.Github.io/assets/114532273/702531e2-f6e1-43be-afaf-ed0e4d9727d4">



My next focus was on the different payer types. I was hoping to find out if the denials were payer specific. What type of payers were giving what denial and were there particular payers responsible for a type of denial. My finding showed that Commercial/Managed Care, Blue Cross/ Blue Shield and Managed Medicaid/Medicare were the payers with most denials.


<img width="409" alt="payertype" src="https://github.com/Tolulope-Akinmoju/Tolulope-Akinmoju.Github.io/assets/114532273/a4773f0e-9734-4845-9179-e572cba5bec5">




  

My next point of analysis was to drill down on these payers to find out the individual payers responsible for the denials and to find what were their reasons. Each denial category can be drilled down to CARC (Claim Adjustment Reason Code) /RARC (Remittance Advice Remark Code) codes to give us specific reasons for the denials observed. From my data, CARC Code 96 and 18 were the top CARC reasons and the associated RARC Codes give us the specific requirement of the payers that contributed to the denials observed. For CARC Code 96, the associated RARC codes were N362, N30 – Patient Ineligibility. Interestingly, when review was done with respect to the different procedures to see if specific procedures were causing the denials, the same denial reasons (CARC/RARC codes) apply which tells us the issues weren’t procedure specific. 


<img width="941" alt="denial procedurecarc" src="https://github.com/Tolulope-Akinmoju/Tolulope-Akinmoju.Github.io/assets/114532273/e74df089-0b8d-4350-97c2-0a02c817a089">

  

Overall, breaking down denials into categories as shown in the table above allows us to classify denials as avoidable or non-avoidable. Doing this helps us to explore different areas where opportunities exist for improvement while ultimately focusing on what is avoidable. 


![carc pix](https://github.com/Tolulope-Akinmoju/Tolulope-Akinmoju.Github.io/assets/114532273/ebfc1b2b-0f56-4ec9-8e39-e0b071f5469c)



For an interactive dashboard report of the analysis performed, Please follow the link [[here](https://app.powerbi.com/view?r=eyJrIjoiN2NmZTFiZTUtOWMxNi00MDAzLThhMzktYTJlNmEwZmM1NzEzIiwidCI6IjAyMTcyZTg2LTgxYWItNGQzZS04MzgxLTQ2YTIxNzBkZGFmZSJ9)]



### Recommendations

•      Study their current processing tools for eligibility and insurance verifications to recommend improvements due to the high volume of denials because of eligibility.

•      Have a plan in place to notify patients in advance for cases where patients do not have coverage.

•      Ensure there is a plan in place that edits your software.

•      Train and retrain staff in cases where there are knowledge gaps.

•      Communicate findings to everyone involved in the process to prevent future occurrence.

•      Have a strategy in place to monitor progress towards reducing denials.



### Conclusion

Going by this data, it is safe to conclude that the different denials observed weren’t provider, payer, or procedure specific. Our findings showed that the top denial for this practice was CARC Code 96(non- covered), and it seems to be with three primary payers. A deeper look showed that the denials have very specific underlying reasons. Documentation and coding, Eligibility process and billing were the major issues reflected here so if we fix these processes in the front end, we would be able to minimize these types of denials in the future. Thanks for reading through my project. I would appreciate any suggestions or feedback.



 

I am open to explore any revenue cycle analyst opportunities out there so feel free to connect with me on [[Linkedin](https://www.linkedin.com/in/tolulope-akinmoju)] and be on the lookout for future data projects from me.




