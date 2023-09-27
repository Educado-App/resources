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

## E00 General Authentication Errors

- **E0001** Authentication token is invalid or expired.
- **E0002** User's role does not have the necessary permissions for this action.

## E01 Login Errors

- **E0101** Invalid username or password.
- **E0102** Account is locked due to multiple failed login attempts. Please try again later.
- (**E0103** Account is not verified. Please check your email for a verification link.)
- (**E0104** Account is suspended or blocked by an administrator.)

## E02 Signup Errors

- **E0201** User with the provided email already exists.
- **E0202** Password does not meet the minimum requirements.
- **E0203** Invalid email format.
- (**E0204** User registration is currently disabled.)
- (**E0205** Could not send a verification email. Please try again later.)

## E03 Logout Errors

- **E0301** User is not authenticated; logout is not possible.

## E04 Password Reset Errors

- **E0401** The provided email is not associated with any account.
- **E0402** Password reset link has expired.
- **E0403** Password reset link is invalid or has already been used.
- **E0404** Password reset code has expired.
- **E0405** Password reset code is invalid or has already been used.

## E05 Verification Errors

- **E0501** Account is already verified.
- **E0502** Verification link has expired.
- **E0503** Verification link is invalid or has already been used.
