# Atividade Prática 4
Por Anthony Bento, Turma 1 Sis Ra: 03231005

CREATE DATABASE sprint2;
USE sprint2;

CREATE TABLE país (
idPaís INT PRIMARY KEY,
nome VARCHAR (30),
capital VARCHAR(40));
 
CREATE TABLE atleta ( 
 idAtleta INT PRIMARY KEY auto_increment, 
 nome varchar(40), 
 modalidade varchar(40), 
 qtdeMedalha INT,
 fkPaís int, 
	CONSTRAINT fkPaís FOREIGN KEY (fkPaís)
		REFERENCES país(idPaís));
        
INSERT INTO atleta (idAtleta, nome, modalidade, qtdeMedalha) VALUES 
(null,'roger rodrigues','futebol','5'), 
(null,'roberto carlos','futebol','3'), 
(null,'drake da silva','basquete','10'), 
(null,'rubinho barriquelo','basquete','7'), 
(null,'joao pereira','volei','2'), 
(null,'davi vinicius','volei','3');
SELECT * FROM atleta;

INSERT INTO país (idPaís, nome, capital) VALUES
('1','Afeganistão','Cabul'),
('2','Brasil','Brasilia'),
('3','Alemanha','Berlim'),
('4','Chile','Santiago');
SELECT * FROM país;
 
UPDATE atleta SET fkPaís = 2 WHERE idAtleta = 1;
UPDATE atleta SET fkPaís = 4 WHERE idAtleta = 2;
UPDATE atleta SET fkPaís = 3 WHERE idAtleta = 3;
UPDATE atleta SET fkPaís = 1 WHERE idAtleta = 4;
UPDATE atleta SET fkPaís = 2 WHERE idAtleta = 5;
UPDATE atleta SET fkPaís = 3 WHERE idAtleta = 6;

SELECT * 
	FROM atleta JOIN país
		ON atleta.fkPaís = país.idPaís;
        
SELECT 
atleta.nome,
país.nome 
	FROM atleta JOIN país
		ON atleta.fkPaís = país.idPaís;
        
SELECT *
	FROM atleta 
		JOIN país ON atleta.fkPaís = país.idPaís WHERE capital = 'Santiago';
        
        

USE sprint2;

CREATE TABLE musica(
idMusica INT PRIMARY KEY auto_increment, 
titulo varchar(40), 
artista varchar(40), 
genero varchar(40),
fkAlbum INT,	
	CONSTRAINT fkAlbum FOREIGN KEY (fkAlbum)
		REFERENCES album (idAlbum));

CREATE TABLE album(
idAlbum INT PRIMARY KEY auto_increment,
nome VARCHAR (40),
tipo  varchar (40),
	CONSTRAINT chkTipo CHECK
		(tipo IN ('digital','fisico')),
dtLancamento DATE);
 
INSERT INTO musica VALUES 
(null, 'PRIDE','KENDRICK LAMAR','RAP'), 
(null, 'GONE GONE','TYLER THE CREATOR','RAP'), 
(null, 'COOL','Kash Dami','ROCK'), 
(null, 'SABOTAGE','KENDRICK LAMAR','ROCK'), 
(null, 'Boys a Liar','TYLER THE CREATOR','POP'), 
(null, 'Stay','Rihanna','POP'), 
(null,'Wifi','Kash Dami','TRAP'), 
(null,'Bandz','Rihanna','TRAP');

INSERT INTO album VALUES
(null,'WHOLLE LOTTA RED','digital','2022-10-12'),
(null,'Die Lit','digital','2021-11-12');

SELECT * FROM musica;
SELECT * FROM album;

UPDATE musica SET fkAlbum = 1 WHERE idMusica = 1;
UPDATE musica SET fkAlbum = 2 WHERE idMusica = 2;
UPDATE musica SET fkAlbum = 2 WHERE idMusica = 3;
UPDATE musica SET fkAlbum = 1 WHERE idMusica = 4;
UPDATE musica SET fkAlbum = 2 WHERE idMusica = 5;
UPDATE musica SET fkAlbum = 1 WHERE idMusica = 6;
UPDATE musica SET fkAlbum = 2 WHERE idMusica = 7;
UPDATE musica SET fkAlbum = 1 WHERE idMusica = 8;

SELECT *
	FROM musica JOIN album
		ON musica.fkAlbum = album.idAlbum;
        
SELECT 
musica.titulo,
album.nome
	FROM musica JOIN album 
		ON musica.fkAlbum = album.idAlbum;
        
SELECT *
	FROM musica JOIN album
		ON musica.fkAlbum = album.idAlbum WHERE tipo = 'digital';
 
