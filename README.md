### gqrx
[GQRX](https://gqrx.dk) SDR software running inside Docker

## Summary
1. Build a GQRX docker image.
2. Create a GQRX docker container.
3. Launch and start the GQRX container from the application menu.
4. When done with GQRX, closing the app will shutdown the container.

## Installation
1. Plug in your RTL-SDR dongle.
2. Clone the repository and run the setup script:

    ```bash
    git clone https://github.com/mikepaxton/gqrx.git
    cd gqrx
    sh run.sh
    ```
   If the image builds successfully, GQRX will start and present you with the application window. Close the application to complete the image build.

## Run docker compose up
Now, run docker compose up -d to create the container. We will later be launching the container from the applications launcher.

```bash
docker compose up -d
```
To be on the safe side lets make sure the DISPLAY environment variable is correctly set and the xhost command is run on your host machine to allow Docker to use your X server.
```bash
xhost +local:docker

```

## Add GQRX to the application menu
Now that we have the container working we can create an application launcher item.

First, make sure gqrx.desktop has the correct permissions.
Then, copy the gqrx.desktop file to its appropriate place.

```bash
chmod 644 gqrx.desktop
cp gqrx.desktop ~/.local/share/applications
```
1. Now, launch Menu Editor from the application launcher.
2. Create a new sub-menu and name it something like Ham Radio.
3. In the Menu Editor search field type gqrx.
4. Drag and drop GQRX into your newly created Ham Radio catagory.
5. Click Save and exit out of Menu Editor.

## Launch the application
Finally, from the application launcher, click on GQRX and let it launch.
It might take a few seconds for the docker container to start up
and the application to start.
