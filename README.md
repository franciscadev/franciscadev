#  Meu Projeto API

API REST construída com Node.js, Express e MongoDB, pronta para deploy no Render.

---

## Estrutura do projeto


/meu-projeto-api
├── index.js
├── routes/
├── models/
├── package.json


---

## Tecnologias

- Node.js
- Express
- MongoDB (Mongoose)
- CORS

---

##  Como rodar localmente

### 1. Instalar dependências
```bash
npm install
2. Iniciar servidor
npm start
 Variáveis de ambiente

Crie um arquivo .env (ou configure no Render):

MONGO_URL=mongodb+srv://usuario:senha@cluster.mongodb.net/meubanco
PORT=3000
 index.js (produção)
const express = require('express');
const cors = require('cors');
const mongoose = require('mongoose');
const usuariosRoutes = require('./routes/usuarios');

const app = express();

// PORTA DO RENDER
const PORT = process.env.PORT || 3000;

// CONEXÃO MONGODB ATLAS
mongoose.connect(process.env.MONGO_URL)
  .then(() => console.log('MongoDB conectado'))
  .catch(err => console.log(err));

app.use(cors());
app.use(express.json());

// ROTAS
app.use('/usuarios', usuariosRoutes);

app.get('/', (req, res) => {
  res.send('API rodando no Render 🚀');
});

app.listen(PORT, () => {
  console.log(`Servidor rodando na porta ${PORT}`);
});
 package.json
{
  "name": "api",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "start": "node index.js"
  },
  "dependencies": {
    "express": "^4.18.2",
    "mongoose": "^7.0.0",
    "cors": "^2.8.5"
  }
}
