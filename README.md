## Smart Blood Donar Discovery & Emergency Blood Request Management Platform

## Problem Statement
Blood is one of the most critical resources required during medical emergencies, accidents, surgeries, and other life-threatening situations. However, finding the right blood group at the right time remains a major challenge. Traditional blood donation systems often depend on manual phone calls, social media requests, and disconnected records maintained by hospitals and blood banks. These processes can cause significant delays, especially when a patient requires blood urgently.

BloodBridge is proposed as a smart, centralized platform that connects blood donors, patients, hospitals, blood banks, and ambulance services in a single digital ecosystem. The primary goal of the platform is to reduce the time required to identify suitable blood donors and improve coordination during emergency situations.
<br>

## Proposed Solution

BloodBridge – Smart Blood Donor Discovery & Emergency Blood Request Management Platform is a centralized healthcare platform designed to solve the delay and coordination problems involved in finding compatible blood during medical emergencies.

The proposed solution connects patients, blood donors, hospitals, blood banks, ambulance services, and administrators through a single digital platform and provides an intelligent workflow for managing blood requirements from emergency request creation to fulfillment.


## Technologies Used

Frontend: React.js, Vite, JavaScript, HTML5, CSS3, Tailwind CSS, Lucide React.
Backend: Node.js, Express.js, REST APIs, MySQL, JWT, bcrypt, CORS, dotenv.
AI & Tools: Google AI Studio, n8n, AI Voice Agent, Git, GitHub, and Visual Studio Code.


## System Architecture
```
Users / Donors / Hospitals / Blood Banks / Ambulances
                         ↓
                React + Vite Frontend
                         ↓
              REST API / JWT Authentication
                         ↓
             Node.js + Express Backend
                         ↓
                     MySQL
                         ↓
       Smart Donor Matching & Request Engine
                         ↓
            n8n Automation / AI Services
                         ↓
          Notifications / Voice Agent


```
## Features


1.Secure User Authentication – Sign up, login, JWT authentication, and role-based access.<br>
2.Smart Donor Discovery – Finds compatible donors based on blood group, eligibility, location, availability, and donation history.<br>
3.Real-Time Donor Sorting – Prioritizes donors who are currently available and willing to donate.<br>
4.Emergency Blood Requests – Create and manage Critical, Urgent, and Normal blood requests.<br>
5.Hospital & Blood Bank Management – Manage blood requests, hospitals, and real-time blood inventory.<br>
6.Ambulance & Emergency Integration – Connect emergency incidents with hospitals and blood requirements.<br>
7.Donor Notifications & Responses – Notify matching donors and allow them to accept or decline requests.<br>
8.Family Member Management – Add family members with email confirmation and emergency details.<br>
9.Request Tracking – Track requests from creation through donor confirmation and fulfillment.<br>
10.Admin Command Center – Monitor donors, hospitals, blood banks, ambulances, requests, and system activity.<br>


## Installation
```
git clone <repository-url>
cd BloodBridge
npm install
```
Configure the MySQL database and create the required .env file with database and JWT credentials.

# Start Backend
```
cd backend
npm run dev
```

# Start Frontend
```
cd frontend
npm run dev
```

Open http://localhost:5173 in your browser to run BloodBridge.

## How to Run

Start the MySQL database and make sure the bloodbridge database is configured.<br>
Start the Backend:
```
cd backend
npm install
npm run dev
```
Start the Frontend in a new terminal:
```
cd frontend
npm install
npm run dev
```
Open the application in your browser:
```
http://localhost:5173
```
Login / Sign Up and start using the BloodBridge platform.


## Demo
Live Demo:https://bloodbridge.ai.studio/
<br>
Demo Video:https://drive.google.com/file/d/1ytkBcrBqQMq4Nfx1BSiXcZeE_tEJm96H/view
<br>
PPT Link:https://docs.google.com/presentation/d/1I8kdt1G5Qte4j4KW8JklOIncKJk5T7mB/edit?usp=sharing&ouid=104249712739982230395&rtpof=true&sd=true
<br>

## Deployment


BloodBridge was built from scratch in Visual Studio Code, with a React/Vite frontend, Node.js/Express backend, and MySQL database. After completing and testing the application locally, the project was integrated with Google AI Studio for the final application workflow and demonstration.
```
VS Code Development
        ↓
React + Vite Frontend
        ↓
Node.js + Express Backend
        ↓
MySQL Database
        ↓
API & Authentication Testing
        ↓
Google AI Studio
        ↓
Final Deployment / Demonstration
```
For your GitHub README, this concise version is suitable.

## Screenshots




## Future Enhancements

AI-powered blood shortage prediction and donor matching.<br>
n8n automation and AI voice-agent integration.<br>
SMS/WhatsApp emergency notifications.<br>
GPS-based real-time donor discovery.<br>
Mobile application and multilingual support.<br>
Advanced analytics for hospitals and blood banks.<br>






