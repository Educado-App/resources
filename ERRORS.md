# Educado error codes

This file contains the error codes used on the Educado platform(s).

Please extend this documentation with any error codes you use in the project. If you want to add a new category, please coordinate with the other teams - bring it up at the next integration team meeting. This way we ensure that there are no clashes in the error codes used.

> **Notice!**\
> This file does not and should not include Portugese translations for errors.\
> These error messages are not meant to be displayed to users.

## Guide for using errors in project

Error codes are defined as strings, in the form `"E{Category}{Code}"`, where *category* and *code* are 2 decimals each, e.g. `"E0101"`. This means there is 100 total possible categories with 100 possible error codes each.

These codes are mainly intended to be used in communication between the frontend(s) and the backend. As such they should be sent in the form of a JSON object.

**Example of JSON response containing an error**

```json
json_response: {
  error:{
    code: 'E0101',
    message: 'something went wrong'
  }
}
```

Both the frontend(s) and backend contain an `errorCodes.js` file, implementing the codes listed in this document. These can be used to easily import and use error codes.

> Error codes shown in parenthesis are reserved, but have not been implemented yet.

## E00 General errors
- **E0000** Unknown error
- **E0001** Authentication token is invalid or expired.
- **E0002** User's role does not have the necessary permissions for this action.
- **E0003** Server could not be reached.
- **E0004** User not found.
- **E0005** No courses found
- **E0006** Course not found.
- **E0007** No sections found.
- **E0008** Section not found.
- **E0009** Course does not contain sections.
- **E0010** Email could not be sent.
- **E0013** Content creator not found
- **E0014** Invalid id
- **E0015** Invalid time interval. Use "day", "week", "month" or "all".
- **E0016** Invalid parameters.


## E01 Login Errors

- **E0101** Invalid email.
- **E0102** Account is locked due to multiple failed login attempts. Please try again later.
- (**E0103** Account is not verified. Please check your email for a verification link.)
- (**E0104** Account is suspended or blocked by an administrator.)
- **E0105** Invalid password.

## E02 Signup Errors

- **E0201** User with the provided email already exists.
- **E0202** Password does not meet the minimum requirements.
- **E0203** Invalid email format.
- (**E0204** User registration is currently disabled.)
- (**E0205** Could not send a verification email. Please try again later.)
- **E0206** Email must contain "@" and ".".
- **E0207** Email must be atleast 6 characters.
- **E0208** Email is required
- **E0209** First and last name are required
- **E0210** Names must be between 1 and 50 characters.
- **E0211** Names must only contain letters, spaces, hyphens and apostrophes.
- **E0212** Password is required
- **E0213** Password must be at least 8 characters.
- **E0214** Password must contain at least one letter.

## E03 Logout Errors

- **E0301** User is not authenticated; logout is not possible.

## E04 Password Reset Errors

- **E0401** The provided email is not associated with any account.
- **E0402** Password reset link has expired.
- **E0403** Password reset link is invalid or has already been used.
- **E0404** Password reset code has expired.
- **E0405** Password reset code is invalid or has already been used.
- **E0406** Too many requests. Please try again later.

## E05 Verification Errors

- **E0501** Account is already verified.
- **E0502** Verification link has expired.
- **E0503** Verification link is invalid or has already been used.

## E06 Subscriptions Errors
- **E0601** Could not subscribe to course.
- **E0602** Could not unsubscribe to course.
- **E0603** Could not get users subscriptions.
- **E0604** Could not check users subscriptions.
- **E0605** Cannot subscribe to course: User is already subscribed to course.
- **E0606** Cannot unsubscribe from course: User is not subscribed to course.

## E07 Point System Errors
-  **E0701** Points added is less than or equal to 0.
-  **E0702** Points must be of type integer.
-  **E0703** Points are required.
-  **E0704** Max level reached.

## E08 Model Update Errors
-  **E0801** Attempted to update illegal field name.
-  **E0802** Field value is identical to the current value.
-  **E0803** Cannot update password directly.
-  **E0804** Points must be a positive number. 
-  **E0805** Old and new password required.
-  **E0806** Old password is incorrect.

## E09 Answer Exercises Errors
- **E0901** This exercise is already in completedExercises.
- **E0902** This section could not be found in the completedSections array.
- **E0903** This course could not be found in the completedCourses array.

## E10  Content Creator Approval Errors
- **E1001** This Content Creator has not been approved
- **E1002** This Content Creator has been rejected
- **E1003** Could not approve Content Creator
- **E1004** Could not reject Content Creator
- **E1005** Could not get Content Creator application
- **E1006** Could not upload application

## E11  Component Errors
- **E1101** The component array has reached its maximum size
- **E1102** The component array reached its maximum number of lectures
- **E1103** No exercises found.
- **E1104** Exercise not found.
- **E1105** No lectures found.
- **E1106** Lecture not found.
