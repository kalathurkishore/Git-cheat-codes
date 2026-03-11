Below is the **same cheat sheet rewritten in a clean, readable format** so it looks like **structured notes instead of raw README text**. This format is easier to scan while working on ML projects.

---

# 🚀 Git for ML Engineers & Data Scientists

### Practical Version Control Cheat Sheet

Machine Learning projects involve more than just code. Typically you manage:

* Source code
* Large datasets
* Trained models
* Checkpoints
* Experiments
* Configurations

Using **only Git** for everything causes issues because ML files are large.

A standard ML workflow combines:

| Tool         | Purpose                       |
| ------------ | ----------------------------- |
| Git          | Code versioning               |
| Git LFS      | Large files (model weights)   |
| DVC          | Dataset & pipeline versioning |
| W&B / MLflow | Experiment tracking           |

---

# 1. Recommended ML Project Structure

A clean ML repository structure:

```
project-name
│
├── data
│   ├── raw
│   └── processed
│
├── models
│   ├── checkpoints
│   └── final
│
├── notebooks
│
├── src
│   ├── data_processing
│   ├── training
│   ├── evaluation
│   └── inference
│
├── configs
├── experiments
├── requirements.txt
├── README.md
└── .gitignore
```

### Why this structure is useful

* Improves **reproducibility**
* Easier **team collaboration**
* Simplifies **debugging**
* Keeps experiments organized

---

# 2. What Should Be Tracked in Git

Git should track **lightweight files only**.

### Track with Git

* Python scripts
* Training code
* Configuration files
* Evaluation scripts
* Experiment metadata
* Documentation

### Avoid tracking in Git

* Datasets
* Model checkpoints
* Model weights
* Logs

These should be handled using **Git LFS or DVC**.

---

# 3. Important `.gitignore` for ML Projects

Typical `.gitignore` configuration:

```
data/
datasets/
models/
checkpoints/

*.pth
*.pt
*.ckpt
*.onnx
*.pkl

wandb/
mlruns/

__pycache__/
.ipynb_checkpoints/
```

### Why this matters

Without `.gitignore`:

* Git history becomes extremely large
* Repositories become slow
* Collaboration becomes difficult

---

# 4. Git LFS (Large File Storage)

Git LFS is used to store **large files such as:**

* Model weights
* Dataset archives
* Pretrained models

Instead of storing the file itself, Git stores a **pointer file**, while the actual file is stored in **LFS storage**.

---

# 5. Installing Git LFS

### Linux

```
sudo apt install git-lfs
```

### Mac

```
brew install git-lfs
```

Initialize LFS in the repository:

```
git lfs install
```

---

# 6. Tracking Large Files with Git LFS

Example: tracking ML model weights.

```
git lfs track "*.pth"
git lfs track "*.pt"
git lfs track "*.onnx"
git lfs track "*.ckpt"
```

This creates a file:

```
.gitattributes
```

Commit it:

```
git add .gitattributes
git commit -m "setup git lfs"
```

Now Git automatically stores large files using **Git LFS**.

---

# 7. Example Workflow Using Git LFS

Add a trained model:

```
git add model.pth
git commit -m "add trained model"
git push origin main
```

Git stores:

* a **pointer file in the repository**
* the **actual model in LFS storage**

---

# 8. DVC (Data Version Control)

DVC helps manage:

* large datasets
* model checkpoints
* ML pipelines
* reproducible experiments

Important idea:

```
Git → tracks code
DVC → tracks data
```

---

# 9. Installing and Initializing DVC

Install DVC:

```
pip install dvc
```

Initialize DVC inside the repository:

```
dvc init
```

Commit the configuration:

```
git add .dvc
git commit -m "initialize dvc"
```

---

# 10. Versioning Datasets with DVC

Add a dataset:

```
dvc add data/dataset
```

This creates a metadata file:

```
dataset.dvc
```

Commit metadata to Git:

```
git add dataset.dvc .gitignore
git commit -m "add dataset with dvc"
```

Actual data is **not stored in Git**.

---

# 11. Configure Remote Storage for DVC

DVC can store datasets in remote storage such as:

* AWS S3
* Google Cloud Storage
* Azure Storage
* SSH servers
* Local storage

Example configuration:

```
dvc remote add -d storage s3://ml-bucket/dvc-store
```

Push dataset to remote storage:

```
dvc push
```

---

# 12. Pull Dataset on Another Machine

When another developer clones the repository:

```
git pull
dvc pull
```

This downloads datasets from remote storage.

---

# 13. Versioning Trained Models with DVC

Example:

```
dvc add models/resnet50.pth
```

Commit metadata:

```
git add models/resnet50.pth.dvc
git commit -m "add trained model"
```

Push model to storage:

```
dvc push
```

---

# 14. ML Experiment Tracking

ML experiments vary based on:

* Hyperparameters
* Dataset versions
* Model architectures
* Training schedules

Popular experiment tracking tools:

| Tool             | Purpose             |
| ---------------- | ------------------- |
| MLflow           | Experiment tracking |
| Weights & Biases | Visualization       |
| TensorBoard      | Training metrics    |

Example setup with Weights & Biases:

```
pip install wandb
wandb init
```

---

# 15. Versioning Model Checkpoints

Typical checkpoint structure:

```
models
 ├── epoch10.pth
 ├── epoch20.pth
 └── best_model.pth
```

Track the best model using DVC:

```
dvc add models/best_model.pth
```

---

# 16. Reproducing Experiments

To reproduce a machine learning experiment:

1. Clone repository

```
git clone repo
```

2. Checkout experiment branch

```
git checkout experiment_branch
```

3. Pull dataset

```
dvc pull
```

4. Run training

```
python train.py
```

This guarantees **full reproducibility**.

---

# 17. Typical ML Development Workflow

A typical ML engineer workflow:

### Step 1 – Create experiment branch

```
git checkout -b experiment-resnet
```

### Step 2 – Modify training code

Edit training scripts or configs.

### Step 3 – Train the model

```
python train.py
```

### Step 4 – Track model with DVC

```
dvc add models/model.pth
```

### Step 5 – Commit code changes

```
git add .
git commit -m "train resnet model"
```

### Step 6 – Push code and data

```
dvc push
git push origin experiment-resnet
```

---

# 18. Recommended Tools for ML Version Control

| Tool             | Purpose                  |
| ---------------- | ------------------------ |
| Git              | Code versioning          |
| Git LFS          | Large files              |
| DVC              | Dataset versioning       |
| MLflow           | Experiment tracking      |
| Weights & Biases | Experiment visualization |
| TensorBoard      | Training metrics         |

---

# 🎯 Key Takeaway

The standard **ML engineering workflow**:

```
Git      → Code version control
Git LFS  → Large model files
DVC      → Dataset & pipeline versioning
W&B / MLflow → Experiment tracking
```

Using this stack enables:

* reproducible experiments
* scalable ML pipelines
* collaborative research
* production-ready workflows

---

✅ Since you work in **Computer Vision / Deep Learning**, the next useful thing is a **real industry ML workflow** that companies use, including:

* dataset versioning pipelines
* experiment registry
* model registry
* ML CI/CD
* deployment pipelines

If you want, I can also show you **“End-to-End ML Git Workflow used in production AI teams”** (this is extremely useful for **AI/ML engineer interviews and real projects).
