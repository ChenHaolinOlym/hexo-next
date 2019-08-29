---
title: 'CS50 Beyond SQL, ORMs, APIs'
tags:
  - CS50
  - beyond
  - sql
  - orms
  - apis
categories:
  - note
  - CS50 Beyond
date: 2019-08-19 00:13:41
---

<iframe src="//player.bilibili.com/player.html?aid=58975882&cid=102777100&page=11" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true" width="100%" height="500px"> </iframe>

<iframe src="//player.bilibili.com/player.html?aid=58975882&cid=102807043&page=6" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true" width="100%" height="500px"> </iframe>

In this course we use PostgreSQL.

## Data Types

Data Type | Usage
:-: | :-:
INTEGER | Storing integer
DECIMAL | Storing floating point number
SERIAL | A SERIAL will increment every time(like AUTOINCREMENT in sqLite)
VARCHAR | For a number of characters
TIMESTAMP | Store time
BOOLEAN | Ture or False
ENUM | Fix finite number of values

## Constraints

Constraints | Meaning
:-: | :-:
NOT NULL | Column cannot be empty
UNIQUE | All the data in that column should be unique
PRIMARY KEY | Primary key of the table. A table can have at most one primary key
DEFAULT | specify the default value of a column
CHECK | Used to enforce some constraints in the database

*Example for CHECK:* CHECK A > 0, means that you can't add negative INTEGER to the column A

## Functions

- SUM
- COUNT
- MIN
- MAX
- AVG

*Example:* `SELECT SUM(*) FROM xxx`/`SELECT COUNT(*) FROM xxx`
The database will return a column which column name is the function name.

## SQLAlchemy

Example code for using SQLAlchemy

```en
from sqlalchemy import create_engine
from sqlalchemy.orm import scoped_session, sessionmaker

engine = create_engine("database address")
db = scoped_session(sessionmaker(bind=engine))
```

After that, use `db.execute` to retrieve data.

SQLAlchemy can insert the arguments safely.
You should use the following way to weite the code.

```en
db.execute("INSERT INTO xxx VALUES (:a, :b, :c)", {"a": a, "b": b, "c": c})
```

## ORMs

ORM stands for Object Relational Mapping.

ORMs let you treat rows and tables inside of a database the same way you would treat an object and classes in an object oriented programming language.

With ORM, you can use a class to reference a table.

"flask_sqlalchemy" is a library that enables you to use sqlalchemy in flask application.

```en
from flask_sqlalchemy import SQLAlchemy

db = SQLAlchemy()

class Flight(db.Model):
    __tablename__ = "flight" (your table name)
    id = db.Column(db.Integer, primary_key=True)     (each represents a column)
    origin = db.Column(db.String, nullable=False)
    destination = db.Column(db.String, nullable=False)
    duration = db.Column(db.Integer, nullable=False)
```

The route file:

```en
app = Flask(__name__)
app.config["SQLALCHEMY_DATABASE_URI"] = "your database url"
app.config["SQLALCHEMY_TRACK_MODIFICATIONS"] = False
db.init_app(app)

def main():
    f = open("flights.csv")
    reader = csv.reader(f)
    for origin, destination, duration in reader:
        flight = Flight(origin=origin, destination=destination, duration=duration)
        db.session.add(flight)
        print(f"Added flight from {origin} to {destination} lasting {duration} minutes.")
    db.session.commit()

if __name__ == "__main__":
    with app.app_context():
        main()
```

Commands in SQLAlchemy:

commands | usage
:-: | :-:
`db.create_all()` | create table
`flight=Flight(origin='xxx', destination='xxx)`<br>`db.session.add(flight)` | insert data
`Flight.query.all()` | `SELECT * FROM flights`
`Flight.query.filter_by(origin="Paris").all()` | `SELECT * FROM flights WHERE origin = 'Paris'`
`Flight.query.filter_by(origin="Paris").count()` | `SELECT COUNT(*) FROM flights WHERE origin = 'Paris'`
`Flight.query.filter_by(id=28).first()`<br>`Flight.query.get(28)` | `SELECT * FROM flights WHERE id = 28`
`flight = Flight.query.get(6)`<br>`flight.duration = 280` | `UPDATE flights SET duration = 280 WHERE id = 6`
`flight = Flight.query.get(28)`<br>`db.session.delete(flight)` | `DELETE FROM flights WHERE id = 28`
`db.session.commit()` | `COMMIT`
`Flight.query.order_by(Flight.origin).all()` | `SELECT * FROM flights ORDER BY origin`
`Flight.query.order_by(Flight.origin.desc()).all()` | `SELECT * FROM flights ORDER BY origin DESC`
`Flight.query.filter(Flight.origin != "Paris").all()` | `SELECT * FROM flights WHERE origin != 'Paris'`
`Flight.query.filter(Flight.origin.like("%a%")).all()` | `SELECT * FROM flights WHERE origin LIKE '%a%'`
`Flight.query.filter(Flight.origin.in_(["Tokyo", "Paris"])).all()` | `SELECT * FROM flights WHERE origin IN ('Tokyo', 'Paris')`
`Flight.query.filter(and_(Flight.origin == "Paris", Flight.duration > 500)).all()` | `SELECT * FROM flights WHERE origin = 'Paris' AND duration > 500`
`Flight.query.filter(or_(Flight.origin == "Paris", Flight.duration > 500)).all()` | `SELECT * FROM flights WHERE origin = 'Paris' OR duration > 500`
`db.session.query(Flight, Passenger).filter(Flight.id == Passenger.flight_id).all()` | `SELECT * FROM flights JOIN passengers ON flights.id = passengers.fought_id`

## APIs

### HTTP Methods

- GET: retrieve resource
- POST: create a new resource
- PUT: replace a resource
- PATCH: update a resource
- DELETE: delete a resource

### Status Codes

- 200 OK
- 201 Created
- 400 Bad Request
- 403 Forbidden
- 404 Not Found
- 405 Method Not Allowed
- 422 Unprocessable Entity
