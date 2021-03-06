---

copyright:

  years: 2015, 2018

lastupdated: "2018-06-14"

---


{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}


# ¿Cómo puedo obtener una rápida respuesta a mi incidencia?
{: #quicktickresp}

Cuando se pone en contacto con el soporte y abre una incidencia de soporte, puede solicitar un nivel de gravedad específico, según el tipo y la urgencia del problema. El nivel de gravedad puede estar relacionado con la celeridad con la que se soluciona el problema.
{:shortdesc}

Usted define la gravedad del problema en función de sus requisitos empresariales y de su nivel de soporte. Para obtener más información sobre los niveles de los planes de soporte, consulte [Planes de soporte](/docs/get-support/index.html). Todas las incidencias se investigan para identificar y resolver la causa raíz del problema. Cuando el equipo de soporte necesite datos de diagnóstico del problema para determinar la causa raíz del problema, se le solicita aprobación para acceder a archivos de registro y a otros datos de determinación de problemas desde la aplicación. Sin estos datos es posible que se retrase la resolución del problema.

## Recopilación de información de diagnóstico
{: #collecting-diagnostic-information}

Para diagnosticar y resolver problemas con los servicios y las aplicaciones de {{site.data.keyword.Bluemix_notm}}, es posible que el equipo de soporte de {{site.data.keyword.Bluemix_notm}} solicite información de diagnóstico. Utilice las instrucciones siguientes para recopilar y proporcionar la información solicitada lo antes posible.

Antes de recopilar la información de diagnóstico, siga estos pasos:

1. Asegúrese de tener la versión más actual de la interfaz de línea de mandatos de Cloud Foundry instalada. Para obtener más información, consulte [Instalación de la interfaz de línea de mandatos de Cloud Foundry](/docs/starters/install_cli.html).
>**Nota:** Si no tiene la versión más actual, después de conectar la línea de mandatos de Cloud Foundry a {{site.data.keyword.Bluemix_notm}}, el mandato `cf logs` no devuelve información.
2. Asegúrese de haber conectado la interfaz de línea de mandatos de Cloud Foundry al lugar en el que se ejecuta {{site.data.keyword.Bluemix_notm}} mediante el mandato `cf api`.

Utilice uno de los scripts siguientes para recopilar información de diagnóstico:

  * Para sistemas operativos Windows, descargue el archivo [bmdiag-general.bat ![icono de enlace externo](../icons/launch-glyph.svg "icono de enlace externo")](http://bluemix-mustgather.mybluemix.net/mustgather/general/bmdiag-general.bat){: new_window} y ejecútelo.
  * Para sistemas operativos Linux, descargue el archivo [bmdiag-general.sh ![icono de enlace externo](../icons/launch-glyph.svg "icono de enlace externo")](http://bluemix-mustgather.mybluemix.net/mustgather/general/bmdiag-general.sh){: new_window} y ejecútelo.

Los scripts utilizan la interfaz de línea de mandatos de Cloud Foundry para extraer la siguiente información del entorno de aplicación:
  * Registro de aplicación
  * Metadatos de aplicación
  * Rutas configuradas
  * Sucesos
  * Servicio de suministro

## Escalamiento de casos de soporte
{: #escalation}

Puede solicitar asistencia adicional escalando su caso al gestor de soporte de {{site.data.keyword.Bluemix_notm}} en servicio si cumple uno de los siguientes criterios:
  * Es un cliente de {{site.data.keyword.Bluemix_notm}} con soporte Premium o avanzado
  * Es un cliente de SoftLayer que funciona bajo el acuerdo de Soporte estándar de SoftLayer

Utilice el proceso de escalamiento para emerger problemas críticos o si cree que su incidencia de soporte no se está resolviendo como es debido. Cuando escala un caso, el gestor en servicio registra la información de la incidencia de soporte, interactúa con los miembros adecuados del equipo técnico de soporte de {{site.data.keyword.Bluemix_notm}} y le proporciona las actualizaciones adecuadas.

Para escalar un caso de soporte, debe tener una incidencia de soporte abierta para el problema.  Además, asegúrese de que proporciona una descripción detallada del problema técnico en la incidencia de soporte que haya abierto.

 Para escalar un caso, complete los pasos siguientes:

  1. Póngase en contacto con el equipo de soporte de {{site.data.keyword.Bluemix_notm}} por teléfono o a través del chat:
    * Si lo hace por teléfono, marque el número siguiente: 866-403-7638.
    * Si lo hace mediante el chat, desde el {{site.data.keyword.Bluemix_notm}} [Centro de soporte ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/unifiedsupport/supportcenter){: new_window} o, si dispone de una cuenta de SoftLayer que no esté enlazada, desde el [portal de clientes ![Icono de enlace externo](../icons/launch-glyph.svg)](https://control.softlayer.com/){:new_window}.
  2. Proporcione el número de incidencia existente y solicite escalar el caso.
  3. Proporcione la justificación del escalamiento y el impacto empresarial de su caso.

Los gestores de soporte de {{site.data.keyword.Bluemix_notm}} están en servicio y disponibles las 24 horas del día, todos los días de la semana. Los gestores en servicio utilizan los recursos adecuados para enfocar su caso y le informan sobre las acciones que se han realizado.
