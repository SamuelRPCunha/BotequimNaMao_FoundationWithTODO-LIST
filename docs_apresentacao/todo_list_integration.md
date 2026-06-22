# Integração do Web Service TODO-LIST

Este documento detalha a integração do web service **TODO-LIST** no projeto **Botequim na Mão**. O objetivo desta integração é adicionar uma funcionalidade de gestão de tarefas internas para a administração do estabelecimento.

## Visão Geral do Web Service

O web service **TODO-LIST** (disponibilizado originalmente através [deste repositório](https://github.com/w2costa/todo_list.git)) foi desenvolvido utilizando a linguagem **Java** juntamente com o framework **Spring Boot**. 

### Funcionalidade

A API fornece funcionalidades de um CRUD (Create, Read, Update, Delete) básico para o gerenciamento de tarefas. As tarefas (`Tarefa`) possuem o seguinte formato de dados (Model):
- `id`: Identificador único (Long, Autoincremento)
- `texto`: Descrição da tarefa (String)
- `createdAt`: Data de criação automática (LocalDateTime)
- `updatedAt`: Data da última modificação automática (LocalDateTime)

### Endpoints Disponíveis

A API expõe a rota principal `/tarefas`, contendo as seguintes operações:
- `GET /tarefas`: Retorna todas as tarefas cadastradas.
- `GET /tarefas/{id}`: Retorna uma tarefa específica através do seu ID.
- `POST /tarefas`: Cria uma nova tarefa. Requer um JSON com o campo `"texto"`.
- `PUT /tarefas/{id}`: Atualiza uma tarefa existente.
- `DELETE /tarefas/{id}`: Remove uma tarefa através de seu ID.

## Modificações Realizadas para a Integração

Para permitir a comunicação entre o frontend (Vite/JavaScript) e o backend (Java/Spring Boot), foram necessárias algumas adaptações:

1. **Inclusão do Backend no Repositório:**
   O código do web service foi clonado e inserido na pasta `backend/` do projeto, mantendo tudo centralizado.

2. **Configuração de CORS (Cross-Origin Resource Sharing):**
   Como o front-end e o back-end rodam em portas diferentes (ex: `5173` para o Vite e `8080` para o Spring Boot), o navegador bloqueia as requisições por questões de segurança. Para resolver isso, foi adicionada a anotação `@CrossOrigin(origins = "*")` na classe `TarefaController.java` do backend, permitindo requisições de qualquer origem.

3. **Interface de Usuário (Frontend):**
   Na página de Gestão (`gestao.html`), foi adicionada uma nova aba chamada **"📝 Tarefas"**. Dentro dessa aba, foi implementado o layout HTML com um painel de visualização e um botão para abrir o Modal de criação e edição.

4. **Lógica em JavaScript (`app.js`):**
   Foi implementado no arquivo `app.js` um conjunto de funções utilizando a `Fetch API` para consumir os endpoints assincronamente:
   - `fetchAndRenderTarefas()`: Realiza a requisição GET e popula o DOM com a lista de tarefas.
   - Evento de `submit` no formulário do Modal para processar tanto o POST (nova tarefa) quanto o PUT (edição).
   - Função `deleteTarefa(id)` atrelada ao botão de exclusão.

## Como Executar o Sistema Completo

Para que a aba de **Tarefas** funcione corretamente, tanto o Frontend quanto o Backend devem estar em execução.

### Passo 1: Iniciar o Web Service (Backend)
1. Navegue pelo terminal até a pasta `backend/`.
2. Execute o projeto Spring Boot. Se estiver utilizando Maven Wrapper, utilize o comando:
   ```bash
   ./mvnw spring-boot:run
   ```
   *(O backend iniciará na porta `8080`)*

### Passo 2: Iniciar o Frontend (Botequim na Mão)
1. Abra um novo terminal na raiz do projeto (onde se encontra o arquivo `package.json`).
2. Instale as dependências (caso não tenha feito):
   ```bash
   npm install
   ```
3. Inicie o servidor Vite:
   ```bash
   npm run dev
   ```
4. Acesse a aplicação no navegador. Faça login como **Administrador** (login: `admin`, senha: `admin`) e navegue até a tela de **Gestão**, selecionando a aba **Tarefas**.
