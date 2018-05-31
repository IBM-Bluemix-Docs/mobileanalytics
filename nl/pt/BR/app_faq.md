---

copyright:
  years: 2015, 2017
lastupdated: "2018-02-19"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# Perguntas Mais Frequentes 
{: #faq}


1. **O que é {{site.data.keyword.mobileanalytics_full}}?**
	
	O {{site.data.keyword.mobileanalytics_full}} é um serviço que fornece insight em tempo real e histórico sobre como seus aplicativos móveis são executados e estão sendo usados. Ao usar o {{site.data.keyword.mobileanalytics_short}}, os desenvolvedores de aplicativos e proprietários de aplicativos podem tomar decisões orientadas a dados monitorando tendências em usuários ativos, sessões, plataformas móveis e travamentos de aplicativos. Também é possível configurar alertas em métricas selecionadas que, uma vez acionadas, enviam mensagens para qualquer terminal REST, incluindo um serviço de push ou seus serviços de sistema de mensagens internas.


2. **O que posso fazer com {{site.data.keyword.mobileanalytics_short}} para {{site.data.keyword.Bluemix_notm}}?**

	Como um Gerente de produto de aplicativos móveis, é possível ver quantas pessoas usam seu aplicativo (métricas do usuário) e quando elas o estão usando (métricas de sessão). Essas informações são apresentadas como uma série temporal e atualizadas em tempo real para que você possa ver o efeito das mudanças feitas em seu aplicativo. É possível filtrar para ver versões específicas do aplicativo ou sistemas operacionais para tomar decisões de descontinuação e priorização. 
	
	Como um Comerciante de aplicativo móvel, você pode usar métricas de usuário e de sessão para monitorar participação, gerenciar a rotatividade e avaliar a efetividade dos esforços de marketing do aplicativo móvel, observando mudanças ao longo do tempo e correlacionando com as suas datas de evento.
	
	Como um Desenvolvedor de aplicativos móveis, é possível usar métricas de travamento para descobrir e resolver problemas de desempenho do aplicativo móvel antes que eles frustrem os usuários e prejudiquem a reputação do aplicativo. É possível monitorar a contagem de travamentos e a taxa de travamento do console de analítica, além de priorizar travamentos que estão afetando a maioria dos usuários. É possível configurar alertas para enviar notificações ou executar ações automatizadas quando os travamentos excedem um determinado limite e é possível solucionar problemas realizando drill down em instâncias de travamento para ver logs de dispositivo e rastreios de pilha de aplicativos.
	
	Assegure-se de não compartilhar nenhuma informação pessoal usando {{site.data.keyword.mobileanalytics_short}}.

3. **Preciso de habilidades de analista de dados para usar o Mobile Analytics?**

	Não, o {{site.data.keyword.mobileanalytics_short}} oferece um console de analítica pronto para uso para partes interessadas nos negócios e para desenvolvedores de aplicativos. Não são necessárias qualificações de consulta.

4. **Posso executar consultas customizadas em meus dados de analítica?**

    O {{site.data.keyword.mobileanalytics_short}} não permite consultas customizadas, mas há consideração para este recurso no futuro.
	
5. **Como conecto meu aplicativo ao {{site.data.keyword.mobileanalytics_short}}?**

    [Faça download de nosso SDK de software livre para iOS ou Android](install-client-sdk.html) ou use a [API de REST](https://mobile-analytics-dashboard.{DomainName}/analytics-service/) do {{site.data.keyword.mobileanalytics_short}} para outras plataformas. 

6. **Em quais regiões do IBM Cloud o Mobile Analytics está disponível?**

    Atualmente, o Mobile Analytics está disponível nos Estados Unidos - Sul e no Reino Unido. A disponibilidade em outras regiões está planejada, mas o período ainda não foi determinado.

7. **Quanto custa esse serviço?**

    Os primeiros 100 milhões de eventos que são coletados a cada mês são grátis e depois, os eventos custarão US$ 1 por milhão de eventos.
	
8. **O que é um evento?**

    Atualmente eventos relatados incluem o início de sessão do aplicativo, término de sessão do aplicativo (incluindo travamento do aplicativo), notificações de alerta e entradas de log.
	
9. **Como posso estimar quanto o serviço vai custar por mês?**

    Como a precificação depende do número de eventos que são enviados para o serviço por conta do cliente, a estimativa de precificação significa estimar eventos.  
	
	O preço que é cobrado é a soma de eventos de todos os aplicativos que você conectou ao {{site.data.keyword.mobileanalytics_short}}. Para um determinado aplicativo, o número de eventos depende do grau de instrumentação do que você implementou no aplicativo, do número de usuários e de quão ativos os usuários são. 
	
	Use esta fórmula para estimar uso:eventos por mês por aplicativo = (usuários por dia)(sessões por usuário por dia)(dias por mês)(eventos por sessão)
	
	Eventos por sessão pode variar amplamente de 2 a várias centenas, dependendo de quais chamadas de rede, analítica customizada, captura de log e definições de alerta o desenvolvedor configurou no aplicativo.

9. **Quanto tempo meus dados de analítica são mantidos?**

    Os dados são mantidos por pelo menos 30 dias.
	
10. **Quanto tempo leva para que os dados sejam exibidos no console do {{site.data.keyword.mobileanalytics_short}}?**

    Os dados no console do {{site.data.keyword.mobileanalytics_short}} são quase em tempo real, o que significa que são exibidos com diferença de segundos dos eventos reais.
	
11. **Qual é a diferença entre o {{site.data.keyword.mobileanalytics_full}} e a analítica móvel localizada no MobileFirst Platform Foundation?**

    Usuário e sessão são muito semelhantes nesses dois consoles, mas a analítica que vem com o MobileFirst Platform Foundation contém métricas adicionais e configurações que permitem que os clientes gerenciem seus próprios clusters de analítica no local. Além disso, o console de analítica do MobileFirst Platform Foundation divide as métricas para adaptadores e procedimentos do adaptador, enquanto que no serviço do {{site.data.keyword.mobileanalytics_short}}, essas métricas são integradas em gráficos e tabelas de solicitação de rede.
	
12. **Estou usando o MobileFirst Platform Foundation no local para desenvolver meus aplicativos, mas não quero hospedar meu próprio cluster de analítica. Posso usar {{site.data.keyword.mobileanalytics_full}} em vez?**

    Sim. Você tem duas opções: se estiver usando o MobileFirst Platform Foundation 7.x ou 8.0 e seus apps forem instrumentados com os SDKs do MobileFirst Platform, poderá configurar seu servidor MobileFirst para relatar dados de analítica para o {{site.data.keyword.mobileanalytics_short}} for {{site.data.keyword.Bluemix_notm}}. Leia a postagem do blog [Configurando os serviços do IBM Cloud Mobile Analytics e Mobile Foundation ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://mobilefirstplatform.ibmcloud.com/blog/2016/07/11/analytics-bm-service/){: new_window} para obter detalhes. Como alternativa, é possível instrumentar seus apps usando o {{site.data.keyword.mobileanalytics_short}} SDK do {{site.data.keyword.Bluemix_notm}} e relatar diretamente para o serviço {{site.data.keyword.mobileanalytics_short}}.
