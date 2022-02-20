# Music Tube

A music video display application which periodically updated the videos from the YouTube Data API.

This repo is just a workflow with [docker-compose.yml](/docker-compose.yml) to run the Music Tube server with a database connection.

## Images

+ Official image for MongoDB: [mongo](https://hub.docker.com/_/mongo)
+ Music Tube server: [jaypsy/music-tube-server](https://hub.docker.com/r/jaypsy/music-tube-server)   
  Source: [j-tesla/music-tube-server](https://github.com/j-tesla/music-tube-server)

For exact dependencies used frontend and backend, checkout [frontend's package.json](/app/frontend/package.json) and [backend's package.json](/app/backend/package.json)

## Setup

### Prerequisites

Git, [Docker](https://docs.docker.com/get-docker/), [Docker Compose](https://docs.docker.com/compose/install/), Google Account

### Getting API key for YouTube Data API

1. Create a project in the [Google Developers Console](https://console.developers.google.com/) and [obtain authorization credentials](https://developers.google.com/youtube/registering_an_application) so your application can submit API requests.
2. After creating your project, make sure the YouTube Data API is one of the services that your application is registered to use:
    1. Go to the [API Console](https://console.developers.google.com/) and select the project that you just registered.
    2. Visit the [Enabled APIs page](https://console.developers.google.com/apis/enabled). In the list of APIs, make sure the status is **ON** for the **YouTube Data API v3**.

### Installation

1. Clone this repo ([How?](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository))
2. Change director into the root of the repo
3. Create `.env` file with required environment variables
    1. Copy [example.env](/example.env)

        ```sh
        cp example.env .env
        ```

    2. Fill .env with environmental variables to be used. (`YOUTUBE_API_KEY` should the API key previously obtained)
4. Run:

    ```sh
    docker-compose up
    ```

    To run in detached mode:

    ```sh
    docker-compose up -d
    ```

### Usage

1. Dashboard is avaialble at root url
2. API endpoint for videos at `/api/videos`
3. To know the port at which the servert is running,
    1. Run

        ```sh
        docker ps
        ```

    2. Look for Image named `music-tube_app`.

    If PORTS field of `music-tube_app` image is soemthing like `0.0.0.0:80->8080/tcp, :::80->8080/tcp`
    Then you can access the server at **<http://0.0.0.0:80/>**
