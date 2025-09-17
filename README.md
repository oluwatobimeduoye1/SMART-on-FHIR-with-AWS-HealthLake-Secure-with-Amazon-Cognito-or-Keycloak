# INTRODUCTION 
AWS HealthLake is a HIPAA-eligible service that enables healthcare organizations to securely store, transform, and analyze health data at scale. It uses ML to extract insights like medications, diagnoses, and procedures, and organizes data in the FHIR standard for a unified patient view.
## SMART on FHIR support in AWS HealthLake
SMART refers to Substitutable Medical Applications, Reusable Technologies.
It’s an open standard that builds on the FHIR (Fast Healthcare Interoperability Resources) framework to provide a secure way for third-party applications to integrate with electronic health records (EHRs) and healthcare data systems.
- Uses OAuth 2.0 and OpenID Connect (OIDC) for secure authentication and authorization.
- Allows apps to access specific patient data with proper consent.
- Makes healthcare apps “substitutable,” meaning they can plug into different systems without heavy rework.

AWS HealthLake FHIR API capabilities support SMART on FHIR, which offers authorization based on the SMART framework using FHIR scopes and launch context. SMART on FHIR enabled HealthLake data store allows SMART on FHIR compliant applications to access data stored in a HealthLake data store. HealthLake data is accessed by authenticating and authorizing requests using an authorization server, and by setting up additional resources in AWS.

## Amazon Cognito
Amazon Cognito is a cost-effective customer identity and access management (CIAM) service that scales to millions of users. It supports social logins, SAML, and OIDC providers, offers advanced security features, complies with industry standards, and integrates seamlessly with front-end and back-end applications.


## AWS App Runner
AWS App Runner is a fully managed service that simplifies building, deploying, and scaling web applications and APIs. It provides automatic scaling, built-in security, and seamless AWS integrations to streamline the application lifecycle.

# Architecture
The following architecture diagrams depict the solutions we are going to build in the PROJECT 

## Amazon Cognito user pool as IdP
The first architectural diagram shows the interaction between SMART on FHIR application, Amazon Cognito user pool as IdP, AWS SMART on FHIR enabled HealthLake, and an AWS Lambda function to validate access tokens and extract relevant FHIR claims.

https://static.us-east-1.prod.workshops.aws/public/a32ab9e1-bec2-46ff-bf8e-ecc29f6a363e/static/architecture_cognito.png<img width="2451" height="1177" alt="image" src="https://github.com/user-attachments/assets/55c2cb52-72d5-4249-9b20-43104125a3fc" />

## Keycloak as IdP
The second architectural diagram shows the interaction between SMART on FHIR application, Keycloak as IdP hosted by AWS App Runner, AWS SMART on FHIR enabled HealthLake, and an AWS Lambda function to validate access tokens and extract relevant FHIR claims.

https://static.us-east-1.prod.workshops.aws/public/a32ab9e1-bec2-46ff-bf8e-ecc29f6a363e/static/architecture_keycloak.png<img width="1888" height="824" alt="image" src="https://github.com/user-attachments/assets/7411b60f-bd02-4028-be8e-1f4ef58f7956" />

















