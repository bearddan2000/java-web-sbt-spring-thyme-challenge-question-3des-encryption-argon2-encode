# java-web-sbt-spring-thyme-challenge-question-3des-encryption-argon2-encode

## Description
A springboot secure web app with thymeleaf support.
Three roles are defined; USER, ADMIN, and SUPER. All roles
can access pages `/home`, `/login`, and `/about`. Only USER
can access `/user` and ADMIN only `/admin` whereas SUPER can
navigate to either and have its own `/super`. Each role
has an action USER=VIEW ONLY, ADMIN=READ/WRITE, SUPER=CREATE.
All password are encrypted with 3DES and encoded with argon2
to insure strong passwords.

3-DES is a 128 byte encryption but a 256 byte AES generated key
was used for the md5 digest password.

Presents a register form to create an inMemoryUser.
Once the user is created it is given the `USER` role
by default and auto logged in.

Presents a reset form to reset passwords on any user,
by default the user is reassigned `USER` role and auto
logged in. Only restriction on passwords are they match;
all validation is done client side.

Uses a challenge question on password rest and user register
to verify user. Customizes user data class by extending the
UserDetailService.

## Tech stack
- java
- sbt

## Docker stack
- openjdk:8-jdk-alpine

## To run
`sudo ./install.sh -u`
Available at http://localhost
- Login with id: user and password: pass
  - Challenge: question="Year you were born?" answer=1900
- Login with id: admin and password: pass
  - Challenge: question=0 answer=1900
- Login with id: super and password: pass
  - Challenge: question=0 answer=1900

## To stop (optional)
`sudo ./install.sh -d`

## For help
`sudo ./install.sh -h`

## Credits
- https://hellokoding.com/spring-security-login-logout-thymeleaf/
- https://www.javainterviewpoint.com/spring-security-inmemoryuserdetailsmanager/
