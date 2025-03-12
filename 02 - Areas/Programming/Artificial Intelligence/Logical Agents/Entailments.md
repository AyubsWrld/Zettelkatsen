Let’s say we have the following knowledge base (**KB**):

1. "All humans are mortal." (**A: Human(x) → Mortal(x)**)
2. "Socrates is a human." (**B: Human(Socrates)**)

From these statements, we can **logically infer**:  
**"Socrates is mortal."** (**Mortal(Socrates)**)

This means **KB entails B**, written as:  
**KB ⊨ Mortal(Socrates)**

✔ Since **Mortal(Socrates) must be true** in all models where "All humans are mortal" and "Socrates is human" are true, this is a **valid entailment**.
___
Tags : #programming #artificial-intelligence