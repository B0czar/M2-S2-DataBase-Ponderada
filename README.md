# M2-S2-DataBase-Ponderada

Criar as tabelas
```
CREATE TABLE alunos (
  id SERIAL PRIMARY KEY,
  nome TEXT NOT NULL,
  sobrenome TEXT NOT NULL,
  data_nascimento DATE NOT NULL
);


CREATE TABLE cursos (
  id SERIAL PRIMARY KEY,
  nome TEXT NOT NULL,
  descricao TEXT
);

CREATE TABLE matriculas (
  id SERIAL PRIMARY KEY,
  aluno_id INTEGER REFERENCES alunos(id),
  curso_id INTEGER REFERENCES cursos(id),
  data_matricula DATE DEFAULT CURRENT_DATE
);
```
Inserir os dados
```
INSERT INTO alunos (nome, sobrenome, data_nascimento) 
VALUES ('Paula', 'Tejano', '2001-02-15'),
('Cuca', 'Beludo', '2000-11-23'),
('Tomás', 'Turbando', '1999-07-12'),
('Mateus', 'Silva', '2002-03-05'),
('Ana', 'Conda', '2001-05-20'),
('Gina', 'Cola', '1998-09-09'),
('Ivo', 'Capeta', '2000-01-01'),
('Bruno', 'Alves', '1997-12-25'),
('César', 'Ferreira', '1999-10-10'),
('Tina', 'Souza', '2003-06-30');

INSERT INTO cursos (nome, descricao) 
VALUES ('Desempregado', 'Especialização em não fazer nada.'),
('Engenharia de Pesca', 'Formação para mestres das redes e anzóis.'),
('Acendedor de Lampião', 'Curso técnico de iluminação à moda antiga.');

INSERT INTO matriculas (aluno_id, curso_id) 
VALUES (1, 1),
(2, 2),
(3, 1),
(4, 3),
(5, 2),
(6, 2),
(7, 3),
(8, 1),
(9, 2),
(10, 3);
```
Search
```
SELECT a.nome AS aluno, a.sobrenome, c.nome AS curso, m.data_matricula
FROM matriculas m
JOIN alunos a ON m.aluno_id = a.id
JOIN cursos c ON m.curso_id = c.id;
```
