# 🚨 LeilãoPro — Plataforma Preditiva de Inteligência em Leilões

O **LeilãoPro** é uma solução Single Page Application (SPA) de alta performance focada na centralização, triagem avançada e análise preditiva de ativos imobiliários públicos oriundos da Caixa Econômica Federal. A plataforma foi projetada para apoiar investidores e arrematantes parceiros na identificação ágil de oportunidades de alto Retorno Sobre o Investimento (ROI), mitigando riscos de aquisição através de cruzamentos socioespaciais e inteligência artificial local.

## 📦 Lean Inception

O alinhamento estratégico, a visão de produto e o mapeamento do escopo do **LeilãoPro** foram consolidados através do framework *Lean Inception* (de Paulo Caroli), integrando dinâmicas de Design Thinking e Lean Startup para a concepção do Mínimo Produto Viável (MVP).

### 🎯 1. Visão do Produto & Objetivos de Negócio
O produto foi concebido sob a premissa de centralizar dados pulverizados de leilões, otimizando o processo de triagem para investidores. Os principais objetivos de negócio mapeados incluem:
* **Mapeamento e Filtro Ágil:** Reduzir o tempo de análise de editais de dias para minutos.
* **Mitigação de Riscos Invisíveis:** Calcular custos ocultos (ITBI, Emolumentos, Leiloeiro) antes do lance.
* **Engajamento e Retenção:** Monetizar a base de usuários através de planos focados em automação e alertas preditivos de alto ROI.

### 👥 2. Personas Segmentadas
O ecossistema atende a perfis distintos com jornadas específicas:
* **Investidor Iniciante:** Necessita de clareza na memória de cálculo de custos adicionais e segurança visual na classificação de risco do ativo.
* **Arrematante Profissional:** Exige filtros altamente reativos, monitoramento assíncrono em background (alertas multicanais) e auditoria de disponibilidade de lotes em tempo real.

### 🌊 3. O Sequenciador de Funcionalidades (Estratégia de Ondas)
A árvore de valor do produto foi distribuída em incrementos lógicos baseados na capacidade técnica e entrega de valor:
* **Onda 1 & 2 (Escopo do MVP v1.0):** Ingestão e parsing automatizado do CSV da Caixa (encoding `ISO-8859-1`), cálculo automático de custos tributários/cartorários, autenticação via Microsoft Entra ID B2C e persistência de favoritos.
* **Onda 3 (Incremento v1.1):** Motor de automação para salvamento de critérios de busca (Alertas) e orquestração do modelo de linguagem local (Ollama) para predição de status jurídico de desocupação.
* **Onda 4 & 5 (Incremento v2.0):** Integração de microsserviços via Evolution API para mensageria push multicanais (WhatsApp e Telegram), histórico de logs em caixa de entrada (Inbox) e geoprocessamento dinâmico de entorno com mapas.

---

## 📦 Wireframes (Mapas de Tela)
`📂 /wireframes-leilaopro`

O ecossistema do MVP e suas evoluções estão organizados em uma arquitetura de Single Page Application (SPA), onde a navegação entre os módulos ocorre de maneira reativa no frontend através do controle de visibilidade de componentes de escopo global. 

A estrutura lógica das visões modulares integradas é detalhada a seguir:

### 1. Dashboard e Painel de Triagem
* **Identificador de Fluxo:** `01.Dashboard.png`
* **Descrição:** Mesa de comando principal do investidor estruturada em três colunas assimétricas. O bloco central contém a barra de pesquisa global, quatro cards horizontais de KPIs consolidados da amostra da planilha, e o painel de triagem encabeçado pelo filtro de *Tipo de Imóvel*, seguido por seletores geográficos (UF, Cidade, Bairro) e inputs de ranges numéricos de limite duplo (Mínimo/Máximo) para Preço, Desconto e Score. A listagem principal conta com paginação nativa a cada 10 linhas e botões rápidos para favoritar.
Painel contextual reativo acoplado ao Dashboard principal. Ao selecionar qualquer imóvel da tabela, este componente atualiza instantaneamente o Score de Rentabilidade preditivo, exibe o diagnóstico legal emitido pelo agente de IA local e processa a memória de cálculo com a somatória exata das custas de ITBI, registro e taxa do leiloeiro, liberando o botão para a visualização ampliada.

### 2. Módulo de Imóveis Favoritados
* **Identificador de Fluxo:** `02.Favoritos.png`
* **Descrição:** Repositório personalizado para auditoria e controle de ativos salvos pelo usuário. Apresenta uma listagem expandida em tela cheia adicionando uma coluna exclusiva de status para informar se o imóvel continua classificado como disponível nos registros de edital da Caixa, disponibilizando links diretos para a ficha técnica interna ou para remoção do item da coleção.

### 3. Ficha Técnica Ampliada (Estilo Airbnb)
* **Identificador de Fluxo:** `03.Ficha técnica.png`
* **Descrição:** Visão analítica profunda dividida em layout horizontal de duas colunas. A metade esquerda reúne a ficha técnica estruturada do lote junto à tabela detalhada de aferição de custos acessórios ocultos. A metade direita dedica 50% da viewport para a ancoragem do container da API do Google Maps, projetado para renderizar o alfinete de geolocalização e os pontos de interesse do entorno socioespacial do imóvel.

### 4. Gerenciador de Alertas Ativos
* **Identificador de Fluxo:** `04.Cadastro de alertas.png`
* **Descrição:** Formulário de criação e parametrização de regras de varredura contínua de background. O layout espelha rigorosamente os mesmos eixos e campos de filtros de intervalos do Dashboard inicial, anexando uma seção de checkboxes de múltipla seleção para que o usuário vincule os canais de disparo de notificação (*E-mail*, *Telegram* e *WhatsApp*).

### 5. Painel de Gestão de Alertas (Meus Alertas)
* **Identificador de Fluxo:** `05.Meus alertas.png`
* **Descrição:** Visão administrativa de monitoramento onde o usuário gerencia suas rotinas automáticas ativas. Cada regra é encapsulada em um card horizontal cinza contendo o resumo dos critérios numéricos e os botões de ação para acionar a edição reativa no formulário ou remover a regra da esteira de processamento do Redis.

### 6. Caixa de Entrada de Notificações
* **Identificador de Fluxo:** `06.Notificações.png`
* **Descrição:** Painel de auditoria estruturado em formato de *Inbox* dividida em duas colunas. O lado esquerdo exibe o feed cronológico de alertas gerados pelos robôs. O lado direito abre o preview em wireframe do template exato de mensagem que foi disparada para os dispositivos do investidor, acompanhado por um relatório de log de sistema que atesta o status de entrega individual por canal.


### 7. Portal de Autenticação (Login)
* **Identificador de Fluxo:** `07.Login.png`
* **Descrição:** Interface limpa e centralizada em foco cognitivo único, atuando como o gateway de segurança da aplicação. Contém o acionador para o fluxo de autenticação de Single Sign-On (SSO) seguro provido pelo **Microsoft Entra ID B2C** e notas de conformidade com as diretrizes da LGPD.

---

## 👤 Autor

| Nome                          | LinkedIn                                                                 | GitHub                                      |
|-------------------------------|--------------------------------------------------------------------------|---------------------------------------------|
| Fabricio dos Santos da Silva   | [linkedin.com/in/fabriciossilva](https://www.linkedin.com/in/fabriciossilva/) | [github.com/FabriciodSantosSilva](https://github.com/FabriciodSantosSilva) |
