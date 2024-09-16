Libraries , similar to a [[Framework]] , are just code written by a different person used to streamline the process of solving a problem . for example , pretend you wanted to interact with strings so you create a library of functions which allow you to interact with strings . 


```js
function getWords(str) {
   const words = str.split(' ');
   return words;
}
function createSentence(words) {
   const sentence = words.join(' ');
   return sentence;
}
```
With this we have just created a library . A library is like going to the grocery store for food  when you want to cook a meal . You don't have to grow an onion from scratch , you can just go to the store and purchase an onion . This is different from a framework , as a framework would be creation of the recipe itself . You have set points wherein you can control the input , yet to produce the final product the power lies within the recipe itself ; That is you **Must** follow it to an extent . 

#### The Technical Difference

The technical difference between a framework and library lies in a term called [[Inversion of Control]] . 