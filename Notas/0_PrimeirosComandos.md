### Comando pra ver todos os Databases

```bash
show dbs
```

### Criando um banco

```bash
use primeiroBanco
```

Ao criar um banco novo, ele não vai ser exibido na lista de bancos, pois ele não tem dados inseridos.

### Inserindo dados

```bash
db.primeiracollection.insertOne({ nome: "Adriano", idade:37 })
```

### Encontrando o dado

```bash
db.primeiracollection.findOne({})
```

#### Exercício

- Insira um dado na nossa collection

```bash
db.primeiracollection.insertOne({ nome: "Silva", idade:73, profissao: "Developer" })
```

- Faça a seleção de dados pra ver o dado inseriro(find)

```bash
db.primeiracollection.find()
```

## MongoDB e Drivers

- Quando utilizamos MongoDB e algumas linguagens, precisamos utilizar o driver da mesma
- Todos estão disponíceis na documentação oficial
- Os comandos do shell são os mesmos que o driver de Javascript(Node), o que facilita muito para as aplicações MERN, MEAN, MEVN
  PS: focaremos em shell
-
