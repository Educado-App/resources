# Feature Progress

This file exclusively shows features progress - see [FEATURES.md](FEATURES.md) for an overview of the features. 

## Table of Contents

- [Certificate Issuance System](#certificate-issuance-system)
- [Social Gamified Learning Experience](#social-gamified-learning-experience)

---

### Certificate Issuance System

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

### Social-Gamified Learning Experience
#### Description:
#### Progress:
