# Template for deploying a python lambda function with dependencies
Setup venv and install requirements

```
make venv
```

Zip `lambda_function.py` and dependencies from venv into `lambda_deployment.zip`
```
make zip
```

Or do both
```
make
```

Clean out old environment
```
make clean
```


TODO: push deployment to AWS using terraform `make deploy`
