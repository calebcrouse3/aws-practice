# Makefile

# Specify the Python interpreter
PYTHON = python3

# Define the virtual environment directory
VENV_DIR = .venv

# Name of the zip file to create
ZIPFILE = lambda_deployment.zip

# Default target is 'all'
all: zip

# Target for creating a virtual environment and installing dependencies
venv: $(VENV_DIR)/bin/activate

# Rule for creating a virtual environment
$(VENV_DIR)/bin/activate: requirements.txt
	test -d $(VENV_DIR) || $(PYTHON) -m venv $(VENV_DIR)
	$(VENV_DIR)/bin/pip install -r requirements.txt
	touch $(VENV_DIR)/bin/activate

# Target to clean the virtual environment (use with caution as this will delete the entire venv directory)
clean:
	rm -rf $(VENV_DIR)

# Target to create a zip file for AWS Lambda deployment, excluding the pip package
zip: venv
	rm -f $(ZIPFILE)
	zip $(ZIPFILE) lambda_function.py
	@cd $(VENV_DIR)/lib/python3.*/site-packages && \
	zip -r ../../../../$(ZIPFILE) . -x '*pip*' -x '*pip/*' -x '*setuptools*' -x '*setuptools/*' -x '*pkg_resources*' -x '*pkg_resources/*' -x '*wheel*' -x '*wheel/*' && \
	cd -

.PHONY: all venv clean zip