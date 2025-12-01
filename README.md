# BetaFold – Protein Secondary Structure Prediction

BetaFold is a deep-learning–based web application that predicts the secondary structure of proteins (Helix, Beta Sheet, Coil) from amino-acid sequences provided in FASTA format. The model uses a hybrid **CNN–BiLSTM architecture** and is trained using curated data from the Protein Data Bank (PDB).

# 🔗 Project Link
Access the live application here:  
[((https://beta-fold-15696080.base44.app/))]
Please input a valid email so that you can sign in because it requires you to add a secutiry code that will be sent to your email

# What BetaFold Does
- Validates FASTA amino-acid sequences (accepts only valid residues).
- Predicts per-residue secondary structures (H, E, C).
- Shows interactive visualizations for the predicted structure.
- Provides short biological interpretations of helices, sheets, and coils.

# Key Features
- Secure login → prediction workflow  
- Deep-learning powered predictions (CNN-BiLSTM)  
- Interactive structure visualization  
- Clean and simple UI for fast analysis  

# Input Format Example
MVLSEGEWQLVLHVWAKVEADVAGHGQDILIRLFKSH
The output comes on the basis of whether it is a helix, coil and sheets.

Tech Stack
- Frontend: React  
- Backend: Python (Flask/FastAPI)  
- Model: TensorFlow/PyTorch  
- Dataset: PDB secondary structure labels

  Code isnt available due to system migration
  
