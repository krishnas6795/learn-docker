# Multi-Stage Dockerfile Example

A multi-stage Dockerfile allows you to build an image using multiple build stages, where each stage can have its own dependencies and build environment. This helps in reducing the final image size by only including necessary artifacts and dependencies in the final stage.

## Example Dockerfile

```Dockerfile
# Stage 1: Build stage
FROM node:14 AS build
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .
RUN npm run build

# Stage 2: Production stage
FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

## In this example:
### Stage 1 (build stage):
- Uses the Node.js official image as the base image.
- Installs dependencies, copies source code, and builds the application.
### Stage 2 (production stage):
- Uses the Nginx official image as the base image.
- Copies the built artifacts from the build stage into the Nginx HTML directory.
- Exposes port 80 and starts the Nginx server.
## Benefits of Multi-Stage Builds
- Reduced Image Size: Only necessary artifacts and dependencies are included in the final image, resulting in a smaller image size.
- Improved Security: Unused dependencies and build tools are not present in the final image, reducing the attack surface.
- Cleaner Build Process: Separation of build stages keeps the Dockerfile organized and facilitates easier maintenance.
- Multi-stage builds are particularly useful for building applications with complex dependencies or multiple build steps. They help optimize Docker image sizes and improve overall performance and security.
