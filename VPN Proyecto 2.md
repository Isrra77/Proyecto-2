# VPN Proyecto 2
## 7690-15-15766 Israel Morales

### Proceso de configuración y sus componentes para el servicio VPN

<p>Al configurar una cuenta en la plataforma de Microsoft Azure, primero se debe de configruar un grupo de recursos:</p>

![Resourdce Group](Imagenes/1.png "Resource group")

<p>Dentro de este grupo de recursos primero se gestiona los siguientes componentes:</P>

1. Virtual network
   - ![VN](Imagenes/2.png "Virtual Network")
   - Creando las siguentes subredes
   - ![VN](Imagenes/3.png "VN Subred")
   - Dando como parametro general
   - ![VN](Imagenes/4.png "VN Parametro")
2. Virtual network gateway
   - Esta configuración nos permitira habilitar el acceso por VPN 
   - ![VNG](Imagenes/5.png "Virtual network gateway")
   - Establecemos los parametros
   - ![VNG](Imagenes/6.png "Virtual network gateway")
   - Y nos asiganara los siguientes datos, incluyendo una IP pública 
   - ![VNG](Imagenes/7.png "Virtual network gateway")
   - Esta configuración también nos permitira la asignación automatica de IP (DHCP) y traducción de nombre de dominio (DNS)
3. Active directory
    - En este grupo de directorios configuramos usuarios, grupos, politicas de empresa, etc.
    - ![AAD](Imagenes/8.png "Azure Active Directory")
      - Usuarios
      - ![AAD](Imagenes/9.png "Azure Active Directory")
4. Azure VPN
    - Habilitamos el servicio de Azure VPN en nuestro active directory usando el enlace:
    - > https://login.microsoftonline.com/common/oauth2/authorize?client_id=41b23e61-6c1e-4545-b367-cd054e0ed4b4&response_type=code&redirect_uri=https://portal.azure.com&nonce=1234&prompt=admin_consent
    - El usuario con rol de Administrador global habilita el servicio
    - ![AVPN](Imagenes/10.png "Azure VPN")
    - Agregamos los usuarios que tendran permitido conectarse por VPN
    - ![AVPN](Imagenes/12.png "Azure VPN Usuarios")
    - Para luego configurar el parametro previo a generar el archivo xaml cargable en la computadora cliente
    - ![AVPN](Imagenes/11.png "Configuracion VPN")
    - Y podremos descargar el archivo de configuración que utilizaremos en cada equipo cliente
    - ![AVPN](Imagenes/13.png "VPN Archivo configuracion")

### Configuración VPN en equipo/servidor cliente

1. Accedemos a la tienda de microsoft para descargar la aplicación Azure VPN
    - ![AVPN](Imagenes/14.png "Azure VPN Microsoft Store")
2. Abrimos la aplicación y escogemos la opción de importar
    - ![AVPN](Imagenes/15.png "Azure VPN Importar")
3. Ubicamos el archivo xaml previamente descargado y aceptamos los parametros
4. Le daremos click al boton "Conectar" 
    - ![AVPN](Imagenes/16.png "Azure VPN Conectar")
5. Ingresaremos el usuario y clave designado en el active directory que cuenta con el permiso de conexión
6. Verificamos que estamos conectados
   - ![AVPN](Imagenes/17.png "Conectados")
