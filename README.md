# 31339

Reproduction for [Renovate discussion 31339](https://github.com/renovatebot/renovate/discussions/31339)

## Current behavior

Renovate currently skips updating Python packages in the poetry manager that have multiple version requirements.

Sample dependency

```toml
[tool.poetry.dependencies]
numpy = [
  {python = "^3.9", version = "^1.26"},
  {python = "^3.8, <3.12", version = "^1.24"}
]
```

Renovate log output:
```
  {
    "datasource": "pypi",
    "skipReason": "multiple-constraint-dep",
    "depName": "numpy",
    "depType": "dependencies",
    "updates": [],
    "packageName": "numpy"
  },
```

## Expected behavior

Renovate should update both constraints of the Python package based on the python version requirements.
