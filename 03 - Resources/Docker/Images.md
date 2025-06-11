> *A **Docker image** is a **read-only, reusable template** that defines everything needed to run a container. You can think of it like a **snapshot of a filesystem and application environment**.*

It contains all the relevant context needed to run an application. Images are built using [[Layers]] where each layer is **cached**, **shared**, and **immutable**. 

#### A `dockerfile` contains: 

- **Base OS layer** (e.g., Ubuntu, Alpine)

- **App code** (e.g., Python, Node.js app)

- **Dependencies** (e.g., libraries, packages)

- **Environment settings** (e.g., env vars, config files)

- **Instructions** from a Dockerfile (e.g., `RUN`, `COPY`, `CMD`)

```dockerfile
FROM node:18        # base image (layer 1)
WORKDIR /app        # layer 2
COPY . .            # layer 3
RUN npm install     # layer 4
CMD ["node", "index.js"]  # layer 5
```

An image is to a container what a recipe is to a dish. 

#### Two important principles
___

- **Docker Images are Immutable**: Anytime we create a docker image it is set in stone. We can only add layers to it after it has been created. That is you can only make a new image or add changes on top of it.
- Container images are composed of layers. Each layer represents a set of file system changes that add, remove, or modify files.

___
Tags: #docker