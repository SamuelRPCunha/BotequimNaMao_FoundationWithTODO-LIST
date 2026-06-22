# Botequim na Mão - Trabalho Final 🍻

**Disciplina:** Programação para Web Designers  
**Atividade:** Trabalho Final (Desenvolvimento de site com HTML, CSS, JS e Framework CSS)

---

## 📖 Sobre o Projeto
O **Botequim na Mão** é uma plataforma fictícia de cardápio digital inteligente e gestão de bar. O sistema permite que clientes visualizem o cardápio, filtrem drinks por ingredientes e que os administradores gerenciem o estoque, controlem o funcionamento e organizem as tarefas internas do estabelecimento.

O projeto foi construído focando em uma interface moderna, amigável e totalmente responsiva, utilizando o framework **Foundation Sites**.

---

## ✅ Requisitos da Atividade Atendidos

Este projeto foi desenhado para cumprir integralmente todos os requisitos solicitados na atividade do Trabalho Final:

### 1. Estrutura de Páginas e Tema Fictício
- O sistema possui **mais de 4 páginas** bem definidas, superando o requisito mínimo:
  - `index.html`: Página inicial com o conceito do bar.
  - `cardapio.html`: Cardápio digital com filtro inteligente de ingredientes.
  - `configuracoes.html`: Tela de customização visual para o usuário.
  - `gestao.html`: Painel de administração (Estoque, Pedidos e TODO List).
  - Outras telas auxiliares (`login.html`, `carrinho.html`, etc).
- Trata-se de uma **empresa fictícia** (Botequim na Mão), com todos os dados gerados exclusivamente para este trabalho.

### 2. Menu de Navegação
- A navegação é garantida através de uma **Top-Bar** global e um menu flutuante (Dropdown) que segue o usuário e garante acesso rápido a todas as áreas do site.

### 3. Configurações Visuais (Javascript e Persistência)
- Uma página exclusiva (`configuracoes.html`) foi criada para alterar o *Look and Feel* do site:
  - **Paleta de Cores:** Estão disponíveis múltiplas opções de paletas de cores, alterando imediatamente a identidade visual de todos os botões e destaques.
  - **Arredondamento de Layout (Border Radius):** Um controle deslizante/switch que permite alterar os componentes do modo clássico (retangular) para o modo *Pill* (arredondado).
- **Persistência:** O JavaScript intercepta as escolhas e salva no `localStorage` do navegador. É possível fechar a aba e, ao retornar, suas configurações visuais (assim como seu modo Claro/Escuro e o tamanho da fonte) estarão preservadas. A página inicial conta com um alerta de uso de dados (estilo aviso de Cookies/LGPD) na primeira visita ou diretamente nas configurações.

### 4. Responsividade (@media e Grid)
- O design foi pensado em modelo **Mobile-First**. O framework **Foundation (XY Grid)** adapta a orientação dos elementos:
  - Em telas Desktop, os elementos se alinham horizontalmente de forma espaçada.
  - Em monitores menores ou Tablets (< 1200px), há adaptação e recolhimento do menu.
  - Em Smartphones (< 600px), todas as colunas quebram para o formato vertical (`.small-12`), fontes e paddings sofrem ajustes e a navegação se condensa em um menu sanduíche ou floating action nativo.

### 5. Web Service (TODO LIST) com AJAX
- Atendendo à exigência da quarta página, incluímos a aba **"📝 Tarefas"** dentro do painel de controle (`gestao.html`).
- A interface gráfica interage em tempo real com o backend Spring Boot fornecido pelo professor via solicitações AJAX (utilizando a API `fetch` nativa e Promises no arquivo `app.js`).
- O Front-End provê um belo layout para Listar (GET), Criar (POST), Atualizar (PUT) e Deletar (DELETE) tarefas no banco de dados local da API.

---

## 🛠️ Tecnologias Utilizadas

- **HTML5 & CSS3** (Vanilla para estilos base e variáveis dinâmicas)
- **JavaScript (ES6+)** (Lógica de carrinho, filtros de cardápio e consumo da API)
- **Vite** (Bundler e Servidor de desenvolvimento)
- **Foundation Sites** (Framework CSS/JS)
- **Java / Spring Boot** (Back-end do TODO LIST, embutido na pasta `backend/`)

---

## 🚀 Como Executar o Projeto Localmente

O projeto exige que tanto o Front-End quanto o Back-End (Web Service TODO-LIST) estejam rodando paralelamente.

### 1. Iniciando o Web Service (Java/Spring Boot)
1. Pelo terminal, acesse a pasta `backend/` na raiz do projeto.
2. Execute o comando do Maven Wrapper:
   ```bash
   ./mvnw spring-boot:run
   ```
   *(Ele irá subir a API Restful na porta `8080`)*

### 2. Iniciando o Front-End (Vite)
1. Em outra janela do terminal, permaneça na raiz do projeto (onde está o `package.json`).
2. Instale as dependências com o npm:
   ```bash
   npm install
   ```
3. Inicie o servidor de desenvolvimento:
   ```bash
   npm run dev
   ```
4. Acesse o IP/Localhost exibido (geralmente `http://localhost:5173`).
5. **Para acessar as Tarefas:** Faça login clicando no menu superior com o usuário e senha `admin`, e dirija-se à tela de **Gestão**.

---
*Trabalho desenvolvido para a disciplina de Programação para Web Designers.*