# Aula do dia 13/05/2025

Nessa aula, entendi melhor o que é um join e como ele funciona. Descobri que existem varios tipos de join:

1. Inner join: Esse join junta as tabelas relacionais, mas apenas com as seções em comum entre elas, em uma nova tabela.

2. Left e right join: Esses joins junta as informações de duas tabelas (uma à esquerda e uma à direita) em uma nova tabela. Diferentemente do inner join, esse join junta todos os atributos das tabelas. Se houver uma coluna em uma que não está na outra, esses joins criam a coluna, mas colocam atributos "null". A nova tabela retornará todos os atributos de uma das tabelas (left - esquerda e right - direita), juntamente com as colunas novas em comum às duas tabelas unidas.

3. Full join: Nesse join, as informações das tabelas são juntas completamente. É uma junção de left e right join.

Além disso, vi na prática, com a atualização do mini site CRUD, como usar o MVC e as consultas:

1. O model e o controller da tabela "aluno", que já tinha sido criada, foi atualizado para, também, colocar as informações de "curso". Essa tabela curso, que foi criada, se relaciona com aluno pois há uma chave primária dela (curso.id) que se transformou em uma chave estrangeira para a tabela aluno (aluno.curso_id). Isso faz com que elas se relacionem.

2. Essas informações foram adicionadas no init.sql, que fica dentro de scripts, adicionando a coluna curso_id na tabela alunos e transformando em uma chave estrangeira.

3. Um LEFT JOIN ocorreu no model de aluno: a consulta para achar todos os alunos de certo curso (findAllComCurso) fez um left join para juntar a tabela "aluno" (à esquerda) com a tabela "cursos" (à direita), unindo a informação dos id's dos alunos na coluna curso_id na tabela. Além disso, foi mostrada uma relação crescente das informações dos alunos.

# Aula do dia 15/05/2025

1. **Models**: no projeto, os models são responsáveis por estruturar a base das operações. Analisando o model de cursos (curso.js dentro de /models), pode-se observar a estrutura CRUD: o async create, async update, async delete e async findAll() representam a estrura do padrão MVC de ler algo, atualizar, deletar e criar. Eles são a base da implementação de métodos.

2. **Controller**: no projeto, o controller é a parte que processa as requisições do servidor. O controller é como se fosse um meio de comunicação entre os Models e os Views, ou seja, é um intermediário que processa as informações dadas pelos Models a partir de endpoints específicos, para que elas sejam processadas e apareçam visíveis no View.

3. **Endpoints**: endpoints são como "suburls", ou seja, são rotas que o servidor executa para responder a partes http do código. em localhost.3000/alunos, por exemplo, o /alunos é o endpoint em que as informações de alunos são criadas, atualizadas, lidas e deletadas, com base nos dados existentes em Models e nas requisições feitas por Controllers.

O modelo MVC, junto com os endpoints e com o node.js, ajudam o sistema a processar o CRUD, e, assim, conseguir adaptar as informações do sistema pelo próprio site.

# Aula do dia 20/05/2025

1. Explique com suas palavras o papel de cada camada da arquitetura MVC usada neste projeto. *Como o Model, o Controller e a View interagem entre si?*

O model funciona como o banco de informações. Nele, são definidas as informações necessárias para a estruturação do site. Nele, são criadas funções que definem o CRUD: create, update, read e delete.

O controller é um intermediário da aplicação. Ele se comunica com o model e com o view por meio das routes, pegando as informações do model e trazendo para o view. 

O view mostra como o site está ficando visualmente. Por meio do index.ejs, um código html é produzido para mostrar o site na prática.

2. Como ocorre o envio e o recebimento de dados no formato JSON neste projeto? *Cite uma rota que responde em JSON e explique seu funcionamento.*

``` javascript
router.get('/', controller.index);
router.post('/', controller.store);
```

Ao fazer uma requisição GET, o controller chama o método findAll() do model para buscar todos os alunos no banco de dados, por exemplo. No POST, o controller usa o método create() do model para criar um novo aluno.

3. Qual a importância de usar HTML básico com formulários e tabelas para organizar e manipular dados no navegador? *Por que esse tipo de estrutura ainda é útil em projetos back-end com Node.js?*

Para visualizar melhor o que está acontecendo com as informações do banco de dados. Ao integrar um front end via API Requests, torna-se muito mais fácil realizar as operações CRUD pelo html do que ter que criar várias solicitações API por meio de um aplicativo externo como o Postman, por exemplo.

# 📚 Revisão Prova de Desenvolvimento Web e Banco de Dados - respostas

---

## 🧪 Questões

### QUESTÃO 1 – Modelagem de Dados Relacional
Considere um sistema universitário que registra cursos, alunos e suas respectivas matrículas. O sistema deve garantir que cada aluno possa se matricular em múltiplas disciplinas, mas uma mesma disciplina também pode ter vários alunos. Além disso, cada disciplina é oferecida por um único professor. O banco de dados relacional deve ser projetado para manter a integridade referencial e evitar redundância de dados.

