# VOC Exporter

Inside this folder is a script for converting Labelbox JSON to VOC file exports. To get a JSON export file from your project, 
visit the export tab of your project and select the JSON option from the dropdown. This will be the file input for the VOC converter script in this directory. 

First clone the repository to access the converter script aka:
```sh
git clone https://github.com/Labelbox/Labelbox.git
```

To get started if you do not already have Docker you'll want to download and install Docker desktop. You can do so here: [docker-hub](https://hub.docker.com/). 

Once you have installed Docker, you may run the converter inside a docker container. To do so simply run the following command from this directory (where `${PATH_TO_INPUT}` is the location of your Labelbox JSON export file on your local machine). 
Note: The VOC export output location if unmodified will be saved in this directory (aka `Labelbox/exporters/voc-exporter/output`).  
```
make run-local-export EXPORT_PATH=${PATH_TO_INPUT}
```

Should you wish to modify the location of the export output, you can also run:
```
make run-local-export EXPORT_PATH=${PATH_TO_INPUT} OUTPUT_DEST=${PATH_TO_DESIRED_OUTPUT}
```

The script will generate a folder `output` containing both the XML annotation files of the VOC export and a folder `images` with the source images. 
 
We HIGHLY recommend you use the Docker container to run the converter script `main.py`.
The docker container provides an isolated environment with the correct dependencies installed, making it easier to setup than even a pipenv.

Finally should you absolutely need to run the script directly we recommend using pipenv. The script uses Python 3.6.4 and `pipenv` to manage dependencies.
                                                                              
To install dependencies, run:
```sh
pipenv install
```

To then run the converter script, run: 
```sh
pipenv python main.py ${PATH_TO_INPUT} ${PATH_TO_OUTPUT}
```
