# DCS Vanilla: DCS Blanked Out

## Prerequisites

Before you begin, ensure you have the following installed on your system:

- [Git](https://git-scm.com/)
- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)

You can verify the installation by running the following commands:

```sh
git --version
docker --version
docker compose version
```
## Running DCS Vanilla using Docker

To run DCS Vanilla using Docker, follow these steps:

1. **Clone the repository:**
    ```sh
    git clone https://github.com/unfoldingWord-box3/dcs-vanilla.git
    ```

2. **Navigate to the repository directory:**
    ```sh
    cd dcs-vanilla
    ```

3. **Start the Docker container:**
    ```sh
    docker compose up -d
    ```

4. **Access DCS Vanilla:**
    Open your web browser and go to [http://localhost:3000](http://localhost:3000).

5. **Sign in as root:**
    ```markdown
    Username: root
    Password: password
    ```

## Troubleshooting

If you encounter any issues, check the Docker container logs:

```sh
docker logs dcs
```

### Stopping the Docker Container

To stop the Docker container, run:
```sh
docker compose down
```
## Customizing the Docker Compose File

If you need to customize the `docker-compose.yaml` file, follow these steps:

1. **Open the `docker-compose.yaml` file:**
    ```sh
    nano docker-compose.yaml
    ```

2. **Modify the necessary configurations:**
    - Change the port mappings under the `ports` section to use a different port.
    - Adjust environment variables as needed.
    - Add or remove services according to your requirements.

3. **Save and close the file:**

4. **Restart the Docker container to apply changes:**

    ```sh
    docker compose down
    docker compose up -d
    ```

## DCS/Gitea Configuration

You can configure the application by editing the `app.ini` file located in the `gitea/gitea/conf` directory.

    nano gitea/gitea/conf/app.ini

Template files you can change (which blank out DCS-specific branding, such as home page and logo) are in the `templates` directory of the `gitea/gitea` directory. Removing them would actually revert back to using DCS's branded home page and logo.

For example:

    nano gitea/gitea/templates/home.tmpl
    nano gitea/gitea/templates/custom/extra_tabs.tmpl

Logos and favicon can be changed here in the `assets/img` direction of `gitea/gitea/public`:

    cd gitea/gitea/public/assets/img/

## Additional Information

For more information on how to run DCS Vanilla with Docker, including with various DB flavors, visit the [Gitea Docker installation documentation](https://docs.gitea.com/installation/install-with-docker).

To learn how to customize the templates and images overriding both Gitea & DCS templates and logos, refer to the [Gitea customization documentation](https://docs.gitea.com/administration/customizing-gitea).

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.