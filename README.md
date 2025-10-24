#  Projeto "Boa Noite, Mãe": Automação n8n com IA



Um workflow de automaçao n8n projetado para enviar uma mensagem de boa noite única e carinhosa, acompanhada de uma imagem gerada por IA, para uma pessoa especial todos os dias.





---



## 🎯 Objetivo do Projeto



Este projeto é uma demonstração de como a automação (n8n) e a IA generativa (Gemini, Groq, DALL-E) podem ser usadas para criar interações pessoais, consistentes e tocantes.



O objetivo deste fluxo é enviar uma mensagem de boa noite para a mãe do autor, Arthur, todas as noites às 21:10, garantindo que cada mensagem seja única e acompanhada de uma arte visual que reflita o sentimento do texto.



## 🤖 Como Funciona: O Fluxo da Automação



O workflow é executado em várias etapas sequenciais:



1.Agendamento (Schedule Trigger): O workflow é iniciado automaticamente todos os dias às 21:10 (CRON: `10 21 \* \* \*`).



2.  Geração de Texto (AI Agent 1 - `agente\_arthur`):

&nbsp;   Um Agente de IA (usando Gemini ou Groq) é acionado com uma persona de "filho dedicado e amoroso".

&nbsp;   O prompt exige que a IA gere uma mensagem curta, carinhosa, com tratamento respeitoso ("a Senhora") e que inclua um versículo bíblico diferente\ (de Salmos, Provérbios, etc.) a cada dia, seguido de uma breve explicação do sentimento do versículo.

&nbsp;   O agente usa memória (`Simple Memory1`) para garantir que os versículos não sejam repetidos.



3.   Armazenamento (Set): A mensagem de texto gerada é armazenada na variável `msg`.



4.  Geração de Prompt de Imagem (AI Agent 2 - `AI Agent`):

&nbsp;   A mensagem de texto (`msg`) é passada para um segundo Agente de IA, que atua como um "Engenheiro de Prompt Visual".

&nbsp;   Este agente tem a missão de traduzir o sentimento da mensagem de boa noite em um prompt de imagem detalhado e artístico em inglês, focando em paleta de cores, simbolismo e composição.



5.  Geração de Imagem (OpenAI):

&nbsp;    O prompt de imagem em inglês é enviado para a API da OpenAI (DALL-E) para gerar uma imagem única que corresponda visualmente ao texto.



6.  Formatação e Envio (Extract from File \& HTTP Request):

&nbsp;    A imagem gerada (binária) é convertida para base64 (`Extract from File`).

&nbsp;    Um nó `HTTP Request` envia a mensagem final para a API do Evolution (um gateway de WhatsApp).

&nbsp;    O destinatário recebe uma única mensagem de WhatsApp contendo:

&nbsp;        A imagem gerada como mídia.

&nbsp;        O texto original de boa noite como legenda da imagem.



## 🛠️ Tecnologias Utilizadas



n8n: Plataforma de automação (low-code) para orquestrar o fluxo.

Google Gemini \& Groq:\ Modelos de Linguagem (LLMs) para a geração de texto criativo.

OpenAI (DALL-E): Modelo de Geração de Imagem para a criação da arte visual.

Evolution API: Gateway de WhatsApp para o envio das mensagens.



## 🚀 Como Usar este Projeto



Para replicar este workflow, você precisará:



1.  Importar o Workflow: Baixe o arquivo `workflow.json` deste repositório e importe-o para a sua instância n8n.

2.  Configurar Credenciais: Você precisará criar e configurar as seguintes credenciais no seu n8n:

&nbsp;    `Google Gemini API`

&nbsp;    `Groq API`

&nbsp;    `OpenAI API`

&nbsp;    Credenciais da sua `Evolution API` (ou outro gateway de WhatsApp).

3.  Personalizar Nós:

&nbsp;  Schedule Trigger (`1e8a5...`): Altere o horário do CRON conforme sua necessidade.

&nbsp;   agente\_arthur (`40d6b...`): Personalize o system message com a persona e as regras que você desejar.

&nbsp;   HTTP Request (`5db46d...`): Altere a `URL` da sua API de WhatsApp e o `number` (número de telefone) de destino.



## 📁 Estrutura do Repositório



`workflow.json`: O arquivo de exportação do n8n contendo toda a lógica do fluxo de trabalho.

`README.md`\: Esta documentação.

`.gitignore`: Arquivo para ignorar arquivos locais do n8n.

`LICENSE`: Licença MIT.



## 👨‍💻 Autor



ArthurDays

&nbsp;    GitHub: `https://github.com/ArthurDays`

&nbsp;    LinkedIn: `www.linkedin.com/in/arthur-days` 

