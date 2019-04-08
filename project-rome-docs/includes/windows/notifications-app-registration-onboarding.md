### <a name="msa-and-aad-authentication-registration"></a><span data-ttu-id="0437f-101">MSA y registro de la autenticación de AAD</span><span class="sxs-lookup"><span data-stu-id="0437f-101">MSA and AAD Authentication Registration</span></span>

<span data-ttu-id="0437f-102">Registro de autenticación de cuenta de Microsoft (MSA) o Azure Active Directory (AAD) es necesario para todas las características del SDK que incluya las notificaciones, excepto para el uso compartido de Nearby API.</span><span class="sxs-lookup"><span data-stu-id="0437f-102">Microsoft Account (MSA) or Azure Active Directory (AAD) authentication registration is required for all features of the SDK including Notifications, except for the Nearby sharing APIs.</span></span> 

<span data-ttu-id="0437f-103">Si aún no tiene una MSA y desea usar uno, registrar en [account.microsoft.com](https://account.microsoft.com/account).</span><span class="sxs-lookup"><span data-stu-id="0437f-103">If you do not already have an MSA and wish to use one, register on [account.microsoft.com](https://account.microsoft.com/account).</span></span>

<span data-ttu-id="0437f-104">A continuación, si utilizas MSA como la autenticación y el marco de identidad para los usuarios, debe registrar la aplicación con Microsoft, siga las instrucciones de la [Portal de registro de aplicación](https://apps.dev.microsoft.com/) (si no tiene un Microsoft cuenta de desarrollador, debe crear una primera).</span><span class="sxs-lookup"><span data-stu-id="0437f-104">Next, if you are using MSA as the authentication and identity framework for your users, you must register your app with Microsoft by following the instructions on the [Application Registration Portal](https://apps.dev.microsoft.com/) (if you do not have a Microsoft developer account, you must create one first).</span></span> <span data-ttu-id="0437f-105">Debería recibir una cadena de identificador de cliente de la aplicación; Asegúrese de recordar la ubicación o guardar esto.</span><span class="sxs-lookup"><span data-stu-id="0437f-105">You should receive a client ID string for your app; make sure to remember the location or save this.</span></span> <span data-ttu-id="0437f-106">Más adelante se usará durante la incorporación de notificaciones de gráfico.</span><span class="sxs-lookup"><span data-stu-id="0437f-106">Later this will be used during Graph Notifications onboarding.</span></span> <span data-ttu-id="0437f-107">Tenga en cuenta que una aplicación mediante la autenticación de MSA debe estar registrada como una aplicación de SDK de Live, como se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="0437f-107">Note that an app using MSA authentication needs to be registered as a Live SDK application as shown below.</span></span>
<span data-ttu-id="0437f-108">![Portal de registro de aplicación](../../notifications/media/msa_app_registration/app_registration_portal.png)</span><span class="sxs-lookup"><span data-stu-id="0437f-108">![Application Registration Portal](../../notifications/media/msa_app_registration/app_registration_portal.png)</span></span>

<span data-ttu-id="0437f-109">Si está escribiendo una aplicación que usa AAD como cuenta profesional o educativa autenticación y cuentas marco de identidad, debe registrar la aplicación a través de [bibliotecas de autenticación de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) con el fin de obtener el identificador de cliente, como se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="0437f-109">If you're writing an app that uses AAD as work account or school account authentication and identity framework, you must register your app via [Azure Active Directory Authentication Libraries](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) in order to get the client ID, as shown below.</span></span> 
 <span data-ttu-id="0437f-110">![Portal de registro de AAD](../../notifications/media/aad_registration_portal/aad_registration_portal.png) al crear un nuevo registro de aplicación, hay algunos permisos necesarios para poder usar las notificaciones de Graph y otras capacidades de plataforma de dispositivo conectado.</span><span class="sxs-lookup"><span data-stu-id="0437f-110">![AAD Registration Portal](../../notifications/media/aad_registration_portal/aad_registration_portal.png) When creating a new app registration, there are a few permissions required in order to use Graph Notifications and other connected device platform capabilities.</span></span> <span data-ttu-id="0437f-111">Consulte a continuación.</span><span class="sxs-lookup"><span data-stu-id="0437f-111">Please see below.</span></span> 
<span data-ttu-id="0437f-112">![AAD Portal: configuración – requiere permisos de registro de](../../notifications/media/aad_registration_portal/aad_registration_portal_permissions.png)</span><span class="sxs-lookup"><span data-stu-id="0437f-112">![AAD Registration Portal – Setting – Required Permissions](../../notifications/media/aad_registration_portal/aad_registration_portal_permissions.png)</span></span>
* <span data-ttu-id="0437f-113">Agregar inicio de sesión de permiso de usuario que se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="0437f-113">Add user sign-in permission shown as below.</span></span>
<span data-ttu-id="0437f-114">![Permisos necesarios: perfil de usuario AAD](../../notifications/media/aad_registration_portal/permissions_1_user.png)</span><span class="sxs-lookup"><span data-stu-id="0437f-114">![Required Permissions – AAD User Profile](../../notifications/media/aad_registration_portal/permissions_1_user.png)</span></span>
* <span data-ttu-id="0437f-115">Agregar permisos de servicio de comandos para obtener información de dispositivo, que se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="0437f-115">Add Command Service permissions for device information, shown as below.</span></span>
<span data-ttu-id="0437f-116">![Permisos necesarios: los dispositivos](../../notifications/media/aad_registration_portal/permissions_2_devices.png)</span><span class="sxs-lookup"><span data-stu-id="0437f-116">![Required Permissions – Devices](../../notifications/media/aad_registration_portal/permissions_2_devices.png)</span></span>
* <span data-ttu-id="0437f-117">Agregue el permiso de Graph notificaciones en actividad fuente Service API, se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="0437f-117">Add Graph Notifications permission under Activity Feed Service APIs, shown as below.</span></span>
<span data-ttu-id="0437f-118">![Permisos necesarios: los dispositivos](../../notifications/media/aad_registration_portal/permissions_3_graph_notifications.png)</span><span class="sxs-lookup"><span data-stu-id="0437f-118">![Required Permissions – Devices](../../notifications/media/aad_registration_portal/permissions_3_graph_notifications.png)</span></span>
* <span data-ttu-id="0437f-119">Al final, si está escribiendo aplicaciones multiplataforma incluida una aplicación de UWP que se ejecutan en Windows, asegúrese de agregar permiso de servicio de notificación de Windows, que se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="0437f-119">At the end, if you are writing cross-platform application including an UWP app running on Windows, make sure to add Windows Notification Service permission, shown as below.</span></span> 
<span data-ttu-id="0437f-120">![Permisos necesarios: WNS](../../notifications/media/aad_registration_portal/permissions_4_wns_push.png)</span><span class="sxs-lookup"><span data-stu-id="0437f-120">![Required Permissions – WNS](../../notifications/media/aad_registration_portal/permissions_4_wns_push.png)</span></span>