S1

1.1

ALTER TABLE medewerkers
ADD geslacht varchar(1);

ALTER TABLE medewerkers ADD CONSTRAINT m_geslacht_chk CHECK (geslacht IN (‘M’, ‘V’));

-=TEST=-

INSERT INTO medewerkers (mnr, naam, voorl, functie, chef, gbdatum, maandsal, comm, afd, geslacht) VALUES (7548, 'Giard', 'G', 'TRAINER', 7903, '1954-11-04', 6000, 0, 20, ‘M’);

INSERT INTO medewerkers (mnr, naam, voorl, functie, chef, gbdatum, maandsal, comm, afd, geslacht) VALUES (7903, 'Giard', 'G', 'TRAINER', 7903, '1954-11-04', 6000, 0, 20, 'D');

ERROR:  new row for relation "medewerkers" violates check constraint "m_gelacht_chk"


1.2



INSERT INTO medewerkers (mnr, naam, voorl, functie, chef, gbdatum, maandsal, afd, geslacht)
VALUES (8000, ‘Donk’, ‘a’, ‘MANAGER’, ‘test1’, ’05-04-1978’, 2300.00, 50, ‘M’);

INSERT INTO afdeling ( anr, naam, locatie, hoofd ) VALUES (50, ‘ONDERZOEK, ‘ZWOLLE’, 7966);

1.3


ALTER TABLE afdelingen
ALTER COLUMN anr NUMERIC(10);

CREATE SEQUENCE afdeling_sequence
START WITH 0
INCREMENT BY 10
MINVALUE 0
MAXVALUE 100000000
NOCYCLE ;

INSERT INTO afdelingen (anr, naam, locatie, hoofd) VALUES (afdeling_sequence.nextval, ‘DEVELOPMENT’, ‘AMERSFOORT’, 7029);

INSERT INTO afdelingen (anr, naam, locatie, hoofd) VALUES (afdeling_sequence.nextval, ‘RESEARCH’, ‘HILVERSUM’, 7123);

INSERT INTO afdelingen (anr, naam, locatie, hoofd) VALUES (afdeling_sequence.nextval, ‘PRODUCTIE’, ‘BRABANT’, 7100);


1.4

ALTER TABLE afdelingen ALTER COLUMN anr NUMERIC(10);

CREATE TABLE adressen (
	postcode varchar(6),
	huisnummer NUMERIC(5),
	ingangsdatum date,
	einddatum date,
	telefoon NUMERIC(10) UNIQUE,
	med_mnr NOT NULL,
	PRIMARY KEY (postcode), PRIMARY KEY (huisnummer), 
	PRIMARY KEY (ingangsdatum),
	FOREIGN KEY (med_mnr) REFERENCES medewerkers (mnr),
	CHECK (einddatum>ingangsdatum)
);

INSERT INTO adressen(postcode, huisnummer, ingangsdatum, einddatum, 
telefoon, med_mnr)
VALUES (‘1316RL’, 86, ‘2020-09-07’, ‘2020-09-10’, 0612345678, 8000);



1.5

ALTER TABLE medewerkers CONSTRAINT verkoper_check ADD CHECK ((comm NOT NULL AND functie= 'VERKOPER') OR (comm NULL AND functie != 'VERKOPER’));
