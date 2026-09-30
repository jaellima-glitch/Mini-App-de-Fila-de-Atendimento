# 🏥 Sistema de Fila de Atendimento

Este projeto consiste em uma aplicação web desenvolvida para organizar e controlar uma fila de atendimento.

Através do sistema, é possível cadastrar clientes, acompanhar quem está aguardando, chamar o próximo da fila, finalizar um atendimento e cancelar um atendimento quando necessário.

O projeto foi desenvolvido utilizando **Python, Flask e SQLite**, com uma interface simples feita em **HTML e CSS**.

---

## 🎯 Objetivo

O principal objetivo da aplicação é facilitar o controle de uma fila de atendimento, mantendo os clientes organizados de acordo com a ordem em que foram cadastrados.

O sistema utiliza o conceito de **FIFO (First In, First Out)**, no qual o primeiro cliente a entrar na fila deve ser o primeiro a ser chamado.

---

## ⚙️ Funcionalidades

O sistema possui as seguintes funções:

* 👤 Cadastrar novos clientes;
* 📋 Visualizar os clientes cadastrados;
* 🔢 Manter a ordem de chegada;
* 📢 Chamar o próximo cliente;
* 🔄 Alterar o status do atendimento;
* ✅ Finalizar um atendimento;
* ❌ Cancelar um atendimento;
* 💾 Salvar os dados no banco SQLite.

---

## 🔄 Como funciona

O processo de atendimento acontece da seguinte maneira:

```text
Cliente é cadastrado
        ↓
Entra na fila
        ↓
Status: Aguardando
        ↓
Próximo cliente é chamado
        ↓
Status: Em atendimento
        ↓
Atendimento finalizado
        ↓
Status: Concluído
```

Caso o atendimento precise ser interrompido, o cliente poderá receber o status **Cancelado**.

---

## 🧠 Sistema FIFO

A fila segue o modelo **FIFO**, que significa:

**First In, First Out**

Em português:

**Primeiro que entra, primeiro que sai.**

Por exemplo:

```text
1. João
2. Maria
3. Carlos
4. Ana
```

Nesse caso, João será chamado primeiro. Depois dele, Maria será a próxima e assim por diante.

Isso evita que clientes que chegaram depois sejam atendidos antes dos que já estavam esperando.

---

## 🛠️ Tecnologias utilizadas

### Backend

* Python
* Flask

### Banco de dados

* SQLite

### Frontend

* HTML5
* CSS3
* Jinja2

---

## 📁 Organização dos arquivos

```text
fila-atendimento/
│
├── app.py
│
├── fila.db
│
├── templates/
│   └── index.html
│
└── static/
    └── style.css
```

### `app.py`

É o arquivo principal do sistema. Nele ficam as rotas e as funções responsáveis pelo funcionamento da aplicação.

### `index.html`

Contém a página principal e os elementos que o usuário utiliza para cadastrar e controlar os atendimentos.

### `style.css`

Responsável pela aparência e organização visual da página.

### `fila.db`

É o banco de dados utilizado para guardar as informações dos clientes.

> O banco é criado automaticamente quando o sistema é executado pela primeira vez.

---

## 🗄️ Banco de dados

O sistema utiliza uma tabela chamada `clientes`.

Ela possui os seguintes campos:

| Campo          | Descrição                            |
| -------------- | ------------------------------------ |
| `id`           | Identificação do cliente             |
| `nome`         | Nome do cliente                      |
| `status`       | Situação atual do atendimento        |
| `data_entrada` | Data e horário em que entrou na fila |

Os status utilizados são:

```text
Aguardando
Em atendimento
Concluído
Cancelado
```

---

## 🚀 Como executar o projeto

### 1. Instalar o Python

É necessário ter o Python instalado no computador.

Para verificar pelo terminal:

```bash
py --version
```

---

### 2. Instalar o Flask

Dentro da pasta do projeto, execute:

```bash
py -m pip install flask
```

---

### 3. Executar a aplicação

No terminal:

```bash
py app.py
```

Se tudo estiver funcionando corretamente, o Flask exibirá um endereço semelhante a:

```text
http://127.0.0.1:5000
```

Abra esse endereço no navegador para acessar o sistema.

---

## 🧪 Testando o sistema

Para verificar se a fila está funcionando corretamente:

1. Cadastre um cliente;
2. Cadastre outros clientes;
3. Observe a ordem em que eles aparecem;
4. Clique em **Chamar próximo**;
5. Verifique a alteração para **Em atendimento**;
6. Finalize o atendimento;
7. Chame o próximo cliente;
8. Teste também a opção de cancelar.

### Exemplo:

```text
João       → Concluído
Maria      → Em atendimento
Carlos     → Aguardando
Ana        → Aguardando
```

Nesse exemplo, João foi atendido antes de Maria porque entrou primeiro na fila.

---

## 📌 Regras principais

* Todo cliente novo começa como **Aguardando**;
* O próximo atendimento segue a ordem de chegada;
* Apenas clientes aguardando podem ser chamados;
* Um cliente chamado passa para **Em atendimento**;
* Um atendimento finalizado recebe o status **Concluído**;
* Um atendimento cancelado recebe o status **Cancelado**;
* Clientes concluídos ou cancelados não voltam para a fila;
* As informações ficam armazenadas no banco de dados.

---

## 📚 O que foi praticado

Com este projeto é possível colocar em prática conceitos como:

* Programação em Python;
* Desenvolvimento de aplicações com Flask;
* Criação de páginas HTML;
* Estilização com CSS;
* Criação e utilização de banco de dados SQLite;
* Comandos SQL;
* Rotas e requisições;
* Formulários;
* Operações de cadastro e alteração de dados;
* Organização de uma fila utilizando FIFO.

---

## 👨‍💻 Finalidade

Este projeto foi desenvolvido com finalidade **educacional**, servindo como prática de desenvolvimento de aplicações web utilizando Python, Flask e SQLite.
