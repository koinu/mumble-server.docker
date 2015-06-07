# A container for running a Mumble server

## Usage

### Set up the data container

Create the data container:

    sudo docker create --name=mumble-data koinu/mumble-server-data

Use whatever means are appropriate to get your murmur.conf, ssl certificate files, and database into the data volume.

Finally, fix the file permissions inside the container:

    sudo docker run --rm --volumes-from=mumble-data --user=root koinu/mumble-server chown -R mumble-server:mumble-server /murmur
    sudo docker run --rm --volumes-from=mumble-data --user=root koinu/mumble-server chmod -R og-rwx mumble-server:mumble-server /murmur

### Running Murmur

    sudo docker run --name=mumble --publish-all=true --volumes-from=mumble-data koinu/mumble-server
