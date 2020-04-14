Estudio SSL/TLS en Diputaciones Provinciales - Abril 2020
=========================================

### Introducción
La entrada en vigor de las Leyes [39/2015](https://www.boe.es/eli/es/l/2015/10/01/39/con) y [40/2015](https://www.boe.es/buscar/act.php?id=BOE-A-2015-10566) recogen aspectos significativos de la relación electrónica entre las Administraciones y los ciudadanos, como pudiera ser el derecho y obligación de relacionarse electrónicamente con las AA.PP, las notificaciones electrónicas o el registros electrónicos de apoderamientos, entre otros. Así mismo, el [artículo 36 LRBRL](https://www.boe.es/buscar/act.php?id=BOE-A-1985-5392) indica que, son competencias propias de las Diputaciones Provinciales la prestación de los servicios de administración electrónica y la contratación centralizada en los municipios con población inferior a 20.000 habitantes. Es por ello, que los sistemas informáticos que ofrecen los servicios de sede electrónica de cada una de estas Administraciones, ofrezcan la seguridad y robustez adecuada para proteger la información manejada.

Este estudio presenta un estado básico de la seguridad de las sedes electrónicas de las diferentes Diputaciones Provinciales de España centrado en configuración de protocolos de comunicaciones, cifrados utilizados y otros parámetros. Se plantea desde un punto de vista general, meramente estadístico, sin entrar en el detalle de configuraciones particulares. 

Se muestran los datos de diputaciones provinciales en las provincias de las comunidades autónomas de Galicia, Aragón, Cataluña, Comunidad Valenciana, Castilla y León, Castilla-La Mancha, Extremadura y Andalucía. Así mismo, se han incluido los datos de las diputaciones forales del País Vasco. Para un estudio futuro se considerarán los cabildos (Comunidad autónoma de Canarias) y los Consejos Insulares (Comunidad Islas Baleares).

| COMUNIDAD AUTÓNOMA   | Nº Diputaciones |
|---------------------:|:---------------:|
| ANDALUCIA            | 8               |
| ARAGON               | 3               |
| CASTILLA Y LEON      | 9               |
| CASTILLA\-LA MANCHA  | 5               |
| CATALUÑA             | 4               |
| COMUNIDAD VALENCIANA | 3               |
| EXTREMADURA          | 2               |
| GALICIA              | 4               |
| PAIS VASCO           | 3               |

Otras comunidades autónomas uniprovinciales como, el Principado de Asturias, Cantabria, Comunidad de Madrid, Región de Murcia, Navarra o La Rioja, no están representadas en el estudio dado que no poseen Diputación Provincial. Del mismo modo, las ciudades autónomas de Ceuta y Melilla, donde las competencias propias de las Diputaciones son asumidas por el propio gobierno y asamblea autonómica tampoco aparecen en el estudio.

### Sedes electrónicas bajo HTTPS
Como era de esperar, en un entorno sensible como las sedes electrónicas de las Diputaciones Provinciales, la totalidad de las mismas ofrecen sus servicios bajo el protocolo HTTPS.

| Uso de HTTPS   | Sedes | %      |
|---------------:|:-----:|-------:|
| Configurado    | 41    | 100,0% |
| No configurado | 0     | 0,0%   |

Sin embargo, destaca que dos sedes (4,9%) no redirección automáticamente de HTTP a HTTPS.

| Redirección | Nº de Sedes | %     |
|-----------:|:-----------:|------:|
| Código 200  | 2           | 4,9%  |
| Código 30x  | 39          | 95,1% |

Así mismo, llama la atención la baja implantación de HSTS. HTTP Strict Transport Security (HSTS) es una política de seguridad web que permite a un servidor web imponer/forzar el uso de TLS para los User-Agent compatibles, como -por ejemplo- un navegador web. El HSTS permite una implementación más efectiva del TLS asegurando que toda la comunicación se lleve a cabo sobre una capa de transporte segura en el lado del cliente. En particular, el HSTS mitiga las variantes de los ataques de "hombre en el medio" (MiTM) en los que el TLS puede ser eliminado de las comunicaciones con un servidor, dejando al usuario vulnerable a mayores riesgos.

| HSTS           | Sedes | %     |
|---------------:|:-----:|------:|
| Configurado    | 3     | 7,3%  |
| No configurado | 38    | 92,7% |

Si bien, la configuración de este mecanismo de seguridad en la parte del servidor web no es complejo, tan solo tres sedes electrónicas lo tienen implementado a la hora de realizar el estudio.

### Server Signature
La firma del servidor (en inglés, Server Signature) es la identidad pública del servidor web. Contiene información sensible que -en general- como buena práctica de seguridad se suele desactivar para evitar la divulgación de las versiones de software utilizadas. Nueve de las sedes estudiadas no han devuelto ningún dato mientras que el resto mostraba la versión y software utilizado para servir los contenidos. Destaca el uso de servidores web Apache, en su rama 2.2 (6 sedes) y 2.4 (7 sedes), y del servidor web nginx (6 sedes). Así mismo, tres sedes todavía utilizan servidores web bajo Microsoft-IIS/7.5, ofrecidos en servidores con sistema operativo Windows Server 2008 R2, fuera de soporte desde enero de 2020.

| Aplicación          | FQDN |
|--------------------:|:----:|
| No Especificado     | 9    |
| Apache/2\.4         | 7    |
| nginx               | 6    |
| Apache/2\.2         | 6    |
| Apache\-Coyote/1\.1 | 5    |
| Microsoft\-IIS/7\.5 | 3    |
| Microsoft\-IIS/8\.5 | 3    |
| BigIP               | 2    |

### Certificados digitales

#### Entidades Emisoras (CA’s)

El prestador de Servicios de Confianza (PSC) Camerfirma, del grupo italiano Inforcert, con 16 sedes electrónicas (39%) ocupa un destacado primer puesto en certificados emitidos para Diputaciones Provinciales. Destaca el PSC vasco, Izenpe S.A., un proyecto de Autoridad Certificadora impulsado por el Gobierno Vasco y las Diputaciones Forales, que emite certificados para las tres diputaciones de la comunidad autónoma del País Vasco.

| Entidad Emisora     | Sedes | %     |
|--------------------:|:-----:|------:|
| AC Camerfirma S\.A  | 16    | 39,0% |
| DigiCert Inc        | 7     | 17,1% |
| FNMT\-RCM           | 5     | 12,2% |
| ACCV                | 4     | 9,8%  |
| IZENPE S\.A\.       | 3     | 7,3%  |
| Let's Encrypt       | 2     | 4,9%  |
| CATCert             | 2     | 4,9%  |
| Firmaprofesional    | 1     | 2,4%  |
| GoDaddy\.com, Inc\. | 1     | 2,4%  |

Si a nivel mundial, el auge de popularidad de la entidad Lets Encrypts, que emite certificados gratuitos, en los últimos meses ha sido destacada, en el ámbito de las Diputaciones, según los datos del estudio, tan solo está implantada en dos sedes electrónicas.

#### Tamaño de Clave

Respecto al tipo de clave usado en los certificados digitales, el 100% de las sedes electrónicas usan el algoritmo RSA. La mayoría de ellas, un 85,4%, utiliza un tamaño de clave de 2048bits, mientras que tan solo seis sedes optaron por un tamaño mayor de 4096 bits. Destaca -por su ausencia- el uso de claves con algoritmos de Curva Eliptica (ECDSA), que con menor número de bits ofrecen una seguridad y robustez de cifrado similar al algoritmo RSA, con mejor rendimiento. La compatibilidad de ECDSA con los actuales navegadores y sistemas operativos es amplia tanto en equipos PC como en dispositivos móviles.

| Key Size      | Sedes | %     |
|--------------:|:-----:|------:|
| RSA 2048 bits | 35    | 85,4% |
| RSA 4096 bits | 6     | 14,6% |

#### Registro CAA

En lo que respecta a la implantación de mecanismos de control de emisión de certificados, ninguna de las sedes del estudio implementa CAA. CAA (Certificate Authority Authorization) es un registro DNS que especifica aquella(s) CA(s) que pueden emitir un certificado digital para el nombre de dominio correspondiente. Los registros de CAA son verificados por las CA antes de emitir el certificado digital.

| CAA            | Sedes | %      |
|---------------:|:-----:|-------:|
| Configurado    | 0     | 0,0%   |
| No configurado | 41    | 100,0% |

#### Cadena de confianza

Relacionado con los certificados digitales, la configuración en la parte servidor de la cadena de confianza, según las buenas prácticas, debe ofrece el certificado final junto con la jerarquía de certificados de la CA emisora (sin agregar la CA raíz, o rootCA). Un 43,9% de las sedes (18 de ellas) muestran errores a la hora de enviar la cadena de confianza. Si bien esto no supone un error con impacto en los usuarios finales que acceden a las sedes, su correcta configuración haría más optimo el acceso a las mismas.

| Jerarquía   | Sedes | %     |
|------------:|:-----:|------:|
| Correcta    | 23    | 56,1% |
| Con errores | 18    | 43,9% |

##### Validación de certificados

En el inicio de la comunicación segura entre un cliente (navegador web) y el servidor web de la sede electrónica se realiza el proceso de validación del certificado digital facilitado por el servidor. Esta validación se puede realizar mediante protocolo OCSP o a través de listas CRL.

La opción más óptima para conocer el estado de revocación de un certificado digital consiste es configurar OCSP Stapling. En este caso, es el servidor quien realiza el proceso de validación del certificado, y el resultado se lo envía al cliente en la negociación inicial TLS, eliminando la necesidad de que los clientes se pongan en contacto con el CA.

| OCSP           | Sedes | %     |
|---------------:|:-----:|------:|
| Configurado    | 2     | 4,9%  |
| No configurado | 39    | 95,1% |

Tan solo dos sedes electrónicas tienen activado la opción de OCSP Stapling, funcionalidad que mejora la seguridad, el rendimiento y la privacidad.

#### Renovación de certificados

Respecto a la renovación de certificados digitales, se observó en el momento de realizar el estudio que, en dos sedes electrónicas, las fechas de expiración estaban a 4 y 17 días vista. Este dato indica una gestión incorrecta del ciclo de vida del certificado, donde las buenas prácticas indican una renovación del certificado 30 días antes de su caducidad, y en el caso de periodos cortos -como los emitidos por Lets Encrypts- pasados 2/3 del tiempo de vida.

### Protocolos y cifrados
#### Protocolos SSL/TLS

Por defecto, el protocolo criptográfico más utilizado en las sedes electrónicas es la versión 1.2 de TLS. Se ofrece en 36 sedes. En la parte positiva en el uso de protocolos por defecto, destacar que una de las sedes ya utiliza TLS v1.3. Mientras que, en el aspecto negativo, aún cuatro sedes no ofrecen más allá de TLS v1.0, un protocolo que apareció en 1999, y que posee múltiples vulnerabilidades de seguridad que se desaconseja su uso hoy en día.

| Protocolo por defecto | Sedes | %     |
|----------------------:|:-----:|------:|
| TLS1\.0               | 4     | 9,8%  |
| TLS1\.2               | 36    | 87,8% |
| TLS1\.3               | 1     | 2,4%  |

Si bien TLS v1.2 es el protocolo por defecto negocia en un 87,8% de los casos, el uso de protocolos depreciados y/o obsoletos en las configuraciones es aún amplio. Tan solo seis sedes ofrecen nada más que TLS v1.2, mientras que la mayoría (25 sedes) ofrecen las tres versiones de TLS (v1, v1.1 y v1.2)

| Protocolos                       | Sedes | %     |
|---------------------------------:|:-----:|------:|
| TLSv1                            | 4     | 9,8%  |
| TLSv1\.2                         | 6     | 14,6% |
| TLSv1\.1 \+ TLSv1\.2             | 5     | 12,2% |
| TLSv1 \+ TLSv1\.1 \+ TLSv1\.2    | 25    | 61,0% |
| TLSv1\.1 \+ TLSv1\.2 \+ TLSv1\.3 | 1     | 2,4%  |

Las mejores prácticas de seguridad recomiendan eliminar las versiones TLS v1 y TLS v1.1, y por supuesto, descartar por completo el uso de versión obsoletas como SSL v2 y SSLv3. Llama la atención que estos últimos protocolos con serías vulnerabilidades de seguridad sigan ofreciéndose en alguna de las sedes estudiadas.

| Se ofrece | SSLv2 | SSLv3 |
|-----------|-------|-------|
| NO        | 40    | 35    |
| SI        | 1     | 6     |

#### Conjunto de Cifrados (Ciphersuite)

Tras el protocolo, el tipo de cifrado (ciphersuite) constituye un parámetro fundamental para la seguridad de la comunicación entre el servidor y el cliente ya que se encarga del cifrado final de los datos, un cifrado simétrico.

Uno de los parámetros que refuerza el concepto de seguridad consiste en que el servidor fuerce su lista de ciphers en la negociación con el cliente; y no al revés. De esta forma se evita que un cliente quiera negociar con un cifrado débil antes que con uno más fuerte. En el estudio de las sedes, aún diez de ellas no fuerzan en sus configuraciones que sea el servidor quien negocie la lista de ciphersuites.

| Orden cipher | Sedes | %     |
|-------------:|:-----:|------:|
| Servidor     | 31    | 24,4% |
| Cliente      | 10    | 75,6% |

Las últimas tendencias marcan el uso de cifrados fuertes con modos de operación en bloques (AEAD). Un total de 34 sedes ofrecen este tipo de cifrado seguro, mientras que siete sedes no lo soportan en sus configuraciones. 

| Tipo de cifrados         | Se ofrece | No |
|-------------------------:|:---------:|---:|
| Strong \(AEAD ciphers\)  | 34        | 7  |
| Medium                   | 40        | 1  |
| Low                      | 11        | 30 |
| 3DES\_IDEA               | 22        | 19 |
| aNULL \(No Encr/noAuth\) | 2         | 39 |

Destaca negativamente el uso de protocolos aNULL, que no aportan ni cifrado ni autenticación) en dos sedes, y el uso casi extendido de cifrados 3DES_IDEA y LOW (cifrados del tipo RC2, RC4 o DES), que verdaderamente, para la negociación con el actual parque de clientes susceptibles de conectar con una sede electrónica, no serían necesarios.

