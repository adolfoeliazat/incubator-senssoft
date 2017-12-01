How to Build Docker Containers
------------------------------

1. Install [``Docker``](http://docker.com) on your machine.
2. Install ``docker-compose`` in an virtual environment. Full instructions can be found [``here``](https://docs.docker.com/compose/install/).
    ```
    $ python3 -m venv env
    $ source env/bin/activate
    $ pip install docker-compose
    ```
3. Before launching the Docker containers, ensure your ``vm_max_map_count`` kernel setting is set to at least 262144.
   Visit [``Running Elasticsearch in Production mode``](https://www.elastic.co/guide/en/elasticsearch/reference/5.5/docker.html#docker-cli-run-prod-mode) for OS specific instructions.
   ```
   # For Linux systems
   $ sysctl -w vm.max_map_count=262144
   ```
4. Additionally, ensure that your kernel setting for the maximum number of file descriptions is at least 65536.
   ```
   # For Linux systems
   $ sysctl -w fs.file-max=65536
   ```
5. To build and run all ``Docker`` containers.
    ```
    $ docker-compose up -d
    ```
6. To run a specific ``Docker`` container.
    ```
    $ docker-compose up -d site
    # Note: site container is instrumented w/ userale; all userale logs will be sent to the
    # elasticsearch docker container.
    ```
7. Verify the deployment by navigating to ``Kibana`` in your favorite browser.
   Please note that Kibana can take upwards of several minutes to start, depending on the available system resources.
    ```sh
    http://localhost:5601
    ```

8. Stop all the containers.
    ```sh
    $ docker-compose stop
    ```
