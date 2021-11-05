# Tutorial API with GraphQL

This project was made for learning proposes only, all information and steps where made from
https://www.twilio.com/blog/graphql-api-python-flask-ariadne


### Tools

 - Flask 
 - Flask-SQLAlchemy
 - Python 3.9
 - Graphql-core
 - Ariadne
 - SQLAlchemy
 
 
 ## General approach
 API for create, update, delete or get some Todo from database.
 **Todo** is a pending task or activity that user wants to achieve.
 
 **TODO table**
 
|  field | type  | description |
|--|--|--|
|id | int  |unique key from todo|
|description| str | todo description, ex: "do homework"|
|completed | bool | specify if task was completed or not|
|due_date | date| date of task creation|

 
### How to run project
1. Create VENV with python 3
2. Go inside new venv created
3. Install requirements file pip install -r requirements.txt
4. Set env var on your venv: 
	export FLASK_APP=main.py
	(this command depends of OS)
5. Execute project
	flask run
6. Visit [127.0.0.1:5000/graphql](http://127.0.0.1:5000/graphql)

### Actions (on GraphQL)
#### CREATING NEW ITEM
Creating new todo item

    mutation newTodo {
      createTodo(description:"Getting married", dueDate:"13-11-2021") {
        success
        errors
        todo {
          id
          completed
          description
        }
      }
    }

#### FETCHING ALL ITEMS
Getting all existing items

    query fetchAllTodos {
      todos {
        success
        errors
        todos {
          description
          completed
          id
        }
      }
    }

#### FETCHING A SIGLE ITEM BY ID
Getting item with id = 2

    query fetchTodo {
	  todo(todoId: "2") {
	    success
	    errors
	    todo { id completed description dueDate }
	  }
	}
#### UPTADE A SIGLE ITEM BY ID
Update item with id = 2, mark as done

    mutation markDone {
      markDone(todoId: "2") {
        success
        errors
        todo { id completed description dueDate }
      }
    }


 #### DELETE A SIGLE ITEM BY ID
Update item with id = 2, mark as done

    mutation {
      deleteTodo(todoId: "2") {
        success
        errors
      }
    }
