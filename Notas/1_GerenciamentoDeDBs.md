## Gerenciamento de DBs

#### Verificar todos os bancos

- Podemos verificar os bancos do sistema com: show `dbs`
- Este comando mostra todos os DBs criados até o momento
- Note que há alguns bancos que o próprio Mongo já cria

#### Criando um banco de dados

- Para criar um banco utilizamos a instrução `use nome_do_banco`
- Isso fará com que o banco seja inicializado porém ele só será registrado de fato quando houver algum dado nele
- Podemos checar o banco atual com o comando: `db`
- O comando `use` também serve para mudar de banco

```bash
use nome do banco ## cria um banco ou muda para o banco
```

```bash
db ## serve para analisarmos em qual banco estamos
```

### Exercicio 2

- Crie um banco de dados

```bash
use meubanco

db

db.meubanco.insertOne({ dado1: "Dado", dado2: "Dado", dado3: "Outro dado"})
```

- Utilize o comando de verificação de banco de dados para exibir todos eles

```bash
show dbs
```

### Criando collections

- Não precisamos explicitamente criar uma collection, basta inserir um dado em alguma
- Com o comando: db.NomeDaCollection.insertOne({dados})
- A Collection será criada automaticamente, e também o banco de dados persistirá no sistema.
- Note que a instrução vai referir sempre ao banco atualizado

```bash
db.meubanco.insertOne({ dado1: "Dado", dado2: "Dado", dado3: "Outro dado"})
```

### Encontrando dados

- Para buscar dados utilizamos o comando `find`
- Este comando recebe um filtro, para selecionarmos dados específicos
- exemplo: `db.minhacollection.find({nome: "João})`
- Neste caso, buscamos por um document com uma chave nome e um valor de João

```bash
use pessoas

db.pessoas.insertOne(nome: "Adriano", idade: 54, profissao: "Carpinteiro")

dp.pessoas.find({ nome: "Adrinao"})
```

### A função pretty

- A função pretty pode ser adicionada a alguns somandos.
- O resultado é um retorno de dados melhor formatado.
- Desta forma fica mais legível e conseguimos entender melhor o que retornar,
- Ela é muito utilizada com o find

```bash
dp.pessoas.find({}).pretty()
```

### Criando uma collection implícita

- Há a possibilidade de criar a collection com um comando também
- Exemplo> `db.createCollecion("nome", {opções})`
- Podemos definir alguns parâmetros de configuração como: número máximo de registros, tamanho máximo da collection e etc.

```bash
db.createCollection("minhacolecao", { capped: true, size: 1000, max: 3 })
```

### Exibindo todas as collections

- Para exibir todas as collections utilizamos: show collections
- Este comando de verificação ajuda a entender melhor o banco de dados
- Lembrando que para uma collection ser criada de fato, ela precisa ter algum dado inserido

```bash
show collections
```

#### Exercício 3

- Crie uma collection com dados de nome de pessoas e salários

```bash
db.salarios.insertOne({nome: "Adriano", salario: 3000})
db.salarios.insertOne({nome: "André", salario: 3800})
db.salarios.insertOne({nome: "Ana", salario: 4000})
```

- Utilize o comando find para verificar os registros dela

```bash
db.salarios.find()
```

- Verifique todas as collections do banco

```bash
show collections
```

### Chave \_id

- Todo registro inserido no banco vem com uma chave chamada \_id
- Esta chave tem como objetivo criar um identificador único para todo registro
- Ele consegue ser único pois é baseado no tempo em que é criado, mesmo que os dados sejam inseridos simultaneamente, ids serão distintos
- Outra funcionalidade interessante é que ele possui um índice, agilizando consultas por esta chave

### Removendo collections

- Podemos remover collections quando elas não forem mais necessárias ou se errarmos o nome, por exemplo
- o comando db.nomeDaColeection.drop()
- Após a execução todos os dados serão removidos também, então muito cuidado

```bash
db.nomeDaColeection.drop()
```

### Removendo Banco de Dados

- Podemos remover os bancos também
- O comando é: db.dropDatabase()
- Após a execução do comando, todos os dados e collections serão excluídos do sistema

```bash
db.dropDatabase()
```
