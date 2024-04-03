# Azure Cognitive Search: Utilizando AI Search para indexação e consulta de Dados :books::pencil2::paperclip:

## O que é: :book: :eyes:
Azure Cognitive Search é um serviço de busca em nuvem oferecido pela Microsoft Azure. Ele permite que os desenvolvedores criem aplicativos de pesquisa avançados que podem buscar e analisar grandes quantidades de dados de forma rápida e eficiente. O Azure Cognitive Search utiliza tecnologias de inteligência artificial, como aprendizado de máquina e processamento de linguagem natural, para melhorar a relevância dos resultados da pesquisa e oferecer recursos como sugestões de consulta e respostas inteligentes. Este serviço é amplamente utilizado em uma variedade de casos de uso, desde pesquisa de conteúdo em aplicativos empresariais até criação de portais de conhecimento e catálogos de produtos online.

## Para que serve? :book: :eyes:
O Azure Cognitive Search serve para oferecer recursos de pesquisa avançada em aplicativos e serviços baseados em nuvem. Ele permite que os desenvolvedores criem experiências de pesquisa poderosas e altamente personalizadas, independentemente do tamanho ou tipo de dados que precisam ser pesquisados. Alguns dos principais usos do Azure Cognitive Search incluem:

1.  **Pesquisa de conteúdo**: Permite aos usuários buscar informações dentro de grandes conjuntos de dados, como documentos, bancos de dados, imagens e vídeos.
    
2.  **Indexação e consulta de dados estruturados e não estruturados**: Ajuda na indexação e pesquisa de dados de diferentes formatos, incluindo texto, JSON, PDF, HTML, imagens e muito mais.
    
3.  **Análise de texto**: Utiliza recursos de processamento de linguagem natural para melhorar a relevância dos resultados da pesquisa, identificar entidades, realizar análise de sentimentos e fornecer sugestões de consulta.
    
4.  **Pesquisa semântica**: Entende o contexto e a intenção por trás das consultas dos usuários, permitindo pesquisas mais intuitivas e relevantes.
    
5.  **Relevância personalizada**: Oferece recursos para ajustar e personalizar os algoritmos de relevância da pesquisa de acordo com as necessidades específicas do aplicativo.
    
6.  **Suporte multilíngue**: Permite a pesquisa e análise de texto em vários idiomas, facilitando a internacionalização de aplicativos.
    
7.  **Integração com outros serviços da Azure**: Integra-se facilmente com outros serviços da Microsoft Azure, como Azure Blob Storage, Azure SQL Database, Azure Cosmos DB e outros, para indexar e pesquisar dados armazenados em diferentes fontes.

## Problema-situação apresentado: :book: :eyes:
Vamos imaginar que você trabalha para a Fourth Coffee, uma rede nacional de cafés. Você foi solicitado a ajudar a criar uma solução de mineração de conhecimento que facilite a busca de insights sobre as experiências dos clientes. Você decide criar um índice do Azure AI Search usando dados extraídos de avaliações de clientes.

## O que esperar desse laboratório:
-   Criar recursos do Azure
-   Extrair dados de uma fonte de dados
-   Enriqueça os dados com habilidades de IA
-   Utilize o indexador do Azure no portal do Azure
-   Consulte seu índice de pesquisa
-   Revise os resultados salvos em uma Loja de conhecimento

##  Resursos necessários para solução do problema:
A solução que você criará para o Fourth Coffee requer os seguintes recursos na sua assinatura do Azure:

-   Um recurso **do Azure AI Search** , que gerenciará a indexação e a consulta.
-   Um recurso **de serviços de IA do Azure** , que fornece serviços de IA para habilidades que sua solução de pesquisa pode usar para enriquecer os dados na fonte de dados com insights gerados por IA.
    
    ⚠ **Nota** Os recursos do Azure AI Search e dos serviços Azure AI devem estar no mesmo local! ⚠
    
-   Uma **conta de armazenamento** com contêineres de blobs, que armazenará documentos brutos e outras coleções de tabelas, objetos ou arquivos.

## Passo a passo 👨🏽‍🏫👨🏽‍💻

