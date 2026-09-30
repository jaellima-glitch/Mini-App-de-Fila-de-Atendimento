# 📋 Requisitos — Sistema de Fila de Atendimento

## 1. Informações do projeto

**Nome do projeto:** Sistema de Fila de Atendimento

**Tecnologias utilizadas:** Python, Flask, SQLite, HTML e CSS.

### Objetivo

Criar uma aplicação web capaz de organizar uma fila de atendimento, permitindo cadastrar clientes, acompanhar a fila, chamar o próximo cliente e controlar o andamento de cada atendimento.

---

# 2. Descrição

O sistema foi pensado para situações em que é necessário organizar pessoas que estão aguardando atendimento.

Quando um cliente é cadastrado, ele entra automaticamente na fila com o status **Aguardando**.

O atendimento deve seguir a ordem de chegada, utilizando a lógica **FIFO (First In, First Out)**.

Além disso, o sistema permite acompanhar o atendimento até sua conclusão ou cancelamento.

---

# 3. Requisitos Funcionais

Os requisitos funcionais representam as funções que devem estar disponíveis no sistema.

| ID   | Requisito             | Descrição                                                                       |
| ---- | --------------------- | ------------------------------------------------------------------------------- |
| RF01 | Cadastro de cliente   | Permitir que um novo cliente seja inserido na fila através do seu nome.         |
| RF02 | Entrada na fila       | Colocar automaticamente o cliente cadastrado como `Aguardando`.                 |
| RF03 | Visualização da fila  | Mostrar na tela os clientes que estão cadastrados no sistema.                   |
| RF04 | Ordem de chegada      | Manter os clientes organizados de acordo com o momento em que entraram na fila. |
| RF05 | Chamar próximo        | Permitir que o atendente chame o próximo cliente disponível.                    |
| RF06 | Controle FIFO         | Selecionar primeiro o cliente que está aguardando há mais tempo.                |
| RF07 | Iniciar atendimento   | Alterar o status do cliente chamado para `Em atendimento`.                      |
| RF08 | Finalizar atendimento | Permitir que um atendimento seja marcado como `Concluído`.                      |
| RF09 | Cancelar atendimento  | Permitir que um atendimento seja marcado como `Cancelado`.                      |
| RF10 | Salvar informações    | Armazenar os dados dos clientes em um banco SQLite.                             |
| RF11 | Identificação         | Criar um ID único para cada cliente cadastrado.                                 |
| RF12 | Registrar entrada     | Guardar a data e o horário em que o cliente entrou na fila.                     |

---

# 4. Requisitos Não Funcionais

Os requisitos não funcionais estão relacionados às características e condições de funcionamento da aplicação.

| ID    | Requisito             | Descrição                                                                           |
| ----- | --------------------- | ----------------------------------------------------------------------------------- |
| RNF01 | Linguagem             | A aplicação deve ser desenvolvida utilizando Python.                                |
| RNF02 | Framework             | O sistema deve utilizar o framework Flask.                                          |
| RNF03 | Banco de dados        | As informações devem ser armazenadas utilizando SQLite.                             |
| RNF04 | Interface             | O sistema deve possuir uma interface web simples e organizada.                      |
| RNF05 | Navegador             | A aplicação deve poder ser acessada através de um navegador moderno.                |
| RNF06 | Organização do código | Os arquivos HTML, CSS e Python devem ficar organizados de forma separada.           |
| RNF07 | Persistência          | Os dados cadastrados devem continuar salvos mesmo depois que o sistema for fechado. |
| RNF08 | Facilidade de uso     | As principais funções devem ser fáceis de encontrar e utilizar.                     |
| RNF09 | Manutenção            | O código deve ser organizado para facilitar futuras modificações.                   |
| RNF10 | Validação             | O sistema deve verificar os dados enviados antes de realizar o cadastro.            |

---

# 5. Regras de Negócio

## RN01 — Cadastro

Ao cadastrar um novo cliente, ele deverá entrar automaticamente na fila com o status:

```text
Aguardando
```

---

## RN02 — Ordem da fila

Os clientes devem permanecer organizados de acordo com a ordem em que foram cadastrados.

Exemplo:

```text
João
↓
Maria
↓
Carlos
```

João deverá ser chamado antes de Maria, e Maria antes de Carlos.

---

## RN03 — Próximo cliente

Ao selecionar **Chamar próximo**, o sistema deverá procurar o primeiro cliente que ainda esteja com o status `Aguardando`.

---

## RN04 — Início do atendimento

Quando um cliente for chamado, seu status deverá mudar de:

```text
Aguardando
```

para:

```text
Em atendimento
```

---

## RN05 — Finalização

Depois que o atendimento terminar, o status deverá ser alterado para:

```text
Concluído
```

---

## RN06 — Cancelamento

Caso seja necessário cancelar um atendimento, o status deverá ser alterado para:

```text
Cancelado
```

Esse cliente não deverá ser chamado novamente.

---

## RN07 — Armazenamento

As informações dos clientes deverão ser mantidas no banco de dados SQLite para que não sejam perdidas quando a aplicação for encerrada.

---

# 6. Casos de Uso

## UC01 — Cadastrar cliente

