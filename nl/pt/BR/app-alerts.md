---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-06"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Configurando alertas
{: #alerts}

## Configurando alertas com Mobile Analytics 

É possível configurar limite nas definições de alerta no console do {{site.data.keyword.mobileanalytics_short}} para monitorar melhor suas atividades.

É possível configurar limites que, se excedidos, acionarão alertas para notificar o monitor do console do {{site.data.keyword.mobileanalytics_short}}. Os alertas acionados podem ser visualizados no console ou os alertas podem ser manipulados por um webhook customizado. <!-- This feature provides a proactive means of detecting app log errors, server log errors, extended periods of network latency, and authentication failures.--> Esse recurso fornece um meio proativo de detectar erros de log do aplicativo e erros de log do servidor de travamentos de aplicativo. Limites e alertas reativos evitam que você filtre seus dados e configure limites em um amplo espectro de granularidade.

## Criando uma definição de alerta para logs do aplicativo
{: #alert-def-client-logs notoc}

É possível criar uma definição de alerta que é baseada em logs do aplicativo.

Neste exemplo, você usa os dados do log do aplicativo para criar uma definição de alerta. O alerta monitora todos os logs do aplicativo que foram recebidos nos últimos cinco minutos e continua a verificação a cada cinco minutos, até que a definição de alerta seja desativada ou excluída. Um alerta é acionado para cada dispositivo que enviou três ou mais logs de erro de aplicativo com o mesmo nome e versão do aplicativo.

1. No console do {{site.data.keyword.mobileanalytics_short}}, clique em **Definições** para acessar a página Definições de alerta.
2. Clique em **Criar alerta** para criar um alerta.
3. Forneça os seguintes valores:
	* Nome do alerta: alerta para logs de app
	* Mensagem: alerta de mensagem de erro
	* Frequência de consulta: 5 minutos
	* Tipo de evento: logs de app
		* Propriedade: nível de log
			* Valor: erro
			* Tipo de Limite
				* Tipo de limite: total para instância do aplicativo

					**Nota**: se você escolher a opção Média para o aplicativo, será feita uma média dos logs de app pelo número de dispositivos. Por exemplo, se você tem dois dispositivos e um dispositivo envia seis logs de app enquanto o outro dispositivo envia três logs de app, a média é de 4,5 logs de app.
				* Operador: é maior que ou igual a 3
	<!-- insert alert definition tab image? -->

4. Clique em **Avançar** e forneça o valor a seguir:
	* Método: somente console de análise

		**Nota**: escolha a opção Console de analítica e Post de rede se também desejar enviar uma mensagem POST com uma carga útil JSON para sua URL customizada. Os campos a seguir estarão disponíveis se você escolher essa opção:
		* URL para autoteste inicial da rede
        * Cabeçalhos
        * Tipo de Autenticação
5. Clique em **Salvar**.

Você criou uma definição de alerta para acionar um alerta no término de cada intervalo de 5 minutos se o número de logs de app atingir seu limite de 3 ou mais logs de erro.

## Criando uma definição de alerta para travamentos de aplicativo
{: #alert-def-app-crash notoc}

É possível criar uma definição de alerta baseada em travamentos de aplicativo.

Neste exemplo, você usa os dados de travamento de aplicativo para criar uma definição de alerta. O alerta monitora todos os travamentos de aplicativo nos últimos dois minutos e continua a verificação a cada dois minutos, até que a definição de alerta seja desativada ou excluída. Um alerta é acionado para cada aplicativo que travou cinco ou mais vezes. Para obter mais informações sobre travamentos de aplicativo, veja [Travamentos de aplicativo](#app_crash).

1. No console do {{site.data.keyword.mobileanalytics_short}}, clique em **Definições** para exibir a página Definições de alertas.
2. Clique em **Criar alerta**.
3. Forneça os seguintes valores:
	* Nome do alerta: alerta para travamentos de aplicativo
	* Mensagem: alerta de travamento de aplicativo
	* Frequência de consulta: travamentos de aplicativo
		* Frequência de consulta: 2 minutos
	* Tipo de evento: travamentos do aplicativo
		* Nome do aplicativo: qualquer aplicativo
		* Versão do aplicativo: qualquer versão
    * Tipo de Limite
      * Tipo de limite: contagem de travamentos
      * Operador: é maior que ou igual a 5
4. Clique na guia **Método de distribuição** e forneça o valor a seguir:
  * Método: somente console de análise

    **Nota**: escolha a opção **Console de análise e post de rede** se desejar também enviar uma mensagem POST com uma carga útil JSON para sua URL customizada. Os campos a seguir estarão disponíveis se você escolher essa opção:
      * URL de post de rede (obrigatório)
      * Cabeçalhos (opcional)
      * Tipo de autenticação (obrigatório)
5. Clique em **Salvar**.

## Gerenciando definições de alerta
{: #managing-alert-definitions notoc}

Neste exemplo, você gerencia suas definições de alerta a partir da página Gerenciamento de alerta.

1. No console do {{site.data.keyword.mobileanalytics_short}}, clique em **Logs**. Essa ação abre a página Logs de alerta.
2. Opcional: alterne a caixa de seleção sob a coluna **Ativado** para ativar ou desativar uma definição de alerta específica.
3. Opcional: clique no ícone **Duplicar** se desejar criar uma cópia de uma definição de alerta e mudar alguns valores.
4. Opcional: clique no ícone **Lápis** se desejar editar uma definição de alerta.
5. Opcional: clique no ícone **Lixeira** se desejar excluir uma definição de alerta.

## Visualizando Detalhes de Alerta
{: #viewing-alert-details notoc}

Neste exemplo, você visualiza os detalhes de seus alertas acionados a partir da página Log de alerta.

1. No console do {{site.data.keyword.mobileanalytics_short}}, clique em **Logs**. Essa ação abre a página Log de alerta.
2. Clique no ícone **+** para qualquer um dos alertas. Essa ação exibe as seções **Definição de alerta** e **Instâncias de alerta**.

    **Nota**: se a definição de alerta correspondente não foi excluída nem modificada, será possível editar a definição de alerta clicando em **Editar alerta**. Caso contrário, o botão **Editar alerta** estará indisponível e a mensagem a seguir será exibida:

    `Essa definição de alerta foi modificada ou excluída.`

3. Opcional: selecione um alerta e clique no ícone **Lixeira** para excluir o alerta.

