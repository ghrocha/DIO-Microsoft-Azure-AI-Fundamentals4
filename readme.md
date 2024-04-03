# Azure Cognitive Search: Utilizando AI Search para indexação e consulta de Dados :books::pencil2::paperclip:

## O que é::book: :eyes:
Azure Cognitive Search é um serviço de busca em nuvem oferecido pela Microsoft Azure. Ele permite que os desenvolvedores criem aplicativos de pesquisa avançados que podem buscar e analisar grandes quantidades de dados de forma rápida e eficiente. O Azure Cognitive Search utiliza tecnologias de inteligência artificial, como aprendizado de máquina e processamento de linguagem natural, para melhorar a relevância dos resultados da pesquisa e oferecer recursos como sugestões de consulta e respostas inteligentes. Este serviço é amplamente utilizado em uma variedade de casos de uso, desde pesquisa de conteúdo em aplicativos empresariais até criação de portais de conhecimento e catálogos de produtos online.

## Para que serve?:book: :eyes:
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

1.  Entre no [portal do Azure](https://portal.azure.com/learn.docs.microsoft.com?azure-portal=true) .    
IMAGEM PASSO 1

IMAGEM PASSO 2

2.  Clique no botão **+ Criar um recurso** , pesquise _Azure AI Search_ e crie um recurso **Azure AI Search com as seguintes configurações:**

    -   **Assinatura** : _sua assinatura do Azure_ .
    -   **Grupo de recursos** : _Selecione ou crie um grupo de recursos com um nome exclusivo_ .
    -   **Nome do serviço** : _um nome exclusivo_ .
    -   **Localização** : _Escolha qualquer região disponível_ .
    -   **Nível de preços** : Básico
 IMAGEM PASSO 3
3.  Selecione **Review + create** e depois de ver a resposta **Validation Success** , selecione **Create** .

   IMAGEM PASSO 4
   
4.  Após a conclusão da implantação, selecione **Ir para o recurso** . Na página de visão geral do Azure AI Search, você pode adicionar índices, importar dados e pesquisar índices criados.

IMAGEM PASSO 5

IMAGEM PASSO 6

IMAGEM PASSO 7

5. Crie um recurso de serviços de IA do Azure
Você precisará provisionar um recurso **de serviços de IA do Azure** que esteja no mesmo local que seu recurso do Azure AI Search. Sua solução de pesquisa usará esse recurso para enriquecer os dados no armazenamento de dados com insights gerados por IA.

6.  Retorne à página inicial do portal do Azure. Clique no botão **＋Criar um recurso** e pesquise os _serviços de IA do Azure_ . Selecione **criar** um plano **de serviços de IA do Azure** . Você será levado a uma página para criar um recurso de serviços de IA do Azure. 

IMAGEM PASSO 8
7. Configure-o com as seguintes configurações:
    -   **Assinatura** : _sua assinatura do Azure_ .
    -   **Grupo de recursos** : _O mesmo grupo de recursos que seu recurso do Azure AI Search_ .
    -   **Região** : _o mesmo local do recurso do Azure AI Search_ .
    -   **Nome** : _Um nome exclusivo_ .
    -   **Nível de preços** : Padrão S0
    -   **Ao marcar esta caixa, confirmo que li e compreendi todos os termos abaixo** : Selecionado
   
8.  Selecione **Revisar + criar** . Depois de ver a resposta **Validation Passed** , selecione **Create** .

IMAGEM PASSO 9

9.  Aguarde a conclusão da implantação e visualize os detalhes da implantação.

IMAGEM PASSO 10

10. Crie uma conta de armazenamento

11.  Retorne à página inicial do portal do Azure e selecione o botão **+ Criar um recurso** .
    
12.  Procure _conta de armazenamento_ e crie um recurso **de conta de armazenamento** com as seguintes configurações:
    -   **Assinatura** : _sua assinatura do Azure_ .
    -   **Grupo de recursos** : _O mesmo grupo de recursos que os recursos do Azure AI Search e dos serviços Azure AI.
    -   **Nome da conta de armazenamento** : _um nome exclusivo_ .
    -   **Localização** : _Escolha qualquer localização disponível_ .
    -   Padrão **de desempenho**
    -   **Redundância** : armazenamento localmente redundante (LRS)
13.  Clique em **Revisar** e em **Criar** . Aguarde a conclusão da implantação e vá para o recurso implantado.
    
    IMAGEM PASSO 12
    
14.  Na conta de Armazenamento do Azure que você criou, no painel de menu esquerdo, selecione **Configuração** (em **Configurações** ).
15.  Altere a configuração de _Permitir acesso anônimo de Blob_ para **Habilitado** e selecione **Salvar** . 

IMAGEM PASSO 13

16. Carregar documentos para o armazenamento do Azure
17.  No painel do menu esquerdo, selecione **Containers** .

18.  Selecione **+ Contêiner** . Um painel do seu lado direito é aberto.
    
19.  Insira as seguintes configurações e clique em **Criar** :
    -   **Nome** : coffeereviews
    -   **Nível de acesso público** : Container (acesso de leitura anônimo para containers e blobs)
    -   **Avançado** : _sem alterações_ .

IMAGEM PASSO 14

20.  Abra o conteiner selecionando seu nome

21.  Em uma nova guia do navegador, baixe as [avaliações de café compactadas](https://aka.ms/mslearn-coffee-reviews) em `https://aka.ms/mslearn-coffee-reviews`e extraia os arquivos para a pasta _de avaliações_ .
    
22.  No portal do Azure, selecione o contêiner _de avaliações de café_ . No contêiner, selecione **Carregar** .
23.  No painel **Carregar blob** , selecione **Selecionar um arquivo** .
  
IMAGEM PASSO 15

24.  Na janela do Explorer, selecione **todos** os arquivos na pasta _de avaliações_ , selecione **Abrir** e, em seguida, selecione **Carregar** .

IMAGEM PASSO 16

26.  Depois que o upload for concluído, você poderá fechar o painel **Upload blob** . Seus documentos estão agora em seu contêiner de armazenamento _de avaliações de café_ .

27. Indexar os documentos
Depois de armazenar os documentos, você poderá usar o Azure AI Search para extrair insights dos documentos. O portal do Azure fornece um _assistente de importação de dados_ . Com este assistente, você pode criar automaticamente um índice e um indexador para fontes de dados suportadas. Você usará o assistente para criar um índice e importar seus documentos de pesquisa do armazenamento para o índice do Azure AI Search.

28.  No portal do Azure, navegue até o recurso Azure AI Search. Na página **Visão geral** , selecione **Importar dados** .
IMAGEM PASSO 17
IMAGEM PASSO 18
 
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
    
   IMAGEM PASSO 19
    
        
33.  Em **Salvar enriquecimentos em um armazenamento de conhecimento** , selecione:
    -   Projeções de imagem
    -   Documentos
    -   Páginas
    -   Frases chave
    -   Entidades
    -   Detalhes da imagem
    -   Referências de imagem
   IMAGEM PASSO 20
   
 35.  Selecione **projeções de blob do Azure: Documento** . Uma configuração para _o nome do contêiner_ com as exibições preenchidas automaticamente do contêiner _de armazenamento de conhecimento_ . Não altere o nome do contêiner.
    
34.  Selecione **Próximo: Personalizar índice de destino** . Altere o **nome do índice** para **coffee-index** .
    
35.  Certifique-se de que a **chave** esteja configurada como **metadata_storage_path** . Deixe **o nome do sugeridor** em branco e **o modo de pesquisa** preenchido automaticamente.
    
36.  Revise as configurações padrão dos campos de índice. Selecione **filtrável** para todos os campos que já estão selecionados por padrão.

IMAGEM PASSO 21

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

IMAGEM PASSO 22

44. Consultar o índice
Use o Search Explorer para escrever e testar consultas. O explorador de pesquisa é uma ferramenta incorporada no portal do Azure que oferece uma maneira fácil de validar a qualidade do seu índice de pesquisa. Você pode usar o Search Explorer para escrever consultas e revisar resultados em JSON.

45.  Na página _Visão geral_ do serviço de pesquisa , selecione **Explorador de pesquisa** na parte superior da tela.

PASSO 23

46. Observe como o índice selecionado é o _índice de café_ que você criou. Abaixo do índice selecionado, altere a _visualização_ para **JSON view** .

PASSO 24

47. No campo **do editor de consultas JSON** , copie e cole:

PASSO 25

50.  Selecione **Pesquisar** . A consulta de pesquisa retorna todos os documentos no índice de pesquisa, incluindo uma contagem de todos os documentos no campo **@odata.count** . O índice de pesquisa deve retornar um documento JSON contendo os resultados da pesquisa.
    
51.  Agora vamos filtrar por localização. No campo **do editor de consultas JSON** , copie e cole:

PASSO 26

52.  Selecione **Pesquisar** . A consulta pesquisa todos os documentos no índice e filtra revisões com localização em Chicago. Você deveria ver `3`no `@odata.count`campo.
    
53.  Agora vamos filtrar por sentimento. No campo **do editor de consultas JSON** , copie e cole:

PASSO 27

54.  Selecione **Pesquisar** . A consulta pesquisa todos os documentos no índice e filtra revisões com sentimento negativo. Você deveria ver `1`no `@odata.count`campo.
    
   ⚠ **Nota** Veja como os resultados são classificados por `@search.score`. Esta é a pontuação atribuída pelo mecanismo de pesquisa para mostrar o quão próximos os resultados correspondem à consulta fornecida. ⚠
    
 55.  Um dos problemas que podemos querer resolver é por que pode haver certas avaliações. Vamos dar uma olhada nas frases-chave associadas à avaliação negativa. O que você acha que pode ser a causa da revisão?

55. Revise o armazenamento de conhecimento
Vamos ver o poder do armazenamento de conhecimento em ação. Ao executar o _assistente Importar dados_ , você também criou um armazenamento de conhecimento. Dentro do armazenamento de conhecimento, você encontrará os dados enriquecidos extraídos pelas habilidades de IA que persistem na forma de projeções e tabelas.
56.  No portal do Azure, navegue de volta para a sua conta de armazenamento do Azure.
57.  No painel do menu esquerdo, selecione **Containers** . Selecione o contêiner **de armazenamento de conhecimento** .

PASSO 28

58. Selecione qualquer um dos itens e clique no arquivo **objectprojection.json** .

PASSO 29

59. Selecione **Editar** para ver o JSON produzido para um dos documentos do seu armazenamento de dados do Azure.

PASSO 30

60. Selecione a localização atual do blob de armazenamento no canto superior esquerdo da tela para retornar à conta de armazenamento _Containers_ .

PASSO 31

61. Em _Containers_ , selecione o contêiner _coffee-skillset-image-projection_ . Selecione qualquer um dos itens.

PASSO 32

62. Selecione qualquer um dos arquivos _.jpg_ . Selecione **Editar** para ver a imagem armazenada no documento. Observe como todas as imagens dos documentos são armazenadas desta forma.

PASSO 33

63.  Selecione a localização atual do blob de armazenamento no canto superior esquerdo da tela para retornar à conta de armazenamento _Containers_ .
    
64.  Selecione **Navegador de armazenamento** no painel esquerdo e selecione **Tabelas** . Há uma tabela para cada entidade no índice. Selecione a tabela _coffeeSkillsetKeyPhrases_ .
    Observe as frases-chave que o armazenamento de conhecimento conseguiu capturar do conteúdo das avaliações. Muitos dos campos são chaves, portanto você pode vincular as tabelas como um banco de dados relacional. O último campo mostra as frases-chave que foram extraídas pelo conjunto de habilidades.
    
## Comentário sobre a aplicação que foi utilizada:🌐📃✏

  

TEXTO AQUI

  

## 😄😁😆👾👻

Estruturado e organizado por Gustavo Henrique.