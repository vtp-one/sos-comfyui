# sos-comfyui

SOS System for ComfyUI

ComfyUI is the most powerful and modular stable diffusion GUI and backend.

For more information about ComfyUI:
 - [ComfyUI](https://github.com/comfyanonymous/ComfyUI)


The SOS-Toolkit version of ComfyUI does not bundle any models during installation. 
You will need to download and place them in your model_data directory manually. 
See the ComfyUI documentation for where to download models from and where to place them. 
The system default uses the SOS-Toolkit local_data service to create a model_data directory which functions as the models directory for ComfyUI. 
Make sure to use the correct folder layout for objects you add. 
There is also a configuration option available to set this to a different directory.


# Requirements
 - [SOS-Toolkit](https://github.com/vtp-one/sos-toolkit)

Follow the instructions to get a working SOS-Toolkit virtual environment. 

Installation instructions assume you already have an activated virtual environment. 

All Commands in the environment are prefaced with: `(sos)$`


# Current Release Target
```
v0.2.2
```


# Install
These steps will pull, install, and run SOS-comfyui. 

You should start from your SOS-Toolkit root directory: `/sos` or it's equivalent in your environment

:warning: WARNING :warning:
```
A SYSTEM CAN RUN ANY TERMINAL COMMAND AND ANY ARBITRARY PYTHON CODE INCLUDING DYNAMICALLY GENERATED CODE
DO NOT INTERACT WITH SYSTEMS THAT YOU DO NOT KNOW, TRUST, OR HAVE THE CAPABILITY TO MANUALLY VERIFY THEIR OPERATION
```

### 1. Pull the sos-comfyui repository and enter it
```
(sos)$ sos-toolkit pull https://github.com/vtp-one/sos-comfyui --remote-branch v0.2.2
(sos)$ cd sos-comfyui
```

### 2. Setup the System
```
(sos)$ sos-toolkit setup
```

### 3. Install the System
```
(sos)$ sos-toolkit install
```
There currently aren't any pre-built containers for ComfyUI. 

Install will be building the container locally and can require 10-20 minutes depending on what base containers are available.

### 4. Run the System
```
(sos)$ sos-toolkit up
```

This command will output a system status message with the address the ComfyUI frontend is available on:
```
{'terminal.print_object': 'COMFYUI SERVER RUNNING ON: http://0.0.0.0:42000'}
```
Open the address in a web browser to access ComfyUI.

### 5. Shutdown the System
```
(sos)$ sos-toolkit down
```


# Configuration
SOS-ComfyUI bundles two configuration methods: changing the profile directory for output data, and changing the model data directory.


### Profile Directory
To change the profile directory use the built-in config action:
```
(sos)$ sos-toolkit config --target=runtime_profile

Input Runtime Profile Name: 

```
Enter a name for the new profile and press enter.
When starting the system, the name will be used to create a directory in the local_data folder:
```
<system_path>/internal/local_data
```
This folder will contain all of the output data generated by ComfyUI.


### Model Data Directory
To change the model data directory use the built-int config action:
```
(sos)$ sos-toolkit config --target=model_data

Input Model Data Path: 

```
Enter the target directory you want to use to store your models and press enter. 
The directory must be valid, and there are currently no safety or validity checks run on the input value.

The default location for storing model data is found in the folder:
```
<system_path>/internal/local_data/model_data
```
If you already have installed models, you will need to manually move them to the new location. Storing data in the folder needs to follow the expected format for ComfyUI. Check out their documentation for more information on how that works.

It is also possible to configure the model data location using `sos-local.yaml`
```
[ sos-comfyui/sos-local.yaml ]
namespace:
  runtime:
    model_data: <YOUR MODEL DATA DIRECTORY>

```


# More Information
 - [SOS-Toolkit](https://github.com/vtp-one/sos-toolkit)
 - [SOS-Test_System](https://github.com/vtp-one/sos-test_system)


# License
LICENSE WILL CHANGE

CURRENT LICENSE: VTP-LICENSE-v0.0.1

FOR APPROVED USE: POLYFORM - STRICT
