# freeCodeCamp: Build a Celestial Bodies Database

## Instructions

For this project, you need to log in to PostgreSQL with psql to create your database. Do that by entering psql --username=freecodecamp --dbname=postgres in the terminal. Make all the tests below pass to complete the project. Be sure to get creative, and have fun!

Don't forget to connect to your database after you create it 😄

Here's some ideas for other column and table names: description, has_life, is_spherical, age_in_millions_of_years, planet_types, galaxy_types, distance_from_earth.

## Requirements & My Solutions
**Create a database named universe**
```
CREATE DATABASE universe;
```
**Connect to the database**
```
\c universe
```
**Create tables named `galaxy`, `star`, `planet`, and `moon`**
- Your database should have at least five tables
```
CREATE TABLE galaxy();
CREATE TABLE star();
CREATE TABLE planet();
CREATE TABLE moon();
CREATE TABLE asteroid();
```
**Define Primary Key Columns**
- Each table should have a primary key
- Each primary key should automatically increment
- Each primary key column should follow the naming convention `table_name_id`.
```
ALTER TABLE galaxy ADD COLUMN galaxy_id SERIAL PRIMARY KEY;
ALTER TABLE star ADD COLUMN star_id SERIAL PRIMARY KEY;
ALTER TABLE planet ADD COLUMN planet_id SERIAL PRIMARY KEY;
ALTER TABLE moon ADD COLUMN moon_id SERIAL PRIMARY KEY;
ALTER TABLE asteroid ADD COLUMN asteroid_id SERIAL PRIMARY KEY;
```
**Define Foreign Key Columns**
- Each "star" should have a foreign key that references one of the rows in `galaxy`
- Each "planet" should have a foreign key that references one of the rows in `star`
- Each "moon" should have a foreign key that references one of the rows in `planet`
- Each foreign key column should have the same name as the column it is referencing
```
ALTER TABLE star ADD COLUMN galaxy_id INT NOT NULL;
ALTER TABLE planet ADD COLUMN star_id INT NOT NULL;
ALTER TABLE moon ADD COLUMN planet_id INT NOT NULL;
```
```
ALTER TABLE star ADD FOREIGN KEY (galaxy_id) REFERENCES galaxy(galaxy_id);
ALTER TABLE planet ADD FOREIGN KEY (star_id) REFERENCES star(star_id);
ALTER TABLE moon ADD FOREIGN KEY (planet_id) REFERENCES planet(planet_id);
```
**Define Secondary Columns**
- Each table should have at least three columns
- The `galaxy`, `star`, `planet`, and `moon` tables should each have at least five columns
- At least two columns per table should not accept `NULL` values
- You should use the `NUMERIC` data type at least once
- You should use the `TEXT` data type at least once
```
ALTER TABLE galaxy ADD COLUMN galaxy_shape VARCHAR(255) NOT NULL;
ALTER TABLE galaxy ADD COLUMN galaxy_color TEXT NOT NULL;
ALTER TABLE galaxy ADD COLUMN age_of_stars TEXT NOT NULL;
```
```
ALTER TABLE star ADD COLUMN constellation VARCHAR(255) NOT NULL;
ALTER TABLE star ADD COLUMN absolute_magnitude NUMERIC(2,1) NOT NULL;
ALTER TABLE star ADD COLUMN distance_from_earth VARCHAR(255) NOT NULL;
```
```
ALTER TABLE planet ADD COLUMN order_from_sun INT NOT NULL;
ALTER TABLE planet ADD COLUMN rings BOOLEAN NOT NULL;
ALTER TABLE planet ADD COLUMN has_life BOOLEAN NOT NULL;
```
```
ALTER TABLE moon ADD COLUMN orbit VARCHAR(255) NOT NULL;
ALTER TABLE moon ADD COLUMN diameter_in_miles INT NOT NULL;
ALTER TABLE moon ADD COLUMN year_discovered INT NOT NULL;
```
```
ALTER TABLE asteroid ADD COLUMN spectral_class VARCHAR(255) NOT NULL;
ALTER TABLE asteroid ADD COLUMN rotation_period_in_hours NUMERIC(6,3) NOT NULL;
ALTER TABLE asteroid ADD COLUMN orbital_period_in_yrs NUMERIC(5,3) NOT NULL;
```
**Create Rows & Values**
- Each table should have at least three rows
- The `galaxy` and `star` tables should each have at least six rows
- The `planet` table should have at least 12 rows
- The `moon` table should have at least 20 rows
```
INSERT INTO galaxy(name, galaxy_shape, galaxy_color, age_of_stars) VALUES ('Andromeda', 'elliptical', 'yellow and red', 'older & smaller');
INSERT INTO galaxy(name, galaxy_shape, galaxy_color, age_of_stars) VALUES ('Whirlpool', 'spiral', 'blue in arms and red in the centre', 'younger stars in arms & older stars at the centre');
INSERT INTO galaxy(name, galaxy_shape, galaxy_color, age_of_stars) VALUES ('Milky Way', 'barred-spiral', 'bright blue', 'very young new born stars');
INSERT INTO galaxy(name, galaxy_shape, galaxy_color, age_of_stars) VALUES ('Large Magellanic Cloud (LMC)', 'irregular', 'unspecified', 'a collection of older and new stars');
INSERT INTO galaxy(name, galaxy_shape, galaxy_color, age_of_stars) VALUES ('Medium Magellanic Cloud (MMC)', 'irregular', 'unspecified', 'a collection of older and new stars');
INSERT INTO galaxy(name, galaxy_shape, galaxy_color, age_of_stars) VALUES ('Small Magellanic Cloud (SMC)', 'irregular', 'unspecified', 'a collection of older and new stars');
```
```
INSERT INTO star(name, constellation, absolute_magnitude, distance_from_earth) VALUES ('Sun', 'n/a', 4.2, '93 million miles');
INSERT INTO star(name, constellation, absolute_magnitude, distance_from_earth) VALUES ('Sirius', 'Canis Major', 1.4, '8.6 light-years');
INSERT INTO star(name, constellation, absolute_magnitude, distance_from_earth) VALUES ('Canopus', 'Carina', -2.5, '74 light-years');
INSERT INTO star(name, constellation, absolute_magnitude, distance_from_earth) VALUES ('Alpha Centauri', 'Centaurus', 4.4, '4.3 light-years');
INSERT INTO star(name, constellation, absolute_magnitude, distance_from_earth) VALUES ('Arcturus', 'Bootes', 0.2, '34 light-years');
INSERT INTO star(name, constellation, absolute_magnitude, distance_from_earth) VALUES ('Vega', 'Lyra', 0.6, '25 light-years');
```
```
INSERT INTO planet(name, order_from_sun, rings, has_life) VALUES ('Saturn', 6, TRUE, FALSE);
INSERT INTO planet(name, order_from_sun, rings, has_life) VALUES ('Mercury', 1, FALSE, FALSE);
INSERT INTO planet(name, order_from_sun, rings, has_life) VALUES ('Uranus', 7, TRUE, FALSE);
INSERT INTO planet(name, order_from_sun, rings, has_life) VALUES ('Neptune', 8, TRUE, FALSE);
INSERT INTO planet(name, order_from_sun, rings, has_life) VALUES ('Jupiter', 5, TRUE, FALSE);
INSERT INTO planet(name, order_from_sun, rings, has_life) VALUES ('Venus', 2, FALSE, FALSE);
INSERT INTO planet(name, order_from_sun, rings, has_life) VALUES ('Pluto', 9, FALSE, FALSE);
INSERT INTO planet(name, order_from_sun, rings, has_life) VALUES ('Earth', 3, FALSE, TRUE);
INSERT INTO planet(name, order_from_sun, rings, has_life) VALUES ('Mars', 4, FALSE, FALSE);
INSERT INTO planet(name, order_from_sun, rings, has_life) VALUES ('Ceres', 10, TRUE, FALSE);
INSERT INTO planet(name, order_from_sun, rings, has_life) VALUES ('Haumea', 11, TRUE, FALSE);
INSERT INTO planet(name, order_from_sun, rings, has_life) VALUES ('Makemake', 12, TRUE, FALSE);
INSERT INTO planet(name, order_from_sun, rings, has_life) VALUES ('Eris', 13, TRUE, FALSE);
```
```
INSERT INTO moon(name, orbit, diameter_in_miles, year_discovered) VALUES ('The Moon', 'Earth', 2152, 1609);
INSERT INTO moon(name, orbit, diameter_in_miles, year_discovered) VALUES ('Ganymede', 'Jupiter', 3270, 1640);
INSERT INTO moon(name, orbit, diameter_in_miles, year_discovered) VALUES ('Titan', 'Saturn', 3202, 1655);
INSERT INTO moon(name, orbit, diameter_in_miles, year_discovered) VALUES ('Callisto', 'Jupiter', 2996, 1640);
INSERT INTO moon(name, orbit, diameter_in_miles, year_discovered) VALUES ('Io', 'Jupiter', 2264, 1640);
INSERT INTO moon(name, orbit, diameter_in_miles, year_discovered) VALUES ('Europa', 'Jupiter', 1940, 1640);
INSERT INTO moon(name, orbit, diameter_in_miles, year_discovered) VALUES ('Triton', 'Neptune', 1682, 1846);
INSERT INTO moon(name, orbit, diameter_in_miles, year_discovered) VALUES ('Mimas', 'Saturn', 246, 1789);
INSERT INTO moon(name, orbit, diameter_in_miles, year_discovered) VALUES ('Phobos', 'Mars', 2152, 1609);
INSERT INTO moon(name, orbit, diameter_in_miles, year_discovered) VALUES ('Deimos', 'Mars', 2152, 1609);
INSERT INTO moon(name, orbit, diameter_in_miles, year_discovered) VALUES ('Amaithea', 'Jupiter', 2152, 1609);
INSERT INTO moon(name, orbit, diameter_in_miles, year_discovered) VALUES ('Himalia', 'Jupiter', 2152, 1609);
INSERT INTO moon(name, orbit, diameter_in_miles, year_discovered) VALUES ('Eiara', 'Jupiter', 2152, 1609);
INSERT INTO moon(name, orbit, diameter_in_miles, year_discovered) VALUES ('Pasiphae', 'Jupiter', 2152, 1609);
INSERT INTO moon(name, orbit, diameter_in_miles, year_discovered) VALUES ('Sinope', 'Jupiter', 2152, 1609);
INSERT INTO moon(name, orbit, diameter_in_miles, year_discovered) VALUES ('Lysithea', 'Jupiter', 2152, 1609);
INSERT INTO moon(name, orbit, diameter_in_miles, year_discovered) VALUES ('Carme', 'Jupiter', 2152, 1609);
INSERT INTO moon(name, orbit, diameter_in_miles, year_discovered) VALUES ('Ananke', 'Jupiter', 2152, 1609);
INSERT INTO moon(name, orbit, diameter_in_miles, year_discovered) VALUES ('Leda', 'Jupiter', 2152, 1609);
INSERT INTO moon(name, orbit, diameter_in_miles, year_discovered) VALUES ('Thebe', 'Jupiter', 2152, 1609);
```
```
INSERT INTO asteroid(name, spectral_class, rotation_period_in_hours, orbital_period_in_yrs) VALUES ('Juno', 'S', 7.210, 4.36);
INSERT INTO asteroid(name, spectral_class, rotation_period_in_hours, orbital_period_in_yrs) VALUES ('Eugenia', 'FC', 5.699, 4.49);
INSERT INTO asteroid(name, spectral_class, rotation_period_in_hours, orbital_period_in_yrs) VALUES ('Eros', 'S', 5.270, 1.76); 
INSERT INTO asteroid(name, spectral_class, rotation_period_in_hours, orbital_period_in_yrs) VALUES ('AnneFrank', 'S', 15.12, 3.29);   
```

## Debugging
From the planet table, we can see that there are several star_id values (like 7, 8, 10, 11, 12, 13) that do not exist in the star table.
    - Update the `star_id` in the `planet` table to reference valid `star_id` values.
```
UPDATE planet SET star_id = 1 WHERE planet_id = 10;  -- Change Ceres to point to Arcturus
UPDATE planet SET star_id = 1 WHERE planet_id = 11;  -- Change Haumea to point to Arcturus
UPDATE planet SET star_id = 1 WHERE planet_id = 12;  -- Change Makemake to point to Arcturus
UPDATE planet SET star_id = 1 WHERE planet_id = 13;  -- Change Eris to point to Arcturus
```
We have also identified several star_id values in the planet table that do not correspond to any existing entries in the startable. 
```
UPDATE planet SET star_id = 1 WHERE star_id IN (7, 8, 9, 11, 12, 13);
```
We have also identified several planet_id values in the moon table that do not correspond to any existing entries in the planet table. 
```
UPDATE moon SET planet_id = 1 WHERE planet_id IN (14, 15, 16, 17, 18, 19, 20);
```
