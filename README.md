# Model Training

## About the model

This project uses **CSRNet**, a deep learning model that takes a microscope image and estimates how many microplastic particles are in it. It does this by producing a "density map" (a heatmap of where particles are), then adding it up to get a count.

![Training curves](training-result/training_curve.png)

### What these charts show

I trained the model for 30 rounds (called epochs). After each round, I checked how well it was doing.

- **Loss** (left chart): how wrong the model is. Lower is better.
- **MAE** (right chart): the average size of the model's mistakes. Lower is better.
- **Blue line**: how the model does on data it learned from.
- **Red line**: how the model does on new data it has never seen.

### Results

| Metric | Training | Validation |
|--------|----------|------------|
| Loss   | ~0.0016  | ~0.0030    |
| MAE    | ~0.024   | ~0.034     |

On a separate test set, the model's average error was **X particles per image** (MAE) with a counting accuracy of **XX%**.

### What this means

Both lines go down, which means the model is learning to detect microplastics. The red line is a bit higher than the blue line, which is normal: the model is slightly better on data it has already seen than on new data. Validation stopped improving after about epoch 20, so training longer would not help much.

### Possible improvements

- Add more training images
- Use data augmentation (flips, rotations, brightness changes)
- Try early stopping around epoch 20

# Setup instructions

1. Must have python interpreter :
    - [Download python](https://www.python.org/downloads/)

2. Create your own folder in your local machine

3. Install *Jupyter notebook* in your local machine, open cmd or terminal and type:
   
   - `pip install notebook`
    
4. After installation of *Jupyter notebook*, open created folder and navigate to its directory in the terminal, create a *venv* or virtual environment, this will be the container of your libraries:

   >Create venv in that folder created
   - `python -m venv {your own name of venv}`
   >Then activate the venv
   - `venv\Scripts\activate`
   >to deactivate
   - `venv\Scripts\deactivate`
   >when activated it will look like this as an example
   - `(venv) C:\Users\[user]\Desktop\microplastics-detection>`

5. Now use the *requirements.txt* to install all libraries required to run the program or code.
   
   >**"REMEMBER KEEP THE VENV ACTIVATED"**

   >paste this once the venv is activated
   - `pip install -r requirements.txt`
   >check if they are installed
   - `pip list`

6. Basically *Jupyter notebook* uses kernels to run its code. So, we already did that by installing it using *requirements.txt*. 

   In order to use our created venv with installed required libraries we will need to use the *ipykernel* (installed already, listed also in the txt file) library to configure the kernel to be used in the notebook.

    **"RECOMMENDED TO PASTE THIS COMMANDS IN THE ACTIVATED VENV"**

      >create your kernel using the venv you created
      - `python -m ipykernel install --user --name=myenv --display-name "Python (myenv)"`
   
   - `--name` : internal kernel name
   - `--display-name` : the name you’ll see inside Jupyter Notebook
   >to check if the kernel is now existing
   - `jupyter kernelspec list`
   > This is optional only if something happened etc. this is how you deleted the kernel
   - `jupyter kernelspec remove [the name of --name kernel setupn from the kernel list]`



7. Now, in the same terminal or cmd where the venv is activated *(It does not matter if it's activated or not as long your terminal is navigated in that folder)* 
     
     >Now type this, this will open the *Jupyter notebook*
     - `jupyter notebook`

8. To change the kernel, after opening the notebook on the top bottom click the *Kernel* then again click the *Change Kernel*

