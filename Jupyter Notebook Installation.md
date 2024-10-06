### Step 1: Install Jupyter Notebook

1. **Install Python and Pip (if not already installed)**:

   If Python is not installed, you can install it with:

   ```bash
   sudo yum install python3.12 -y
   sudo yum install python3.12-pip -y 
   sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.12 1
   sudo update-alternatives --config python3
   [oracle@vbox bin]$ sudo update-alternatives --config python3

There are 3 programs which provide 'python3'.

  Selection    Command
-----------------------------------------------
*+ 1           /usr/bin/python3.6
   2           /usr/bin/python3.11
   3           /usr/bin/python3.12

Enter to keep the current selection[+], or type selection number: 3

   sudo yum install ca-certificates -y
   sudo update-ca-trust force-enable
   python3 -m ensurepip --upgrade
   python3 -m pip install --upgrade pip
  # NumPy (for numerical computations)
  pip3.12 install numpy --trusted-host pypi.org --trusted-host files.pythonhosted.org --timeout 100
  # Pandas (for data manipulation and analysis)
  pip3.12 install pandas --trusted-host pypi.org --trusted-host files.pythonhosted.org --timeout 100
  # Matplotlib (for data visualization)
  pip3.12 install matplotlib --trusted-host pypi.org --trusted-host files.pythonhosted.org --timeout 100
  # Seaborn (for statistical data visualization)
  pip3.12 install seaborn --trusted-host pypi.org --trusted-host files.pythonhosted.org --timeout 100
  # Scikit-learn (for machine learning)
  pip3.12 install scikit-learn --trusted-host pypi.org --trusted-host files.pythonhosted.org --timeout 100
  # SciPy (for scientific computing)
  pip3.12 install scipy --trusted-host pypi.org --trusted-host files.pythonhosted.org --timeout 100
  # Statsmodels (for statistical models and tests)
  pip3.12 install statsmodels --trusted-host pypi.org --trusted-host files.pythonhosted.org --timeout 100
  # Jupyter Notebook (for interactive notebooks)
  pip3.12 install jupyter --trusted-host pypi.org --trusted-host files.pythonhosted.org --timeout 100
  # XGBoost (for gradient boosting algorithms)
  pip3.12 install xgboost --trusted-host pypi.org --trusted-host files.pythonhosted.org --timeout 100
  # TensorFlow (for deep learning)
  pip3.12 install tensorflow --trusted-host pypi.org --trusted-host files.pythonhosted.org --timeout 100
  # Keras (for deep learning)
  pip3.12 install keras --trusted-host pypi.org --trusted-host files.pythonhosted.org --timeout 100
  # PyTorch (for deep learning)
  pip3.12 install torch --trusted-host pypi.org --trusted-host files.pythonhosted.org --timeout 100
  # LightGBM (for gradient boosting algorithms)
  pip3.12 install lightgbm --trusted-host pypi.org --trusted-host files.pythonhosted.org --timeout 100
  # CatBoost (for gradient boosting algorithms)
  pip3.12 install catboost --trusted-host pypi.org --trusted-host files.pythonhosted.org --timeout 100
  # NLTK (for natural language processing)
  pip3.12 install nltk --trusted-host pypi.org --trusted-host files.pythonhosted.org --timeout 100
  # Spacy (for advanced natural language processing)
  pip3.12 install spacy --trusted-host pypi.org --trusted-host files.pythonhosted.org --timeout 100
  # Plotly (for interactive visualizations)
  pip3.12 install plotly --trusted-host pypi.org --trusted-host files.pythonhosted.org --timeout 100
  # PyCaret (for low-code machine learning)
  pip3.12 install pycaret --trusted-host pypi.org --trusted-host files.pythonhosted.org --timeout 100
  # Dash (for building dashboards)
  pip3.12 install dash --trusted-host pypi.org --trusted-host files.pythonhosted.org --timeout 100
  # OpenCV (for computer vision)
  pip3.12 install opencv-python --trusted-host pypi.org --trusted-host files.pythonhosted.org --timeout 100
  # PySpark (for large-scale data processing with Spark)
  pip3.12 install pyspark --trusted-host pypi.org --trusted-host files.pythonhosted.org --timeout 100
  # Dask (for parallel computing)
  pip3.12 install dask --trusted-host pypi.org --trusted-host files.pythonhosted.org --timeout 100
  # Joblib (for saving machine learning models)
  pip3.12 install joblib --trusted-host pypi.org --trusted-host files.pythonhosted.org --timeout 100
  
  

--- Step 2: Configure PySpark with Jupyter Notebook

1. **Update `.bashrc` for PySpark and Jupyter Integration**:

   Open your `.bashrc` file:

   vi ~/.bashrc

   Add the following environment variables for PySpark:

   ```bash
   # environment variables for PySpark
   export PYSPARK_PYTHON=python3
   export PYSPARK_DRIVER_PYTHON=jupyter
   export PYSPARK_DRIVER_PYTHON_OPTS="notebook"
   ```

   **Reload the `.bashrc` file**:
   source ~/.bashrc

	jupyter notebook --generate-config
	enter y 
	vi /home/oracle/.jupyter/jupyter_notebook_config.py
	add below lines
	c.NotebookApp.ip = '0.0.0.0'  # Listen on all interfaces
	c.NotebookApp.open_browser = False  # Do not open a browser automatically
	c.NotebookApp.port = 8888  # Use port 8888 (or any other port you want)



--- Step 3: Launch Jupyter Notebook with PySpark

1. **Start Jupyter Notebook**:

   Now you can start a Jupyter notebook with PySpark by simply running the following command:
   pyspark
  This will open a Jupyter Notebook in your browser, and you can start writing Spark code interactively.

2. **Access Jupyter Notebook**:

   After launching `pyspark`, Jupyter Notebook will open in your default browser. If you're running it on a remote machine, you can access it by navigating to:
   http://<VM-server-ip>:8888
   You will see a list of files in your home directory, and from here, you can create a new notebook and start coding with Spark.

--- Step 4: Test PySpark in Jupyter

1. Create a new notebook and run the following code to verify the PySpark setup:

   ```python
   # Test PySpark in Jupyter Notebook
   from pyspark.sql import SparkSession

   spark = SparkSession.builder.appName("JupyterTest").getOrCreate()
   data = [('Alice', 1), ('Bob', 2), ('Cathy', 3)]
   df = spark.createDataFrame(data, ['Name', 'Value'])
   df.show()
   ```

   This will create a simple DataFrame and display it in the notebook, confirming that PySpark is working correctly within Jupyter.

--- Summary:
- **Install Jupyter** using `pip`.
- **Install PySpark** and configure it with Jupyter.
- **Start Jupyter Notebook** using `pyspark`, and you're ready to code interactively with Spark!


