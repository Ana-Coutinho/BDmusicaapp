# BDmusicaapp

# Exercício 1
```
CREATE TABLE IF NOT EXISTS musicas (
id UUID PRIMARY KEY NOT NULL DEFAULT gen_random_uuid() ,
song_name VARCHAR(100),
song_path TEXT NOT NULL,
song_duration TIME NOT NULL,
song_date DATE NOT NULL,
singer VARCHAR(55) NOT NULL REFERENCES musicos(id),
composer VARCHAR(55) REFERENCES musicos(id),
song_poster BYTEA,
genre VARCHAR(55) NOT NULL,
)
```

# Exercício 2
```
CREATE TABLE IF NOT EXISTS musicos (
id UUID PRIMARY KEY NOT NULL DEFAULT gen_random_uuid() ,
specification ROLE NOT NULL,
name VARCHAR(55) NOT NULL,
date_of_birth DATE NOT NULL,
date_of_death DATE,
type VARCHAR(55) NOT NULL,
most_known_song UUID REFERENCES musicas(id),
biography TEXT,
)

CREATE TYPE role as ENUM (
'singer',
'composer',
)
```

# Exercício 3
```
CREATE TABLE IF NOT EXISTS usuarios (
id UUID PRIMARY KEY NOT NULL DEFAULT gen_random_uuid(),
email VARCHAR(55) NOT NULL UNIQUE,
password VARCHAR(55) NOT NULL,
full_name VARCHAR(55) NOT NULL,
age SMALLSERIAL NOT NULL,
prefered_genre VARCHAR(55),
creation_date DATE NOT NULL,
last_access TIMESTAMP NOT NULL,
phone CHAR(13) NOT NULL,
plan PLANOS NOT NULL,
)

CREATE TYPE planos AS ENUM (
'free',
'premium',
'premium plus',
)
```

# Exercício 4
```
singer(VARCHAR55) NOT NULL => singer VARCHAR(55) NOT NULL REFERENCES musicos(id),
```
```
composer VARCHAR(55) NOT NULL => composer VARCHAR(55) NOT NULL REFERENCES musicos(id),
```
```
most_known_song UUID  => most_known_song UUID REFERENCES musicas(id),
```
# Exercício 5
## Musicas
```
INSERT INTO musicas (song_name, song_path, song_duration, song_date, singer, genre) VALUES
('mypc/user/localfiles/songs',
'The Sharpest Lives',
'03:21',
'23/05/2006',
'My Chemical Romance',
'Alternative Rock',
)
```
```
INSERT INTO musicas (song_name, song_path, song_duration, song_date, singer, composer, genre) VALUES
('mypc/user/localfiles/songs',
'New Person, Same Old Mistakes',
'06:03',
'15/07/2015',
'Tame Impala',
'Kevin Parker',
'Alternative',
)
```
```
INSERT INTO musicas (song_name, song_path, song_duration, song_date, singer, composer, genre) VALUES
('mypc/user/localfiles/songs',
'Bodysnatchers',
'04:02',
'01/05/2008',
'Radiohead',
'Thom Yorke',
'Indie',
)
```
## Artistas
```
INSERT INTO musicos (specification, name, date_of_birth, type, biography) VALUES ( 'singer',
'Lovejoy',
'08/95/2021',
'rock',
'Lovejoy are an English indie rock band formed in Brighton in 2021. The band consists of lead vocalist and rythmm guitarist William Gold, lead guitarist Joe Goldsmith, drummer Mark Boardman and bassist Ash Kabosu, with all four sharing songwriting duties.',
)
```
```
INSERT INTO musicos (specification, name, date_of_birth, date_of_death, type, biography) VALUES ( 'composer',
'Kurt Cobain',
'20/02/1967',
'05/04/1994',
'Grunge',
'Kurt Donald Cobain was a north-american singer, famous for creating, singing and being the guitarist for Nirvana.',
)
```
```
INSERT INTO musicos (specification, name, date_of_birth, type, biography) VALUES ( 'singer',
'Freddie Mercury',
'05/09/1946',
'24/11/1991',
'rock',
'Lead vocalist of the rock band Queen.',
)
```
```
INSERT INTO musicos (specification, name, date_of_birth, type, biography) VALUES ( 'composer',
'Ludwig van Beethoven',
'17/12/1770',
'26/03/1827',
'classical',
'Famous German composer and pianist.',
)
```
```
INSERT INTO musicos (specification, name, date_of_birth, type, biography) VALUES ( 'composer',
'Johann Sebastian Bach',
'31/03/1756',
'28/07/1750',
'baroque',
'Renowned German composer and musician',
)
```
## Usuarios
```
INSERT INTO usuarios (email, password, full_name, age, prefered_genre, creation_date, last_access, plan) VALUES ('johndoe@gmail.com',
'john123doe',
'john doe',
'30',
'rock',
'13/11/2022',
'free',
)
```
```
INSERT INTO usuarios (email, password, full_name, age, creation_date, last_access, plan) VALUES ('janedoe@gmail.com',
'doe121110',
'jane doe',
'25',
'classical',
'17/02/2023',
'premium',
)
```
