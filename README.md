# Git Assignment - HeroVired

## Introduction
Welcome to the **Git Assignment** repository for HeroVired! This project is designed to help you master Git and GitHub workflows while building a Python-based application. The repository includes tasks related to basic arithmetic operations, geometric calculations, and handling large files using Git LFS. It also demonstrates branching strategies, bug fixes, and collaborative development practices.

---

## Files
1. **CalculatorPlus**: A Python application for basic arithmetic operations and square root calculations.
2. **Geometry Calculator**: A Python program to compute the area of a circle and a rectangle.
3. **Git LFS Integration**: Demonstrates how to handle large binary files efficiently using Git LFS.

---

## Tasks and Implementation

### Task 1: CalculatorPlus
- **Objective**: Enhance a basic calculator application by adding a square root feature and fixing a division bug.
- **Steps**:
  1. **Create the Repository**:
     - Create a private GitHub repository named `git_assignment_HeroVired`.
     - Clone the repository locally:
       ```bash
       git clone https://github.com/your-username/git_assignment_HeroVired.git
       cd git_assignment_HeroVired
       ```
  2. **Create a Development Branch**:
     - Create and switch to a `dev` branch:
       ```bash
       git checkout -b dev
       ```
     - Add the initial calculator code to `calculator_plus.py`:
      
  3. **Merge with Main and Release Version 1**:
     - Merge `dev` into `main`:
       ```bash
       git checkout main
       git merge dev
       ```
     - Create a `v1.0` release:
       ```bash
       git tag v1.0
       git push origin main --tags
       ```
  4. **Implement Square Root Feature**:
     - Create a new branch `feature/sqrt`:
       ```bash
       git checkout -b feature/sqrt
       ```
     - Implement the `square_root` function in `calculator_plus.py`:
       ```python
       def square_root(self, x):
           return math.sqrt(x)
       ```
     - Test the feature by uncommenting and running the relevant code in `calculator_plus.py`.
     - Commit the changes:
       ```bash
       git add calculator_plus.py
       git commit -m "Added square root feature"
       ```
     - Push the `feature/sqrt` branch to the remote repository:
       ```bash
       git push origin feature/sqrt
       ```
  5. **Bug Fixation**:
     - Switch back to the `dev` branch:
       ```bash
       git checkout dev
       ```
     - Fix the `divide` function to handle division by zero:
       ```python
       def divide(self, a, b):
           if b == 0:
               raise ValueError("Cannot divide by zero.")
           return a / b
       ```
     - Commit the fix:
       ```bash
       git add calculator_plus.py
       git commit -m "Fixed division by zero bug"
       ```
     - Push the updated `dev` branch to the remote repository:
       ```bash
       git push origin dev
       ```
  6. **Feature Addition and Release Version 2**:
     - Merge `feature/sqrt` into `dev`:
       ```bash
       git checkout dev
       git merge feature/sqrt
       ```
     - Resolve any conflicts and test the application.
     - Push the updated `dev` branch to the remote repository:
       ```bash
       git push origin dev
       ```
     - Merge `dev` into `main` and create a `v2.0` release:
       ```bash
       git checkout main
       git merge dev
       git tag v2.0
       git push origin main --tags
       ```

---

### Task 2: Git LFS for Large Files
- **Objective**: Learn how to use Git LFS to manage large binary files.
- **Steps**:
  1. **Install Git LFS**:
     - Update the package list and install Git LFS:
       ```bash
       sudo apt update
       sudo apt install git-lfs
       ```
  2. **Initialize Git LFS**:
     - Navigate to your repository and enable Git LFS:
       ```bash
       git lfs install
       ```
  3. **Create a Dedicated Branch for Git LFS**:
     - Create and switch to a new branch `lfs`:
       ```bash
       git checkout -b lfs
       ```
  4. **Track Large Files with Git LFS**:
     - Specify file types to be managed by Git LFS:
       ```bash
       git lfs track "*.bin"
       ```
     - Add and commit the `.gitattributes` file:
       ```bash
       git add .gitattributes
       git commit -m "Configure Git LFS for large files"
       ```
     - Push the `.gitattributes` file to the remote repository:
       ```bash
       git push origin lfs
       ```
  5. **Add and Commit a Large File**:
     - Create a sample 300 MB binary file:
       ```bash
       dd if=/dev/urandom of=testfile.bin bs=1M count=300
       ```
     - Add and commit the file:
       ```bash
       git add testfile.bin
       git commit -m "Added a large test binary file"
       ```
  6. **Push to the Remote Repository**:
     - Push the changes to the remote repository:
       ```bash
       git push origin lfs
       ```
  7. **Validate Git LFS Implementation**:
     - Verify tracked files:
       ```bash
       git lfs ls-files
       ```
     - Check the pointer file:
       ```bash
       git show HEAD:testfile.bin
       ```

---

### Task 3: Geometry Calculator
- **Objective**: Implement a geometry calculator using Git stash to manage incomplete changes.
- **Steps**:
  1. **Create a Geometry Calculator Branch**:
     - Create and switch to a new branch `geometry-calculator`:
       ```bash
       git checkout -b geometry-calculator
       ```
  2. **Implement Circle Area Feature**:
     - Create a sub-branch `feature/circle-area`:
       ```bash
       git checkout -b feature/circle-area
       ```
     - Implement the circle area calculation in `geometry_calculator.py`:
       ```python
       import math

       class GeometryCalculator:
           def calculate_circle_area(self, radius):
               return math.pi * radius ** 2
       ```
     - Stash incomplete changes:
       ```bash
       git stash
       ```
     - Push the `feature/circle-area` branch to the remote repository:
       ```bash
       git push origin feature/circle-area
       ```
  3. **Implement Rectangle Area Feature**:
     - Create a sub-branch `feature/rectangle-area`:
       ```bash
       git checkout -b feature/rectangle-area
       ```
     - Implement the rectangle area calculation in `geometry_calculator.py`:
       ```python
       def calculate_rectangle_area(self, length, width):
           return length * width
       ```
     - Stash incomplete changes:
       ```bash
       git stash
       ```
     - Push the `feature/rectangle-area` branch to the remote repository:
       ```bash
       git push origin feature/rectangle-area
       ```
  4. **Complete and Merge Features**:
     - Switch back to `feature/circle-area`, apply stashed changes, and complete the implementation:
       ```bash
       git checkout feature/circle-area
       git stash pop
       ```
     - Commit the changes:
       ```bash
       git add geometry_calculator.py
       git commit -m "Implemented circle area feature"
       ```
     - Push the updated `feature/circle-area` branch to the remote repository:
       ```bash
       git push origin feature/circle-area
       ```
     - Repeat for `feature/rectangle-area`:
       ```bash
       git checkout feature/rectangle-area
       git stash pop
       git add geometry_calculator.py
       git commit -m "Implemented rectangle area feature"
       git push origin feature/rectangle-area
       ```
  5. **Merge into Main**:
     - Merge both features into `geometry-calculator`:
       ```bash
       git checkout geometry-calculator
       git merge feature/circle-area
       git merge feature/rectangle-area
       ```
     - Push the `geometry-calculator` branch to the remote repository:
       ```bash
       git push origin geometry-calculator
       ```
     - Merge `geometry-calculator` into `dev` and then into `main`.
     
     
     
     
     
     
     
     