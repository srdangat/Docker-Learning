## What is Multi-Stage Dockerfile

A multi-stage Dockerfile is a technique used in Docker to build Docker images more efficiently by splitting the build process into multiple stages.
Each stage can have its own base image, dependencies,and tasks, and you can selectively copy artifacts from one stage to another.
The final image will only include the contents from the last stage, which helps reduce the size and complexity of the final image.

**Key Concepts**

1. **Stage Definition**
Each stage in a multi-stage Dockerfile is defined with a FROM statement. You can give each stage a name using the AS keyword, which makes it easier to reference in subsequent stages.

2. **Artifacts Transfer**
You can copy files or artifacts from one stage to another using the COPY --from=<stage> instruction. This allows you to transfer only the necessary files, such as compiled binaries, configuration files, or static assets, into the final image.

3. **Reduced Image Size**
By separating the build and runtime stages, you can avoid including unnecessary tools and dependencies (e.g., compilers, build tools) in the final image. This results in a smaller, more secure image.

4. **Optimization**
Multi-stage builds can significantly optimize Docker images by reducing layers, reusing intermediate layers, and reducing the build context. This approach also allows for better caching, which speeds up the build process.

**Benefits**

1. **Smaller Final Image** 
Only the final stage’s contents are included in the final image, reducing its size and surface area.

2. **Security** 
By excluding unnecessary build tools and libraries, the attack surface of the final image is reduced.

3. **Simplified Maintenance** 
Separate stages allow for clear separation of concerns, making the Dockerfile easier to maintain and extend.

4. **Build Efficiency** 
Docker caches each stage, so unchanged stages do not need to be rebuilt, making the overall build process faster.