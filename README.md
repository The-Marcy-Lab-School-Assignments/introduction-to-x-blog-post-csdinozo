# FastAPI — Python

By [Catalina Dinozo](https://github.com/csdinozo)


## Introduction

FastAPI is a modern, high-performance framework for building Application Program Interfaces with Python based on standard Python type hints. [Sebastián Ramírez](https://github.com/tiangolo) created this framework through combining various alternative frameworks, plug-ins, and tools in adherence to existing standards. Based on tests by the framework's internal development team, FastAPI increases development speed by about 200 to 300% and reduces about 40% of developer errors. With 86.5 thousand stars on GitHub, FastAPI is among the most popular backend frameworks given its lightweight and modular design and ease of use.


## Reasons to Use

FastAPI's growing popularity stems from its asynchronous processing and modular design, making it well applicable to high-traffic applications. The framework's basis in Pydantic ensures data integrity and consistency through type hints and validation. Given its asynchronous capabilities, FastAPI is suitable for applications requiring real-time communication such as messaging, telehealth, and shopping platforms.


## Installation and Setup

* For frameworks (including React and Express): setup/installation/configurations, core concepts, key methods or approaches. Include code snippets with explanations.
1) After creating a [virtual environment](https://docs.python.org/3/library/venv.html), install FastAPI in the terminal.

```py
pip install "fastapi[standard]"
```

Ensure `"fastapi[standard]"` is in quotes, so it will work in all terminals.

2) Create a `main.py` file.

```py
from fastapi import FastAPI

app = FastAPI()
```

3) Run the server using the terminal.

```py
fastapi dev main.py
```


## Core Concepts

* Asynchronous Programming: Using Python's `async` and `await` keywords, FastAPI can handle multiple requests simultaneously, allowing concurrency.
* Dependency Injection: Path operation functions declare what they require to run, and FastAPI provides the code with these dependencies, allowing for shared logic and database connections and enforced security, authentication, and role requirements.

    ```py
      from fastapi import APIRouter, Depends
      from schemas.users import UserPrivateOut
      from utils.user import get_current_user
      from pydantic import BaseModel
      from db import get_db
      
      class MessageResponse(BaseModel):
          message: str
      
      router = APIRouter(prefix="/user", tags=["User"])
      
      @router.get("/me")
      def get_my_user_data(current_user: User = Depends(get_current_user)) -> UserPrivateOut:
          return UserPrivateOut.from_orm(current_user)
    ```

    - The `get_my_user_data` path operation function uses `Depends(get_current_user)` to instruct FastAPI to call the `get_current_user` function and inject its return value into the `current_user` parameter

* Pydantic: Pydantic models use Python type hints to ensure data conforms to the expected format and automatically generates validation errors for invalid inputs. FastAPI automatically deserializes request data and serializes response data based on Pydantic models.

    ```py
      from .base import OrmBase

      class UserCreate(OrmBase):
          username: str
          email: str
          password: str

      @router.post("/register")
      def register(user_create: UserCreate, db: Session = Depends(get_db)):
          return create_user(db, user_create)
    ```

    - `UserCreate(OrmBase)` defines a Pydantic model named `User`.
    - `username`, `email`, and `password` are fields with their respective type hints.
    - The `register` function takes a `user_create` parameter of type `UserCreate` and a `db` parameter of `Session` — defaulting to the value of the `get_db` function. FastAPI automatically validates the incoming request body against the UserCreateModel.
 
* Query and Optional Parameters: Function parameters not part of the path parameters are automatically interpreted as query parameters — after the `?` in a URL and separated by `&` characters. FastAPI automatically recognizes default variables — such as those defaulted explicitly with `None` — as optional and those without default values as required.

    ```py
      from fastapi import APIRouter, Depends, HTTPException
      from sqlalchemy.orm import Session
      from models import Post
      from schemas.posts import PostOut
      from crud.post import get_all_posts
      from typing import List
      from db import get_db
    
      @router.get("/posts", response_model=List[PostOut])
      def get_posts(count: int = 20, skip: int = 0, db: Session = Depends(get_db)) -> List[PostOut]:
          posts = get_all_posts(db, skip = skip, limit = count)
          return posts
    ```

    - The `get_posts` function retrieves a list of all posts in the database.
    - Its query parameters `count` and `skip` are defaulted to allow for pagination, such that the URLs 'http://127.0.0.1:8000/posts/?count=20&skip=0' and 'http://127.0.0.1:8000/posts/' will both display 20 posts, bypassing zero initial items.


## Compare and Contrast

* For programming languages: What are the key differences between the new language and JavaScript? What are the commonalities?
* For frameworks (including React and Express): What are the alternatives to this framework? Can you compare this framework to anything we've learned in the Core Curriculum? What are the tradeoffs when choosing this framework compared to the alternatives?

## Conclusion & Tips for learning this language/framework.

* Wrap things up
* Provide links to resources that you used to help you learn the language.
