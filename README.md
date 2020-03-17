## Building

### Docker

In order to run this application you will need an installation of `docker` including the command `docker-compose`.

One way to install docker is to get a copy of docker desktop. Below are links to instructions for installing docker desktop on mac and windows.
- [Installation instructions on windows](https://docs.docker.com/docker-for-windows/)
- [Installation instructions on mac](https://docs.docker.com/docker-for-mac/install/)

### Environment

To succesfully run the project, various secret values and configuration options need to be defined in two seperate `.env` files for the client (`client.env`) and for the server (`server.env`).

The files will be formatted as so*:

`client.env`
```
GOOGLE_CLIENT_ID=(YOUR PROJECTS CLIENT ID)
```

`server.env`
```
SESSION_SECRET=(YOUR CHOSEN SESSION SECRET)
GOOGLE_CLIENT_ID=(YOUR PROJECTS CLIENT ID)
```

*(each key value pair should be on one line each)

The **session secret** can be arbitraily chosen (but should be secure in the same way a password should be) however the **google client id** must be associated with a valid google api console project. In order to create a project visit the [google API developer console](https://console.developers.google.com/?pli=1) and create a project. Once a project is created you can find/create an **OAuth 2.0 Client ID** on the `Credentials` page which you can then add to both `.env` files.

Ensure that both `.env` files are in the same repository as the source code, i.e alongside this README file.

### Building

To build the project, ensure your *current directory* is the repository containing the source code and the `docker-compose.yml` file. Then run

```bash
docker-compose build
```

followed by

```bash
docker-compose up
```

You will then be informed where the project is being hosted. By default it will be hosted on port 1234. This can be modified by changing the `client.ports` property in the `docker-compose.yml` from `"1234:1234"` to `"1234:(your preferred port here)"`