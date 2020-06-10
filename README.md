# Generic University
 Generic University's IT department are excited to release their new tool so students can see all their grades online! Although still under construction some hacker has used Sublist3r and found it despite it being under construction. Thankfully Generic University have a bug bounty program and `*.genericuniversity.ac.uk` is in scope, no one seems to have noticed this under construction tool yet so get out there are find those bugs!

## Vulnerable API
This is a Laravel App which I've used for several demos which is vulnerable to a number of vulnerabilities on the OWASP API top 10. This is not a CTF, the bugs are quite clear and not hidden, however I suspect this will be a useful demo!

### Vulnerabilities
Find out more about the [OWASP API Top 10](https://owasp.org/www-project-api-security/)
- API1:2019 Broken Object Level Authorization
- API2:2019 Broken User Authentication
- API3:2019 Excessive Data Exposure
- API5:2019 Broken Function Level Authorization
- API6:2019 Mass Assignment
- API7:2019 Security Misconfiguration

### Your Goals
1) Find the emails of the administrator
2) Brute force the API to find new endpoints
3) Find out what grades everyone got in a class
4) Edit someone's grade
5) Make an account
6) Login to your account
7) Access admin control panel
8) Delete everything
9) Restore everything

### Inital Setup
You will need to setup PHP, a webserver and a database suitable for laravel, you can use something like XAMPP on windows, or set it up yourself, [to these requirements](https://laravel.com/docs/7.x/installation#server-requirements). You can google to find manual setup instructions such as [1](https://websiteforstudents.com/install-laravel-php-framework-on-ubuntu-16-04-17-10-18-04-with-apache2-and-php-7-2-support/).

1. Clone `git clone https://github.com/InsiderPhD/Generic-University/`
2. run `composer update`
4. Change the `.env`
5. run `php artisan migrate`
6. run `php artisan db:seed`

### Manual Instalation (on Kali Linux)

1. sudo apt update
2. sudo apt install composer
3. sudo apt install php-xml
4. git clone https://github.com/InsiderPhD/Generic-University.git
5. cd Generic-University
6. composer update
7. cp .env.example .env

mysql:
8. sudo service mysql status
start if needed
9. sudo service mysql start

10. sudo mysql -u root
11. create database genericuniversity;
12. use mysql;
13. update user set password=PASSWORD("password") where user='root';
14. update user set plugin='' where user='root';
15. flush privileges;
16. quit

17. vim (edit file) .env

DB_DATABASE=genericuniversity
DB_USERNAME=root
DB_PASSWORD=password

:wq ( in case you didn't know how to quit vim :)

18. php artisian migrate
19. php artisan db:seed
20. php artisan key:generate
21. php artisan serve

22. open http://127.0.0.1:8000/

enjoy hacking api :)
