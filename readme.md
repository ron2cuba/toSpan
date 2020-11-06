# Function to surround a word in `$shop.name` in Prestashop by span

- You can select what you want by the selector in first argument
- You can select the word to surround in second argument
- You can add a class in third argument

Select a string, split it and check that every word exists if true surround by span

```js
/**
 * Select a string, split it and check that every word exists if true surround by span
 * insertion d'un span avec une classe pour un mot choisi dans le titre
 * @param {string} selector equivalent du queryselector
 * @param {string} wordToSurround mot a entourer d'une span
 * @param {string} spanClass classe pour la span
 */
const toSpan = (selector, wordToSurround, spanClass) => {
    //creation d'un catcher et stockage dans elt
    let elt = document.querySelector(selector);
    //si elt n'exixte pas on return
    if(!elt) return;

    // On explode le contenu de l'élément en tableau suivant les espaces
    let parts = elt.innerHTML.split(" ");

    //pour chaque mot de parts
    parts.forEach((word, index, array)=>{
        //si eltcontient le wordToSurround
        if(word == wordToSurround){
            //on prend le mot dans le tableau parts à l'index et on remplace par
            array[index] = `<span class="${spanClass}">${word}</span>`;
        }
    });
    //joindre les elements html (du tableau parts) dans elm
    // console.log(parts);

    elt.innerHTML = parts.join(" ");
}
toSpan("h1.h1", "word to surround", "class to add");
```