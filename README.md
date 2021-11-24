# Identificação da Linguagem Natural
<h3> LanguageNaturalUnderstanding</h3>
<h6>Uma introdução básica sobre o Processamento da Linguagem Natural (PLN). O PLN é composto de diversas técnicas que possibilitam a interpretação textual de forma automática, independentemente do tamanho do documento. Então, let's go!</h6>
<p> I) Ajuste seu ambiente Python, gerenciador de pacotes, PIP e Jupyter. <br>
    II) Instale o módulo de acesso à API entre parenteses
      (pip install --upgrade watson-developer-cloud) <br>
    III) Acesse sua API <br>
  IV) Inicie o carregamentos dos módulos. E utilizaremos basicamente dois módulos: json e watson_developer_cloud</p><br>
<p>O primeiro (json) é utilizado para manipular as informações retornadas pela API. O formato jason (Javascript Object Notation) é amplamente utilizado em acessos a serviços. Ele é equivalente ao tipo dicionário do Python, isto é, um conjunto de um ou mais chave-valor. Já o módulo watson_developer_cloud contém os métodos e tipos necessários para acesso às diversas APIS do Watson.</p><br>
<h6>Vamos executar o código.</h6>
import json
from watson_developer_cloud import NaturalLanguageUnderstandingV1 
from watson_developer_cloud.natural_language_understanding_v1 import 
Features, ConceptsOptions, RelationsOptions, EmotionOptions, EntitiesOptions, SemanticRolesOptions, SentimentOptions

<br><p> O primeiro bloco, são importados os módulos json e, a partir de watson_developer_cloud, o procedimento NaturalLanguageUnderstandingV1.  
O segundo bloco, as caracteristicas do texto serão extraídas.
Além das características (Features) importadas, estão disponiveis como Palavra Chave (KeywordsOptions) e metaDados (MetadataOptions).</p><br>
<p>Observação: Para verificar todas as opções de módulos a serem importados, apertar tab após a palavra import, será exibida uma lista de módulos para importar.</p>
<p>Para executar as demais funcionalidades: <br>

<!-- Instanciar um objeto -->
<h4> Instanciar um objeto de acesso à API.</h4>
natural_language_understanding = NaturalLanguageUnderstandingV1( <br>
  username='coloque_aqui_seu_usuario', <br>
  password='aqui_sua_senha', <br>
  version='2021-08-17') <br>
  
<p>As informações acima estão disponiveis sobre o serviço habilitado na seção de credenciais (credentials).</p><br>

<h4>Para consultar a API</h4>
<p>O metodo analyze é chamado, o seu retorno é posto com variavel response. O retorno da API, colocado em response, está estruturado como um dicionário.<p>
  
response = natural_language_understanding.analyze(  <br>
  text='Who is the primer minister of England?',  <br>
  features=Features(   <br>
    concepts=ConceptsOptions(), <br>
    emotion=EmotionOptions(), <br>
    entities=EntitiesOptions(), <br>
    sentiment=SentimentOptions(), <br>
    )) 
  <br>
  
Para visualizar melhor o retorno, utilize o código em seguida:
  print(json.dumps(response, indent=2))
  <br>
  <p>Vamos ao resultado! O código abaixo, observe que as caracteristicas são sentimentos relacionado a pergunta feita, observe também que como se trata de uma pergunta os resultados estão neutros. Cada chave na raiz foi referenciadas no dicionário na linha da citação após Features na chamada à API.</p>

{     <br>
  "emotion": {     <br>
    "document": {        <br>
      "emotion": {      <br>
        "anger": 0.149442,  <br>
        "joy": 0.151672,     <br>
        "sadness": 0.117418,   <br>
        "fear": 0.047087,      <br> 
        "disgust": 0.198362     <br>
      }     <br>
    }   <br>
  },   <br>
}   <br>
<p>Essa pequena demonstração de código é um exemplo pois, o resultado é muito extenso, aproveite para testar você também.</p>

<p>A inteligência artificial identifica o sentimento do usuário seja positivo, negativo ou neutro. Além dessa Análise de Sentimentos existe diversas tarefas realizadas pelo PLN, irei citar algumas:</p>
<p>Análise: Parsing Sintático, Parsing Discursivo, Etiquetação morfossintática e Identificação de entidades. </p>
<p>Transformação: Tradução instantanea de idiomas e Sumarização automática.</p>
<p>Geração textual: Consiste em colocar em linguagem natural algum conhecimento em alguma base de conhecimento.</p>
