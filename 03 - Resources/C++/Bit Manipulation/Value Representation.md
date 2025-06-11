The subset of the [[Object Representation]] bits that encode the value of the object.

> If you have a `struct`, its **object representation** includes **all the bits** used to store it — including any **padding bits** added for alignment or spacing.

> The **value representation** includes **only the bits that store the values of the struct's members** — not the padding bits.

Bits in the object representation of a type or object that are not part of the value representation are _padding bits_.
___
Tags : #programming #cpp 