# Bootstrap your TensorFlow Instance



## install python 3

    sudo apt-get update
    sudo apt-get -y upgrade

select "keep local version installed when prompted"

    python3 -V
    sudo apt-get install -y python3-pip
    sudo apt-get install build-essential libssl-dev libffi-dev python-dev


## install stable version of tensorflow

    pip3 install tensorflow==1.13.1
    
## install libraries

    pip3 install numpy
    pip3 install matplotlib

## install anaconda/jupyter notebook

    wget https://repo.continuum.io/archive/Anaconda2-5.3.1-Linux-x86_64.sh
    bash Anaconda2-5.3.1-Linux-x86_64.sh
 
    Do you wish the installer to prepend the Anaconda3 install location to 
    PATH in your /home/ubuntu/.bashrc ? [yes|no] [no] >>> yes

    Do you wish to proceed with the installation of Microsoft VSCode? [yes|no]
    >>> no

### create password
    
    
    ipython
    
first two lines of notebook should be

    from IPython.lib import passwd
    
    passwd()
    
enter a secure password you can remember
copy down the 'sha1:88f19c174703:ba6c1478d8fcae828a4ae3117498f874a1fa7221'

    exit
    
### create secure config file

    jupyter notebook --generate-config
    

### generate a ssl cert

    mkdir certs
    
    cd certs
    
    sudo openssl req -x509 -nodes -days 365 -newkey rsa:1024 -keyout mycert.pem -out mycert.pem

Answer question leaving unknown blank with ','


### configure jupyter

    cd ~/.jupyter/

    sudo nano jupyter_notebook_config.py
    
insert this into document

    # Kernel config
    c.IPKernelApp.pylab = 'inline'  # if you want plotting support always in your notebook
    
    # Notebook config
    c.NotebookApp.certfile = u'/home/ubuntu/certs/mycert.pem' #location of your certificate file
    c.NotebookApp.ip = '*'
    c.NotebookApp.open_browser = False  #so that the ipython notebook does not opens up a browser by default
    c.NotebookApp.password = u'sha1:88f19c174703:ba6c1478d8fcae828a4ae3117498f874a1fa7221'  #the encrypted password we generated above
    # Set the port to 8888, the port we set up in the AWS EC2 set-up
    c.NotebookApp.port = 8888

### create folder for notebooks

    cd ~
    
    mkdir Notebooks
    
    cd Notebooks



### Visit Jupyter notebook in local browser

Your EC2 instance will have a long url, like this:

ec2-18-232-129-34.compute-1.amazonaws.com

Visit that URL in your browser: (make sure to include the https at the beginning, or you’ll have access errors.)

https://ec2-18-232-129-34.compute-1.amazonaws.com:8888

Bypass any security concerns your browser may 

Enter your password



## Troubleshooting

If you get an error that port is in use

    ps -fA | grep /bin/jupyter-notebook
    
    sudo kill -9 <process-id>