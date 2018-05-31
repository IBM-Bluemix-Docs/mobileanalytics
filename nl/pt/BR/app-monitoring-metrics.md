---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-06"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Usando métricas e eventos
{: #usingmetrics}

## Monitorando Aplicativos com Mobile Analytics

O {{site.data.keyword.mobileanalytics_full}} fornece monitoramento e análise para seus aplicativos móveis. É possível registrar logs do aplicativo e monitorar dados com o SDK do cliente {{site.data.keyword.mobileanalytics_short}}. Os desenvolvedores podem controlar quando enviar esses dados para o serviço {{site.data.keyword.mobileanalytics_short}}. Quando os dados forem entregues para o {{site.data.keyword.mobileanalytics_short}}, será possível usar o console do {{site.data.keyword.mobileanalytics_short}} para obter insights analíticos sobre seus aplicativos, dispositivos e logs do aplicativo.
{: shortdesc}

##Métricas predefinidas

Com as **métricas predefinidas**, é possível responder perguntas como:

* Quantos novos usuários eu tenho?  
* Quantas pessoas estão usando ativamente meu aplicativo?  
* Com que frequência as pessoas estão usando meu aplicativo? 
* Que hora do dia as pessoas estão usando meu aplicativo?  
* Quais modelos de dispositivo meus usuários preferem? 
* Quando deverei descontinuar o suporte para sistemas operacionais legados? 
* Quais aplicativos estão tendo problemas de desempenho?  

##Eventos Customizados

Incluindo seus próprios **eventos customizados**, é possível responder perguntas como: 

* Quais recursos são mais e menos usados?  
* Onde os usuários estão entrando e saindo do meu app?  
* Quais atividades os usuários estão visualizando mais?  
* Os usuários estão concluindo fluxos de trabalho no app (por exemplo, funis de conversão)?   

Os logs do lado do cliente e os dados de uso são coletados automaticamente e enviados para o serviço Mobile Analytics on demand. Os desenvolvedores e administradores podem usar o painel do serviço {{site.data.keyword.mobileanalytics_short}} para visualizar os dados que são coletados pelo SDK do cliente.

## Visualização de dados
{: data-visualization notoc}

Todos os dados coletados pelo serviço de analítica podem ser visualizados por meio do painel do {{site.data.keyword.mobileanalytics_short}} que é acessível no seu painel do {{site.data.keyword.Bluemix_notm}} clicando na instância do tile de serviço do IBM {{site.data.keyword.mobileanalytics_short}}. <!--You can also create custom charts, based on data that is collected by the analytics service in the dashboard.--> Além de uma visão rápida de sua analítica móvel, o recurso analítico inclui a capacidade de executar uma procura bruta nos logs de clientes, dados capturados de travamento do cliente e quaisquer dados extras que você forneça explicitamente por meio de chamadas de função de API do cliente que são alimentadas no serviço {{site.data.keyword.mobileanalytics_short}}. 

