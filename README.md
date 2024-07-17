# Praticando SQL Curso Proz Banco de dados Simples...

Lembre-se, cada desafio é uma chance de crescer. Não se desanime com os erros; eles são degraus no caminho do aprendizado. E acima de tudo, divirta-se! 
O aprendizado mais eficaz acontece quando nos engajamos e nos interessamos pelo que estamos fazendo.

 Vamos imaginar uma tabela de alunos com as seguintes colunas: ID, Nome, Ano, Nota e uma tabela de professores com as colunas ID, PNome, UNome.

#### crie uma base de dados;
```sql
CREATE DATABASE Escola;

```

#### crie tabelas nessa base de dados (Estudantes);
```sql
CREATE TABLE Estudantes (
    EstudanteID INT PRIMARY KEY AUTO_INCREMENT,
    Nome VARCHAR(100),
    DataNascimento DATE
);

```
#### Tabela cursos (Exemplo)
```sql
CREATE TABLE Cursos (
    CursoID INT PRIMARY KEY AUTO_INCREMENT,
    NomeCurso VARCHAR(100),
    Descricao TEXT
);
```

#### Tabela Matriculas (Exemplo)
```sql
CREATE TABLE Matriculas (
    MatriculaID INT PRIMARY KEY AUTO_INCREMENT,
    EstudanteID INT,
    CursoID INT,
    DataMatricula DATE,
    FOREIGN KEY (EstudanteID) REFERENCES Estudantes(EstudanteID),
    FOREIGN KEY (CursoID) REFERENCES Cursos(CursoID)
);
```

#### Insira dados em cada tabela (Estudantes)
```sql
INSERT INTO Estudantes (Nome, DataNascimento) VALUES
('João Silva', '2000-01-15'),
('Maria Souza', '2001-05-23'),
('Pedro Oliveira', '1999-11-30');
```

#### Insira dados em cada tabela (Cursos)
```sql
INSERT INTO Cursos (NomeCurso, Descricao) VALUES
('Matemática', 'Curso de Matemática Básica e Avançada'),
('História', 'Curso de História Geral e do Brasil'),
('Ciência da Computação', 'Curso de Fundamentos e Avançado em Computação');
```

#### Insira dados em cada tabela (Matriculas)
```sql
INSERT INTO Matriculas (EstudanteID, CursoID, DataMatricula) VALUES
(1, 1, '2024-01-01'),
(1, 3, '2024-01-15'),
(2, 2, '2024-01-20'),
(3, 1, '2024-01-25'),
(3, 2, '2024-02-10');
```

#### Utilizando os comandos Joins para realizar consultas nas tabelas (estudantes matriculados em cada curso)
```sql
SELECT Estudantes.Nome AS NomeEstudante, Cursos.NomeCurso
FROM Matriculas
JOIN Estudantes ON Matriculas.EstudanteID = Estudantes.EstudanteID
JOIN Cursos ON Matriculas.CursoID = Cursos.CursoID;
```

#### Utilizando os comandos Joins para realizar consultas nas tabelas (cursos e o número de estudantes matriculados em cada um)
```sql
SELECT Cursos.NomeCurso, COUNT(Matriculas.EstudanteID) AS NumeroEstudantes
FROM Cursos
JOIN Matriculas ON Cursos.CursoID = Matriculas.CursoID
GROUP BY Cursos.NomeCurso;
```

#### Utilizando os comandos Joins para realizar consultas nas tabelas (detalhes das matrículas)
```sql
SELECT Estudantes.Nome AS NomeEstudante, Cursos.NomeCurso, Matriculas.DataMatricula
FROM Matriculas
JOIN Estudantes ON Matriculas.EstudanteID = Estudantes.EstudanteID
JOIN Cursos ON Matriculas.CursoID = Cursos.CursoID;
```
