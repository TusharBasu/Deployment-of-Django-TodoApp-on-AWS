# Deployment-of-Django-TodoApp-on-AWS

<!--
<iframe width="560" height="315" src="https://www.youtube.com/watch?v=0Led6QnDhIY" frameborder="0" allowfullscreen></iframe>
-->

Used this simple Todo list app build with django to deploye on aws.

<img width="1440" alt="todoApp" src="https://github.com/TusharBasu/Deployment-of-Django-TodoApp-on-AWS/assets/126240600/a9580b1d-483b-474a-a11f-153495299887">

First check on Local server if it's working or not.

-Open VS Code >Create a Projects folder and clone the app using "git clone" command.
````bash
git clone 'https://github.com/TusharBasu/django-todo.git'
````
(Prerequisite git should be installed in system and a working GitHub account.)

Git installation file- https://www.git-scm.com/download/win (for windows)

GitHub- Click here https://github.com/ and create an account.

![Screenshot 2024-06-10 003236](https://github.com/TusharBasu/Deployment-of-Django-TodoApp-on-AWS/assets/126240600/faa91e32-fa2d-4e3c-9191-903608a1462b)

-Enable Virtual Environment to testing out application by running this command- "python -m venv .venv" 

-for activate virtual environment run- ".\.venv\Scripts\activate"

Here we can see virtual environment is succefully activated!!!
![image](https://github.com/TusharBasu/Deployment-of-Django-TodoApp-on-AWS/assets/126240600/98e9dc10-9c9b-4877-be41-43c716f95cd6)



>[!Note]
>Download django for further process. Run command- "pip install django"

![image](https://github.com/TusharBasu/Deployment-of-Django-TodoApp-on-AWS/assets/126240600/18b72e54-47af-4c05-9667-a6465e44b449)

After Installation run this command
````bash
python manage.py makemigrations
````

![image](https://github.com/TusharBasu/Deployment-of-Django-TodoApp-on-AWS/assets/126240600/4d9276ad-cfbd-4e9a-af3b-6d51f945a1ff)

This will create all the migrations file (database migrations) required to run this App.

Now, to apply this migrations run the following command
```bash
$ python manage.py migrate
```

![image](https://github.com/TusharBasu/Deployment-of-Django-TodoApp-on-AWS/assets/126240600/89d89251-0b71-424c-850a-42ea3418290b)


One last step and then our todo App will be live. We need to create an admin user to run this App. On the terminal, type the following command and provide username, password and email for the admin user
```bash
$ python manage.py createsuperuser
```

Now let's make the App live. Start the server by following command

```bash
$ python manage.py runserver
```
we can see server is running now and I can access my app on http://127.0.0.1:8000/ 

![image](https://github.com/TusharBasu/Deployment-of-Django-TodoApp-on-AWS/assets/126240600/2c35f8f6-653d-42da-9ce1-0dc58b8bf9c6)

![image](https://github.com/TusharBasu/Deployment-of-Django-TodoApp-on-AWS/assets/126240600/fd765d11-3ece-41c4-b373-650999f9dc7f)

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


# ***Now Deployment on AWS.***

## -First Create a Micro service EC2 instance on aws.

![image](https://github.com/TusharBasu/Deployment-of-Django-TodoApp-on-AWS/assets/126240600/8ad3c472-f9a8-4710-aeba-36051bb0e6ab)

## -Connect instance using EC2 Instance Connect.

![image](https://github.com/TusharBasu/Deployment-of-Django-TodoApp-on-AWS/assets/126240600/ed985311-e1f8-49e8-8a09-f5600fdb7adf)


>[!Note]
>Commands for Fullfill Prerequisite for EC2 instance.
````bash
sudo apt-get update
sudo apt install python3-pip
pip3 install django
````

-Making project directory in ubuntu ec-2 server and cloning the app into it by using these commands.

````bash
mkdir projects
````

````bash
cd projects
````
````bash
git clone https://github.com/TusharBasu/django-todo.git
````

![Screenshot 2024-06-10 165935](https://github.com/TusharBasu/Deployment-of-Django-TodoApp-on-AWS/assets/126240600/e5b5cd94-dac2-4c22-af3c-35c1f391ecb3)

-Creating Superuser, email id and password for the django app on EC2 Instance.

![Screenshot 2024-06-11 011202](https://github.com/TusharBasu/Deployment-of-Django-TodoApp-on-AWS/assets/126240600/0931dc6f-9725-449c-889d-c95a5f86f0f0)

-Using bash command to run server
```bash
python3 manage.py runserver 0.0.0.0:8001
````
## ***Using 0.0.0.0:80001*** for globally access my app.

![Screenshot 2024-06-11 011202](https://github.com/TusharBasu/Deployment-of-Django-TodoApp-on-AWS/assets/126240600/b4e66149-589c-448c-9fc8-d6aa9709b7df)

## -Edit ***inbound rules*** and add ***custom TCP*** to run my application anywhere.

![Screenshot 2024-06-11 013757](https://github.com/TusharBasu/Deployment-of-Django-TodoApp-on-AWS/assets/126240600/3e2d3b6a-055e-4d35-831c-5a3bf90ee68c)

## Configure settings.py file for allowing host to anywhere.
````bash
nano todoApp/settings.py
````

>[!Note]
>put '*' in allowed host to allow any server access.
>
![Screenshot 2024-06-11 014453](https://github.com/TusharBasu/Deployment-of-Django-TodoApp-on-AWS/assets/126240600/b27dc62b-3cee-4dab-a8b0-bbdd798deb27)

## Now run command to activate server
```bash
python3 manage.py runserver 0.0.0.0:8001
```
![Screenshot 2024-06-11 015219](https://github.com/TusharBasu/Deployment-of-Django-TodoApp-on-AWS/assets/126240600/ea5bd997-4089-4dd4-a617-26da2ccc0ac9)

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# > Finally!!! We Deployed our todo app on AWS using ec-2 instance, we can access our application on url: http://54.210.81.142:8001/

![Screenshot 2024-06-11 015450](https://github.com/TusharBasu/Deployment-of-Django-TodoApp-on-AWS/assets/126240600/fcbdb8c8-f740-4e06-81be-a345767d899c)











