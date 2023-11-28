# Central Resource Hub: Educado Guidelines

Welcome to the Educado Guidelines Central Resource Hub! This repository stands as the heart of information and collaboration for all things related to Educado, our innovative and transformative project. Here, we are committed to developing educational solutions that empower learners and educators while fostering a culture of shared knowledge.

### FEATURES.md

[Go to features](./FEATURES.md)

This file outlines the planned core features and functionalities of the Educado Platform. It provides a comprehensive overview of what our project aims to achieve and how it stands out in its field.

### ISSUE_TEMPLATE.md

[Go to issue template](./ISSUE_TEMPLATE.md)

When you encounter a problem, want to suggest an enhancement, or have a question, this issue template is your go-to resource. It guides you through creating structured and informative issue reports, ensuring that our team can address your concerns effectively.

### CODE_OF_CONDUCT.md

[Go to code of conduct](./CODE_OF_CONDUCT.md)

We value respectful and inclusive collaboration. Our Code of Conduct sets the expectations for behavior within our community. It promotes a welcoming environment where everyone can contribute positively and engage in meaningful discussions.

### PULL_REQUEST_TEMPLATE.md

[Go to PR template](./PULL_REQUEST_TEMPLATE.md)

If you're contributing code to our project, this pull request template streamlines the process. It helps you provide the necessary context about your changes, making it easier for our team to review and merge your contributions smoothly.

Feel free to explore these files, contribute to our project, and be part of our vibrant community. Your input is valuable to us, and together we can shape the future of ProjectX!

### Setting up and running the content creator web application (frontend)
1. Clone **educado-frontend** repository from Github
2. Add .env file in the **app** folder with the following values:
   - VITE_CERT_URL
   - VITE_BACKEND_URL
3. Navigate to **app** folder: `cd app`
4. Run in terminal: `npm install`
5. Run in terminal: `npm run dev`
6. Open link from terminal to visit the page

Requires that the backend and certificate services are running. Check their respective guides to run them.
If run successfully you will be met by the login screen when you open the page:
![image](https://github.com/Educado-App/resources/assets/65400638/66636a5c-1eea-43d0-9b22-20669741c2a6)

Create a new user by clicking the *Cadastre-se agora* button and fill out the required information. If you can't be bothered to use use your own mail then use a temporary mail. After logging in, you will be redirected to the courses page, which can be seen below. Note that the page looks different if there aren't any courses in the database.
![image](https://github.com/Educado-App/resources/assets/65400638/ef965ec7-74ac-4595-be77-e1ad6d582ace)

