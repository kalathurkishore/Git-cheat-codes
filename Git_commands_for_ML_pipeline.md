Here is a clean, readable cheat sheet (not in raw README markdown) for Git for ML Engineers & Data Scientists.
It is structured so you can easily understand and remember the workflow for datasets, models, and experiments.


---

🚀 Git for ML Engineers & Data Scientists – Practical Cheat Sheet

Machine Learning projects involve more than just code. You usually deal with:

Source code

Large datasets

Trained models

Checkpoints

Experiments

Configurations


Using only Git for everything creates problems with large files, so ML workflows typically combine:

Git → code versioning

Git LFS → large model files

DVC → dataset & pipeline versioning

Experiment tracking tools (W&B / MLflow)



---

1. Recommended ML Project Structure

A clean ML project repository typically looks like this:

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

Good structure helps with:

reproducibility

collaboration

easier debugging



---

2. What Should Be Tracked in Git

Git should track only lightweight files:

Track with Git:

Python scripts

training code

configs

evaluation scripts

experiment metadata


Avoid tracking:

datasets

checkpoints

model weights

logs


These should be handled with Git LFS or DVC.


---

3. Important .gitignore for ML Projects

Typical ML .gitignore:

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

This prevents huge files from entering the Git history.


---

4. Git LFS (Large File Storage)

Git LFS is used to store large files such as model weights or dataset archives.

Instead of storing files directly, Git stores a pointer file.

Install Git LFS

Linux

sudo apt install git-lfs

Mac

brew install git-lfs

Initialize LFS

git lfs install


---

Track Large Files

Example for model files:

git lfs track "*.pth"
git lfs track "*.pt"
git lfs track "*.onnx"
git lfs track "*.ckpt"

This creates a .gitattributes file.

Commit it:

git add .gitattributes
git commit -m "setup git lfs"

Now Git automatically stores large files using LFS.


---

5. Example Workflow with Git LFS

Add trained model:

git add model.pth
git commit -m "add trained model"
git push origin main

Git stores only a pointer, while the actual file is stored in LFS storage.


---

6. DVC (Data Version Control)

DVC is used to manage:

large datasets

model checkpoints

ML pipelines

reproducible experiments


Git tracks code, while DVC tracks data.


---

7. Install and Initialize DVC

Install:

pip install dvc

Initialize in project:

dvc init

Commit configuration:

git add .dvc
git commit -m "initialize dvc"


---

8. Versioning Datasets with DVC

Add dataset:

dvc add data/dataset

This creates a .dvc file.

Commit metadata:

git add dataset.dvc .gitignore
git commit -m "add dataset with dvc"

Actual data is stored outside Git.


---

9. Configure Remote Storage

DVC stores large data in remote storage such as:

AWS S3

Google Cloud

Azure

SSH servers

local storage


Example:

dvc remote add -d storage s3://ml-bucket/dvc-store

Push dataset:

dvc push


---

10. Pull Dataset on Another Machine

When someone clones the repository:

git pull
dvc pull

This downloads the dataset from remote storage.


---

11. Versioning Trained Models

Example:

dvc add models/resnet50.pth

Commit metadata:

git add models/resnet50.pth.dvc
git commit -m "add trained model"

Push model to storage:

dvc push


---

12. ML Experiment Tracking

Experiments change with:

hyperparameters

dataset versions

architectures

training schedules


Popular experiment tracking tools:

Tool	Purpose

MLflow	experiment tracking
Weights & Biases	visualization
TensorBoard	training metrics


Example:

pip install wandb
wandb init


---

13. Versioning Model Checkpoints

Typical structure:

models
 ├── epoch10.pth
 ├── epoch20.pth
 └── best_model.pth

Track best model:

dvc add models/best_model.pth


---

14. Reproducing Experiments

To reproduce results:

1. Clone repository


2. Pull dataset


3. Run training



Example:

git clone repo
git checkout experiment_branch
dvc pull
python train.py

This ensures full reproducibility.


---

15. Typical ML Development Workflow

Daily ML workflow usually looks like this:

1. Create experiment branch



git checkout -b experiment-resnet

2. Modify training code


3. Train model



python train.py

4. Track model



dvc add models/model.pth

5. Commit changes



git add .
git commit -m "train resnet model"

6. Push data and code



dvc push
git push origin experiment-resnet


---

16. Recommended Tools for ML Version Control

Tool	Purpose

Git	code versioning
Git LFS	large files
DVC	dataset versioning
MLflow	experiment tracking
Weights & Biases	visualization
TensorBoard	training metrics



---

🎯 Key Takeaway

The standard ML engineering workflow:

Git → version control for code
Git LFS → large model files
DVC → dataset + pipeline versioning
W&B / MLflow → experiment tracking

This combination enables reproducible and scalable ML pipelines.


---

If you want, I can also give you a 🔥 "ML Git Workflow used in companies like Google, Tesla, and OpenAI" which includes:

dataset versioning pipelines

experiment registry

model registry

CI/CD for ML

production deployment workflow.
