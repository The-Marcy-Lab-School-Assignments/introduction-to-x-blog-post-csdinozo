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



## Compare and Contrast

* For programming languages: What are the key differences between the new language and JavaScript? What are the commonalities?
* For frameworks (including React and Express): What are the alternatives to this framework? Can you compare this framework to anything we've learned in the Core Curriculum? What are the tradeoffs when choosing this framework compared to the alternatives?

## Conclusion & Tips for learning this language/framework.

* Wrap things up
* Provide links to resources that you used to help you learn the language.
