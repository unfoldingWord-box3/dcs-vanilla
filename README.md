# DCS Vanilla: DCS Blanked Out

## Table of Contents

- [Prerequisites](#prerequisites)
- [Installing DCS Vanilla using Docker](#installing-dcs-vanilla-using-docker)
- [Troubleshooting](#troubleshooting)
- [Stopping the Docker Container](#stopping-the-docker-container)
- [Customizing the Docker Compose File](#customizing-the-docker-compose-file)
- [DCS/Gitea Configuration](#dcsgitea-configuration)
- [Additional Information](#additional-information)
- [License](#license)

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
## Installing DCS Vanilla using Docker

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

5. **Initial Configuration your instance of DCS:**

    The first time you you go to [http://localhost:3000](http://localhost:3000) you will get the setup screen so you can configure your instance to your liking. This allso allows you to set up a database and an admin user. For other databases other than SQLite3, you will have to start a docker container for them too. See https://docs.gitea.com/installation/install-with-docker#databases for more details.

6. **Sign-in**

    Once you have filled out the Initial Configuration and installed Gitea, it will sign you in. You're set! Log out to see what the home page looks like (pretty boring!). See [DCS/Gitea Configuration](#dcsgitea-configuration) below for how to customize the home page, nav bar and logo.

## Troubleshooting

If you encounter any issues, tail the Docker container logs:

```sh
docker logs -f dcs
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

The homepage (removing it puts back the DCS home page you see at https://git.door43.org/about):

    nano gitea/gitea/templates/home.tmpl

The top navbar (removing it puts back the `Catalog` and `About DCS` links):

    nano gitea/gitea/templates/base/head_navbar.tmpl

The repo tabs (remove them to put back the `Metadata` and `Preview` tabs):

    nano gitea/gitea/templates/custom/extra_tabs.tmpl

Logo and favicon images (removing them will put back the green and black cirular DCS logo):

    cd gitea/gitea/public/assets/img/

## Additional Information

For more information on how to run DCS Vanilla with Docker, including with various DB flavors, visit the [Gitea Docker installation documentation](https://docs.gitea.com/installation/install-with-docker).

To learn how to customize the templates and images overriding both Gitea & DCS templates and logos, refer to the [Gitea customization documentation](https://docs.gitea.com/administration/customizing-gitea).

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.