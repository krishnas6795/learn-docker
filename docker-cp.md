# Docker cp command
You can copy files between the host machine and a Docker container using the docker cp command. Here's how you can do it:

```bash
docker cp <host_path> <container_id>:<container_path>
```
Example:
```bash
docker cp /path/to/local/file.txt my_container:/app/file.txt
```

This command will copy the file file.txt from the host machine to the /app directory inside the container named my_container.

```bash
docker cp <container_id>:<container_path> <host_path>
```
Example:
```bash
docker cp my_container:/app/file.txt /path/to/local/file.txt
```

This command will copy the file file.txt from the /app directory inside the container named my_container to the /path/to/local/ directory on the host machine.

- Make sure to replace <host_path>, <container_id>, <container_path> with your actual paths and container ID.
