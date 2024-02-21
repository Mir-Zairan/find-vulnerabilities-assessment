# find-vulnerabilities-assessment

# The various vulnerabilities that I discovered are mainly:

## Cross-Site Scripting Vulnerability:

Outputting variables such as $filename in places like templates/index.php and error messages to the browser directly without proper sanitization can lead to this particular type of attack. Hackers can run Js code and steal various sort of information including session id.

## File upload Vulnerability: 

In src/Controller.php there is a method for uploading a file but file type validation isn't in place . This can be tormenting as hackers can easily upload malicious files including PHP scripts and spread malware.

## Authorization flaws:

Lacks of authorization checks can be seen in src/Files.php to verify whether a user logged in has the right to perform a particular action on files. This could lead to users accessing or modifying the files that they don't own.
 
## Unnesccesary Information Disclosure:

In app.php 'error_reporting(E_ALL)' could expose sensitive info in a production env. if display errors are not turned off. Hacker can use this info to craft an attack on the server or application.

## Poor Session Mangement:

In index.php, sessions are being started without taking proper security measures like regenerating sessions IDs upon login or setting various other cookie attributes like HttpOnly, Secure etc. This could lead to session hijacking and fixation attacks.

## CSRF:

No CSRF token is used in forms. This could lead to unintentional actions being performed by the user that can impact data intregity.
