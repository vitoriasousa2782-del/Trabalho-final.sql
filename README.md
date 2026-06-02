CREATE DATABASE IF NOT EXISTS I2_Vitoria;
USE I2_Vitoria;
CREATE TABLE tb_pessoas (
    id_pessoas INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(45) NOT NULL,
    cpf VARCHAR(14) NOT NULL,
    data_nascimento DATE NOT NULL
);

INSERT INTO tb_pessoas (nome, cpf, data_nascimento) VALUES
('Leonardo', '098648978-42', '1999-12-02'),
('Bianca', '026579879-11', '1998-10-30'),
('Tamires', '578648798-12', '2004-07-02');

CREATE TABLE tb_alunos (
    id_alunos INT PRIMARY KEY AUTO_INCREMENT,
    matricula INT NOT NULL,
    id_pessoas INT,
    FOREIGN KEY (id_pessoas) REFERENCES tb_pessoas(id_pessoas)
);

INSERT INTO tb_alunos (matricula, id_pessoas) VALUES
(244, 1),
(344, 2);

CREATE TABLE tb_professores (
    id_professores INT PRIMARY KEY AUTO_INCREMENT,
    matricula INT NOT NULL,
    id_pessoas INT,
    FOREIGN KEY (id_pessoas) REFERENCES tb_pessoas(id_pessoas)
);

INSERT INTO tb_professores (matricula, id_pessoas) VALUES
(144, 3);

CREATE TABLE tb_turnos (
    id_turnos INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(45) NOT NULL,
    horario_inicio TIME NOT NULL,
    horario_fim TIME NOT NULL
);

INSERT INTO tb_turnos (id_turnos, nome, horario_inicio, horario_fim) VALUES
(100, 'Matutino', '07:15:00', '12:00:00'),
(200, 'Vespertino', '13:30:00', '17:30:00'),
(300, 'Noturno', '19:00:00', '22:55:00');

CREATE TABLE tb_cursos (
    id_cursos INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(45) NOT NULL,
    sigla VARCHAR(45) NOT NULL,
    id_turnos INT,
    FOREIGN KEY (id_turnos) REFERENCES tb_turnos(id_turnos)
);

INSERT INTO tb_cursos (id_cursos, nome, sigla, id_turnos) VALUES
(52, 'Técnico em Informática', 'TI', 200),
(54, 'Técnico em Administração', 'TA', 300);
