# Política de Privacidade — WhatsApp → Jira Ticket Creator

**Última atualização:** 20 de maio de 2026
**Extensão:** WhatsApp → Jira Ticket Creator
**Responsável:** Webner Soluções em Tecnologia da Informação
**Contato:** webner@webner.com.br

---

## 1. Visão geral

A extensão **WhatsApp → Jira Ticket Creator** ("a extensão") foi desenvolvida para uso corporativo. Ela permite que um colaborador, a partir de uma conversa já aberta no WhatsApp Web, gere um ticket no Jira analisando o conteúdo com um modelo de IA. **Toda a operação ocorre localmente no navegador do usuário** — não existe servidor próprio operado pela Webner que receba, processe ou armazene os dados da conversa.

Esta política descreve quais dados são tratados, com que finalidade, para onde são enviados e como você pode exercer seus direitos.

---

## 2. Dados que a extensão acessa

A extensão acessa os seguintes dados **apenas quando o usuário clica no botão da extensão**:

| Categoria | Conteúdo | Origem |
|---|---|---|
| Conteúdo da conversa | Mensagens de texto da conversa atualmente aberta no WhatsApp Web, com remetente e horário | `web.whatsapp.com` (DOM) |
| Anexos | Imagens da conversa (convertidas de blob para base64) | `web.whatsapp.com` (DOM) |
| Metadados | Nome do contato/grupo da conversa | `web.whatsapp.com` (DOM) |
| Credenciais do usuário | Chave de API do provedor de IA, URL/e-mail/token de API do Jira | Informadas pelo próprio usuário na tela de configurações |
| Lista de solicitantes | CSV publicado em Google Sheets contendo lista de pessoas autorizadas a solicitar tickets (somente leitura) | Documento público interno da Webner |

A extensão **não coleta**: histórico de navegação, cookies de outros sites, dados de identificação pessoal além dos já presentes na conversa selecionada, telemetria, métricas de uso ou analytics.

A extensão **não envia mensagens** pelo WhatsApp e **não automatiza interações** no WhatsApp Web — limita-se a ler o conteúdo da conversa aberta pelo usuário no momento do clique.

---

## 3. Como os dados são tratados

### 3.1 Onde os dados trafegam

Quando o usuário aciona a criação de um ticket, os dados saem **diretamente do navegador** (extensão) para os seguintes serviços, sem passar por nenhum servidor da Webner:

| Destino | Dados enviados | Finalidade |
|---|---|---|
| **Anthropic Claude API** (`api.anthropic.com`) *ou* **OpenAI API** (`api.openai.com`) — conforme escolha do usuário | Texto da conversa + chave de API do próprio usuário | Análise da conversa pelo modelo de IA para gerar título, descrição, prioridade e classificação do ticket |
| **Atlassian Jira Cloud** (`*.atlassian.net`) | Conteúdo do ticket + anexos + credenciais de autenticação do próprio usuário | Criação do ticket e upload de anexos |
| **Google Docs / Sheets** (`docs.google.com`) | Apenas requisição de leitura (GET) | Obter o CSV público com a lista de solicitantes autorizados |

### 3.2 Onde os dados ficam armazenados

- **Credenciais (chaves de API e tokens):** armazenadas exclusivamente no `chrome.storage.local` do navegador do próprio usuário. Nunca são enviadas para servidores da Webner ou de terceiros, exceto quando usadas para autenticar diretamente com as APIs declaradas acima.
- **Conteúdo da conversa:** **não é persistido pela extensão**. Após a criação do ticket, o conteúdo é descartado da memória do navegador.
- **Histórico de tickets criados:** apenas referências curtas (chave do ticket e link) podem ser armazenadas no `chrome.storage.local` do usuário para exibição na tela "Tickets recentes" — sem o conteúdo das mensagens originais.

A Webner **não opera nenhum banco de dados** que receba os dados da conversa.

---

## 4. Base legal e finalidade (LGPD)

