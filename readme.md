# NuSMV Practicals

<small>This repository contains the practicals of the course "Formal Methods in Software Engineering" which is a part of the curriculum of the 7th semester of the BSc. (Hons.) Software Engineering program at General Sir John Kotelawala Defence University.</small>
 
## Table of Contents

- [NuSMV Practicals](#nusmv-practicals)
  - [Table of Contents](#table-of-contents)
  - [Prerequisites for Running NuSMV Files](#prerequisites-for-running-nusmv-files)
    - [For Windows](#for-windows)
    - [For Linux](#for-linux)
    - [Using the Provided Batch File to set the environmental variables](#using-the-provided-batch-file-to-set-the-environmental-variables)
- [Running NuSMV Models](#running-nusmv-models)
  - [Method 1: Single-Command Execution](#method-1-single-command-execution)
  - [Method 2: Interactive Execution](#method-2-interactive-execution)
      - [Start the NuSMV interactive shell by typing:](#start-the-nusmv-interactive-shell-by-typing)
      - [Load the SMV file:](#load-the-smv-file)
      - [Process the model step by entering theses commands sequentially:](#process-the-model-step-by-entering-theses-commands-sequentially)
      - [Inspect the current state:](#inspect-the-current-state)
      - [Execute the model:](#execute-the-model)
      - [To quit the interactive shell, when finished:](#to-quit-the-interactive-shell-when-finished)
    
---

## Prerequisites for Running NuSMV Files 

### For Windows

1. **Download:**
    - Visit the official NuSMV website and download the latest Windows package (usually provided as a ZIP file).

2. **Installation:**
    - Extract the ZIP file to a directory of your choice (e.g., `C:\NuSMV`).

3. **Environment Variables Setup:**
    - **`bin` Directory:**
      - Locate the `bin` folder inside the extracted directory.
      - Add the full path of the `bin` folder to the system PATH:
         - Right-click on "This PC" > Properties > Advanced system settings > Environment Variables.
         - Under "System variables", select `Path` and click "Edit".
         - Click "New" and paste the path (e.g., `C:\NuSMV\bin`).
    - **`include` Directory:**
      - Locate the `include` folder inside the extracted directory.
      - Create a new system variable if it does not already exist:
         - In Environment Variables, click "New" under System variables.
         - Set the **Variable name** to `INCLUDE_PATH` and the **Variable value** to the full path (e.g., `C:\NuSMV\include`).
    - **`lib` Directory:**
      - Similarly, locate the `lib` folder.
      - Create a new system variable:
         - Set the **Variable name** to `LIBRARY_PATH` and the **Variable value** to the full path (e.g., `C:\NuSMV\lib`).
    - Click OK to apply all the changes.

4. **Verify Installation:**
    - Open a new Command Prompt window and type:
  
      ```bash
      NuSMV -h
      ```

      You should see the help message for NuSMV, confirming that the executable is correctly accessible.

5. **Compiling Files:**
    - Note that NuSMV does not compile modeling files (`.smv`) in the typical sense. However, if you have scripts or batch files (like `set_env.bat`), verify they reference the correct paths and variables.

### For Linux

1. **Download:**
    - Download the NuSMV package from the official website or clone the repository if available.
    - Alternatively, download the distribution package (e.g., a `.tar.gz` file).

2. **Installation:**
    - Extract the downloaded file:
  
      ```bash
      tar -xzvf nusmv-<version>.tar.gz
      ```

    - Change into the extracted directory and compile:
  
      ```bash
      ./configure
      make
      sudo make install
      ```

      This will compile and install NuSMV to the default directories.

3. **Environment Variables Setup:**
    - If NuSMV is installed to a custom location, add its `bin` directory to your PATH:
      - Edit your shell configuration file (e.g., `~/.bashrc` or `~/.profile`) and add:
  
        ```bash
        export PATH=/path/to/nusmv/bin:$PATH
        ```

      - Save the file and apply the changes with:
  
        ```bash
        source ~/.bashrc
        ```

    - If needed, set additional variables for `include` and `lib`:
      - Append lines such as:
  
        ```bash
        export INCLUDE_PATH=/path/to/nusmv/include
        export LIBRARY_PATH=/path/to/nusmv/lib
        ```

4. **Verify Installation:**
    - Open a new terminal window and type:
  
      ```bash
      NuSMV -h
      ```

      This should display the NuSMV help details.

5. **Compiling Files:**
    - As with Windows, NuSMV interprets `.smv` source files and does not require traditional compilation.

### Using the Provided Batch File to set the environmental variables

Before starting your work, you can initialize the environment using the provided batch file.  
**Important:** Make sure to update the paths in the batch file (`set_env.bat`) to match the location where you extracted NuSMV.

You can run the batch file by typing in Command Prompt:

```bash
set_env.bat
```

---
# Running NuSMV Models

## Method 1: Single-Command Execution

Use this method when you want to run a NuSMV model in one go without any interactive modifications. Execute the following command in the Command Prompt:

```bash
NuSMV -int -source <file>.smv
```

Where `<file>.smv` is the file you want to run.

Replace <file>.smv with the name of the SMV file you wish to run. The output will be displayed directly in the terminal (or redirected to a file if you use output redirection).

## Method 2: Interactive Execution

Use this method to interactively run NuSMV, which lets you change the initial state and inspect intermediate results.

#### Start the NuSMV interactive shell by typing:

```bash
NuSMV -int
```

#### Load the SMV file:

```bash
read_model -i <file>.smv
```

Replace <file>.smv with the file name of your model.

#### Process the model step by entering theses commands sequentially: 

```bash
flatten_hierarchy
encode_variables
build_model
pick_state -i
```
#### Inspect the current state:

```bash
print_all_states
```

#### Execute the model:
```bash
simulate -k <steps>
```

Replace `<steps>` with the number of steps you want to simulate.

#### To quit the interactive shell, when finished:

```bash
quit
```

If you wish to save the output to a file during interactive execution, you can redirect the output when you start NuSMV:

```bash
NuSMV -int -source <file>.smv > <output>.txt
```

Replace `<file>.smv` with your model file's name and `<output>.txt` with the name of the file where the output should be saved.

To run the program and save its output to a file, execute the command below:

```bash
NuSMV -int > <output>.txt
```

Replace `<output>.txt` with the name of the file where you want the output saved.

<hr style="border: 0; height: 2px; background: linear-gradient(to right, rgba(0,0,0,0), #3498db, rgba(0,0,0,0));" />

<div align="center">
    <a href="https://github.com/TYehan">
        <img src="https://img.shields.io/badge/Crafted by-Tharindu Yehan-blue?style=flat-square">
    </a>
</div>
