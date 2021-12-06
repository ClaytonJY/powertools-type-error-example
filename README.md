# AWS Lambda Powertools - Reprex for #849

This is a minimal reprex for [issue #849](https://github.com/awslabs/aws-lambda-powertools-python/issues/849#issuecomment-986449730) in the [`aws-lambda-powertools`](https://github.com/awslabs/aws-lambda-powertools-python/) package.

The file `extending_builtin_models.py` is copied from [the docs](https://awslabs.github.io/aws-lambda-powertools-python/latest/utilities/parser/#extending-built-in-models).

The `pydantic` plugin for `mypy` is configured via `pyproject.toml`; everything else is "vanilla".

## Steps to reproduce
1. have a recent version of `poetry` and a 3.9.* version of python available
1. clone this repo and `cd` into it
1. `poetry install` to install the deps into an environment
1. `poetry run mypy extending_builtin_models.py`

You should see an error like
```bash
extending_builtin_models.py:17: error: Incompatible types in assignment (expression has type "Order", base class "EventBridgeModel" defined the type as "Dict[str, Any]")
Found 1 error in 1 file (checked 1 source file)
```