I. O relacionamento entre alunos e disciplinas deve ser representado por uma tabela associativa contendo chaves estrangeiras de ambas as tabelas.  (ok)
II. A entidade professor deve possuir chave primária que é referenciada na tabela de disciplinas.  (ok)
III. Uma disciplina pode ser associada a múltiplos professores, o que justifica a criação de uma tabela adicional. (não, pois cada disciplina é oferecida por um único professor) 
IV. O uso de constraints como FOREIGN KEY garante que registros referenciados existam nas tabelas originais.  (ok)

**É correto o que se afirma em:**  
**A) I, II e IV, apenas.**  
B) I e III, apenas.  (x)
C) II, III e IV, apenas.  (x)
D) I, II e III, apenas.  (x)
E) Todas as afirmativas estão corretas. (x)

### QUESTÃO 2 – Arquitetura Cliente-Servidor com MVC
No desenvolvimento de uma aplicação web baseada em Node.js e Express, o time de desenvolvimento decidiu adotar o padrão arquitetural MVC. A aplicação deve permitir que o cliente interaja via navegador, enviando requisições HTTP para o servidor, que responderá com páginas dinâmicas.

I. O Controller processa requisições e repassa dados para o Model, retornando a resposta ao cliente.  (ok)
II. O Model interage com a View diretamente para exibir os dados processados.  (não - tem o intermédio das rotas e do controller)
III. A View representa a saída visual da aplicação e é gerada a partir das informações processadas pelo Controller.   (ok)
IV. Separar lógica de negócio e interface facilita a manutenção e reuso de código.  (ok)

**É correto o que se afirma em:**  
**A) I, III e IV, apenas.**
B) I e II, apenas.  (X)
C) III e IV, apenas.  
D) II, III e IV, apenas.  (X)
E) Todas as afirmativas estão corretas. (x)

### QUESTÃO 3 – Banco de Dados Não Relacionais
Uma startup desenvolvendo uma aplicação de redes sociais decidiu utilizar um banco de dados do tipo NoSQL para armazenar informações de perfis de usuários, postagens e relações de amizade. A escolha se deu pela flexibilidade de estrutura e pela necessidade de escalar horizontalmente a aplicação com facilidade.

I. Bancos de dados orientados a documentos são ideais para armazenar dados com estrutura variável, como perfis de usuário.  (?, mas acho que não)
II. Bancos do tipo grafo são adequados para representar relações como "amizade" entre usuários.  (ok)
III. A consistência eventual é uma característica típica dos bancos NoSQL, diferente dos bancos relacionais.  (ok)
IV. Em um banco do tipo chave-valor, cada registro precisa estar normalizado em três formas normais.  (?)

**É correto o que se afirma em:**  
A) I, II e III, apenas.  
B) I e IV, apenas.  (x)
**C) II e III, apenas.**  
D) I, III e IV, apenas.  (x)
E) Todas as afirmativas estão corretas.

### QUESTÃO 4 – Requisições Assíncronas com Controllers
Em uma aplicação que utiliza o framework Express.js, o aluno foi encarregado de implementar a lógica do backend. O sistema recebe requisições assíncronas do frontend utilizando a Fetch API e responde com dados obtidos de um banco PostgreSQL. A lógica de cada rota é implementada em controladores assíncronos.

I. O uso de async/await facilita a leitura de código assíncrono em JavaScript.  (ok)
II. Requisições POST e DELETE podem ser tratadas no mesmo controller desde que a rota esteja definida corretamente.  (ok)
III. Controllers devem concentrar a lógica de negócio e persistência para simplificar o projeto.  (não - a lógica de negócios é concentrada nos models)
IV. As funções assíncronas exigem tratamento de erros com try/catch para evitar travamentos na aplicação.  (ok)

**É correto o que se afirma em:**  
**A) I, II e IV, apenas.**  
B) II e III, apenas.  (x)
C) I, III e IV, apenas.  (x)
D) I, II e III, apenas.  (x)
E) Todas as afirmativas estão corretas. (X)

### QUESTÃO 5 – Anatomia de uma Aplicação em Camadas
Um grupo de desenvolvedores está projetando uma aplicação web corporativa e decidiu utilizar uma arquitetura em camadas para garantir a manutenibilidade e a escalabilidade do sistema. O sistema será dividido entre a camada de apresentação (frontend), a camada de negócios (backend) e a camada de dados (banco de dados). Cada camada terá responsabilidades bem definidas.

I. A camada de apresentação é responsável por interagir com o usuário, exibindo informações e coletando entradas.  (ok)
II. A camada de negócios aplica as regras funcionais e validações, separando-se da interface e da lógica de persistência.  (ok)
III. A camada de dados deve encapsular o acesso ao banco, impedindo o acesso direto por outras camadas.  
IV. A ausência de camadas intermediárias favorece o acoplamento e reduz a reutilização de componentes.  (ok)

**É correto o que se afirma em:**  
A) I, II e III, apenas.  (x)
B) II, III e IV, apenas.  (x)
C) I, III e IV, apenas.  (X)
D) I, II e IV, apenas.  
**E) Todas as afirmativas estão corretas.**

