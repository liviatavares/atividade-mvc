## Aula do dia 13/05/2025

Nessa aula, entendi melhor o que é um join e como ele funciona. Descobri que existem varios tipos de join:

1. Inner join: Esse join junta as tabelas relacionais, mas apenas com as seções em comum entre elas, em uma nova tabela.

2. Left e right join: Esses joins junta as informações de duas tabelas (uma à esquerda e uma à direita) em uma nova tabela. Diferentemente do inner join, esse join junta todos os atributos das tabelas. Se houver uma coluna em uma que não está na outra, esses joins criam a coluna, mas colocam atributos "null". A nova tabela retornará todos os atributos de uma das tabelas (left - esquerda e right - direita), juntamente com as colunas novas em comum às duas tabelas unidas.

3. Full join: Nesse join, as informações das tabelas são juntas completamente. É uma junção de left e right join.

Além disso, vi na prática, com a atualização do mini site CRUD, como usar o MVC e as consultas:

1. O model e o controller da tabela "aluno", que já tinha sido criada, foi atualizado para, também, colocar as informações de "curso". Essa tabela curso, que foi criada, se relaciona com aluno pois há uma chave primária dela (curso.id) que se transformou em uma chave estrangeira para a tabela aluno (aluno.curso_id). Isso faz com que elas se relacionem.

2. Essas informações foram adicionadas no init.sql, que fica dentro de scripts, adicionando a coluna curso_id na tabela alunos e transformando em uma chave estrangeira.

3. Um LEFT JOIN ocorreu no model de aluno: a consulta para achar todos os alunos de certo curso (findAllComCurso) fez um left join para juntar a tabela "aluno" (à esquerda) com a tabela "cursos" (à direita), unindo a informação dos id's dos alunos na coluna curso_id na tabela. Além disso, foi mostrada uma relação crescente das informações dos alunos.

