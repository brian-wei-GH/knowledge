# PyCharm -- GitHub repository

```textile
using django as an example
```

## part 1: setting

this markdown file is a manual for how to download the code from GitHub and work successfully. 

1. download from "your_repository_name" repository 
   
   1. open PyCharm IDE
   
   2. click top-right "Get from VCS" button 
   
   3. login your Github account
   
   4. select "your_repository_name" repository and click "clone" button 

2. creating env (.venv)
   
   1. top-right gear icon (settings)
   
   2. Project: your_project > python interpreter
   
   3. python interpreter dropdown menu (select python version) (better select python 3.11 / 3.12) 
   
   4. where? ==> add interpreter (top-right blue words) dropdown menu 
   
   5. select "Add Local Interpreter..."
   
   6. check Environment: "New" and click OK button 

3. Install library: (using + icon ) (this page is the same as python interpreter)

4. check the website Readme and install all necessary libraries. (**NOTE: make sure versions are the same**)

5. turn on the terminal (in PyCharm left-down corner with terminal icon) 
   
   1. writing the code (checking your Django version)
      
      ```textile
      pip install django==5.1.1 
      ```
   
   2. also, creating dataset format by using terminal
      
      ```textile
      python manage.py makemigrations
      ```
      
      ```textile
      python manage.py migrate              
      ```

6. run the IDE 

## part 2: pull/push code

1. when others upload their code to the repository, you need to pull the code before push the code to the repository.
   
   1. how to pull? find the "Git" in the toolbar (title bar) (cannot find the toolbar? The toolbar is the top line of your laptop, same with the Apple icon, file, date/time, wifi, and other icons)
   2. in the Git drop-down menu, click pull (troubleshot: checking your "Git Remotes"(path: Git > Manage Remotes...) is linking with the correct repository)

2. when you want to push the code to the repository:
   
   1. find the "Commit" icon in your left toolbox (the second icon "-o-" under the folder icon)
   2. click "Changes"
   3. you must write down the commit (try to explain the changes you made to the code.)
   4. you can select both "Commit" (blue button) or "Commit and Push.."
   5. if you select "Commit" blue button, go to "Git" > "push.." to push the code to the repository

## part 3: commit

1. you can check commits on the GitHub
2. in PyCharm, go to the left toolbox and click "Git icon" (left-bottom icon, under "!" problem icon). when you click the icon, click "Log" and you can see commits
