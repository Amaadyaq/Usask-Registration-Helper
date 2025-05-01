# cmpt370_team19

## Installation (only required to install docker (docker installs all dependencies in a container))
- go to directory you want to install in
- git init (if needed)
- git remote add origin https://git.cs.usask.ca/vwg123/cmpt370_team18.git
- git branch -M main
- git pull origin main
- docker compose up -d
- docker attach django-docker
- then inside the docker container enter
    - python3 manage.py runserver 0.0.0.0:8000
- now the web application is visible on the browser with url localhost:8000

## Dependencies and versions
- asgiref==3.8.1
- Django==4.2.19
- djangorestframework==3.15.2
- sqlparse==0.5.1
- tzdata==2024.2
- psycopg2==2.9.10
- selenium==4.29.0
- django_filter

## Running the web app
- python manage.py runserver 
- py manage.py runserver (for windows)

## Format required for USASK term csv files 
- crn,subject,title,course_num,section,campus,instructor,days,start_dates,end_dates,times,linked,rmp_links,credits
- 31656,AREC,Agricultural Data Analytics II,262,02,USask - Main Saskatoon Campus,Patrick Lloyd-Smith,"'Monday,Wednesday,Friday'",'06-Jan-2025','04-Apr-2025','11:30  AM - 12:20  PM',"31658,31657",,3
- ...
- (upon testing qoutations are not required for data with spaces in it)
- Also if the term file doenst have rmp_links (fresh from scraper), you must run the file through add_rmp_links.py which uses profCodes which was updated in March 2025(updating this every year is preferable).

## Importing new csv into database
- sqlite3 db.sqlite3 (this works or mac and linux)
- .mode csv 
- .import csvfilename tablename
- note: for classes the tablename is HelperApp_SchoolClass

## When making changes to models or if having database issues
- delete everything in migrations folder except for __init__ file
- delete db.sqlite3
- run commands 
    - python manage.py makemigrations
    - python manage.py migrate
- import term csv to db

## Other Usefull Commands
- to add an admin 
    - python manage.py createsuperuser
- to migrate (do when making changes to django files and the changes are not updated)
    - python manage.py makemigrations
    - python manage.py migrate
