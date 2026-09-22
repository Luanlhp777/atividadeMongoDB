# Atividade MongoDB — Playlist de Músicas

Projeto desenvolvido em aula para praticar conceitos de **Banco de Dados NoSQL com MongoDB**, utilizando uma aplicação de playlist de músicas como cenário.

A atividade trabalha com criação de banco, coleções, documentos JSON, relacionamentos por referência e estruturas aninhadas.

---

## Objetivo da atividade

Praticar conceitos fundamentais do MongoDB, incluindo:

- criação de banco de dados;
- criação de coleções;
- inserção de documentos;
- utilização de `ObjectId`;
- armazenamento de arrays;
- documentos aninhados;
- relacionamento entre coleções;
- organização de dados em formato JSON;
- modelagem NoSQL.

---

## Tecnologias utilizadas

- MongoDB
- MongoDB Compass
- JSON
- NoSQL
- Git
- GitHub

---

## Estrutura do repositório

```text
atividadeMongoDB/
├── Atividade_210926.pdf
├── anotacoes.txt
├── minha_playlist_musicas.musicas.json
├── minha_playlist_musicas.playlists.json
├── minha_playlist_musicas.sessoes_usuarios.json
└── minha_playlist_musicas.usuarios.json
```

---

## Banco de dados

O banco utilizado na atividade foi:

```text
minha_playlist_musicas
```

A estrutura foi dividida em quatro coleções principais:

```text
musicas
usuarios
playlists
sessoes_usuarios
```

---

## Coleção `musicas`

Responsável por armazenar as informações das músicas cadastradas.

Exemplo de documento:

```json
{
  "titulo": "Imagine",
  "ano": 1971,
  "artista": "John Lennon",
  "album": "Imagine",
  "generos": [
    "Rock",
    "Pop"
  ],
  "compositores": [
    "John Lennon"
  ],
  "duracao_segundos": 183,
  "avaliacao_media": 4.8
}
```

Também foi cadastrada a música:

```text
Billie Jean — Michael Jackson
```

A coleção utiliza arrays para armazenar informações como:

```text
generos
compositores
```

---

## Coleção `usuarios`

Armazena os dados dos usuários da aplicação e suas avaliações de músicas.

Exemplo:

```json
{
  "nome": "Luan Araujo",
  "email": "luan@email.com",
  "avaliacoes": [
    {
      "musica_id": "ObjectId",
      "nota": 5,
      "comentario": "Uma música clássica e marcante."
    }
  ]
}
```

As avaliações ficam armazenadas como documentos dentro do array:

```text
avaliacoes
```

Cada avaliação possui:

```text
musica_id
nota
comentario
```

O campo `musica_id` referencia um documento da coleção `musicas`.

---

## Coleção `playlists`

Responsável por armazenar as playlists criadas pelos usuários.

Exemplo:

```json
{
  "usuario_id": "ObjectId",
  "nome": "Minhas músicas favoritas",
  "musicas": [
    {
      "musica_id": "ObjectId",
      "titulo": "Imagine",
      "ano": 1971
    }
  ]
}
```

A playlist possui referência ao usuário através de:

```text
usuario_id
```

E cada música é relacionada através de:

```text
musica_id
```

---

## Coleção `sessoes_usuarios`

Armazena informações relacionadas às sessões de acesso dos usuários.

Exemplo:

```json
{
  "usuario_id": "ObjectId",
  "token_autenticacao": "xyz789abc123",
  "dispositivo": "Celular Android",
  "criado_em": "Date",
  "expira_em": "Date"
}
```

Essa coleção trabalha com:

- referência ao usuário;
- token de autenticação;
- dispositivo utilizado;
- data de criação;
- data de expiração da sessão.

---

## Relacionamento entre as coleções

Apesar de o MongoDB ser um banco NoSQL orientado a documentos, nesta atividade foram utilizadas referências entre documentos.

Fluxo simplificado:

```text
usuarios
   │
   ├── avaliações
   │      ↓
   │   musicas
   │
   ├── playlists
   │      ↓
   │   musicas
   │
   └── sessoes_usuarios
```

Os relacionamentos são realizados utilizando valores do tipo:

```text
ObjectId
```

---

## Estruturas NoSQL utilizadas

Durante a atividade foram utilizados dois conceitos importantes.

### Documentos aninhados

Exemplo:

```text
usuario
└── avaliacoes[]
```

As avaliações ficam armazenadas dentro do próprio documento do usuário.

### Referências entre documentos

Exemplo:

```text
playlist.usuario_id
```

referencia:

```text
usuarios._id
```

E:

```text
playlist.musicas[].musica_id
```

referencia:

```text
musicas._id
```

---

## Conceitos praticados

- Banco de Dados NoSQL
- MongoDB
- MongoDB Compass
- Collections
- Documents
- ObjectId
- Arrays
- Embedded Documents
- Referências entre documentos
- JSON
- Modelagem NoSQL
- Relacionamento entre coleções

---

## Arquivos JSON

Os arquivos `.json` presentes no repositório representam as coleções criadas durante a atividade e podem ser utilizados para estudo, backup ou importação no MongoDB Compass.

```text
minha_playlist_musicas.musicas.json
minha_playlist_musicas.usuarios.json
minha_playlist_musicas.playlists.json
minha_playlist_musicas.sessoes_usuarios.json
```

---

## Status

✅ Atividade concluída.

Foram criadas e testadas as coleções necessárias para representar uma aplicação de playlist utilizando MongoDB.

---

## Autor

**Luan Araujo**

Projeto acadêmico desenvolvido para prática de **MongoDB, Banco de Dados NoSQL e modelagem orientada a documentos**.
