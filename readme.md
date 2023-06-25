# Python Jupyterlab, Geopython and friends "requirements.txt" for Windows 10 #
----------------------------------------------------------------------------------

This repo allows you to quickly setup a Jupyterlab with Geopandas environment on Windows from a requirements.txt file with pip. 
It also installs a bunch of other things, from well known modules like pytest and FastAPI to underexposed gems like ftfy, glom or tqdm - mainly everything I need to have with me to setup a Python environment offline.

👉 This repo is mostly meant for my own use, your milage may vary

👉 Main reason why this exists: pip includes a download feature which allows convenient installations from a USB drive with no internet present

👉 You think some library is missing? Cool! Please open an issue.


# Instructions #

Install Python
--------------
Get it from https://www.python.org/ - currently it's version 3.11.4

Install it for all users if you can, if not, just for you.

Go with the defaults. (Do not select to add it on the Path, it's not necessary)


Create a virtual directory
--------------------------

Whereever you want it:

- Open "cmd.exe".
- Navigate with "cd" commands to where you want to create it
- Run "py -3 -m venv *global_venv*" (where *global_venv* stands for the name you want to give it)


Activate the virtual directory
------------------------------
- Open "cmd.exe".
- Navigate with "cd" commands into the virtual directory you created in the last step
- run "Scripts/activate" to activate it (The names should autocomplete, type "S"-[Tab]-"a"-[Tab][Enter])


Install everthing else
----------------------
Inside "cmd.exe" navigate to where you compied the files from this repo
With the activated virtual directory, run
  
    python -m pip install pip -U

then

    python -m pip install -r requirements.txt


Start Jupyterlab
----------------------
Inside "cmd.exe", with the still activated virtual directory run 
  
    start python -m jupyterlab

The *start* command opens a new cmd window and then starts Jupyterlab in your browser.
This keeps the original window open, so if you find any library missing, you can pip install it right away!
  

❌📶 Offline use 
-----------------
This is where pip really shines - you can install almost anything with no internet or behind company firewalls!  
  
Copy everything needed onto a USB drive with the command
  
    python -m pip download -r requirements.txt

Then later install from within that folder
  
    python -m pip install -r requirements.txt --no-index --find-links .


🥶 Frozen version
------------------
The requirements.txt doesn't freeze the version numbers. 
By not freezing the requirements you will always get the newest working versions possible. This also means that installing can break when dependencies change.
Because of that there's also a frozen version of the requirements.txt file called requirements_frozen.txt. Which "works on my machine"™️.

👉 The frozen file is a fallback and may not always be up to date!

  
  