**Ator:** Atendente

**Objetivo:** Adicionar uma pessoa à fila.

### Passos

1. O atendente acessa o sistema.
2. Digita o nome do cliente.
3. Clica em **Entrar na fila**.
4. O sistema verifica o nome informado.
5. O cliente é salvo no banco.
6. O cliente aparece na fila como `Aguardando`.

---

## UC02 — Visualizar fila

**Ator:** Atendente

**Objetivo:** Consultar os clientes e verificar a situação de cada atendimento.

### Passos

1. O atendente abre a página inicial.
2. O sistema consulta os dados salvos.
3. Os clientes são apresentados na tela.
4. O status de cada cliente é exibido.

---

## UC03 — Chamar próximo cliente

**Ator:** Atendente

**Objetivo:** Iniciar o atendimento do próximo cliente.

### Passos

1. O atendente clica em **Chamar próximo**.
2. O sistema procura clientes com status `Aguardando`.
3. A ordem de chegada é verificada.
4. O primeiro cliente da fila é selecionado.
5. O status passa para `Em atendimento`.

---

## UC04 — Concluir atendimento

**Ator:** Atendente

**Objetivo:** Informar que o atendimento terminou.

### Passos

1. O atendente localiza o cliente que está sendo atendido.
2. Seleciona a opção **Concluir**.
3. O sistema muda o status para `Concluído`.
4. A alteração é salva no banco.

---

## UC05 — Cancelar atendimento

**Ator:** Atendente

**Objetivo:** Retirar um atendimento da fila.

### Passos

1. O atendente localiza o cliente.
2. Seleciona **Cancelar**.
3. O sistema altera o status para `Cancelado`.
4. O cliente deixa de ser considerado para os próximos atendimentos.

---

# 7. Estrutura do banco de dados

A aplicação terá uma tabela chamada:

```text
clientes
```

A estrutura será:

| Campo          | Tipo     | Descrição                          |
| -------------- | -------- | ---------------------------------- |
| `id`           | INTEGER  | Número de identificação do cliente |
| `nome`         | TEXT     | Nome informado no cadastro         |
| `status`       | TEXT     | Estado atual do atendimento        |
| `data_entrada` | DATETIME | Data e hora do cadastro            |

---

# 8. Estados do atendimento

Um cliente poderá passar pelos seguintes estados:

```text
              ┌──────────────┐
              │  Aguardando  │
              └──────┬───────┘
                     │
                     ▼
             ┌────────────────┐
             │ Em atendimento │
             └───────┬────────┘
                     │
                     ▼
              ┌──────────────┐
              │  Concluído   │
              └──────────────┘
```

Também poderá ocorrer:

```text
Aguardando
     │
     ▼
Cancelado
```

---

# 9. Critérios de aceitação

O projeto deverá atender aos seguintes pontos:

* [ ] Cadastrar um novo cliente;
* [ ] Mostrar o cliente na fila;
* [ ] Iniciar o cliente com status `Aguardando`;
* [ ] Manter a ordem de chegada;
* [ ] Chamar o primeiro cliente disponível;
* [ ] Alterar o status para `Em atendimento`;
* [ ] Permitir finalizar um atendimento;
* [ ] Permitir cancelar um atendimento;
* [ ] Impedir que clientes cancelados sejam chamados novamente;
* [ ] Impedir que clientes concluídos sejam chamados novamente;
* [ ] Salvar os dados no SQLite;
* [ ] Manter os dados depois de fechar e abrir novamente a aplicação.

---

# 10. Ambiente necessário

Para executar o projeto será necessário:

* Python 3 instalado;
* Flask instalado;
* Navegador web;
* Editor de código, como VS Code.

### Instalação

```bash
py -m pip install flask
```

### Execução

```bash
py app.py
```

Depois de iniciar o servidor, acessar:

```text
http://127.0.0.1:5000
```

---

# 11. Resultado esperado

Ao acessar a aplicação, o usuário deverá conseguir cadastrar clientes e visualizar a situação da fila.

Um exemplo de funcionamento:

```text
┌─────────────────────────────────────┐
│       FILA DE ATENDIMENTO           │
├─────────────────────────────────────┤
│ Nome: [____________________]        │
│                                     │
│       [ Entrar na fila ]            │
│       [ Chamar próximo ]            │
├─────────────────────────────────────┤
│ Nome       Status                   │
│                                     │
│ João       Concluído                │
│ Maria      Em atendimento           │
│ Carlos     Aguardando               │
│ Ana        Aguardando               │
└─────────────────────────────────────┘
```

Dessa forma, o atendente consegue acompanhar os clientes e controlar cada etapa do atendimento.

---

# 12. Conclusão

O sistema tem como finalidade facilitar o gerenciamento de uma fila de atendimento através de uma aplicação web simples.

Durante o desenvolvimento são utilizados conceitos de **Python, Flask, SQLite, HTML, CSS, SQL, requisições web e lógica FIFO**, permitindo colocar em prática diferentes conhecimentos de desenvolvimento de sistemas.

O projeto também pode ser expandido futuramente com recursos como senha de atendimento, painel de chamada, histórico de atendimentos, pesquisa de clientes e diferentes tipos de fila.
