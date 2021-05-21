This is going to be the repository where I will be storing my Mac Mini M1 chip tensor flow projeccts

Installing tensorFlow for a mac Mini will be completed by following the complete guide at https://www.ai-buzz.com/18-steps-to-install-tensorflow_macos-on-m1-macbook-2020/ .

Here is an abridged step by step guide mostly for my own conceptualization of what needs to be done to get tensorflow working.

1. Install miniforge from https://github.com/conda-forge/miniforge/#download
    use bash command to install from Downloads and complete prompt
2. Now that Conda is working, you will want to restart your terminal and navigate to where you want to create your conda virtual environment. Then you can run the command
    codna create --name python38(orwhateveryouwantittobe) python=3.8
3. Activate your virtual environment in termanl (or if you wanna jump straight into vscode, you can perform this in the vscode terminal) by navigating to the directory where the vnv is installed and running 
    conda activate python38 (orwhateveryounamedyourvenv)
    you have now entered... the tensorZone... (sort of)
4. Download the most recent version of tensor flow for macOS m1 chip from theis link https://github.com/apple/tensorflow_macos/releases/tag/v0.1alpha3 . Read the readme pls
    Unzip the folder in downloads using the command 
        -tar xvf (whateverVersionofTensorFlowYouDownloaded)
        MAKE SURE YOU DOWNLOAD THE ACTUAL TENSORFLOW FILE AND NOT THE ADD-ONS. Add ons can be added later on, but thats a whole different thing rn
        its a tar file not a wheel file
5. You should now have a file in your downloads named tensorflow_macos. inside, there is a file named arm64. Navigate to this file in terminal.
6. Now while we are still inside our conda environment and the arm64 folder, we are going to create two new variables libs and env.
    1. in terminal type pwd to get the working directory which has returns the arm64 directorypath. copy this path
    2. enter the command libs="(paste directory here)"
    3. Find your current Conda vnv by running the command 
        conda env list
    4. this will give you a list of all your conda environments and their corresponding paths. Copy the path with the star next to it.
    5. create an env variable by running the command
        env="(paste the path you copied here)"
7. Using the Conda installer, install cached-property and six using the commands
    Conda install cached-property six
8. now we are going to pip install some packages

    pip install --upgrade -t "$env/lib/python3.8/site-packages/" --no-dependencies --force "$libs/tensorflow_addons_macos-0.1a3-cp38-cp38-macosx_11_0_arm64.whl"
        and
    pip install --upgrade -t "$env/lib/python3.8/site-packages/" --no-dependencies --force "$libs/h5py-2.10.0-cp38-cp38-macosx_11_0_arm64.whl"


    (yes these are copypasta-ble :) (smile))
9. a buncha more conda package installations
    conda install -c conda-forge -y astunparse
    conda install -c conda-forge -y gast
    conda install -c conda-forge -y opt_einsum
    conda install -c conda-forge -y termcolor
    conda install -c conda-forge -y typing_extensions
    conda install -c conda-forge -y wheel
    conda install -c conda-forge -y typeguard

    (The guide says to not do them all at once, but I did them all at once and didn't have any issues)
    (if you want to do them all at once, run the conda installation one more time to make sure all of these were installed successfully(check to see if terminal says theyre already installed after you run it the second time))

     pip install wrapt flatbuffers tensorflow_estimator google_pasta keras_preprocessing protobuf
     (i had to install some specific versions of some packages using xx=='version', but i d actually dont think it matters and was more of a warning)
10.  install tensor flow using this command 
   
    pip install --upgrade -t "$env/lib/python3.8/site-packages/" --no-dependencies --force "tensorflow_macos-0.1a3-cp38-cp38-macosx_11_0_arm64.whl"
    pip install tensorboard

11. Check to see if everything is running smoothly from the command prompt by runnning
    python
    >>import tensorflow

    If there are no errors, then YAY you did it :). now we can have fun doing some deep learning tin this conda vnv

Just remember to activate this vnv anytime you want to run something with tensor flow, or if you're using vscode, you can set it up to run natively in the terminal. :) 