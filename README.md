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

<img width="2451" height="1177" alt="image" src="https://github.com/user-attachments/assets/55c2cb52-72d5-4249-9b20-43104125a3fc" />

## Keycloak as IdP
The second architectural diagram shows the interaction between SMART on FHIR application, Keycloak as IdP hosted by AWS App Runner, AWS SMART on FHIR enabled HealthLake, and an AWS Lambda function to validate access tokens and extract relevant FHIR claims.

<img width="1888" height="824" alt="image" src="https://github.com/user-attachments/assets/7411b60f-bd02-4028-be8e-1f4ef58f7956" />


Both solutions use native AWS services following the Well-Architected Framework to ensure secure, reliable, efficient, and cost-optimized architecture.


# Securing HealthLake with Cognito User Pool
I will create an interaction between SMART on FHIR application, Amazon Cognito user pool as IdP, SMART on FHIR enabled AWS HealthLake, and an AWS Lambda function to validate access tokens and extract relevant FHIR claims. 

### I will achieve this by provisioning the following components:

- A Cognito user pool: This acts as a centralized user directory, managing user registration, authentication, and authorization.
- User pool resource servers: These resource servers define custom authorization scopes for your FHIR REST API. These scopes will specify the specific data and actions users are allowed to access within the HealthLake data store.
- A user pool app client: This component represents your FHIR application within Cognito and allows users to securely interact with the FHIR REST API.
- A HealthLake service role: This IAM role has the necessary permissions to carry out the FHIR REST API request, and its ARN needs to be returned by the token validation Lambda function.
- A token validation Lambda function: This Lambda function can decode the access token provided in the authorization header of the FHIR REST API request sent by the client application.
- A SMART on FHIR enabled HealthLake data store: This data store leverages the SMART on FHIR framework for authorization with HealthLake.

Then, we will test the solution with Postman to make FHIR REST API requests and retrieve patient records from the HealthLake data store by authenticating and authorizing with the Cognito user pool.

## Create a user pool
We will first create an Amazon Cognito user pool.



















