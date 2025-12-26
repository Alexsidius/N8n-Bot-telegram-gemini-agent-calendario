# n8n-telegram-calendar-agent

Automação de agendamento de compromissos via **Telegram**, utilizando **IA (Google Gemini)** e integração com **Google Calendar**, construída no **n8n**.

Este projeto demonstra o uso de **AI Agents**, **integração entre APIs** e **regras de negócio bem definidas** para resolver um problema real de forma automatizada.

---

## 📌 Visão Geral

O workflow permite que usuários agendem, consultem, atualizem e deletem compromissos diretamente pelo chat do Telegram, usando linguagem natural (texto ou áudio).

A IA é responsável por:
- Interpretar datas e horários informados em português
- Validar regras de negócio (dias úteis, horários permitidos)
- Decidir quando criar, consultar, atualizar ou excluir eventos

---

## 🚀 Funcionalidades

- 📅 Agendamento automático no Google Calendar
- 💬 Interação via Telegram (texto e áudio)
- 🎙️ Transcrição de áudio usando Google Gemini
- 🧠 AI Agent com regras claras de negócio
- ❌ Bloqueio de agendamentos em finais de semana
- ⏰ Controle de conflitos de horário
- 📩 Envio de convite por e-mail ao participante

---

## 🧩 Arquitetura do Workflow

Fluxo simplificado:

```text
Telegram Trigger
   ↓
Identificação de Texto ou Áudio
   ↓
(Áudio) → Transcrição com Gemini
   ↓
Normalização do Texto
   ↓
AI Agent (interpretação + decisão)
   ↓
Google Calendar (Consultar / Agendar / Deletar)
   ↓
Resposta ao usuário no Telegram

## 🛠️ Tecnologias Utilizadas

n8n – Orquestração e automação de workflows

Telegram Bot API – Canal de comunicação

Google Calendar API – Gestão de eventos

Google Gemini (PaLM) – IA para interpretação e transcrição

LangChain Nodes (n8n) – Implementação de AI Agent

JavaScript – Normalização de entradas

▶️ Como Utilizar
1. Importar o Workflow

Abra o n8n

Clique em Import Workflow

Importe o arquivo:

workflow/telegram_google_calendar_agent.json

2. Configurar Credenciais

Após importar o workflow, configure manualmente as seguintes credenciais no n8n:

Telegram Bot API

Google Calendar OAuth2

Google Gemini (PaLM) API


### 🔒 Nenhuma credencial, token ou dado sensível é versionado neste repositório.

3. Ativar o Workflow

Ative o workflow no n8n

O webhook do Telegram será gerado automaticamente

### ⚙️ Regras de Negócio Implementadas

Agendamentos apenas de segunda a sexta-feira

Horário permitido: 09:00 às 18:00

Duração fixa de 1 hora

Bloqueio automático de conflitos de agenda

Datas convertidas para formato ISO com timezone America/Sao_Paulo

Uso exclusivo de dados reais do Google Calendar (sem memória fictícia)

### 🔐 Segurança e Boas Práticas

Nenhuma credencial é exposta no JSON

Webhooks e IDs sensíveis não são versionados

Separação clara entre lógica, infraestrutura e segredos

Workflow importável e reutilizável em qualquer instância do n8n

🔮 Possíveis Melhorias Futuras

Suporte a múltiplos usuários e calendários

Confirmação de agendamento via Telegram

Integração com Outlook Calendar

Persistência em banco de dados

Interface administrativa para gestão de horários
