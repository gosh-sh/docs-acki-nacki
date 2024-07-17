# **AnyTree**


## **Overview**



GOSH introduces **AnyTree** — the first software deployment system secured by the blockchain.

With AnyTree, any mutations of your code, down to every dependency, as well as operations, including builds and every artifact, are logged, timestamped, signed, and verified when used on GOSH

[Use AnyTree on GOSH](anytree-all.md#working-with-anytree) to benefit from added security, not only for your builds, but also the source code itself. Every single object in code delivered by AnyTree on GOSH is wrapped in a special executable ontology object, making GOSH AnyTree an unparalleled tool to allow businesses to log, and clearly tell what they are deploying where

GOSH AnyTree works with any Git storage. There’s no need to change workflows, no need to upload any private or public repositories to any external service, and you can keep using your favorite package managers, and be sure that your software supply chain is secured by AnyTree

It’s worth noting, however, that while the integration of AnyTree for Git offers an enhanced layer of security, it might not include the full array of features available on GOSH. 

!!! info
    The current version of AnyTree only supports Linux.



## **Working with AnyTree**

Detailed info can be found [here](working-with-gosh/anytree.md)
or use quick start.



### **Quick start**



1. **Install [**Git Remote Helper**](working-with-gosh/git-remote-helper.md#installation) using the installation script**

    ``` sh
    wget -O - \
      https://raw.githubusercontent.com/gosh-sh/gosh/dev/install.sh \
      | bash -s
    ```

    [Checking](working-with-gosh/git-remote-helper.md#verifying-the-installation-result) the installation results.

2. **Install [**AnyTree**](working-with-gosh/anytree.md#installation-anytree) using the installation script**

    ``` sh
    wget -O - \
      https://raw.githubusercontent.com/gosh-sh/anytree/dev/install.sh 
      | bash -s
    ```

    ```
    export PATH=$PATH:$HOME/.gosh
    ```

    By default, script installs latest release to the default path `$HOME/.gosh/`, but you can customize it with env variables:

    ```bash
    TAG=0.3.0 BINARY_PATH=/usr/local/bin ./install.sh
    ```

    You can check installation by running:

    ``` sh
    anytree --help
    ```

3. **Setup a GOSH project**

    You need a GOSH repository.  
    If you haven't used a GOSH-repository you can upload your github-repository to GOSH through [onboarding](https://app.gosh.sh/onboarding){:target="_blank"} or create a [GOSH-account](https://app.gosh.sh/){:target="_blank"} and [create a new one](working-with-gosh/gosh-web/repository.md).

    Go to your GOSH-repository

    and run:

    ``` sh
    gosh init
    ```

4. **Generation `SBOM file`**

    Prerequisites:

    * Docker
    * Python3 with pip (required to generate a `SBOM-file`)

    To create artifacts, you will need an `SBOM file` created  according to the [Cyclone DX specification](https://cyclonedx.org/docs/1.5/json/){:target="_blank"}

    !!! info
        The example file can be viewed [here](https://github.com/gosh-sh/anytree/blob/dev/tools/python/sbom.json){:target="_blank"}

    If you have a Rust project, you can generate an `SBOM file` using the script [generate-sbom.py](https://github.com/gosh-sh/anytree/blob/dev/tools/python/generate-sbom.py){:target="_blank"}  
    (*scripts for other programming languages will coming soon*)

    !!! Note
        either copy script to your cargo project and run `python3 generate-sbom.py` or check and configure variables in script

        ![](images/anytree_config_script.jpg)


    !!! info
        If necessary, install the dependencies for the script to work.  
        Run in the folder where the script is located:

        ```
        pip3 install -r requirements.txt
        ```

    **Possible options are described in the *help*:**

    ```
    python3 generate-sbom.py --help
    ```


    After running the script you should get the following output at the end:

    ```
    Updated SBOM written to /home/user/gosh/v5_x/v5.1.0/git-remote-gosh/sbom.json
    ```


    <!-- ![](../images/anytree_sbom_written_to.jpg) -->


5. **Now you are ready to build artifact**

    run:

    ```
    anytree build sbom.json
    ```

    As a result, a binary file of project will be created
    and you should get similar output at the end:

    ```
    Successfully copied 15.8MB to /home/user/.cache/anytree/builder/anytree-builder-5aba4439-2642-4b7f-bc3c-affd8c9839fd/target
    ```
    And your artifacts will be accessible in this folder


    !!! Warning
        **If the hash that was calculated when creating the SBOM file differs from the hash that AnyTree checks, an error like this will be output:**

    ![](images/anytree_error_wrong_hash.jpg)

    !!! Tip
        Place the SBOM-file in the same folder where `GOSH.yaml` is located.




## **Working with AnyTree without GOSH**




Prerequisites:

    * Docker
    * Python3 with pip (required to generate a `SBOM-file`)


1. **Install AnyTree**

    ```
    wget -O - https://raw.githubusercontent.com/gosh-sh/anytree/dev/install.sh | bash -s
    ```

    ```
    export PATH=$PATH:$HOME/.gosh
    ```

    By default, script installs latest release to the default path `$HOME/.gosh/`, but you can customize it with env variables:

    ```bash
    TAG=0.3.0 BINARY_PATH=/usr/local/bin ./install.sh
    ```

2. **Now you need the `SBOM file`.**

    Prerequisites:

    * Docker
    * Python3 with pip (required to generate a `SBOM-file`)

    To create artifacts, you will need an `SBOM file` created  according to the [Cyclone DX specification](https://cyclonedx.org/docs/1.5/json/){:target="_blank"}

    !!! info
        The example file can be viewed [here](https://github.com/gosh-sh/anytree/blob/dev/tools/python/sbom.json){:target="_blank"}{:target="_blank"}  

    If you have a Rust project, you can generate an `SBOM file` using the script [generate-sbom.py](https://github.com/gosh-sh/anytree/blob/dev/tools/python/generate-sbom.py){:target="_blank"}  
    (*scripts for other programming languages will coming soon*)

    !!! Note
        either copy script to your cargo project and run `python3 generate-sbom.py` or check and configure variables in script

        ![](images/anytree_config_script.jpg)


    !!! info
        If necessary, install the dependencies for the script to work.  
        Run in the folder where the script is located:

        ```
        pip3 install -r requirements.txt
        ```


    **Possible options are described in the *help*:**

    ```
    python3 generate-sbom.py --help
    ```

    ```
    usage: generate-sbom.py [-h] [--cargo-lock CARGO_LOCK_PATH] [--cargo-toml CARGO_TOML_PATH] [--initial-sbom INITIAL_SBOM_PATH]
                            [--sbom-output SBOM_OUTPUT_PATH] [--project-src PROJECT_SRC_PATH] [--project-commit PROJECT_COMMIT]
                            [--project-url PROJECT_URL]

    Generate software bill of materials (SBOM) for Rust project

    options:
    -h, --help            show this help message and exit
    --cargo-lock CARGO_LOCK_PATH
                            Path to Cargo.lock file. Default - ./Cargo.lock
    --cargo-toml CARGO_TOML_PATH
                            Path to Cargo.toml file. Default - ./Cargo.toml
    --initial-sbom INITIAL_SBOM_PATH
                            Optional. Path to initial SBOM JSON file if need to append existing SBOM. Default - initial-sbom.json. Will ignore
                            if file doesn't exist.
    --sbom-output SBOM_OUTPUT_PATH
                            Path to output SBOM JSON file. Default - sbom.json
    --project-src PROJECT_SRC_PATH
                            Path to the Rust project source if not in root git directory. Not relates to local file system path. Relates to
                            path inside repo structure. For example we can use v5_x/v5.1.0/git-remote-gosh which means s://github.com/gosh-
                            sh/gosh/v5_x/v5.1.0/git-remote-gosh
    --project-commit PROJECT_COMMIT
                            Commit of the project. Default - commit parsed with 'git rev-parse HEAD' command in dir where Cargo.lock is
                            located.
    --project-url PROJECT_URL
                            URL of the project's repository. Default - project URL parsed with 'git config --get remote.origin.url' command in
                            dir where Cargo.lock is located.
    ```

    !!! For_example
        Run the generation of the `SBOM-file` for the rust project `Git Remote Helper` latest version:

        ```
        python3 ~/gs/generate-sbom.py --cargo-lock ~/gosh/v5_x/v5.1.0/git-remote-gosh/Cargo.lock --cargo-toml ~/gosh/v5_x/v5.1.0/git-remote-gosh/Cargo.toml --sbom-output ~/gosh/v5_x/v5.1.0/git-remote-gosh/sbom.json --project-src v5_x/v5.1.0/git-remote-gosh
        ```

        The script downloads all dependencies specified in `cargo.lock`, counts all hashes and the generated sbom.json will be placed in the root folder of the project.

        After running the script you should get the following output at the end:

        ```
        Updated SBOM written to /home/user/gosh/v5_x/v5.1.0/git-remote-gosh/sbom.json
        ```

        And generated `sbom.json` file in the following [format](https://github.com/gosh-sh/anytree/blob/dev/tools/python/sbom.json){:target="_blank"}  


        <!-- ![](../images/anytree_sbom_written_to.jpg) -->


3. Now you can use sbom.json to build your project.  
    run:
<!-- To create a project and get a binary file with the correct hashes, run: -->
        ```
        anytree build sbom.json
        ```

As a result, a binary file of project will be created
and you should get similar output at the end:


```
Successfully copied 15.8MB to /home/user/.cache/anytree/builder/anytree-builder-5aba4439-2642-4b7f-bc3c-affd8c9839fd/target
```
And your artifacts will be accessible in this folder


!!! Warning
    If the hash that was calculated when creating the SBOM file differs from the hash that AnyTree checks, an error like this will be output:

    ![](images/anytree_error_wrong_hash.jpg)