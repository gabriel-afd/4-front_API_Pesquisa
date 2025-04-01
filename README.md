# Front-end: Pesquisa de Operadoras de Saúde 🚀

Este é o front-end do projeto de **busca de operadoras de saúde**, desenvolvido com **Vue.js 3**. Ele consome a API back-end implementada em Java Spring Boot e permite buscas interativas com filtros como nome, cidade e UF.

---

### ✅ Passos para rodar localmente

1. Clone o repositório:

```bash
git clone https://github.com/gabriel-afd/4-front_API_Pesquisa.git
```

2. Antes de executar o projeto, você precisa ter instalado:

- [Node.js (versão LTS)](https://nodejs.org)
  > O `npm` (Node Package Manager) já vem incluso ao instalar o Node.js.

Para verificar se estão corretamente instalados: 

```bash
node -v
npm -v 

3. Abra a pasta do projeto clonado no VSCode

4. Instale as dependências:
```
npm install
```

5. Execute o servidor e o projeto ficará disponivel em seu localhost:

```
npm run serve
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


