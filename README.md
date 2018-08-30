# vscode-python Pytest bug with multiple python projects

This repo includes two python projects with multiple test files.

To cause the bug, attempt via pytest configuration in VSCode to run the tests of only ONE project.


## Option 1
Ignore project-b - causes all project-a tests to be run when running a singular test method (plus the chosen test method is run a second time)

```json
{
    "python.unitTest.pyTestArgs": [
        ".",
        "--ignore=project-b"
    ]
}
```

## Option 2
Only run project-a. Path resolution is wrong (like project_a/tests/test_all.py, should be project-a/project_a/tests/test_all.py to work), so running single test method doens't work at all
```json
{
    "python.unitTest.pyTestArgs": [
        "project-a"
    ]
}
```