### QUESTÃO 6 – Paradigmas de Programação
Durante uma aula sobre linguagens de programação, foram apresentados diversos paradigmas, como o imperativo, o funcional e o orientado a objetos. Cada paradigma adota uma forma distinta de modelar o comportamento do sistema e manipular os dados.

I. A programação funcional preza pela imutabilidade de dados e evita efeitos colaterais.  (ok)
II. O paradigma orientado a objetos favorece o encapsulamento e reutilização por meio de herança.  (ok)
III. A programação imperativa descreve a lógica do programa por meio de comandos sequenciais.  (ok)
IV. No paradigma funcional, o uso de loops tradicionais como for e while é incentivado em detrimento de funções como map e reduce. (Ok)

**É correto o que se afirma em:**  
A) I, II e III, apenas.  
B) II e IV, apenas.  (x)
C) I, III e IV, apenas.  (x)
D) I, II e IV, apenas.  (x)
**E) Todas as afirmativas estão corretas.**

### QUESTÃO 7 – Setup de Ambiente com Node.js, VSCode e Supabase
Ao iniciar o desenvolvimento de um projeto fullstack, uma equipe de estudantes realizou a instalação do Node.js, configurou o editor VSCode com extensões úteis, e utilizou o Supabase como backend. O objetivo era integrar de forma eficiente o frontend com um banco relacional escalável.

I. O VSCode oferece terminal integrado, sugestões automáticas de código e controle de versão integrado.  (ok)
II. O comando npm install express é utilizado para adicionar o framework Express a um projeto Node.js.  (ok)
III. O Supabase fornece serviços de autenticação e banco de dados prontos para uso com suporte a SQL.  (ok)
IV. Após inicializar um projeto Node com npm init -y, não é necessário criar manualmente o package.json.  (ok)

**É correto o que se afirma em:**  
A) I, II e IV, apenas.  
B) I, II e III, apenas.  
C) II, III e IV, apenas.  
D) I, III e IV, apenas.  
**E) Todas as afirmativas estão corretas.**

### QUESTÃO 8 – Chave Primária e Estrangeira
Em uma base de dados relacional, o uso adequado de chaves primárias e estrangeiras é essencial para manter a integridade dos dados e garantir que os relacionamentos entre as tabelas sejam consistentes. Um analista júnior precisa revisar o modelo lógico antes da implementação.

I. Uma chave primária identifica unicamente cada linha da tabela e não aceita valores nulos.  (ok)
II. Uma chave estrangeira estabelece um vínculo entre duas tabelas e pode ter valores nulos em alguns casos.  (ok)
III. O uso de chaves estrangeiras ajuda a evitar inserções de dados inválidos em colunas que dependem de outras tabelas.  (ok)
IV. Uma tabela pode conter múltiplas chaves primárias, desde que em colunas diferentes.  (?- mas acho que sim)

**É correto o que se afirma em:**  
A) I, II e III, apenas.  
B) I e IV, apenas.  (x)
C) II e III, apenas.  (x)
D) I, III e IV, apenas.  (x)
**E) Todas as afirmativas estão corretas.**

### QUESTÃO 9 – Introdução ao Padrão MVC
O padrão de arquitetura MVC visa organizar o código de uma aplicação em três camadas: Model, View e Controller. Essa separação permite dividir tarefas de forma clara, além de tornar o desenvolvimento colaborativo mais eficiente.

I. O Model representa os dados e suas regras de validação e persistência.  (ok)
II. A View trata da apresentação dos dados ao usuário, podendo ser renderizada dinamicamente com EJS ou Handlebars.  (ok)
III. O Controller centraliza a lógica de negócio e se comunica tanto com o Model quanto com a View.  (ok)
IV. É uma boa prática permitir que a View invoque diretamente métodos do banco de dados para maior eficiência.  (não, deve ter o controller para intermediar)

**É correto o que se afirma em:**  
**A) I, II e III, apenas.** 
B) II e IV, apenas.  (X)
C) I, III e IV, apenas.  (x)
D) I, II e IV, apenas.  (x)
E) Todas as afirmativas estão corretas. (X)

### QUESTÃO 10 – Estrutura e Semântica do HTML
A criação de páginas web bem estruturadas e acessíveis depende do uso adequado dos elementos HTML, especialmente aqueles introduzidos no HTML5, que trouxeram mais significado semântico ao conteúdo exibido.

I. O uso de `<article>`, `<section>` e `<nav>` melhora a semântica e a acessibilidade das páginas.  (ok)
II. A tag `<div>` é apropriada para estruturar conteúdo quando não há uma alternativa semântica adequada.  (Ok)
III. A marcação correta de cabeçalhos hierárquicos ajuda na navegação de leitores de tela.  (ok)
IV. Elementos semânticos são ignorados por mecanismos de busca e servem apenas para estilização visual.  (não)

**É correto o que se afirma em:**  
**A) I, II e III, apenas.** 
B) II e IV, apenas.  (x)
C) I, III e IV, apenas.  
D) I, II e IV, apenas.  (X)
E) Todas as afirmativas estão corretas.

---
