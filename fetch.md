# Pour toi Étudiant 1

le fetch est une fonction asynchrone qui permet d'appeler une autre machine, une api qui selon le retour nécessitera la gesiton des errerus ou la gestion des résultats. 

Pour cela le fetch peut avoir besoin de certains paramètre en entete et/ou en corps qu'on appelle header et body d'une requete. Pour consommer une ressource comme les endpoints d'API qui sont les routes d'une que tu as pu implémenter coté router. Le retour de la requete est appelé réponse. La réponse de la requete peut retourner également un code de status http qui categorise si une requete c'est bien passé par exemple, si une opération s'est bien déroulé ou pas, etc. https://en.wikipedia.org/wiki/List_of_HTTP_status_codes
On fait appelle a une ressource avec une methode get, post, put, delete selon que l'on ai implementer ces methodes dans l'API. par exemple on peut creer une resource via un appel GET, mais c'est plutot avec un POST que l'on crée un item dans une ressource.

un exemple sur router.get("/deck/add/:id", cardController.addCard);
ceci est une route /deck/add/:id 
c'est pour cela que l'entité, le composant qui définit les routes se nomme router, c'est a dire aiguilleur comme une aiguilleur de chemin de faire qui gere quel chemin prendre quand un train va passer.

tu trouveras dans ce fichier un exemple concret

Utile des liens vers la documentation de mozilla pour comprendre plus en details au besoin
https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch

https://developer.mozilla.org/en-US/docs/Web/API/fetch

hésite pas à me demander si tu as d'autres questions

# exemple de fetch, on va utiliser la methode fetch pour envoyer une requete au server de l'API pour utiliser la ressources necessaire, ici la resources deck

petite precision dans le router, il faudrait utiliser le verbe .post au lieu de .get

ce code sur dans ton router
router.get("/deck/add/:id" , deckController.addDeck);
devrait etre 
router.post("/deck/add/:id" , deckController.addDeck);

ensuite le code exemple pour appeler la route post /deck/add/:id


# le code
// définit une fonction asynchrone createDeck qui prend une url et une donnée par défaut au format objet
async function createDeck(url, data = {}) { 
  // appel de la ressource url avec fetch en utilisant
  const response = await fetch(url, {
    method: "POST", // avec la methode utilisée pour consommer la ressource
    mode: "cors", // permet de gerer l'appel a une ressoruce hors du domaine de la machine client, par exemple un site web utilise une api avec un autre nom de domaine
    headers: {
      "Content-Type": "application/json", // precise le format du flux ici json
    },
    body: JSON.stringify(data), // ici le body où l'on sérialise, convertit au format caractère
  });
  return response.json(); // parses JSON response into native JavaScript objects
}

postData("http://localhost:5432/deck/add/", { id: 42 }).then((data) => {
  console.log(data); 
});

# la serialization
la serialization est un procédé pour traduire un objet ou tableau en un format de chaine de caractere pour le transfert de donné à travers un réseau en utilisant JSON.stringify

on peut ensuite utiliser la deserialisation pour transformer une chaine de caractere en objet JSON ou tableau de donnée, en utilisant JSON.parse

pour en savoir plus
https://developer.mozilla.org/en-US/docs/Glossary/Serialization

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse