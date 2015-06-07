# A container for running a Mumble server

## Usage

### Set up the data container

Create the data container:

    sudo docker create --name=mumble-data koinu/mumble-server-data

Use whatever means are appropriate to get your murmur.conf, ssl certificate files, and database into the data volume.

Finally, fix the file permissions inside the container:

    sudo docker run --rm --volumes-from=mumble-data --user=root koinu/mumble-server chown -R mumble-server:mumble-server /murmur
    sudo docker run --rm --volumes-from=mumble-data --user=root koinu/mumble-server chmod -R og-rwx /murmur

### Running Murmur

    sudo docker run --name=mumble --detach --publish=64738:64738 --publish=64738:64738/udp --volumes-from=mumble-data --restart=always koinu/mumble-server
