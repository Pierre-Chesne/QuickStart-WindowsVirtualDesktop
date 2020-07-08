# Création d'une "Golden Image" pour Windows Virtual Desktop
Exemple d'un fichier de configuration pour la création d'une "Golden Image" avec Packer (Hashicorp).<br/>
Contenue de l'image:<br/>
- Windows 10 MultiUser avec Office 365
- Installation de FSLogix avec les paramétrages de la base de registre Windows (Profiles Enabled;DeleteLocalProfileWhenVHDShouldApply;VHDLocations)
- Installation de VLC

Prérequis: <br/>
1. Creation d'un Service Principal Name<br/>
Exemple en Azure CLI: ``az ad sp create-for-rbac --name PackerServicePrincipal``<br/>
Récupérer : Application (client) ID - Password - TenantID<br/>
Il faudrat également l'id de l'abonnement<br/>
2. Installer Packer<br/>
https://www.packer.io/<br/>
3. Ecrire le fichier de configuration Packer <br/>
Voir l'exemple ``.\Wvd-Image.json``<br/>
4. Construire l'image <br/>
Exemple : ``packer build .\Wvd-Image.json``<br/>


Explications des variables:<br/>

``"variables": {  
        "sp_Id": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx", //ID du "Servive Principal Name"         
        "sp_Secret": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx", //Secret du "Servive Principal Name"
        "tenant_Id": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx", //Id du "Tenant AD"
        "subscription_Id": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx", //ID de l'abonement

        "image_Rgname":"RG-Image-Packer", //Resource group de l'image
        "image_Name":"WVD-FSlogix-VLC-Image-v0.5-test", //Nom de l'image
        "image_location":"East US 2", //Region de l'image
        "image_size":"Standard_D2s_v3", // Template matériel de l'image   

        "Os":"Windows", // Type d'OS
        "Publisher":"MicrosoftWindowsDesktop", //Publisher de l'image
        "Offer":"office-365", //Famille de l'OS
        "SKU":"19h2-evd-o365pp", // Image

        "dept_tag":"Engineering", //Tag 1
        "task_tag":"Image deployment", //Tag 2

        "Share_Profils_location":"storagefslogix.file.core.windows.net", //paramétrage de FSLogix (ex:\\storagefslogix.file.core.windows.net)
        "Share_Profils_folder":"profiles" //paramétrage de FSLogix (ex: \\storagefslogix.file.core.windows.net\profiles)
    }``
