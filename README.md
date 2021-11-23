# LanguageNaturalUnderstanding
<h6>Uma introdução básica sobre o Processamento da Linguagem Natural (PLN). O PLN é composto de diversas técnicas que possibilitam a interpretação textual de forma automática, independentemente do tamanho do documento.</h6>
<p>Para executar as demais funcionalidades: <br>

O primeiro bloco, são importados os módulos json e, a partir de watson_developer_cloud, o procedimento NaturalLanguageUnderstandingV1.
  
<!-- Para verificar os módulos criados a serem importados, apertar tab após a palavra import, será exibida uma lista de módulos para importar. -->
  
O segundo bloco, as caracteristicas do texto serão extraídas.
Além das características (Features) importadas, estão disponiveis como Palavra Chave (KeywordsOptions) e metaDados (MetadataOptions).</p><br>

import json
from watson_developer_cloud import NaturalLanguageUnderstandingV1 
from watson_developer_cloud.natural_language_understanding_v1 import 
Features, ConceptsOptions, RelationsOptions, EmotionOptions, EntitiesOptions, SemanticRolesOptions, SentimentOptions

<!-- Instanciar um objeto -->
<h4> Instanciar um objeto de acesso à API.</h4>
natural_language_understanding = NaturalLanguageUnderstandingV1( <br>
  username='coloque_aqui_seu_usuario', <br>
  password='aqui_sua_senha', <br>
  version='2021-08-17') <br>
  
<!-- Informações disponiveis sobre o serviço habilitado na seção de credenciais. -->
<h4>Para consultar a API</h4>
<p>O metodo analyze é chamado, o seu retorno é posto com variavel response.
response = natural_language_understanding.analyze(  <br>
  text='Who is the prime minister of England?',  <br>
  features=Features(   <br>
    concepts=ConceptsOptions(), <br>
    emotion=EmotionOptions(), <br>
    entities=EntitiesOptions(), <br>
    sentiment=SentimentOptions(), <br>
    )) 
  <br>
  
<!--Para visualizar melhor o retorno -->
  print(json.dumps(response, indent=2))
  <br>
  <p>As caracteristicas abaixo foram referenciadas no dicionário na linha da citação após Features.</p>

{
  "emotion": {
    "document": {
      "emotion": {
        "anger": 0.149442, 
        "joy": 0.151672, 
        "sadness": 0.117418, 
        "fear": 0.047087, 
        "disgust": 0.198362
      }
    }
  }, 
  "sentiment": {
    "document": {
      "score": 0.0, 
      "label": "neutral"
    }
  }, 
  "language": "en", 
  "entities": [
    {
      "relevance": 0.33, 
      "text": "president", 
      "type": "JobTitle", 
      "count": 1
    }, 
    {
      "relevance": 0.33, 
      "text": "Brazil", 
      "disambiguation": {
        "subtype": [
          "GovernmentalJurisdiction", 
          "CompanyShareholder", 
          "Country"
        ], 
        "name": "Brazil", 
        "dbpedia_resource": "http://dbpedia.org/resource/Brazil"
      }, 
      "type": "Location", 
      "count": 1
    }
  ], 
  "concepts": [
    {
      "relevance": 0.886784, 
      "text": "President", 
      "dbpedia_resource": "http://dbpedia.org/resource/President"
    }, 
    {
      "relevance": 0.862208, 
      "text": "President of the United States", 
      "dbpedia_resource": "http://dbpedia.org/resource/President_of_the_United_States"
    }, 
    {
      "relevance": 0.845824, 
      "text": "Politics of Brazil", 
      "dbpedia_resource": "http://dbpedia.org/resource/Politics_of_Brazil"
    }
  ], 
  "usage": {
    "text_characters": 31, 
    "features": 5, 
    "text_units": 1
  }
}

<!-- Como se trata de uma pergunta os resultados estão neutros. -->
