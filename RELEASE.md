# Release Instructions

This document describes how to release a new version of PDBFixer to PyPI and GitHub.

## Prerequisites

1. Update the version number in `setup.py` and `pyproject.toml`:
   ```python
   __version__ = '1.11.0'  # Update this to your new version
   ```

   ```toml
  version = "1.11.0"       # Update this to your new version
  ```

2. Ensure `ISRELEASED = False` in `setup.py` (the workflow will automatically set it to `True` during the build)

## Release Process

### Step 1: Test Release (Recommended)

1. Go to the [Actions tab](../../actions) in your GitHub repository
2. Click on "Build and Release" workflow
3. Click "Run workflow"
4. Select:
   - Branch: `master` (or your release branch)
   - PyPI target: `testpypi`
5. Click "Run workflow"

The workflow will:
- Build the source distribution and wheel
- Upload to TestPyPI
- You can verify the package at: https://test.pypi.org/project/pdbfixer/

### Step 2: Production Release

1. Once you've verified the test release, run the workflow again
2. This time select:
   - Branch: `master`
   - PyPI target: `pypi`
3. Click "Run workflow"

The workflow will:
- Build the source distribution and wheel
- Upload to PyPI
- Create a git tag `v{version}`
- Create a GitHub release with the built artifacts
