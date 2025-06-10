# scikit-learn-jetson
Learning basic ML concepts on the Jetson Orin Nano 


Part 1: Set up Conda Environment and Jupyter Notebook on Jetson Orin Nano
The full Anaconda distribution is quite large and might be overkill for the Jetson Orin Nano. We'll use Miniconda, which is a lightweight alternative.

Install Miniconda for aarch64:
Open a terminal on your Jetson Orin Nano.

    mkdir -p ~/miniconda3
    wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-aarch64.sh -O ~/miniconda3/miniconda.sh
    bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
    rm ~/miniconda3/miniconda.sh


This downloads the Miniconda installer for ARM664 architecture, runs it silently, and then removes the installer script.
Initialize Conda:

Bash

~/miniconda3/bin/conda init
You might need to close and reopen your terminal or run source ~/.bashrc (or source ~/.zshrc if you're using zsh) for the changes to take effect. You should see (base) prepended to your command prompt, indicating the base Conda environment is active.

Create a New Conda Environment for Scikit-learn:
It's good practice to create a separate environment for your project to manage dependencies cleanly.

Bash

conda create -n sklearn_env python=3.9  # You can choose a Python version suitable for the scikit-learn tutorial.
Confirm with y when prompted.

Activate Your New Environment:

Bash

conda activate sklearn_env
Your prompt should now show (sklearn_env).

Install Jupyter Notebook:
Install Jupyter Notebook within your activated sklearn_env.

Bash

conda install jupyter notebook
Alternatively, you can use pip: pip install jupyter notebook (if conda install has issues).
Also, install ipykernel so your Conda environment can be recognized by Jupyter:

Bash

pip install ipykernel
python -m ipykernel install --user --name=sklearn_env --display-name "Python (scikit-learn_env)"
Install Scikit-learn and other necessary libraries:

Bash

conda install scikit-learn numpy pandas matplotlib scipy
If you encounter issues with conda install for scikit-learn on the Jetson, you might need to try pip install or check for specific aarch64 wheels (pre-compiled packages) if available. Sometimes, due to the ARM architecture, direct conda install might lead to compilation issues. If conda install fails, try:

Bash

pip install scikit-learn numpy pandas matplotlib scipy
Note: For some specialized libraries (like PyTorch or TensorFlow) on Jetson, you often need to install NVIDIA-provided pre-built .whl files rather than using pip or conda directly. However, scikit-learn usually has better cross-platform support.

Launch Jupyter Notebook:
Navigate to the directory where you plan to store your tutorial notebooks.

Bash

cd ~/
jupyter notebook
This will start the Jupyter server and open a new tab in your web browser (if you have a graphical desktop environment and browser installed on your Jetson). If not, it will print a URL with a token in the terminal. Copy and paste this URL into a web browser on a different computer on the same network to access your Jupyter Notebook remotely (replace localhost with your Jetson's IP address).


General Workflow for Your Scikit-learn Tutorials:
On your Jetson Orin Nano:

Open a terminal.
Navigate to your repository: cd ~/scikit-learn-jetson-tutorial
Activate your Conda environment: conda activate sklearn_env
Pull any latest changes from GitHub (if you're collaborating or working from multiple locations): git pull origin main
Launch Jupyter Notebook: jupyter notebook
Work on your scikit-learn tutorial.
Save your notebooks.
In the terminal (after stopping Jupyter or in a new terminal):
git add .
git commit -m "Meaningful commit message"
git push origin main
