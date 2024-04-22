# YouTube Clone 
## Fullstack Clone focusing on System Design & Backend Functionality | NO YOUTUBE API USED

## 🤖 Introduction

I wanted to create a similar clone to the YouTube application but focusing purely on the system design aspect and the back end engineering aspect of youtube. There is a front end to this project but it is bare bones because I wanted to essentially recreate the YouTube API that they offer for YouTube clone like applications and recreate it using Firebase and GCP.

## ⚙️ Tech Stack
- TypeScript
- Next.js 14
- Express.js
- Docker
- FFmpeg
- Firebase Auth
- Firebase Functions
- Firebase Firestore
- Google Cloud Storage
- Google Cloud Pub/Sub
- Google Cloud Run

## 📒 System Design

Here I will breakdown the choice of features and design for this project and the reasoning behind each:
### What we want
  -  Users can sign in/out using Google Auth
  -  Users can upload videos ONLY while signed in
  -  Users can view a list of uploaded videos by signed in users (signed in or not)
  -  Users can view individual videos on a seperate watch page (signed in or not)
  -  Videos can be transcoded to multiple formats (Now only in 360p)

### High Level Design
1) Cloud Storage is going to store and raw and processed videos using FFmpeg to convert all videos to 360p just for testing purposes.
2) Google Cloud Pub/Sub is used to send messages to the custom video processing service.
3) Cloud Run will host a <i>non-public</i> video processing service. Then, after those raw videos turn into processed videos and are transcoded, they are uploaded to Google Cloud Storage.
4) Cloud Firestore will store the metadata for each video individually.
5) Cloud Run then will host a Next.js app, which serves as the YouTube web client.
6) Next.js app will make API calls to Firebase Functions
7) Firebase Functions will then fetch the videos from Cloud Firestore and return them.

   
