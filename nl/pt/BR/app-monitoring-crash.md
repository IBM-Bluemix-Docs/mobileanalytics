---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-06"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Monitoramento de travamentos de aplicativo
{: #monitor-app-crash}

É possível visualizar informações sobre travamentos do seu aplicativo no console do {{site.data.keyword.mobileanalytics_short}} para monitorar melhor e solucionar problemas de seus aplicativos.

## Monitoramento de travamento de aplicativo
{: #app-crash notoc}

Na página **Travamentos**, a tabela **Visão geral de travamento** mostra as colunas de dados a seguir:

* Aplicativo: nome do aplicativo
* Travamentos: número total de travamentos para esse aplicativo
* Total de usos: número total de vezes que um usuário abre e fecha esse aplicativo
* Taxa de travamento: porcentagem de travamentos por uso

É possível ver rapidamente as informações sobre os travamentos de seu aplicativo na tabela **Travamentos**.
<!--In the **Overview** page of the **Dashboard** section,--> O gráfico de barras **Travamentos** mostra um histograma de travamentos ao longo do tempo.

É possível exibir dados de travamento de duas maneiras:

1. Exibir taxa de travamento: taxa de travamento ao longo do tempo
2. Exibir total de travamentos: total de travamentos ao longo do tempo

## Resolução de problemas de travamento de aplicativo
{: #app-crash-troubleshooting notoc}

A página **Resolução de problemas** no console do <!-- **Applications** section of the --> {{site.data.keyword.mobileanalytics_short}} oferece uma visualização granular dos travamentos do seu app, usando a tabela **Resumo do travamento**.

A tabela **Resumo de travamento** é classificável e inclui as colunas de dados a seguir:

* Travamentos
* Dispositivos
* Último travamento
* Aplicativo
* OS
* Message

Clique no ícone + próximo a qualquer entrada para exibir a tabela **Detalhes do travamento**, que inclui as colunas a seguir:

* Horário do travamento
* Versão de Aplicativo
* Versão do Sistema Operacional
* Modelo de dispositivo
* ID do dispositivo
* Download: link para fazer download dos logs que levaram ao travamento

Expanda qualquer entrada na tabela **Detalhes do travamento** para obter mais detalhes, incluindo um rastreio de pilha.

**Nota**: os dados da tabela **Resumo de travamento** são preenchidos consultando os logs de app de nível fatal. Se o seu aplicativo não coletar logs do aplicativo fatais, nenhum dado estará disponível.
