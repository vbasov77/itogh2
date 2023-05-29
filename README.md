��������� ������� cat � ��������� ������������ ������� Linux, ������� ��� ���?�� �������� �������� 
(�������� ���� ��������, �������, ��������) � ������� ��������� �������� ���� ��������, ���������� � ����), � ����� ���������� ��. ����������� ���������� ���������� ���?��. ������������� ���?�, ��� ��� ����� ��� (������ ��������).
<img src="images/1.jpg"/>

2. ������� ����������, ����������� ���� ����.

<img src="images/2.jpg"/>

3. ���������� �������������� ����������� MySQL. ���������� ����� ����� �� ����� �����������.

<img src="images/3.jpg"/>

<img src="images/4.jpg"/>

4. ���������� � ������� deb-����� � ������� dpkg.

<img src="images/5.jpg"/>

5. �������� ������� ������ � ��������� ubuntu

Task 1
mkdir Kennel
cd ~/Kennel
cat > home_animals
cat > pack_animals
cat home_animals pack_animals > animals
cat animals
mv animals mans_friends
ls -ali

Task 2
cd ..
mkdir Kennel_system
cd ~/Kennel
mv mans_friends ~/Kennel_system
cd ~/Kennel_system
ls -ali

Task 3
sudo wget https://dev.mysql.com/get/mysql-apt-config_0.8.23-1_all.deb
sudo dpkg -i mysql-apt-config_0.8.23-1_all.deb
sudo apt-get update
sudo apt-get install mysql-server

Task 4
sudo wget https://download.docker.com/linux/ubuntu/dists/jammy/pool/stable/amd64/docker-ce-cli_20.10.13~3-0~ubuntu-jammy_amd64.deb
sudo dpkg -i docker-ce-cli_20.10.133-0ubuntu-jammy_amd64.deb
sudo dpkg -r docker-ce-cli

6. ���������� ���������, � ������� ���� ����� ������������ �����, �������� �������� � ������� ��������, � ������� ������� 
� ������ �������� �������� ������ ������: ������, �����, ������, � � ����� ������� �������� ������: ������, �������� � ����).

<img src="images/6.jpg"/>

7. � ������������ MySQL ����������� ������� ���� ������ ������� ���������
   CREATE DATABASE Human_friends;

8. ������� ������� � ��������� �� ��������� � ��

USE Human_friends;
CREATE TABLE animal_classes
(
Id INT AUTO_INCREMENT PRIMARY KEY,
Class_name VARCHAR(20)
);

INSERT INTO animal_classes (Class_name)
VALUES ('�������'),
('��������');


CREATE TABLE packed_animals
(
Id INT AUTO_INCREMENT PRIMARY KEY,
Genus_name VARCHAR (20),
Class_id INT,
FOREIGN KEY (Class_id) REFERENCES animal_classes (Id) ON DELETE CASCADE ON UPDATE CASCADE
);

INSERT INTO packed_animals (Genus_name, Class_id)
VALUES ('������', 1),
('����', 1),  
('��������', 1);

CREATE TABLE home_animals
(
Id INT AUTO_INCREMENT PRIMARY KEY,
Genus_name VARCHAR (20),
Class_id INT,
FOREIGN KEY (Class_id) REFERENCES animal_classes (Id) ON DELETE CASCADE ON UPDATE CASCADE
);

INSERT INTO home_animals (Genus_name, Class_id)
VALUES ('�����', 2),
('������', 2),  
('������', 2);

CREATE TABLE cats
(       
Id INT AUTO_INCREMENT PRIMARY KEY,
Name VARCHAR(20),
Birthday DATE,
Commands VARCHAR(50),
Genus_id int,
Foreign KEY (Genus_id) REFERENCES home_animals (Id) ON DELETE CASCADE ON UPDATE CASCADE
);

9. ��������� �������������� ������� �������(��������), ��������� ������� ��� ��������� 
� ������ ��������

INSERT INTO cats (Name, Birthday, Commands, Genus_id)
VALUES ('����', '2011-01-01', '��-��-��', 1),
('����', '2016-01-01', "���������!", 1),  
('����', '2017-01-01', "", 1);

CREATE TABLE dogs
(       
Id INT AUTO_INCREMENT PRIMARY KEY,
Name VARCHAR(20),
Birthday DATE,
Commands VARCHAR(50),
Genus_id int,
Foreign KEY (Genus_id) REFERENCES home_animals (Id) ON DELETE CASCADE ON UPDATE CASCADE
);
INSERT INTO dogs (Name, Birthday, Commands, Genus_id)
VALUES ('���', '2020-01-01', '�� ���, ������, ����, �����', 2),
('����', '2021-06-12', "������, ������, ����", 2),  
('�����', '2018-05-01', "������, ������, ����, ����, ���", 2),
('����', '2021-05-10', "������, ������, ��, �����", 2);

CREATE TABLE hamsters
(       
Id INT AUTO_INCREMENT PRIMARY KEY,
Name VARCHAR(20),
Birthday DATE,
Commands VARCHAR(50),
Genus_id int,
Foreign KEY (Genus_id) REFERENCES home_animals (Id) ON DELETE CASCADE ON UPDATE CASCADE
);
INSERT INTO hamsters (Name, Birthday, Commands, Genus_id)
VALUES ('�����', '2020-10-12', '', 3),
('�������', '2021-03-12', "����� ������", 3),  
('������', '2022-07-11', NULL, 3),
('�����', '2022-05-10', NULL, 3);

