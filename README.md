# flask_CRUD_tutorial (TODO APP)

This repository is for flask TODOs APP. Here (readme.md) is only reference piece of code. To get Full code download the project

## Database set up (I am using flask-sqlalchemy)
```
pip install flask
pip install flask-sqlalchemy
```

```py
app.config["SQLALCHEMY_DATABASE_URI"] = "sqlite:///todo.db"
app.config["SQLALCHEMY_TRACK_MODIFICATIONS"] = False
db = SQLAlchemy(app)
```

## Creating simple TODOs class
```py
class Todo(db.Model):
    sno = db.Column(db.Integer,primary_key=True)
    title = db.Column(db.String(200), nullable=False)
    desc = db.Column(db.String(500), nullable=False)
    date_created = db.Column(db.DateTime, default=datetime.now())

    def __repr__(self) -> str:
        return f"{self.sno} - {self.title}"
```

## Adding Data
```py
todo = Todo(title="some_title", desc="some_desc")
db.session.add(todo)
db.session.commit()
```

## Get Data
```py
allTodo = Todo.query.all()
```

## Update Data
```py
todo = Todo.query.filter_by(key=value).first()
todo.title = "new_title"
todo.desc = "new_desc"
db.session.commit()
```

## delete data
```py
todo = Todo.query.filter_by(key=value).first()
db.session.delete(todo)
db.session.commit()
```

## Break-down of code: Todo.query.filter_by(key=value).first()
* `Todo` : is name of the class. <br>
* `query.filter_by(key=value)` : is used to get values matching the condition (key=value). <br>
* `first()` : return the first row with matching (key=value). <br> <br>


## Reference
YouTube ( code with harry) - https://www.youtube.com/watch?v=oA8brF3w5XQ&t=4232s <br>
SQL-Alchemy - https://flask-sqlalchemy.readthedocs.io/en/stable/quickstart/ <br>
Flask - https://flask.palletsprojects.com/en/stable/quickstart/ <br>
GeeksforGeeks - https://www.geeksforgeeks.org/flask-tutorial/ <br>


