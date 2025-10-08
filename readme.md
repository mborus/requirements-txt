# Python Jupyterlab, Geopython and friends "requirements.txt" for Windows 11 and/or WSL2 #

This repo allows me (and you) to quickly setup a Jupyterlab with Geopandas environment on Windows from a requirements.txt file with pip. 
It also installs a bunch of other things, from well known modules like pytest and FastAPI to underexposed gems like ftfy, glom or tqdm - mainly everything I need to have with me to setup a Python environment offline.

👉 This repo is mostly meant for my own use, your milage may vary

👉 This repo works on Windows 11. It is no longer tested for Windows 10

👉 Main reason why this exists: pip includes a download feature which allows convenient installations from a USB drive with no internet present

👉 You think some library is missing? Cool! Please open an issue.


# Instructions #

Install Python 3.13
---------------------------
Get it from https://www.python.org/ - as of 2025-04-12 it's version 3.13.3.

Install it for all users if you can, if not, just for you.

Go with the defaults. (Do not select to add it on the Path, it's not necessary)

👉 Python 3.14 was released 2025-10-08. Since not all libraries support it yet, there's a `requirements_314.txt` with what's installable with the others commented out. Over the next weeks I'll retry and add back what works.


Create a virtual directory
--------------------------

Whereever you want it:

- Open "cmd.exe".
- Navigate with "cd" commands to where you want to create it
- Type:

    py -3 -m venv *global_venv*

(where *global_venv* stands for the name you want to give it)


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


WSL2/Ubuntu use
--------------------
The script should also work with the Windows Subsystem for Linux to install everything.

I assume you have a working Python install for Python3.13 that can create venvs and use pip to install.

You will run into smaller problems, though. For example starting Jupyter will throw a confusing error instead of starting your browser and you need to manually paste the link into your browser.

Note: I tested it on WSL2/Ubuntu 20.04.06 LTS, installed using pip. 


❌📶 Offline use 
-----------------
This is where pip really shines - you can install almost anything with no internet or behind company firewalls!  
  
Copy everything needed onto a USB drive with the command
  
    python -m pip download -r requirements.txt

Then later install from within that folder
  
    python -m pip install -r requirements.txt --no-index --find-links .

👉 Don't forget to put the current Python installer on that drive!

👉 You also may want to download pip so you have the newest version on the drive.


🥶 Frozen version
------------------
The requirements.txt doesn't freeze the version numbers. 
By not freezing the requirements you will always get the newest working versions possible. This also means that installing can break when dependencies change.
Because of that there's also a frozen version of the requirements.txt file called requirements_frozen.txt. Which "works on my machine"™️.

👉 The frozen file is a fallback and may not always be up to date!


Usage of uv instead of pip
--------------------------
As of 2024-11-04, uv doesn't support downloading. It does support installing from the downloads. To speed up things a lot, your can manually install uv at the destination before using uv to install the rest. It worked great on Windows, on WSL2/Ubuntu uv crashed with a thread error.
