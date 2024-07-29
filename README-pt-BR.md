# Teste de Wordpress + Tagging e Infraestrutura

## Instruções

### 1. Fork do Repositório
1. **Fork:**
   - Acesse o repositório fornecido e clique no botão "Fork" para criar uma cópia do repositório na sua conta do GitHub.

2. **Clone:**
   - Clone o repositório forkado para sua máquina local:
     ```sh
     git clone https://github.com/sua-conta/nome-do-repositorio.git
     cd nome-do-repositorio
     ```

### 2. Configuração do Ambiente Local com Docker

#### Passo 1: Instalar Docker

- Acesse [Docker Desktop](https://www.docker.com/products/docker-desktop) e siga as instruções para instalar o Docker no seu sistema.

#### Passo 2: Iniciar os Containers

- No terminal, navegue até o diretório onde o arquivo `docker-compose.yml` está localizado e execute o seguinte comando:

  ```sh
  docker-compose up -d
  ```

#### Passo 3: Acessar o WordPress

- Abra o navegador e vá para `http://localhost:8080`
- Siga as instruções para configurar o WordPress.

### 3. Resolver o Problema de SSL Localmente

#### Passo 1: Instalar mkcert

- Siga as instruções para instalar o [mkcert](https://github.com/FiloSottile/mkcert).

#### Passo 2: Criar e Instalar Certificados Locais

- No terminal, execute os seguintes comandos:

  ```sh
  mkcert -install
  mkcert localhost
  ```

#### Passo 3: Configurar o Nginx (Opcional)

- Caso esteja usando o Nginx como servidor web, configure o Nginx para usar os certificados gerados pelo mkcert.

### 4. Criar o Blog

- Siga o design fornecido no link do Figma: [Joico Blog Design](https://www.figma.com/file/McGbv5WCdqD8w4ZAuKLBiO/Joico---Blog?node-id=0%3A1&t=Z1aB2hfyPg9jqHkI-1)
- O blog precisa ser responsivo. Utilize quaisquer ferramentas (Elementor, Page Builder, código customizado, etc).

### 5. Inserir o Google Tag Manager

- Utilize o seguinte código para inserir o Google Tag Manager no site:

  ```html
  <!-- Google Tag Manager -->
  <script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':
  new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],
  j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src=
  'https://www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);
  })(window,document,'script','dataLayer','GTM-W3F9TBV');</script>
  <!-- End Google Tag Manager -->
  ```

### 6. Mapear Eventos usando Eventos do GA4 ou UA

- Envio de formulário (lead)
- Buscas
- Remarketing
- WhatsApp (caso tenha)
- Caso não tenha "ações valiosas" mencionadas, mapear:
   - Itens de scroll
   - Posts clicáveis (título e ID do post)
   - Reportar ao Google Analytics via Google Tag Manager

### 7. Exportar o Banco de Dados

- Após finalizar o desenvolvimento, exporte o banco de dados WordPress para um arquivo SQL.
- No terminal, execute o comando abaixo para exportar o banco de dados do container Docker:

  ```sh
  docker exec -t nome-do-container-db mysqldump -u exampleuser -pexamplepass exampledb > backup.sql
  ```

### 8. Submeter o Trabalho

1. **Commit e Push:**
   - Adicione, commit e envie suas alterações para o seu repositório forkado:
     ```sh
     git add .
     git commit -m "Finalização do teste"
     git push origin main
     ```

2. **Pull Request:**
   - Crie um Pull Request no repositório original para revisão.

3. **Enviar o Banco de Dados:**
   - Inclua o arquivo `backup.sql` no repositório antes de criar o Pull Request ou envie o arquivo separadamente conforme as instruções fornecidas.
   - Incluir nome de usuário e senha utilizados para login no WordPress
