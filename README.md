# Copying the encrypted file from Docker host to the Running Container

To copying the encrypted file from App Server 2 (the Docker host) to the ubuntu\_latest container without modifying it, run the following command:

`docker cp /tmp/nautilus.txt.gpg ubuntu_latest:/home/`

Verification Step:

To confirm the file was copied successfully, you can list the files in the `/home/` directory inside the container:

`docker exec ubuntu_latest ls -l /home/`

#### Breakdown

* Source: `/tmp/nautilus.txt.gpg` (This is the path on the host).
* Destination: `ubuntu_latest:/home/` (This targets the container named `ubuntu_latest` and places the file in the `/home/` directory).
* Integrity: The `docker cp` command performs a bit-for-bit copy, so the GPG encryption remains intact and the file is not modified.
