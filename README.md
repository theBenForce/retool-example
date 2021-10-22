# Retool Example

This repository provides an example Retool applicaiton to track
your vehicle's efficiency.

![Preview](https://i.imgur.com/jXZSzlA.png)

Import the `Fillups.json` file into retool and connect it to
a SQL Server database after running the following SQL script.

```sql
CREATE TABLE vehicle (
  vehicle_id int NOT NULL IDENTITY PRIMARY KEY,
  user_id varchar(32) NOT NULL,
  name varchar(128) NOT NULL,
  image_url varchar(256)
)

CREATE TABLE fillup (
  fillup_id int NOT NULL IDENTITY PRIMARY KEY,
  vehicle_id int NOT NULL,
  timestamp datetime NOT NULL DEFAULT GETDATE(),
  volume float NOT NULL,
  distance float NOT NULL,
  efficiency AS distance / volume,
  CONSTRAINT FK_Vehicle FOREIGN KEY (vehicle_id)
  REFERENCES vehicle (vehicle_id)
)
```
