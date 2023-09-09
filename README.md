# Tax Document Reader Application 

The Tax Document Reader Application is an advanced cloud-based 
software specifically designed to streamline the data extraction process from 
tax file documents and efficiently store the extracted information in a 
database. Its primary objective is to simplify and expedite tax file processing 
for government organisations, facilitating accurate data for calculations of 
individual taxes for taxpayers.

The users of the application are organisations who need to process the tax 
documents and performance targets for the application include fast and 
accurate data extraction, secure storage of sensitive tax information, and 
seamless retrieval of the data based on the user's email address and 
automate the process of sending emails to users whose email addresses 
are extracted from the uploaded tax documents, ensuring that they receive 
relevant notifications whenever any requirements arise.

**AWS Services Used:**

1) Aws Lambda
2) Aws Gateway
3) Aws DynamoDB
4) Aws SNS
5) AWS EC2
6) AWS S3
7) Amazon Textract

**Front End:** 
The web application on EC2 instances were developed with react 
component-based architecture, virtual DOM for efficient updates, 
declarative syntax, and vast ecosystem, React stands out as the optimal 
option for frontend development. 

Additionally, it facilitates server-side rendering, collaborates 
seamlessly with React Native for mobile app development, and boasts an 
active and engaged community. Its user-friendly learning curve and robust 
state management support further cement React's position as a leading 
frontend framework .

**Back End:**

Lambda functions are implemented using Node.js, which is an 
excellent choice for backend development due to its asynchronous and 
non-blocking nature, enabling efficient handling of multiple requests 
simultaneously.

It uses JavaScript for both frontend and backend, has a vast 
package ecosystem, and offers high performance for real-time applications. 
Its active community ensures continuous support and updates, while its 
event-driven architecture allows for easy scalability. Node.js is well-suited 
for real-time applications and rapid prototyping, making it a top pick for 
backend development.

For data extraction from documents, Python was utilized due to its 
suitability for compute-intensive tasks like Optical Character Recognition 
(OCR). Python provides a wide range of libraries and tools that excel in 
handling OCR and other document processing tasks efficiently.


**Architecture**

![image](https://github.com/Kovarthanan-murugan/Dal_CSCI_5410_DocumentReaderProject/assets/90558927/7f515ee0-c4b3-424a-9c3b-8a29a1c11ef4)

**System Deployment to the Cloud:**

 Using Cloud formation service provided by AWS that allows to 
define and manage AWS infrastructure using code templates. It simplifies 
the process of provisioning and maintaining resources, enabling you to 
create stacks of AWS resources easily. With CloudFormation, you can 
automate the deployment of various AWS services and efficiently manage 
complex environments.

It supports rollback, change sets, and integration with other AWS 
services, making it a valuable tool for infrastructure as code (IaC) and cloud 
resource management.

In the process of provisioning the backend for application, begin by 
creating essential components such as the REST API, S3 bucket, and 
DynamoDB resources. Subsequently, configured the Lambda functions and 
pass the relevant details of these services as environment variables. These 
environment variables serve as crucial inputs that the Lambdas utilize to 
execute their operations effectively.

Once the backend setup is complete, proceeded to provide the 
provisioned API URL as an environment variable to an EC2 instance. This 
EC2 instance is responsible for hosting the frontend of our application, 
ensuring smooth integration between the backend and frontend 
components.