📕 Passo 1:
### Crie um recurso _do Azure AI Search_
1. Entre no [portal do Azure](https://portal.azure.com/learn.docs.microsoft.com?azure-portal=true) .    
![Passo 1](https://github.com/ghrocha/DIO-Microsoft-Azure-AI-Fundamentals4/assets/96626042/11cff50f-69e4-40cb-ae4c-17aa4d4b539e)
![Passo 2](https://github.com/ghrocha/DIO-Microsoft-Azure-AI-Fundamentals4/assets/96626042/08e73d8d-2ed9-45e3-bd0f-93b5fa294927)
2.  Clique no botão **+ Criar um recurso** , pesquise _Azure AI Search_ e crie um recurso **Azure AI Search com as seguintes configurações:**

    -   **Assinatura** : _sua assinatura do Azure_ .
    -   **Grupo de recursos** : _Selecione ou crie um grupo de recursos com um nome exclusivo_ .
    -   **Nome do serviço** : _um nome exclusivo_ .
    -   **Localização** : _Escolha qualquer região disponível_ .
    -   **Nível de preços** : Básico
![Passo 3](https://github.com/ghrocha/DIO-Microsoft-Azure-AI-Fundamentals4/assets/96626042/489cc055-50e6-470f-91c1-c0e71ee93d29)
3.  Selecione **Review + create** e depois de ver a resposta **Validation Success** , selecione **Create** .
![Passo 4](https://github.com/ghrocha/DIO-Microsoft-Azure-AI-Fundamentals4/assets/96626042/203119e1-e9f4-42d8-b946-6e1b66304478)
4.  Após a conclusão da implantação, selecione **Ir para o recurso** . Na página de visão geral do Azure AI Search, você pode adicionar índices, importar dados e pesquisar índices criados.
![Passo 5](https://github.com/ghrocha/DIO-Microsoft-Azure-AI-Fundamentals4/assets/96626042/c8d48495-c021-467e-9538-397ab275314b)
![Passo 6](https://github.com/ghrocha/DIO-Microsoft-Azure-AI-Fundamentals4/assets/96626042/712f8597-81ef-4452-abb4-af88f14b797c)
![Passo 7](https://github.com/ghrocha/DIO-Microsoft-Azure-AI-Fundamentals4/assets/96626042/32b97d44-22af-44c0-b1ab-aa583a599092)
5. Crie um recurso de serviços de IA do Azure
Você precisará provisionar um recurso **de serviços de IA do Azure** que esteja no mesmo local que seu recurso do Azure AI Search. Sua solução de pesquisa usará esse recurso para enriquecer os dados no armazenamento de dados com insights gerados por IA.
6.  Retorne à página inicial do portal do Azure. Clique no botão **＋Criar um recurso** e pesquise os _serviços de IA do Azure_ . Selecione **criar** um plano **de serviços de IA do Azure** . Você será levado a uma página para criar um recurso de serviços de IA do Azure. 
![Passo 8](https://github.com/ghrocha/DIO-Microsoft-Azure-AI-Fundamentals4/assets/96626042/95d4c3f5-1e69-401c-9263-559837acbc36)
7. Configure-o com as seguintes configurações:
    -   **Assinatura** : _sua assinatura do Azure_ .
    -   **Grupo de recursos** : _O mesmo grupo de recursos que seu recurso do Azure AI Search_ .
    -   **Região** : _o mesmo local do recurso do Azure AI Search_ .
    -   **Nome** : _Um nome exclusivo_ .
    -   **Nível de preços** : Padrão S0
    -   **Ao marcar esta caixa, confirmo que li e compreendi todos os termos abaixo** : Selecionado
   
8.  Selecione **Revisar + criar** . Depois de ver a resposta **Validation Passed** , selecione **Create** .
![Passo 9](https://github.com/ghrocha/DIO-Microsoft-Azure-AI-Fundamentals4/assets/96626042/7df4181a-4bda-4759-a241-0bedde5a6668)
9.  Aguarde a conclusão da implantação e visualize os detalhes da implantação.
![Passo 10](https://github.com/ghrocha/DIO-Microsoft-Azure-AI-Fundamentals4/assets/96626042/666504e7-60d2-4c65-8912-db4ad5e92dc2)
10. Crie uma conta de armazenamento
11.  Retorne à página inicial do portal do Azure e selecione o botão **+ Criar um recurso** .
12.  Procure _conta de armazenamento_ e crie um recurso **de conta de armazenamento** com as seguintes configurações:
    -   **Assinatura** : _sua assinatura do Azure_ .
    -   **Grupo de recursos** : _O mesmo grupo de recursos que os recursos do Azure AI Search e dos serviços Azure AI.
    -   **Nome da conta de armazenamento** : _um nome exclusivo_ .
    -   **Localização** : _Escolha qualquer localização disponível_ .
    -   Padrão **de desempenho**
    -   **Redundância** : armazenamento localmente redundante (LRS)
![Passo 11](https://github.com/ghrocha/DIO-Microsoft-Azure-AI-Fundamentals4/assets/96626042/825925b6-2f13-432e-bca7-59ee2de80678)
14.  Clique em **Revisar** e em **Criar** . Aguarde a conclusão da implantação e vá para o recurso implantado.
![Passo 12](https://github.com/ghrocha/DIO-Microsoft-Azure-AI-Fundamentals4/assets/96626042/48fea71b-f07a-4a18-99bc-58bce9519232)
15.  Na conta de Armazenamento do Azure que você criou, no painel de menu esquerdo, selecione **Configuração** (em **Configurações** ).
16.  Altere a configuração de _Permitir acesso anônimo de Blob_ para **Habilitado** e selecione **Salvar** . 
![Passo 13](https://github.com/ghrocha/DIO-Microsoft-Azure-AI-Fundamentals4/assets/96626042/af20e4ac-fe48-4570-a72f-9bca1e977b58)
16. Carregar documentos para o armazenamento do Azure
17.  No painel do menu esquerdo, selecione **Containers** .
18.  Selecione **+ Contêiner** . Um painel do seu lado direito é aberto.
19.  Insira as seguintes configurações e clique em **Criar** :
    -   **Nome** : coffeereviews
    -   **Nível de acesso público** : Container (acesso de leitura anônimo para containers e blobs)
    -   **Avançado** : _sem alterações_ .
![Passo 14](https://github.com/ghrocha/DIO-Microsoft-Azure-AI-Fundamentals4/assets/96626042/a56082ce-fdf1-4542-b7f3-1b570d1519ca)
20.  Abra o conteiner selecionando seu nome
21.  Em uma nova guia do navegador, baixe as [avaliações de café compactadas](https://aka.ms/mslearn-coffee-reviews) em `https://aka.ms/mslearn-coffee-reviews`e extraia os arquivos para a pasta _de avaliações_ .
22.  No portal do Azure, selecione o contêiner _de avaliações de café_ . No contêiner, selecione **Carregar** .
23.  No painel **Carregar blob** , selecione **Selecionar um arquivo** .
IMAGEM PASSO 15
24.  Na janela do Explorer, selecione **todos** os arquivos na pasta _de avaliações_ , selecione **Abrir** e, em seguida, selecione **Carregar** .
![Passo 15](https://github.com/ghrocha/DIO-Microsoft-Azure-AI-Fundamentals4/assets/96626042/7455180d-ea09-4580-9b29-341b25f2af81)
26.  Depois que o upload for concluído, você poderá fechar o painel **Upload blob** . Seus documentos estão agora em seu contêiner de armazenamento _de avaliações de café_ .
![Passo 16](https://github.com/ghrocha/DIO-Microsoft-Azure-AI-Fundamentals4/assets/96626042/04fb1e2b-4aac-4ae2-b9a6-ef1d7285463f)
27. Indexar os documentos
Depois de armazenar os documentos, você poderá usar o Azure AI Search para extrair insights dos documentos. O portal do Azure fornece um _assistente de importação de dados_ . Com este assistente, você pode criar automaticamente um índice e um indexador para fontes de dados suportadas. Você usará o assistente para criar um índice e importar seus documentos de pesquisa do armazenamento para o índice do Azure AI Search.
28.  No portal do Azure, navegue até o recurso Azure AI Search. Na página **Visão geral** , selecione **Importar dados** .
![Passo 17](https://github.com/ghrocha/DIO-Microsoft-Azure-AI-Fundamentals4/assets/96626042/cdb7cbe0-835a-48b5-a968-423710fe99cc)
![Passo 18](https://github.com/ghrocha/DIO-Microsoft-Azure-AI-Fundamentals4/assets/96626042/16efbb4e-b2a3-4783-a7d1-1bd5881cba03) 
29.  Na página **Conectar-se aos seus dados** , na lista **Fonte de Dados** , selecione **Azure Blob Storage** . Preencha os detalhes do armazenamento de dados com os seguintes valores:
    -   **Fonte de dados** : Armazenamento de Blobs do Azure
    -   **Nome da fonte de dados** : coffee-customer-data
    -   **Dados a extrair** : Conteúdo e metadados
    -   **Modo de análise** : Padrão
    -   **Cadeia de conexão** : *Selecione **Escolha uma conexão existente** . Selecione sua conta de armazenamento, selecione o contêiner **de avaliações de café** e clique em **Selecionar** .
    -   **Autenticação de identidade gerenciada** : Nenhuma
    -   **Nome do contêiner** : _esta configuração é preenchida automaticamente depois que você escolhe uma conexão existente_ .
    -   **Pasta Blob** : _deixe em branco_ .
    -   **Descrição** : Avaliações sobre Fourth Coffee Shops.
30.  Selecione **Próximo: Adicionar habilidades cognitivas (opcional)** .
31.  Na secção **Anexar Serviços Cognitivos** , selecione o seu recurso de serviços Azure AI.
32.  Na seção **Adicionar enriquecimentos** :
    -   Altere o **nome da qualificação** para **coffee-skillset** .
    -   Marque a caixa de seleção **Habilitar OCR e mesclar todo o texto no campo merged_content** .
        ⚠ **Nota** É importante selecionar **Habilitar OCR** para ver todas as opções de campo enriquecido. ⚠
    -   Certifique-se de que o **campo Dados de origem** esteja configurado como **merged_content** .
    -   Altere o **nível de granularidade de enriquecimento** para **Páginas (blocos de 5.000 caracteres)** .
    -   Não selecione _Habilitar enriquecimento incremental_
    -   Selecione os seguintes campos enriquecidos:
![Passo 19](https://github.com/ghrocha/DIO-Microsoft-Azure-AI-Fundamentals4/assets/96626042/fa15dd0f-edc4-42ec-9585-85c52cf8ad9d)
33.  Em **Salvar enriquecimentos em um armazenamento de conhecimento** , selecione:
    -   Projeções de imagem
    -   Documentos
    -   Páginas
    -   Frases chave
    -   Entidades
    -   Detalhes da imagem
    -   Referências de imagem
 ![Passo 20](https://github.com/ghrocha/DIO-Microsoft-Azure-AI-Fundamentals4/assets/96626042/6110069b-f6d4-432a-8a3b-5a213c0ddc15)
 35.  Selecione **projeções de blob do Azure: Documento** . Uma configuração para _o nome do contêiner_ com as exibições preenchidas automaticamente do contêiner _de armazenamento de conhecimento_ . Não altere o nome do contêiner.
 34.  Selecione **Próximo: Personalizar índice de destino** . Altere o **nome do índice** para **coffee-index** .
 35.  Certifique-se de que a **chave** esteja configurada como **metadata_storage_path** . Deixe **o nome do sugeridor** em branco e **o modo de pesquisa** preenchido automaticamente.
 36.  Revise as configurações padrão dos campos de índice. Selecione **filtrável** para todos os campos que já estão selecionados por padrão.
![Passo 21](https://github.com/ghrocha/DIO-Microsoft-Azure-AI-Fundamentals4/assets/96626042/21423c4d-673d-492f-8f50-b2e465bd8225)
37.  Selecione **Próximo: Criar um indexador** .
38.  Altere o **nome do indexador** para **coffee-indexer** .
39.  Deixe a **programação** definida como **Once** .
40.  Expanda as **opções avançadas** . Certifique-se de que a opção **Base-64 Encode Keys** esteja selecionada, pois as chaves de codificação podem tornar o índice mais eficiente.
41.  Selecione **Enviar** para criar a fonte de dados, o conjunto de habilidades, o índice e o indexador. O indexador é executado automaticamente e executa o pipeline de indexação, que:
    -   Extrai os campos de metadados do documento e o conteúdo da fonte de dados.
    -   Executa o conjunto de habilidades cognitivas para gerar campos mais enriquecidos.
    -   Mapeia os campos extraídos para o índice.
42.  Volte à página de recursos do Azure AI Search. No painel esquerdo, em **Gerenciamento de pesquisa** , selecione **Indexadores** . Selecione o **indexador de café** recém-criado . Espere um minuto e selecione **↻ Atualize** até que o **Status** indique sucesso.
43.  Selecione o nome do indexador para ver mais detalhes.   
![Passo 22](https://github.com/ghrocha/DIO-Microsoft-Azure-AI-Fundamentals4/assets/96626042/b539c06a-9ba3-4fdc-a894-30aadc7a31f1)
44. Consultar o índice
Use o Search Explorer para escrever e testar consultas. O explorador de pesquisa é uma ferramenta incorporada no portal do Azure que oferece uma maneira fácil de validar a qualidade do seu índice de pesquisa. Você pode usar o Search Explorer para escrever consultas e revisar resultados em JSON.
45.  Na página _Visão geral_ do serviço de pesquisa , selecione **Explorador de pesquisa** na parte superior da tela.
![Passo 23](https://github.com/ghrocha/DIO-Microsoft-Azure-AI-Fundamentals4/assets/96626042/91b05b9e-64b9-499e-80e8-1b579146fc2c)
46. Observe como o índice selecionado é o _índice de café_ que você criou. Abaixo do índice selecionado, altere a _visualização_ para **JSON view** .
![Passo 24](https://github.com/ghrocha/DIO-Microsoft-Azure-AI-Fundamentals4/assets/96626042/ac69c18f-28e2-4981-8ddc-1ece52b0d619)
47. No campo **do editor de consultas JSON** , copie e cole:
![Passo 25](https://github.com/ghrocha/DIO-Microsoft-Azure-AI-Fundamentals4/assets/96626042/e2d72bb4-fd80-4f07-a9d7-a02361686e44)
48. Selecione **Pesquisar** . A consulta de pesquisa retorna todos os documentos no índice de pesquisa, incluindo uma contagem de todos os documentos no campo **@odata.count** . O índice de pesquisa deve retornar um documento JSON contendo os resultados da pesquisa.
49. Agora vamos filtrar por localização. No campo **do editor de consultas JSON** , copie e cole:
![Passo 26](https://github.com/ghrocha/DIO-Microsoft-Azure-AI-Fundamentals4/assets/96626042/6e96ad6d-0214-4fb8-aed8-d702932a79c6)
50. Selecione **Pesquisar** . A consulta pesquisa todos os documentos no índice e filtra revisões com localização em Chicago. Você deveria ver `3`no `@odata.count`campo.
51. Agora vamos filtrar por sentimento. No campo **do editor de consultas JSON** , copie e cole:
![Passo 27](https://github.com/ghrocha/DIO-Microsoft-Azure-AI-Fundamentals4/assets/96626042/81dbc55f-6fc1-4f4e-9d1e-2b776df6cc09)
52. Selecione **Pesquisar** . A consulta pesquisa todos os documentos no índice e filtra revisões com sentimento negativo. Você deveria ver `1`no `@odata.count`campo.
⚠ **Nota** Veja como os resultados são classificados por `@search.score`. Esta é a pontuação atribuída pelo mecanismo de pesquisa para mostrar o quão próximos os resultados correspondem à consulta fornecida. ⚠ 
53.  Um dos problemas que podemos querer resolver é por que pode haver certas avaliações. Vamos dar uma olhada nas frases-chave associadas à avaliação negativa. O que você acha que pode ser a causa da revisão?
54. Revise o armazenamento de conhecimento
Vamos ver o poder do armazenamento de conhecimento em ação. Ao executar o _assistente Importar dados_ , você também criou um armazenamento de conhecimento. Dentro do armazenamento de conhecimento, você encontrará os dados enriquecidos extraídos pelas habilidades de IA que persistem na forma de projeções e tabelas.
55.  No portal do Azure, navegue de volta para a sua conta de armazenamento do Azure.
56.  No painel do menu esquerdo, selecione **Containers** . Selecione o contêiner **de armazenamento de conhecimento** .
![Passo 28](https://github.com/ghrocha/DIO-Microsoft-Azure-AI-Fundamentals4/assets/96626042/63a7ffbd-ecaa-4e62-90d2-69fb2b990045)
57. Selecione qualquer um dos itens e clique no arquivo **objectprojection.json** .
![Passo 29](https://github.com/ghrocha/DIO-Microsoft-Azure-AI-Fundamentals4/assets/96626042/b23eed0b-de2c-4058-9231-df40d60192b8)
58. Selecione **Editar** para ver o JSON produzido para um dos documentos do seu armazenamento de dados do Azure.
![Passo 30](https://github.com/ghrocha/DIO-Microsoft-Azure-AI-Fundamentals4/assets/96626042/dac02cb7-eb53-4a0d-b4fa-65e04d49cf1b)
59. Selecione a localização atual do blob de armazenamento no canto superior esquerdo da tela para retornar à conta de armazenamento _Containers_ .
![Passo 31](https://github.com/ghrocha/DIO-Microsoft-Azure-AI-Fundamentals4/assets/96626042/857d22e5-040b-490f-a001-bf6a7569882d)
60. Em _Containers_ , selecione o contêiner _coffee-skillset-image-projection_ . Selecione qualquer um dos itens.
![Passo 32](https://github.com/ghrocha/DIO-Microsoft-Azure-AI-Fundamentals4/assets/96626042/65bac40d-93ad-4f07-8757-16dc19ad57c3)
61. Selecione qualquer um dos arquivos _.jpg_ . Selecione **Editar** para ver a imagem armazenada no documento. Observe como todas as imagens dos documentos são armazenadas desta forma.
![Passo 33](https://github.com/ghrocha/DIO-Microsoft-Azure-AI-Fundamentals4/assets/96626042/6dd13994-4385-4cf2-a376-f8e23a368daa)
62.  Selecione a localização atual do blob de armazenamento no canto superior esquerdo da tela para retornar à conta de armazenamento _Containers_ .
63.  Selecione **Navegador de armazenamento** no painel esquerdo e selecione **Tabelas** . Há uma tabela para cada entidade no índice. Selecione a tabela _coffeeSkillsetKeyPhrases_ .
    Observe as frases-chave que o armazenamento de conhecimento conseguiu capturar do conteúdo das avaliações. Muitos dos campos são chaves, portanto você pode vincular as tabelas como um banco de dados relacional. O último campo mostra as frases-chave que foram extraídas pelo conjunto de habilidades.
    
## Comentário sobre a aplicação que foi utilizada:🌐📃✏
Eu tentei refazer diversas vezes mas não obtive sucesso. aquele mesmo erro persistiu.  
Sobre o seu uso: 
Aplicações de e-commerce: Empresas de comércio eletrônico podem usar o Azure Cognitive Search para melhorar a experiência do usuário ao oferecer recursos de pesquisa avançada, como sugestões de consulta, filtragem refinada e classificação relevante de resultados de pesquisa.
Portais de conteúdo: Plataformas de mídia, blogs e sites de notícias podem utilizar o Azure Cognitive Search para ajudar os usuários a encontrar rapidamente o conteúdo relevante através de recursos como busca por palavras-chave, categorização automática de conteúdo e sugestões de conteúdo relacionado.
Aplicações de RH e recrutamento: Empresas podem implementar o Azure Cognitive Search em sistemas de gestão de recursos humanos para facilitar a busca e seleção de candidatos com base em habilidades específicas, experiência e outras qualificações relevantes.
Aplicações de assistência médica: Organizações de saúde podem utilizar o Azure Cognitive Search para desenvolver sistemas de pesquisa que ajudem médicos e profissionais de saúde a acessar rapidamente informações clínicas relevantes, protocolos de tratamento e pesquisas médicas.  

Plataformas de suporte ao cliente: Empresas podem integrar o Azure Cognitive Search em sistemas de suporte ao cliente para fornecer aos agentes acesso rápido a informações relevantes, respostas a perguntas frequentes e histórico de interações com os clientes.
São alguns exemplos.
Ao usar o Azure Cognitive Search, aprendi a configurar adequadamente o serviço, ajustar parâmetros de relevância, monitorar e otimizar o desempenho, integrar com outras ferramentas da Microsoft e gerenciar custos. Além disso, aproveiteis recursos de suporte e comunidade para resolver problemas e compartilhar experiências. Esses aprendizados são essenciais para maximizar o valor do Azure Cognitive Search.
## 😄😁😆👾👻

Estruturado e organizado por Gustavo Henrique.