El orden de los cifrados más usados sería el siguiente:
| ORDEN | Sedes | CIPHER\_Hex   | CIPHER\_NAME                                 |
|------:|:-----:|:--------------|:---------------------------------------------|
| 1     | 27    | cipher\_xc030 | TLS\_ECDHE\_RSA\_WITH\_AES\_256\_GCM\_SHA384 |
| 2     | 26    | cipher\_xc028 | TLS\_ECDHE\_RSA\_WITH\_AES\_256\_CBC\_SHA384 |
| 3     | 24    | cipher\_xc014 | TLS\_ECDHE\_RSA\_WITH\_AES\_256\_CBC\_SHA    |
| 4     | 20    | cipher\_x9f   | TLS\_DHE\_RSA\_WITH\_AES\_256\_GCM\_SHA384   |
| 5     | 11    | cipher\_x6b   | TLS\_DHE\_RSA\_WITH\_AES\_256\_CBC\_SHA256   |


Es curioso que a nivel de cifrado simétrico prevalece AES de 256 bits respecto a AES-128 bits, cuando con 128 bits ofrece un nivel de seguridad suficiente con un mejor rendimiento. 

### Cabeceras de Seguridad

Para la mejora de la seguridad de sitios webs, existen una serie de cabeceras de respuesta HTTP relacionadas con la seguridad que aportan niveles adicionales de protección. Una práctica recomendada consiste en implementar este tipo de cabeceras, siempre que sea posible. Servicios online gratuitos como [Security Headers](https://securityheaders.com/) proporciona un mecanismo para evaluar el estado actual del servidor, y desplegar aquellas cabeceras pendientes.

| Grado | Sedes | %     |
|------:|:-----:|------:|
| A     | 1     | 2,4%  |
| B     | 1     | 2,4%  |
| C     | 6     | 14,6% |
| D     | 8     | 19,5% |
| F     | 20    | 48,8% |
| R     | 5     | 12,2% |

Casi la mitad de las sedes estudiadas, el 48,8%, obtienen un grado F (Fail) en su puntuación; es decir, no implementan cabeceras de seguridad alguna. Tan solo seis sedes (14,6%) incluye en su configuración al menos cuatro cabeceras para alcanzar el grado C, que indica un nivel aceptable de seguridad en ese aspecto.

Las cabeceras de seguridad más utilizadas se muestran en la siguiente table:

| Cabecera                    | Usos |
|----------------------------:|:----:|
| X\-Content\-Type\-Options   | 14   |
| X\-XSS\-Protection          | 14   |
| X\-Frame\-Options           | 13   |
| Strict\-Transport\-Security | 10   |
| Referrer\-Policy            | 3    |
| Content\-Security\-Policy   | 1    |

### Herramientas y documentos

Para la obtención de los datos necesarios para realizar el estudio se han utilizado las siguientes herramientas:

- Script SSL Certificate Check - http://prefetch.net/code/ssl-cert-check 
- Script testssl.sh-3.0 – https://github.com/drwetter/testssl.sh
- SSL labs Test - https://www.ssllabs.com/ssltest/
- Hardenize - https://www.hardenize.com/
- Immuniweb SSL Security Test - https://www.immuniweb.com/ssl/
- Security Headers - https://securityheaders.com/
- Lista Ciphersuites en Hex - https://testssl.sh/openssl-iana.mapping.html
- Security/Server Side TLS - https://wiki.mozilla.org/Security/Server_Side_TLS
- Mozilla SSL Configuration Generator - https://ssl-config.mozilla.org/
- OWASP TLS - https://cheatsheetseries.owasp.org/cheatsheets/TLS_Cipher_String_Cheat_Sheet.html

### Anexo 1 - Sedes electrónicas de Diputaciones Provinciales

| DIPUTACION                             | PROVINCIA   | COMUNIDAD            |
|----------------------------------------|-------------|----------------------|
| ov\.dipalme\.org                       | ALMERIA     | ANDALUCIA            |
| sede\.dipucadiz\.es                    | CADIZ       | ANDALUCIA            |
| www\.dipucordoba\.es                   | CORDOBA     | ANDALUCIA            |
| sede\.dipgra\.es                       | GRANADA     | ANDALUCIA            |
| sede\.diphuelva\.es                    | HUELVA      | ANDALUCIA            |
| sede\.dipujaen\.es                     | JAEN        | ANDALUCIA            |
| sede\.malaga\.es                       | MALAGA      | ANDALUCIA            |
| sedeelectronicadipusevilla\.es         | SEVILLA     | ANDALUCIA            |
| sede\.dphuesca\.es                     | HUESCA      | ARAGON               |
| 236ws\.dpteruel\.es                    | TERUEL      | ARAGON               |
| dpz\.sedelectronica\.es                | ZARAGOZA    | ARAGON               |
| diputacionavila\.sedelectronica\.es    | AVILA       | CASTILLA Y LEON      |
| sede\.diputaciondeburgos\.es           | BURGOS      | CASTILLA Y LEON      |
| sede\.dipuleon\.es                     | LEON        | CASTILLA Y LEON      |
| sede\.diputaciondepalencia\.es         | PALENCIA    | CASTILLA Y LEON      |
| sede\.diputaciondesalamanca\.gob\.es   | SALAMANCA   | CASTILLA Y LEON      |
| sedeelectronica\.dipsegovia\.es        | SEGOVIA     | CASTILLA Y LEON      |
| portaltramitador\.dipsoria\.es         | SORIA       | CASTILLA Y LEON      |
| www\.sede\.diputaciondevalladolid\.es  | VALLADOLID  | CASTILLA Y LEON      |
| diputaciondezamora\.sedelectronica\.es | ZAMORA      | CASTILLA Y LEON      |
| sede\.dipualba\.es                     | ALBACETE    | CASTILLA\-LA MANCHA  |
| sede\.dipucr\.es                       | CIUDAD REAL | CASTILLA\-LA MANCHA  |
| sede\.dipucuenca\.es                   | CUENCA      | CASTILLA\-LA MANCHA  |
| ofv\.dguadalajara\.es                  | GUADALAJARA | CASTILLA\-LA MANCHA  |
| diputacion\.toledo\.gob\.es            | TOLEDO      | CASTILLA\-LA MANCHA  |
| seuelectronica\.diba\.cat              | BARCELONA   | CATALUÑA             |
| seu\.ddgi\.cat                         | GERONA      | CATALUÑA             |
| seuelectronica\.diputaciolleida\.cat   | LERIDA      | CATALUÑA             |
| seuelectronica\.dipta\.cat             | TARRAGONA   | CATALUÑA             |
| diputacionalicante\.sedelectronica\.es | ALICANTE    | COMUNIDAD VALENCIANA |
| dipcas\.sedelectronica\.es             | CASTELLON   | COMUNIDAD VALENCIANA |
| www\.sede\.dival\.es                   | VALENCIA    | COMUNIDAD VALENCIANA |
| sede\.dip\-badajoz\.es                 | BADAJOZ     | EXTREMADURA          |
| sede\.dip\-caceres\.es                 | CACERES     | EXTREMADURA          |
| sede\.dacoruna\.gal                    | LA CORUÑA   | GALICIA              |
| www\.sede\.deputacionlugo\.org         | LUGO        | GALICIA              |
| sede\.depourense\.es                   | ORENSE      | GALICIA              |
| sede\.depo\.gal                        | PONTEVENDRA | GALICIA              |
| e\-s\.araba\.eus                       | ALAVA       | PAIS VASCO           |
| egoitza\.gipuzkoa\.eus                 | GIPUZCOA    | PAIS VASCO           |
| www\.ebizkaia\.eus                     | VIZCAYA     | PAIS VASCO           |
