
###Getting solr and extracting

 Download solr from [apache.org](http://www.apache.org/dyn/closer.cgi/lucene/solr/)
 and extract it (relative to the mirosubs  project directory) at 
 `../buildout/parts/solr`.

###Multi core setup

 1. Go to directory ../buildout/parts/solr/example/solr/

 2. Create a file solr.xml which will have info about your multicore setup.  
    File `MIROSUBS_DIR../buildout/parts/solr/example/solr/solr.xml`:

        <solr persistent="true" sharedLib="lib">
            <cores adminPath="/admin/cores">
                <core name="core0" instanceDir="." >
                    <property name="dataDir" value="/data/core0" />
                </core>
                <core name="core1" instanceDir="." >
                    <property name="dataDir" value="/data/core1" />
                </core>
            </cores>
        </solr>

###Running as a daemon


 1. Install the program [daemon](http://www.libslack.org/daemon/)
   ([available](http://packages.debian.org/sid/daemon) in debian repositories)

 2. Create this shell script and place it in some directory (say ~/bin)  
    File `$HOME/bin/solr`:


        #!/bin/bash

        # The root directory in which mirosubs django project exists
        MIROSUBS_ROOT=/home/rohan/workspace/python/mirosubs/mirosubs/

        SOLR_DIR=$MIROSUBS_ROOT../buildout/parts/solr/example

        PROCESS_NAME='mirosubs-solr'


        start () {
            echo "Starting the solr daemon..."
            daemon -n $PROCESS_NAME -D $SOLR_DIR -X 'java -jar start.jar'
            ## Wait a bit as it takse some time befor solr server starts
            sleep 2
            echo "Done."
        }

        stop () {
            # stop daemon
            echo "Stopping the solr daemon..."
            daemon -n $PROCESS_NAME --stop
            ## Wait a bit as it takse some time befor solr server stop
            sleep 1
            echo "Done."
        }

        restart() {
            stop
            start
        }

        case $1 in
            start)
                start
                ;;
            stop)
                stop
                ;;
            restart)
                restart
                ;;

            *)
            echo "Usage: solr {start|restart|stop}"
            exit 3
        esac

 3. Mark file `solr` as executable and add directory containing it to the path

    `chmod +x solr`  
    `export PATH=$PATH:$HOME/bin`

 4. Command for usage: solr {start|restart|stop}

 5. You can set solr to start automatically on boot, by adding the start coman
    to your xsessionrc

