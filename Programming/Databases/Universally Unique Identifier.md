### What is a UUID?

A **UUID (Universally Unique Identifier)** is a 128-bit value used to uniquely identify objects or entities in a distributed system. UUIDs are designed to be unique across both time and space, without requiring a central authority to manage the IDs.

UUIDs are commonly used in software development to uniquely identify database records, objects in a system, or users. They are particularly useful in distributed systems where coordination between multiple servers or components isn't feasible.

### Structure of a UUID:
A typical UUID looks like this: `550e8400-e29b-41d4-a716-446655440000`. It consists of 32 hexadecimal characters, split into five groups separated by hyphens (8-4-4-4-12 format).

### Types of UUIDs:
- **UUID Version 1**: Uses the current time and MAC address for uniqueness.
- **UUID Version 4**: Most commonly used; generates a random value for uniqueness.
- **UUID Version 5**: Uses a SHA-1 hash of a namespace identifier.

### UUID Characteristics:
- **Globally unique**: No need for a central authority.
- **128-bit size**: Provides over 340 undecillion possible values (2^128).
- **Non-sequential**: For most versions (e.g., version 4), UUIDs appear random and are not sequential.

### Notes on UUID:
1. **UUID is globally unique**: Used to uniquely identify resources in distributed systems without conflict.
2. **Format**: It is a 128-bit value represented in a 36-character string (8-4-4-4-12 format with hyphens).
3. **Common UUID Version**: 
   - **Version 4 (random)** is the most commonly used, and it generates random numbers for uniqueness.
4. **Uses**: Commonly used for database keys, user IDs, transaction IDs, and in many APIs.
5. **No central coordination**: UUIDs can be generated independently, making them ideal for systems where different entities need to create unique identifiers without coordination.
6. **Libraries**: Many programming languages provide libraries for generating UUIDs (e.g., `uuid` in JavaScript, `uuid` in Python).

UUIDs are widely used due to their simplicity and their ability to guarantee uniqueness across different systems and networks.

_____
Tags : #programming #databases 