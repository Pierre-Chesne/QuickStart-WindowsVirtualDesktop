# Création d'une "Golden Image" pour Windows Virtual Desktop
Exemple de configuration d'un fichier de création d'une "Golden Image" avec Packer (Hashicorp).<br/>
https://www.packer.io/<br/>
Contenue de l'image:<br/>
- Windows 10 MultisUser avec Office 365
- Installation de FSLogix avec les paramétrages de la base de registre
- Installation de VLC

Exemple : ``packer build Wvd-Image.json``