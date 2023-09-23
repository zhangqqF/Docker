# Docker

>zhangqq  
>Sep 23, 2023  
>Chongqing

---


## Get start with docker

1. Create a docker from the image python:3.7.8

   ```
   docker run -it --name my1docker -p 80:20 python:3.7.8 /bin/bash
   ```

2. Install jupyter

   ```
   pip install jupyter
   ```

   Using jupyter notebook in docker:

   - Start the container `docker container start [id]`

   - Enter the container `docker exec -it [id] bash`

   - Update `apt-get update`

   - Install vim `apt-get install vim`

   - Generate the config file for jupyter notebook `jupyter-notebook --generate-config`

   - Set the password

     - Enter python environment `ipython`
     - `from notebook.auth import passwd`
     - `passwd(algorithm='sha1')`
     - Enter a password and verify
     - Copy the sha1 output
     - Exit the python environment `exit`

   - Open the config file to modify `vim ~/.jupyter/jupyter_notebook_config.py`

     - Add the contains to any where:

       ```
       c.NotebookApp.ip = '*'
       c.NotebookApp.port = 20
       c.NotebookApp.open_browser = False
       c.NotebookApp.allow_remote_access = True
       c.NotebookApp.password = u'sha1:db6a31935bc1:7e8b88dd49cb9725c5043617825899c32ea2b3e1'
       ```

     - Save and exit the file: *Esc->:wq*

   - **Forward port** a ip:port (ex. 10.217.7.225:80) then open in web.
