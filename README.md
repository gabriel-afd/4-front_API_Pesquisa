# Front-end: Pesquisa de Operadoras de Saúde 🚀

Este é o front-end do projeto de **busca de operadoras de saúde**, desenvolvido com **Vue.js 3**. Ele consome a API back-end implementada em Java Spring Boot e permite buscas interativas com filtros como nome, cidade e UF.

---

### ✅ Passos para rodar localmente
### 1. Clone o repositório:

```bash
git clone https://github.com/gabriel-afd/4-front_API_Pesquisa.git
```

---

### 2. Instale o Node.js

Antes de executar o projeto, é necessário ter o **Node.js** instalado.

Baixe e instale a versão LTS em:  
👉 [https://nodejs.org](https://nodejs.org)

> O `npm` (Node Package Manager) já vem incluso com o Node.js.

Após a instalação, verifique se tudo está funcionando corretamente:

```bash
node -v
npm -v
```

---

### 3. Abra a pasta do projeto clonado no VS Code

```bash
cd 4-front_API_Pesquisa
code .
```

---

### 4. Instale as dependências do projeto:

```bash
npm install
```

---

### 5. Execute o servidor de desenvolvimento:

```bash
npm run serve
```

Após a inicialização, o projeto estará disponível no seu navegador em:

```
http://localhost:8080
```


---


## 🎓 Descrição do Projeto

O usuário pode digitar um termo, selecionar uma UF e/ou digitar uma cidade para buscar operadoras de saúde de forma filtrada.

- A busca é feita com base na API REST criada no back-end
- Resultados são exibidos com paginação (10 por página)
- Caso não existam resultados, uma mensagem amigável é exibida

---

## 🔄 Integração com a API

Este front consome a rota:

```http
GET http://localhost:8080/operadoras/busca
```

Parâmetros disponíveis:
- `termo` (ex: nome fantasia, razão social, cnpj etc.)
- `cidade`
- `uf`

Exemplo de URL gerada:
```
http://localhost:8080/operadoras/busca?termo=saude&cidade=Recife&uf=PE
```

---

## 🚪 Deploy

O front-end está publicado em:

👉 https://front-api-pesquisa-deploy.onrender.com/

> ⚠️ O Render pode demorar de **20 a 50 segundos** no primeiro acesso gratuito (free tier)


---

## 👤 Autor

**Gabriel Medeiros de Mendonça**  
[github.com/gabriel-afd](https://github.com/gabriel-afd)  
gmedeiros144@gmail.com