CREATE TABLE horses
(       
Id INT AUTO_INCREMENT PRIMARY KEY,
Name VARCHAR(20),
Birthday DATE,
Commands VARCHAR(50),
Genus_id int,
Foreign KEY (Genus_id) REFERENCES packed_animals (Id) ON DELETE CASCADE ON UPDATE CASCADE
);
INSERT INTO horses (Name, Birthday, Commands, Genus_id)
VALUES ('����', '2020-01-12', '�����, �����', 1),
('�����', '2017-03-12', "�����, �����, ���", 1),  
('������', '2016-07-12', "�����, �����, ���, ���", 1),
('������', '2020-11-10', "�����, �����, ���", 1);

CREATE TABLE donkeys
(       
Id INT AUTO_INCREMENT PRIMARY KEY,
Name VARCHAR(20),
Birthday DATE,
Commands VARCHAR(50),
Genus_id int,
Foreign KEY (Genus_id) REFERENCES packed_animals (Id) ON DELETE CASCADE ON UPDATE CASCADE
);
INSERT INTO donkeys (Name, Birthday, Commands, Genus_id)
VALUES ('������', '2019-04-10', NULL, 2),
('������', '2020-03-12', "", 2),  
('������', '2021-07-12', "", 2),
('���������', '2022-12-10', NULL, 2);

CREATE TABLE camels
(       
Id INT AUTO_INCREMENT PRIMARY KEY,
Name VARCHAR(20),
Birthday DATE,
Commands VARCHAR(50),
Genus_id int,
Foreign KEY (Genus_id) REFERENCES packed_animals (Id) ON DELETE CASCADE ON UPDATE CASCADE
);
INSERT INTO camels (Name, Birthday, Commands, Genus_id)
VALUES ('��������', '2022-04-10', '�������', 3),
('�����', '2019-03-12', "����������", 3),  
('�����', '2015-07-12', "���������", 3),
('������', '2022-12-10', "��������", 3);

10. ������ �� ������� ���������, �.�. ��������� ������ ��������� � ������ �������� �� �������. ���������� ������� ������, 
� ���� � ���� �������.

SET SQL_SAFE_UPDATES = 0;
DELETE FROM camels;

SELECT Name, Birthday, Commands FROM horses
UNION SELECT  Name, Birthday, Commands FROM donkeys;

11. ������� ����� ������� �������� �������� � ������� ������� ��� �������� ������ 1 ����, �� ������ 3 ��� � � ��������� 
������� � ��������� �� ������ ���������� ������� �������� � ����� �������

CREATE TEMPORARY TABLE animals AS
SELECT *, '������' as genus FROM horses
UNION SELECT *, '����' AS genus FROM donkeys
UNION SELECT *, '������' AS genus FROM dogs
UNION SELECT *, '�����' AS genus FROM cats
UNION SELECT *, '������' AS genus FROM hamsters;

CREATE TABLE yang_animal AS
SELECT Name, Birthday, Commands, genus, TIMESTAMPDIFF(MONTH, Birthday, CURDATE()) AS Age_in_month
FROM animals WHERE Birthday BETWEEN ADDDATE(curdate(), INTERVAL -3 YEAR) AND ADDDATE(CURDATE(), INTERVAL -1 YEAR);

SELECT * FROM yang_animal;

12. ���������� ��� ������� � ����, ��� ���� �������� ����, ����������� �� ������� �������������� � ������ ��������.

SELECT h.Name, h.Birthday, h.Commands, pa.Genus_name, ya.Age_in_month
FROM horses h
LEFT JOIN yang_animal ya ON ya.Name = h.Name
LEFT JOIN packed_animals pa ON pa.Id = h.Genus_id
UNION
SELECT d.Name, d.Birthday, d.Commands, pa.Genus_name, ya.Age_in_month
FROM donkeys d
LEFT JOIN yang_animal ya ON ya.Name = d.Name
LEFT JOIN packed_animals pa ON pa.Id = d.Genus_id
UNION
SELECT c.Name, c.Birthday, c.Commands, ha.Genus_name, ya.Age_in_month
FROM cats c
LEFT JOIN yang_animal ya ON ya.Name = c.Name
LEFT JOIN home_animals ha ON ha.Id = c.Genus_id
UNION
SELECT d.Name, d.Birthday, d.Commands, ha.Genus_name, ya.Age_in_month
FROM dogs d
LEFT JOIN yang_animal ya ON ya.Name = d.Name
LEFT JOIN home_animals ha ON ha.Id = d.Genus_id
UNION
SELECT hm.Name, hm.Birthday, hm.Commands, ha.Genus_name, ya.Age_in_month
FROM hamsters hm
LEFT JOIN yang_animal ya ON ya.Name = hm.Name
LEFT JOIN home_animals ha ON ha.Id = hm.Genus_id;

13. ������� ����� � ������������� ������� � ������������� �� ���������.
14. �������� ���������, ����������� ������ ������� �������� ��������. � ��������� ������ ���� ���������� ��������� ����������:
    14.1 ������� ����� ��������
    14.2 ���������� �������� � ���������� �����
    14.3 ������� ������ ������, ������� ��������� ��������
    14.4 ������� �������� ����� ��������
    14.5 ����������� ��������� �� ����

15. ������?�� ����� �������, � �������� ���� ����� add(), �������������? �������� ����������? int ����������? �� 1 ��� ������� 
�������� ����� �������� �������� ���, ����� � �������� ������ ���� ����� ���� �������� � ����� try-with-resources. 
����� ������� ����������, ���� ������ � �������� ���� ������� ���� �� � ��������� try �/��� ������ ������� ������. 
�������� ������� � ������� try, ���� ��� ��������� ��������� ��������� ��� ����.

<img src="images/7.jpg"/>

