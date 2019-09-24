# Empay-SSOWebApp-


This document defines the project plan of the Empay application. 
The overview includes objectives of the project, organization of the 
project team, development process that is going to be used during the project, assessment of 
possible risks, communication used between project stakeholders and project plan that includes 
time schedule and activity plan.


Background of our this project is to address the problem with today's daily enterprise where employees from different department have to sign in to to multiple different applications. Without an easy way to sign into multiple apps, employees will have to create a new account for each application they use and remember there credentials. It is then up to the employee to remember and sign in to all their applications needed to do there daily task. If only there was a way for user to single sign on to all of their applications all at once.  We developed our Empay web app to addresses the following problems

The objective of our Empay app is to allow employees to single sign on to multiple apps that the company provides and to keep their authentication running until the user logouts. Our focus is to provide the user with a simple login screen when first signing in to the company application. From there, the employee can easily access their jenkins, github, and all of their google applications. 

2.2 Project Requirements

Single sign onto enterprise applications
Be able to be directed to web portal
Be able to show employee profiles
Be able to view 80,000 employee details using Pagination
Be able to search/edit employee salary records
Be able to single sign onto Jenkins integrated with Github, Github and GSuites 


2.3 Use Cases

#
Use case
Steps to take
System Response
1
Employees can single sign onto an enterprise app to access a set of applications
Sign Up for an Okta account and then log in.
Show a web portal with a series of enterprise-based apps
2
Admin can single sign onto the enterprise app to view 80,000 employee details as well as their salary, to further modify them
Sign Up for an Okta account and then Log In
Show 80,000 employee records in the form of pagination, allow them to locate specific employee records with Filter enabled, same for their salary records. Can delete/modify salary also.
3
Employees can access a set of applications without more steps required for authentication 
Click on one of the tabs to get directed to any app
It skips the authentication request and directly logs the user into the app
4
Any commits made on the Github will notifies Jenkins
Make commits to Github
Record built within Jenkins







2.4 Architecture & High-Level Design

Single Sign On with Okta OpenID Connect, SAML, Jenkins, GitHub, GSuites




We used the OpenID Connect protocol on top of OAuth 2.0 to provide authentication with an ID token that contains a broader scope and claims for identity, so that different systems can interoperate, share authentication state and user information, which achieves the goal of Identity Access Management. And we used SAML as the federated identity to allow users single sign on into different service providers( Jenkins, Github, Google Suites) with single identity provider(Okta). 


Note:
The Service Provider never interacts with the Identity Provider directly. The browser acts as the middleman to redirect all the flows.
The Service Provider needs to know which Identity Provider to redirect before it knows the user.
The authentication could be initiated by either the Service Provider (SP-Initiated SSO) or the Identity Provider (IP-Initiated SSO)

Database Hosting with AWS RDS, CORS, EXPRESS, NODE, and SQL

We used AWS RDS (Relational Database System) to host our database on the Cloud, then used local MySQL workbench to insert all employee data provided on Github(https://github.com/datacharmer/test_db). Later, we used Express, Node, CORS and SQL to build the REST API and server that allows for HTTP requests and responses to and from our app to either fetch or modify data in the database. SQL was used to query and modify the database. 

App hosting with AWS EC2

To host the App on a public IP address, we used AWS EC2 as the cloud platform.

UI Construction with React JS/ Packages

To build the UI, we used ReactJS framework. To display employee data, we used 
react bootstrap packages( react-bootstrap-table, react-bootstrap-table2-paginator & react-bootstrap-table2-filter) which helped us set up a table and set pagination properties, along with another Filter package to help us locate specific employee records. 

Overview




Organization



Customer
The target customers are listed below:
Enterprise Admin/Manager
Enterprise Employees


Development process
          
Since we realized that SSO (Single Sign On) is the #1 feature of this project, we spent time experimenting both Auth0 and Okta, and we finally managed to figure it out with Okta OpenID Connect and SAML approach. For the SSO Integration part, we used SAML to configure the authentication with Jenkins, Github Enterprise as well as Google Suites. Before doing the integration, we needed to download Jenkins, set up an Github Enterprise account and new Google accounts. We then hosted Jenkins and Github on AWS EC2, so that we can use public IP to integrate Jenkins with our enterprise Github.
Another main feature of this app is to display 80,000 employee records fetched from Github using pagination. The first step we took was to set up a cloud database system, AWS RDS instance, then insert all the data into the database with local MySQL workbench by establishing connections with the Cloud database. Then, we set up the API and server using Express, Node, SQL, and CORS to allow fetching/modifying database data to/from our app with HTTP response/request. To actually display the data on our App UI, we need to reply on React JS and its packages. We used a REACT Bootstrap library to build the table, added pagination properties and filters.

