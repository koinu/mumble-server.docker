# A container for running a Mumble server

## Usage

### Set up the data volume

Create a data volume for the config file, ssh certificate files, and database:

    sudo docker volume create murmur

Use whatever means are appropriate to get your murmur.conf, ssl certificate files, and database (if you have an existing one) into the volume.

Finally, fix the file permissions:

    sudo docker run --rm -v murmur:/murmur --user=root koinu/mumble-server chown -R mumble-server:mumble-server /murmur
    sudo docker run --rm -v murmur:/murmur --user=root koinu/mumble-server chmod -R og-rwx /murmur

### Running Murmur

    sudo docker run --name=mumble --detach --publish=64738:64738 --publish=64738:64738/udp -v murmur:/murmur --restart=always koinu/mumble-server
