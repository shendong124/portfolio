
#RNA 3D Structure Prediction - Model Summary

**Model Type**: Graph Neural Network (GNN)  
**Architecture**: 2-layer GCNConv + Fully Connected output  
**Target**: Predict 3D coordinates of each RNA residue

---

##Model Features

**Node Features (per residue):**
- Primary sequence (one-hot encoded): D_seq = 4
- K-mer features: D_kmer = [len(kmer_feature_names)]
- Dot-bracket structure vector: 3
- MFE (Minimum Free Energy): 1
- Entropy (from MSA): 1
- PSSM (Position-Specific Scoring Matrix): 5  
**→ Total node feature dimension: [x_dim]**

**Edge Construction:**
- Sequential residue connections (i, i+1)
- Base-pairing edges from BPPM (threshold > 0.5)
- Mutual Information edges from MSA (threshold > 0.0)
- All edges are bidirectional with scalar weights

---

##Hyperparameters

| Hyperparameter       | Value                     |
|----------------------|---------------------------|
| Hidden dimension     | 128                       |
| Learning rate        | 0.0005                    |
| Epochs               | 20                        |
| Batch size           | 1                         |
| Loss function        | Coord MSE + 0.5 × Distance MSE |
| Optimizer            | Adam                      |

---

##Training Metrics

| Epoch | Loss     | TM-score |
|-------|----------|----------|
| 01    | 5050.04  | 0.5177   |
| 02    | 5606.62  | 0.6033   |
| 03    | 4063.89  | 0.6642   |
| 04    | 1874.56  | 0.7138   |
| 05    | 3654.47  | 0.6911   |
| 06    | 766.03   | 0.7434   |
| 07    | 1310.03  | 0.7524   |
| 08    | 305.51   | 0.7661   |
| 09    | 294.18   | 0.7835   |
| 10    | 3441.85  | 0.7093   |
| 11    | 1135.16  | 0.7611   |
| 12    | 356.19   | 0.7927   |
| 13    | 392.70   | 0.8027   |
| 14    | 468.89   | 0.8023   |
| 15    | 175.00   | 0.8135   |
| 16    | 178.41   | 0.8184   |
| 17    | 187.85   | 0.8199   |
| 18    | 139.44   | 0.8275   |
| 19    | 189.96   | 0.8254   |
| 20    | 152.51   | 0.8316   |

---

##Validation Result

**Average TM-score on validation set**: **0.8159**
