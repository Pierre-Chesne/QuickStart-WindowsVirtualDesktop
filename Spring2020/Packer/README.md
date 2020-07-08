# Création d'une "Golden Image" pour Windows Virtual Desktop
Exemple de configuration d'un fichier de création d'une "Golden Image" avec Packer (Hashicorp).<br/>
Contenue de l'image:<br/>
- Windows 10 MultiUser avec Office 365
- Installation de FSLogix avec les paramétrages de la base de registre Windows (Profiles Enabled;DeleteLocalProfileWhenVHDShouldApply;VHDLocations)
- Installation de VLC

Prérequis: <br/>
1 - Creation d'un Service Principal Name<br/>
Exemple en Azure CLI: ``az ad sp create-for-rbac --name PackerServicePrincipal``<br/>
Récupérer : Application (client) ID - Password - TenantID<br/>
Il faudrat également l'id de l'abonnement<br/>
2 - Installer Packer<br/>
https://www.packer.io/<br/>
3 - Ecrire le fichier de configuration Packer <br\>
Voir l'exemple Wvd-Image.json
4 - Construire l'image <br/>
Exemple : ``packer build .\Wvd-Image.json`` <br/>




