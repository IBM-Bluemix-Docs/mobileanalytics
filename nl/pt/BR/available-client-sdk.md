---

copyright:
 years: 2018

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# SDKs para Mobile Analytics
{: #install-sdk}
Última atualização: 18 de janeiro de 2018
{: .last-updated}

Os {{site.data.keyword.mobileanalytics_short}} Client SDKs estão atualmente disponíveis para Android, iOS, Cordova e Web. Abaixo estão os links para SDKs específicos da plataforma.

Consulte o [documento](install-client-sdk.html) para obter informações detalhadas sobre instalação e conceitos técnicos.

{: shortdesc}

## SDKs para Android

   Instalando o [Android Client SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-analytics)


## SDKs para iOS

   Instalando o [iOS Client SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-analytics)

   
## SDKs para Cordova

   Instalando o [Cordova Client SDK](https://www.npmjs.com/package/bms-core)
   
## SDKs para Web

   Instalando o [Web Client SDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-web-analytics/)
   
**Nota**: para o Web SDK, é necessário configurar sua instância de serviço Mobile Analytics para permitir um servidor de aplicativos. Forneça a URL do seu servidor de aplicativos por meio da API de REST de Configuração de Serviço por meio da UI do Swagger. Os métodos POST, GET, PUT e DELETE são fornecidos para as operações CRUD da configuração de serviço que é uma lista de URLs permitidas. Para configurações GET e DELETE de sua instância de serviço, use sua chave API. Para criar e atualizar a configuração de serviço, use os métodos POST e PUT com as URLs permitidas listadas como o corpo {"allowedUrls":["http://abc.com","https://www.xyz.com"]}. Se você acessando de um navegador no mesmo sistema que o servidor da web, forneça "http://localhost" como a URL permitida.
