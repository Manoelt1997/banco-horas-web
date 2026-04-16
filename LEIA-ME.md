# Banco de Horas 2026 — Guia de Instalação

## O que é este aplicativo?

Aplicativo desktop para monitoramento de banco de horas da Live Roupas Esportivas, desenvolvido com Electron (tecnologia usada no VS Code, Slack, Discord, etc.).

---

## Pré-requisitos

Você precisará instalar **Node.js** (inclui o npm):

1. Acesse: https://nodejs.org
2. Baixe a versão **LTS** (recomendada)
3. Execute o instalador e siga os passos
4. Após instalar, abra o **Prompt de Comando** e verifique:
   ```
   node --version
   npm --version
   ```

---

## Como instalar e rodar o aplicativo

### Passo 1 — Extraia os arquivos
Extraia a pasta `banco-horas-app` em qualquer local do seu computador (ex: `C:\banco-horas-app`).

### Passo 2 — Instale as dependências
Abra o **Prompt de Comando** como administrador, navegue até a pasta e rode:

```cmd
cd C:\banco-horas-app
npm install
```

Aguarde o download dos pacotes (pode levar alguns minutos na primeira vez).

### Passo 3 — Execute o aplicativo
```cmd
npm start
```

O aplicativo abrirá automaticamente.

---

## Como gerar o instalador (.exe) para Windows

Após o Passo 2, execute:

```cmd
npm run build:win
```

Isso gerará na pasta `dist/`:
- **`Banco de Horas 2026 Setup.exe`** — instalador completo (cria atalho no desktop e menu iniciar)
- **`Banco de Horas 2026 Portable.exe`** — versão portátil, sem instalação necessária

---

## Acesso ao sistema

- **Usuário:** `manoel.filho`
- **Senha:** `91989710193*AuLo`

---

## Regras do sistema

| Regra | Detalhe |
|-------|---------|
| Jornada padrão | 8h48min/dia |
| Tolerância | 15 minutos diários — diferenças de até ±15min = banco zero no dia |
| Ciclo 1 | Janeiro–Fevereiro → quitação em Fevereiro |
| Ciclo 2 | Março–Agosto → quitação em Agosto |
| Ciclo 3 | Setembro–Dezembro → quitação em Dezembro |
| Impacto PLR | Banco negativo no mês de quitação pode afetar o PLR |

---

## Onde os dados são salvos?

Os registros de ponto são salvos localmente no seu computador via `localStorage` do Electron. Não há necessidade de internet após a instalação.

---

## Suporte

Em caso de dúvidas ou problemas, entre em contato com o suporte interno.
