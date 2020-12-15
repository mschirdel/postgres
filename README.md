# **PostgreSQL Server**


Prerequisites: Docker Engine.

## **Run the Server**
check the `docker-compose.yaml` if you'd need to have different username and password and db name other than `My*` please edit those. 
To run the server then you need this command. 
`$ docker-compose up` <br/> 

**_If this is the first time using Docker, install the Docker Desktop._**<br/>
Check your Docker Desktop version by clicking the the Docker Desktop icon in the taskbar to show the drop-down menu, and open <code>About Docker Desktop</code>.<br/> This will show the <code>Docker Desktop</code> version in the middle of the window, the <code>Engine</code> version below, and other version numbers.<br/>Compare your version numbers to the following:<br/>
- <code>Recommended Docker Desktop version: 2.1.0</code><br/>
- <code>Recommended Engine version: 19.03</code>

If you have version(s) lower than the above version numbers, update Docker Desktop. This can easily be done by clicking the Docker Desktop icon in the taskbar to show the drop-down menu, then <code>Check for Updates</code>.


## **Some Docker Tips**
- **Stop a container:** 
  - Use <code>docker ps</code> to list running containers.
  - Copy the name of the Image (_under the Names column_)
  - Use the Terminal command <code>docker stop your-image-name</code>
  - When the container is successfully stopped, Docker will print the name of the Image in the terminal
- **Remove unused containers:** 
  - Use the Terminal command <code>docker system prune</code> (followed by <code>y</code> to confirm) to remove all of the old and unused containers.
  - It is recommended you do this after `docker stop`ing a container
  - This will _NOT_ remove the Images, which means you only need to enter your specific <code>docker run ... </code> command that you used in [Run Server Docker Image](#run-server-docker-image) when you want to use the simulator again.
- **List images built successfully:** use the Terminal command <code>docker images</code>.
- **If your container is spontaneously dying,** it may be due to the memory allocation given to Docker.
    - <code>Docker Desktop -> Preferences -> Advanced</code> and adjust the slider settings to allow Docker to use more resources.
### _Example of Stopping Docker Container_
  - <code>docker ps</code>: list running containers
  - copy the simserver container named <code>nifty_murdock</code> listed in the _last column, Names_ 
  - <code>docker stop nifty_murdock</code>: stops the container
  - <code>docker system prune</code> then <code>y</code> when asked to confirm: deletes old container and reclaims space
(Terminal responses are green)

```diff
    username:/ username$ docker ps
+    CONTAINER ID      IMAGE        COMMAND              CREATED          STATUS          PORTS                      NAMES
+    119de3df985d      simserver    "python server.py"   14 seconds ago   Up 12 seconds   0.0.0.0:5000->5000/tcp     nifty_murdock

    username:/ username$ docker stop nifty_murdock
+    nifty_murdock

    username:/ username$ docker system prune
+    WARNING! This will remove:
+    - all stopped containers
+    - all networks not used by at least one container
+    - all dangling images
+    - all dangling build cache

    Are you sure you want to continue? [y/N] y
+    Deleted Containers:
+    119de3df985ddce4bee7d12899896ec66a72c9768cebe347df8303eba38e71ad
```

## More Info on Docker Image with Postgres
    <https://linuxhint.com/run_postgresql_docker_compose/>