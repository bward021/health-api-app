# Flask Api Template
​
This is a simple template to help start a project off on the right foot.
​
## Setup
- Setup Virtual Environment
```
$ python -m venv venv
$ source venv/bin/activate
(venv) $ _
```
​
- Install the packages
```
(venv) $ pip install -r requirements.txt
```
​
## Running The Server
```
(venv) $ flask run
```
​
## Database Setup
​
We're using `flask-migrate` with `alembic` to do our database migrations.  You will notice there is already a migrations folder.  This keeps track of our migrations.  For more information read the [flask-migrate docs](https://flask-migrate.readthedocs.io/en/latest/), [alembic](https://alembic.sqlalchemy.org/en/latest/), or [this tutorial](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-iv-database).
​
- Setting up an initial migration
  - You only need to do this if your starting fresh.  If you already have migration folder you can skip this step.
```
(venv) $ flask db init
```
​
- After changing a model run the migrate command
```
(venv) $ flask db migrate -m "Message"
```
​
- After running the migrate command, run the upgrade command
```
(venv) $ flask db updgrade
```

## Creating appsqlite file
```
>>> from app import db
>>> db.create_all()
```

# Flask API Template

1. Create the environment
```
$ python -m venv venv
```
  - retart the terminal to jump into the environment

2. Create some files and folders
  - main.py
  - app (folder)
    - everything will live in this folder for the app
  
3. Set up the following:
  - README
  - GIT
  - .flaskenv
  - .env

4. inside the app folder create the following:
  - __init__.py
  - routes.py

5. Install Flask

6. run the following command:

```
$ pip freeze > requirements.txt
```

7. put the following in the __init__ file in app
```
from flask import Flask
from config import Config

app = Flask(__name__)
app. config.from_object(Config)

from app import routes
```

8. set up a .vscode folder with settings.json to correct formatting. (autoformatter will want every import at the top but with this flask some need to be at the bottom)
```json
{
  "editor.formatOnSave": false,
    "[python]": {
    "editor.tabSize": 4
  },
}
```

9. Open routes folder and put following
```
from app import app
```

10. After doing so you are able to create the routes in this file

11. go to main and 
```
from app import app
```

12. in your .flaskenv file put the following:
```
FLASK_APP=main.py
```

13. Run the following command in the terminal
```
$ flask run
```

14. set up your git repository

15. add new file to core called config.py. add the following code: 
```python
import os
from dotenv import load_dotenv

basedir = os.path.abspath(os.path.dirname(__file__))
load_dotenv(os.path.join(basedir, '.env'))

class Config(object):
    SECRET_KEY = os.environ.get('SECRET_KEY') or 'YOU-WILL-NEVER-GUESS'
    SQLALCHEMY_DATABASE_URI = os.environ.get('DATABASE_URL') or 'sqlite:///' + os.path.join(basedir, 'app.sqlite')
    SQLALCHEMY_TRACK_MODIFICATIONS = False
```

16. run the following code
```
$ pip install flask-sqlalchemy flask-migrate
```