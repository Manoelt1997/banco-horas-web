# Banco de Horas 2026 — Guia de Deploy

## Arquivos do projeto

```
banco-horas-web/
└── index.html   ← único arquivo necessário
```

---

## PASSO 1 — Criar projeto no Firebase (gratuito)

1. Acesse **https://console.firebase.google.com**
2. Clique em **"Criar um projeto"**
3. Dê o nome: `banco-horas-2026`
4. Desative o Google Analytics (não é necessário) → **Criar projeto**

---

## PASSO 2 — Ativar o Firestore Database

1. No menu lateral, clique em **Firestore Database**
2. Clique em **"Criar banco de dados"**
3. Escolha **"Iniciar no modo de produção"** → Avançar
4. Selecione a região: **us-east1** (ou southamerica-east1) → **Ativar**

---

## PASSO 3 — Configurar regras de segurança do Firestore

No Firestore, clique na aba **"Regras"** e substitua o conteúdo por:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /entries/{document} {
      allow read, write: if true;
    }
  }
}
```

Clique em **"Publicar"**.

> ⚠️ Essas regras permitem acesso livre. Para o seu uso pessoal com login no app está ok, mas se quiser mais segurança, entre em contato para configurar autenticação Firebase.

---

## PASSO 4 — Registrar o app Web no Firebase

1. Na página inicial do projeto, clique no ícone **`</>`** (Adicionar app Web)
2. Nome do app: `banco-horas-web`
3. **NÃO** ative o Firebase Hosting → **Registrar app**
4. Você verá um bloco `firebaseConfig` assim:

```javascript
const firebaseConfig = {
  apiKey: "AIzaSy...",
  authDomain: "banco-horas-2026.firebaseapp.com",
  projectId: "banco-horas-2026",
  storageBucket: "banco-horas-2026.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abc123..."
};
```

**Guarde esses valores** — você vai precisar deles.

---

## PASSO 5 — Deploy no Vercel (gratuito)

### Opção A — Via interface web (mais simples)

1. Acesse **https://vercel.com** e crie uma conta gratuita (pode usar Google)
2. Clique em **"Add New Project"**
3. Escolha **"Import Git Repository"** ou **"Deploy without Git"**
4. Para deploy direto, use o **Vercel CLI**:

```bash
npm install -g vercel
cd banco-horas-web
vercel
```

Siga as instruções. No final, você receberá uma URL como:
`https://banco-horas-2026.vercel.app`

### Opção B — Via GitHub (recomendado para atualizações fáceis)

1. Crie um repositório no **GitHub** (pode ser privado e gratuito)
2. Faça upload do `index.html`
3. No Vercel, importe esse repositório
4. Toda vez que você atualizar o arquivo no GitHub, o Vercel publica automaticamente

---

## PASSO 6 — Configurar Firebase no app

1. Acesse sua URL do Vercel no navegador
2. Faça login com `manoel.filho` / `91989710193*AuLo`
3. O modal de configuração do Firebase abrirá automaticamente
4. Preencha com os valores do `firebaseConfig` do Passo 4
5. Clique em **"Salvar e conectar"**
6. O badge no menu lateral mudará para **"Sincronizado"** ✓

---

## Como funciona a sincronização

| Situação | Comportamento |
|----------|---------------|
| Firebase configurado | Dados salvos na nuvem, sincronizados entre PC e celular em tempo real |
| Sem Firebase | Dados salvos localmente no navegador (cada dispositivo tem seus próprios dados) |
| Sem internet | App funciona com os dados já carregados, sincroniza quando voltar |

---

## Regras do sistema

| Regra | Detalhe |
|-------|---------|
| Jornada padrão | 8h48min/dia |
| Tolerância | 15 min diários — diferenças de até ±15min = zero no banco |
| Ciclo 1 | Janeiro–Fevereiro → quitação em Fevereiro |
| Ciclo 2 | Março–Agosto → quitação em Agosto |
| Ciclo 3 | Setembro–Dezembro → quitação em Dezembro |
| PLR | Banco negativo no mês de quitação pode impactar o PLR |

---

## Acesso

- **URL:** sua URL do Vercel
- **Usuário:** `manoel.filho`
- **Senha:** `91989710193*AuLo`
