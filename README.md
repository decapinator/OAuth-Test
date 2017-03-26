Bienvenue dans l'application Java OAuth du développeur Intuit.

Cet exemple d'application est destiné à fournir un exemple fonctionnel de gestion d'OAuth.

**Conditons Préalables:**

• Dernière version de Java - Cet exemple utilise Java 1.7

• Apache Tomcat ou tout serveur Web (l'exemple est configuré pour s'exécuter sur le port 8080,
si vous utilisez un numéro de port différent, veuillez mettre à jour le code en conséquence)

• Pour l'implémentation Oauth, cet exemple utilise la bibliothèque de Java Signpost(https://code.google.com/p/oauth-signpost/)

• Compte Developer.intuit.com

• Une application sur developer.intuit.com et le jeton d'application, la clé de consommateur et le secret de consommateur associés.

**Instructions pour la première utilisation:**

• Cloner le repo GitHub dans votre espace de travail

• Configurer les jetons de l'application: accédez à votre application sur developer.intuit.com et copiez la clé du consommateur OAuth et le jeton du consommateur OAuth 

à partir "Keys tab". Ajoutez ces valeurs au fichier app.properties dans notre dossier OauthSample.

• Créez le code à l'aide de mvn install (à partir d'IDE ou à partir de l'invite de commande)

• Déployer le fichier généré sur le serveur Web.

**Exécutez l'application:**

• Lancez l'application-http://localhost:8080/OauthSample

• Connectez votre application à Quickbooks, en cliquant sur le bouton «Connexion à QuickBooks» et suivez les instructions à l'écran.

• Après avoir correctement connecté l'application à QuickBooks, vous pouvez afficher l'ID, 
le jeton Oauth et le secret Oauth dans les log de votre serveur.

• Vous allez être redirigé vers le findallcustomers.jsp qui effectue un appel au point d'extrémité du client QBO pour lire un 
enregistrement client (par Id).

**Structure du projet:**

• RequestTokenServlet.java: Servlet pour déclencher le flux Oauth, appelle le noeud final du jeton de demande.
La réponse est envoyée au CallBack Url de Oauth.

• AccessTokenServlet.java: Il s'agit de l'URL OauthCallback configurée dans app.properties. 

Lit les paramètres de HttpSession et appelle le point d'extrémité de jeton d'accès pour récupérer le jeton d'accès et le secret
• OauthUtils.java: Lit le fichier de propriétés

• app.properties: configurez la clé de consommateur, le secret, l'URL de rappel Oauth et l'URL QBO dans ce fichier

• index.jsp: Contient le code pour ajouter le bouton «Se connecter à QuickBooks».

• connect.jsp: Fermez le popup Oauth et redirigez-le vers findallcustomers.jsp

• findallcustomers.jsp: Code nécessaire pour appeler le point d'extrémité client QBO pour récupérer tous les clients
