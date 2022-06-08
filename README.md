Running `poetry install` in this repository brings up the following dependency conflicts:

```bash
0 bubblyworld @ ~/Workspace/python/azure-issues - [] $ poetry install
Updating dependencies
Resolving dependencies... (24.1s)

Writing lock file

  SolverProblemError

  The current project's Python requirement (3.10.4) is not compatible with some of the required packages Python requirement:
    - azureml-train-automl-client requires Python >=3.6,<3.9, so it will not be satisfied for Python 3.10.4

  Because no versions of azureml-pipeline match >1.42.0,<2.0.0
   and azureml-pipeline (1.42.0) depends on azureml-pipeline-steps (>=1.42.0,<1.43.0), azureml-pipeline (>=1.42.0,<2.0.0) requires azureml-pipeline-steps (>=1.42.0,<1.43.0).
  And because no versions of azureml-pipeline-steps match >1.42.0,<1.43.0
   and azureml-pipeline-steps (1.42.0) depends on azureml-train-automl-client (>=1.42.0,<1.43.0), azureml-pipeline (>=1.42.0,<2.0.0) requires azureml-train-automl-client (>=1.42.0,<1.43.0).
  Because azureml-train-automl-client (1.42.0.post1) requires Python >=3.6,<3.9
   and no versions of azureml-train-automl-client match >=1.42.0,<1.42.0.post1 || >1.42.0.post1,<1.43.0, azureml-train-automl-client is forbidden.
  Thus, azureml-pipeline is forbidden.
  So, because azure-issues depends on azureml-pipeline (^1.42.0), version solving failed.

  at /usr/local/Cellar/poetry/1.1.13/libexec/lib/python3.10/site-packages/poetry/puzzle/solver.py:241 in _solve
      237│             packages = result.packages
      238│         except OverrideNeeded as e:
      239│             return self.solve_in_compatibility_mode(e.overrides, use_latest=use_latest)
      240│         except SolveFailure as e:
    → 241│             raise SolverProblemError(e)
      242│
      243│         results = dict(
      244│             depth_first_search(
      245│                 PackageNode(self._package, packages), aggregate_package_nodes

  • Check your dependencies Python requirement: The Python requirement can be specified via the `python` or `markers` properties

    For azureml-train-automl-client, a possible solution would be to set the `python` property to "<empty>"

    https://python-poetry.org/docs/dependency-specification/#python-restricted-dependencies,
    https://python-poetry.org/docs/dependency-specification/#using-environment-markers
```