O tratamento de dados segue as bases legais da **Lei Geral de Proteção de Dados (LGPD — Lei nº 13.709/2018)**:

- **Execução de contrato / interesse legítimo do empregador** (art. 7º, V e IX): a extensão é uma ferramenta de produtividade corporativa interna usada por colaboradores autorizados.
- **Consentimento** (art. 7º, I): o usuário aciona manualmente cada captura — nada é executado de forma automática ou em segundo plano.

**Finalidade única:** transformar uma conversa de atendimento já mantida via WhatsApp em um ticket estruturado no Jira, eliminando o trabalho manual de cópia.

---

## 5. Terceiros

Os dados enviados às APIs externas estão sujeitos às políticas de privacidade dos respectivos fornecedores:

- **Anthropic:** https://www.anthropic.com/legal/privacy
- **OpenAI:** https://openai.com/policies/privacy-policy
- **Atlassian (Jira):** https://www.atlassian.com/legal/privacy-policy
- **Google (Docs/Sheets):** https://policies.google.com/privacy

A Webner não controla o tratamento de dados feito por esses fornecedores. Recomendamos a leitura das políticas de cada um antes do uso.

---

## 6. Conversas com terceiros

O WhatsApp é um meio de comunicação que envolve **duas ou mais partes**. Ao usar a extensão para capturar uma conversa, o usuário é responsável por:

- Avaliar se o conteúdo da conversa pode ser processado por modelos de IA de terceiros.
- Garantir que o interlocutor está ciente, quando aplicável, do uso corporativo da conversa para abertura de tickets.
- Cumprir as normas internas da sua organização e a legislação aplicável (LGPD, sigilo profissional, segredos comerciais etc.).

---

## 7. Segurança

- Credenciais ficam confinadas ao `chrome.storage.local` do navegador, isolado por origem.
- Comunicação com todas as APIs é feita exclusivamente via **HTTPS**.
- A extensão **não executa código remoto**: todo o JavaScript executado vem empacotado no `.zip` revisado pela Chrome Web Store.
- Permissões solicitadas são as mínimas necessárias (`activeTab`, `scripting`, `storage`).

Nenhum sistema é 100% seguro. Em caso de incidente envolvendo a extensão, comunique imediatamente o contato indicado abaixo.

---

## 8. Retenção e descarte

- **Conteúdo da conversa:** não retido — descartado da memória após a criação do ticket.
- **Credenciais:** permanecem no navegador do usuário até serem removidas manualmente. O usuário pode apagá-las a qualquer momento limpando os dados da extensão (`chrome://extensions` → detalhes da extensão → "Limpar dados") ou removendo a extensão.
- **Tickets criados no Jira:** ficam sob a política de retenção da própria instância Jira da organização do usuário.

---

## 9. Direitos do titular (LGPD)

Como a extensão não armazena dados em servidor próprio, os direitos do titular (acesso, correção, eliminação, portabilidade etc.) devem ser exercidos:

- **Sobre dados no Jira:** com o administrador da instância Jira da sua organização.
- **Sobre dados nas APIs de IA:** com o respectivo fornecedor (Anthropic ou OpenAI).
- **Sobre dados no navegador:** diretamente pelo usuário, removendo a extensão ou seus dados locais.

Para dúvidas adicionais, contate: **webner@webner.com.br**.

---

## 10. Crianças e adolescentes

A extensão destina-se a uso corporativo por colaboradores adultos. Não é destinada nem direcionada a menores de 18 anos.

---

## 11. Alterações nesta política

Esta política pode ser atualizada para refletir mudanças na extensão ou na legislação aplicável. A data de "Última atualização" no topo do documento indica a versão vigente. Alterações materiais serão comunicadas via descrição da extensão na Chrome Web Store.

---

## 12. Contato

**Webner Soluções em Tecnologia da Informação**
E-mail: webner@webner.com.br

Para dúvidas sobre esta política, exercer direitos previstos na LGPD ou reportar incidentes, utilize o e-mail acima.
