# Example Scenarios

This section details example scenarios for using the API. Each scenario assumes that the Employer has set up and authenticated the API. 

- **Employer:** A customer or integration partner who is using the Vervoe system. 
- **Candidate:** A person who is being assessed by the Vervoe system.  
- **External System:** A system that the Employer has integrated with the Vervoe API. For example, an ATS, internal dashboard, or a web-application. 

---
### Example Scenario 1: Employer creates assessment content and views assessments in another system

1. **Employer** 
   
   In Vervoe, the Employer creates their own assessment content or selects from the Public Assessment Library. This is saved in the employer’s Private Assessments in Vervoe. 


2. **Employer**

   Employer clicks a link to view their Assessments. 


3. **External System **

   API call to Vervoe: Get list of assessments


4. **Vervoe API **
   
   API response to External System: Get list of assessments  


5. **Employer **

   Employer views a list of their Private Assessments in their ATS. 



### Example Scenario 2: Employer sends an assessment to a candidate 

1. **Employer** 
   
   Employer details what assessment they want to send (see Scenario 1) to a particular candidate (including their email, first name, and last name). 


2. **External System**

  API call to Vervoe: POST Invite candidate to complete assessment 


3. **Vervoe API**

  Vervoe API invites the candidate to the assessment. API response to External System:Invite candidate to complete assessment


4. **External System**

  Receives Vervoe API response including the specific URL for the candidate to access the assessment.


5. **Employer**

  Employer emails the URL to the candidate access the assessment. (The URL could also be embedded in a button for the candidate through the External System).




### Example Scenario 3: Employer views a candidate’s results for an assessment

1. **Employer** 

  Employer wants to view the candidate’s results for an assessment so they click on a view score button in the External System.


2. **External System**

  API call to Vervoe: GET Get candidate assessment report 


3. **Vervoe API**

  Vervoe API sends the details of the results. API response to External system: Get candidate assessment report


4. **External System**

  External System loads and displays the results. 


5. **Employer**

  Employer views the candidate’s results for the assessment. 


---

<!-- theme: success -->

> To learn more about the API solution or to set up your access please contact: [sales@vervoe.com](mailto:sales+api@vervoe.com). 