# beRi demo (tested on Ubuntu-16.04)
This demo was tested on Ubuntu-16.04 which comes pre-installed with bash, Python 3.6, git, and curl.  The beRi package have been built using Python 3.6.
Other versions of Python/Ubuntu have not been tested.  Know bugs include [renv Issue #32](https://github.com/datasnakes/renv/issues/32)


## First commands as new user:
```bash
# Make directories
mkdir scripts
mkdir GitHub
mkdir demo

# Download and/or install important dependencies
if ! type "pip" > /dev/null; then
    cd ~/scripts
    curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
    python3.6 get-pip.py --user
    exec bash --login
    pip install --user poetry cookiecutter
else
    pip install --user poetry cookiecutter
fi

# Setup renv
cd ~/GitHub
git clone https://github.com/datasnakes/renv
cd renv
git checkout santina/symlink
poetry install -vvv
poetry build
pip install --user dist/renv*.whl

# Setup rinse
cd ~/GitHub
git clone https://github.com/datasnakes/rinse
cd rinse
poetry install -vvv
poetry build
pip install --user dist/rinse*.whl

# Setup rut
cd ~/GitHub
git clone https://github.com/datasnakes/rut
cd rut
git checkout old_remotes
poetry install -vvv
poetry build
pip install --user dist/rut*.whl

cd ~/demo
```
