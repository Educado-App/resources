# Feature Progress

This file exclusively shows features progress - see [FEATURES.md](FEATURES.md) for an overview of the features. 

## Table of Contents

- [Certificate Issuance System](#certificate-issuance-system)
- [Social Gamified Learning Experience](#social-gamified-learning-experience)
- [Mobile Offline Mode](#mobile-offline-mode)
- [Content creator website](#content-creator-website)
---

## Certificate Issuance System

#### Description:

The certificate issuance system is a feature that distributes certificates to users that shows their work/achievements. These certificates are given to both students and content creators. The students receive certificates when they complete a course, such that they have proof that they have completed a course. The content creators receive a certificate when they request one, such that they can prove they have have authored it. 

#### Progress:

- [Certificate issuance microservice](https://github.com/Educado-App/educado-certificate-service) has been created to handle certificates.
  - :heavy_check_mark: Through this microservice, one can create, retrieve, download and retrieve certificates.
  - :x: Security is considered in the microservice
- Content creator certificates: 
  - :heavy_check_mark: Certificates are created and stored in the database upon publication of a course.
  - :heavy_check_mark: The content creator is able to look through their certificates, which shows relevant information (course name, creator, estimated course duration, number of subscribers, average rating). 
  - :heavy_check_mark: The content creator can preview a pdf of their certificate, which generates with the dynamically updated information.
  - :x: The content creator can download a pdf of their certificate.
- Student certificates:
  - :heavy_check_mark: The student is able to to look through which certificates they have received, which shows relevant information.
  - :x: The student is able to preview/download a pdf of their certificate, which generates with the dynamically updated information.
  - :x: A certificate is generated as a student has finished a course.

---

## Social-Gamified Learning Experience
#### Description:
The social-gamified learning experience is a feature that encourages the students to use the app more and socialise through the application. As of now, the students receive points when answering exercises for a section which is a part of a course. The points are used to level up and compete against other students through a leaderboard, which is still to be implemented.
#### Progress:
- Leaderboard: 
  - :heavy_check_mark: Route created in back-end
  - :x: Leaderboard design implemented in frontend
- Extra points logic
  - :heavy_check_mark: Route created in back-end for giving extra points when in a section (answering multiple exercises correctly in a row).
  - :x: Logic implemented in front-end

---


## Mobile Offline Mode

#### Description: 
The Mobile Offline Mode is designed to ensure continuous access to Educado's resources, even in the absence of an internet connection. Tailored for users with inconsistent internet access, especially in underprivileged areas, this feature ensures uninterrupted learning.

#### Progress: 
- **Download a course:** Function created to download all data relating to a course from the backed. The locally stored data is arranged in the same manner the frontend expect from the backend. All data with one exception is store in the cache using asyncStorage. The key schema is a capital letter corresponding to the first letter of the component (ex. I for image) + the ID of the parent object (ex. I + componentID for images). The exception is videos, which are stored as base64 in a jason file.
  
- **Managing data fetching when offline/online:** StorageService and NetworkService manage and control if the app should fetch the data from the backend or use locally stored data. They have not been implemented in the point system as there where not time left when it was introduced.
  
- **Access course when offline:** You can access all the sections/lectures/exercises of a downloaded course when offline.  However, beacuse of time limitations, the tracking of point system, as well as the users progress, **does not** work when offline. An idea could be to track the users progress and points in AsyncStorage when offline.

- **Download only specific sections:** Another feature that is not yet implemented. 

#### Known issues/improvements  

  

- **Name scheme for individual users:** At the moment the course object is saved with a unique key (userID + courseID), but the rest of the elements are not assigned a key that is unique to the user. The solution to this would be to just add the userID to all keys. Another related/similar issue is how the videos is saved.  They have the same problems, but it should not be solved in the same suggested way as the video files take up a lot of storage space. One solution could be to have a counter stored, to count how many times a video has been downloaded. In fact, this might be a better solution for all the stored objects. That way you don’t have duplicates and only have to change the counter and delete a course object when a course has been downloaded by multiple users.  

  Why: Because this will allow multiple users using the same device to not accidentally delete saved courses from each other.  

- **Dividing StorageService into multiple files:** StorageService is quite large and handle multiple tasks, it also doesn’t adhere to the three-layer structure.  

  An approach to this is to separate the store functionality and the control functionality so one you have a controller that governs whether it should fetch data from the backend or the local storage, and a storage manager that manage storage and ODM functions. This would also help to adhere to the three-layer structure.  

  If you want to separate it more, you could divide Storage and ODM functions, or separate user storage and course storage. 

  An issue has also been made for this https://github.com/Educado-App/educado-mobile/issues/219#issue-2014293688 

- **Points not working offline:** Points does not work offline, this is because all the logic for handling it is on the backend and the point system does not use StorageService for backend calls. The fix would be to move the logic into StorageService, and have all calls to the backend go through StorageService. This would also help in adhering to the three-layer structure.


## Content creator website
#### Description:
Content creator website is made for the Educados content creators to view, edit, and create courses and the content for them.

#### Progress:
- Course:
  - :heavy_check_mark: A courses can be created
  - :heavy_check_mark: A courses can be edited
  - :x: Cover image upload   
  - :x: Cover image has a size limit 
  - :heavy_check_mark: The list of sections can be reorder in the course 
  - :x: The ordered list of sections can be saved
  - :heavy_check_mark: A courses "description" has a length limit
  - :x: A courses "name" has length limit  

- Sections:
  - :heavy_check_mark: A section can be created
  - :heavy_check_mark: A section can be edited
  - :heavy_check_mark: A lectures can be add to the section
  - :heavy_check_mark: A exercises can be add to the section
  - :heavy_check_mark: The list of lectures and exercises can be reorder in the section
  - :heavy_check_mark: The ordered list of lectures and exercises can be saved
  - :x: Upon saving incorrectly ("name" or "description" field empty), show an error message instead of a success message.
  - :heavy_check_mark: Component (lectures and exercises) counter is visually implemented.
  - :x: Component (lectures and exercises) counter is functionally implemented.
  - :x: A sections "name" and "description" has a length limit  

- Lectures:
  - :heavy_check_mark: A lecture can be created
  - :heavy_check_mark: A lecture can be edited
  - :heavy_check_mark: A lecture can be deleted
  - :x: A lecture can be previewed in phone view
  - :x: Video upload
  - :x: Video has a size limit 
  - :x: A lectures "name" and "description" has a length limit 

- Exercises:
  - :heavy_check_mark: A exercise can be created
  - :heavy_check_mark: A exercise can be edited
  - :heavy_check_mark: A exercise can be deleted
  - :x: A exercise can be previewed in phone view
  - :x: A exercises "name", "question", "answer", and "feedback" has a length limit 

---
