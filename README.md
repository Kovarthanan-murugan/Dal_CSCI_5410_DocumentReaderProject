# Serverless-Trivia-Game

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

**Architecture**

![image](https://github.com/Kovarthanan-murugan/Dal_CSCI_5410_DocumentReaderProject/assets/90558927/7f515ee0-c4b3-424a-9c3b-8a29a1c11ef4)


**Lambda Explanation:**

**1. onConnectFunction:**

**Path:** backend/lambda/onConnectFunction.mjs

When the client request for new connection, Aws websocket  will create new connection for that client and lambda which as been get as a target for $connect route will get trigged and in this lambda the connection id and other details sent by the client as a request parameters when making the connection request will be stored in a database.



**2. getRequestFunction:**

**Path:** backend/lambda/getRequestFunction.mjs
This Lambda will get triggerd if the request body of the connection as the route **getRepsonseFromClient** which will trigger the lambda getRequestFunction to process the request by fetching the requested source, in this case the quiz requested by the users and other details like team members and players currently ready the play the same game.

And this data will be sent to another lambda **sendQuestionToClient** to send data to the client in the define interval mentioned for that particular requested quiz.

**3. sendQuestionToClient:**

**Path:** backend/lambda/sendQuestionToClient.mjs

It will send the data(quiz question)to all the connected client for that particular quiz at the time in the regular interval defined for that particular quiz.

**4. getResponseFunction:**

**Path:** backend/lambda/getResponseFunction.mjs

Each connected client will get the data from the server and will be provided with option to send response to the server, in this case each player will be displayed with the questions with they can answer individually and send resposne.

Each response from each client will be evaluated and scores will be update in a database which will later be used to calculate the performance of the player individually.


**5. onDisconnectFunction:**

**Path:** backend/lambda/onDisconnectFunction.mjs

When a client exits the game lobby, there connection will be disconnected and they will no longer get the data from the server.

**6. reponseToEndPoint:**

**Path:** backend/lambda/reponseToEndPoint.mjs
It provides options to other module done in different cloud services to access and modify content in the databases.

**Output:**
![image](https://github.com/Kovarthanan-murugan/Serverless-Trivia-Game/assets/90558927/82b83660-07f2-4dc2-9b16-3ebab6694f22)
![image](https://github.com/Kovarthanan-murugan/Serverless-Trivia-Game/assets/90558927/eabc419a-a7e1-40dd-8848-a1df0cbc3465)
![image](https://github.com/Kovarthanan-murugan/Serverless-Trivia-Game/assets/90558927/c1ce58e2-1461-429e-9f0f-74df5b2db7e5)
![image](https://github.com/Kovarthanan-murugan/Serverless-Trivia-Game/assets/90558927/597ea56d-c1d9-4f00-a2f4-1ec3166c6bbb)
![image](https://github.com/Kovarthanan-murugan/Serverless-Trivia-Game/assets/90558927/95107926-341f-4795-b89b-c49c64c0bad1)
![image](https://github.com/Kovarthanan-murugan/Serverless-Trivia-Game/assets/90558927/31049e62-f57b-454a-b233-ccda0f217c8f)

# Module2 User Profile Management

The application provides users with a comprehensive view of their profile details, including first 
name, last name, email, and age. Additionally, it offers insights into the user's game history 
performance. Users can not only view this information but also make changes to their existing 
profile values, which are then updated in the database and seamlessly propagated to all the 
relevant locations where these operations are executed.

**Features Implemented**

**1. User Details Display:** I have created a React frontend component that makes API calls to the 
Node.js backend hosted on GCP Cloud Functions. The backend interacts with Google Firestore 
to fetch and display user details on the frontend.

**2. User Details Editing:** The React frontend includes an editable form that allows users to modify 
their details. When users submit the form, it sends a request to the Node.js backend. The backend 
processes the request and updates the relevant user details in Google Firestore.
Game History Performance: I integrated Module 5 In-game Experience to track the player's 
performance. Module 5 sends events to the Node.js backend hosted on Cloud Functions 
whenever there is a change in the player's score. The backend processes these events and updates 
the game history performance data in Google Firestore.

**Services Used:**

**1. GCP Cloud Functions:** The Node.js backend is successfully hosted on GCP 
Cloud Functions. This choice of a serverless solution enables efficient handling of 
HTTP requests and automatic scaling based on demand. The implementation of 
Cloud Functions allows the application to optimize resource usage and costeffectively manage serverless computing. Integrating this backend with other GCP 
services ensures smooth communication and interoperability among different 
modules.
20

**2. Google Firestore :** The implementation of Google Firestore as the NoSQL 
document database has been successfully completed. This choice facilitates 
performing various operations related to user details in GCP. Firestore's flexible 
structure enables the storage of user profile information and game history 
performance data in a scalable and organized manner. Its integration with the 
backend has been effectively established, allowing seamless data flow and retrieval 
for the application's requirements. The utilization of Firestore provides a robust and 
efficient database solution within the GCP environment

**Architecture**

![image](https://github.com/Kovarthanan-murugan/Serverless-Trivia-Game/assets/90558927/c303468e-026b-4e23-af2a-8ba9d913c615)

The GCP-hosted Node.js backend has been seamlessly deployed onto Cloud Functions. This strategic decision to opt for a serverless approach ensures efficient management of HTTP requests and automatic scaling in response to demand fluctuations. By utilizing Cloud Functions, the application maximizes resource utilization and adeptly manages serverless computing, all while optimizing costs. Integrating this backend with other GCP services fosters smooth inter-module communication, promoting seamless functionality across various components.

![image](https://github.com/Kovarthanan-murugan/Serverless-Trivia-Game/assets/90558927/20ca31db-45bb-4146-b55c-c72827b2ff9f)

The integration of Google Firestore as the chosen NoSQL document database has been successfully executed. This selection greatly facilitates a range of operations concerning user details within the GCP ecosystem. Leveraging Firestore's adaptable structure, the application securely stores user profile information and game-related historical performance data in an organized and scalable manner. The backend's tight integration with Firestore ensures the uninterrupted flow of data, enabling efficient retrieval to fulfill the application's needs. The utilization of Firestore presents a resilient and effective database solution within the broader GCP environment.

**Output:**

**Retrieving User Profile Details**

![image](https://github.com/Kovarthanan-murugan/Serverless-Trivia-Game/assets/90558927/2855447a-a4eb-4a76-a63d-dd0ec5ba1eda)

**Editing User Profile Details**

![image](https://github.com/Kovarthanan-murugan/Serverless-Trivia-Game/assets/90558927/a4ffd2e6-7a60-4e40-8365-a009e61fdc7a)

**Game History Update**

![image](https://github.com/Kovarthanan-murugan/Serverless-Trivia-Game/assets/90558927/5945a698-40a2-428d-8c5f-20dc15efa921)
