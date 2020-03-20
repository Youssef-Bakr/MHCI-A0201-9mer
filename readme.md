# Objective
Evaluate several MHC-I epitope prediction algorithms (IEDB ANN, MHCFlurry, and NetMHCpan-BA) in prediction of high affinity MHC-I binders (IC50 < 500 nM) for human HLA-A02:01 9-mer dataset.

# Data Sources

1. Dataset with Experimental IC50 obtained from [IEDB](http://tools.immuneepitope.org/mhci/download/)
2. IEDB ANN4.0, NetMHCpan-BA4.0, NetMHCpan-EL4.0 predictions performed on [IEDB website](http://tools.immuneepitope.org/mhci/)
3. MHCFlurry1.4.3 prediction performed using [MHCFlurry Python Library](https://github.com/openvax/mhcflurry)

# Main Findings

## 1. Linearity of predicted IC50 vs experimental IC50 exists on a "grand" scale

### ANN: ln(predicted) vs ln(experiment) 
![ANN](https://github.com/xinyu-dev/MHCI-A0201-9mer/blob/master/pics/4.png)

### MHCFlurry: ln(predicted) vs ln(experiment) 
![MHCFlurry](https://github.com/xinyu-dev/MHCI-A0201-9mer/blob/master/pics/5.png)

### NetMHC4.0-BA: ln(predicted) vs ln(experiment) 
![NetMHC4.0-BA](https://github.com/xinyu-dev/MHCI-A0201-9mer/blob/master/pics/6.png)

## 2. Prediction of "affinity bins" is more accurate for binders with IC50 > 500 nM. Accuracy for binders < 500 nM is around 50%

### Accuracy Plot
![binaccuracy](https://github.com/xinyu-dev/MHCI-A0201-9mer/blob/master/pics/14a.png)

### Confusion Matrix Plot
![confusion](https://github.com/xinyu-dev/MHCI-A0201-9mer/blob/master/pics/13.png)

### ROC plot

#### ROC plot considering all 4 bins (All data, cutoff=500 nM)
![ROC](https://github.com/xinyu-dev/MHCI-A0201-9mer/blob/master/pics/15.png)

AUC Values: 
- ANN:           0.9643469790128615
- MHCFlurry:     0.9676191738052338
- NetMHCpan-BA:  0.9687774127471976
- NetMHCpan-EL:  0.9492001330979879

#### ROC plot considering data with experimental IC50 <500 nM (IC50 in (0, 500]: cutoff=50 nM)
![ROC](https://github.com/xinyu-dev/MHCI-A0201-9mer/blob/master/pics/16.png)

AUC Values: 
- ANN:           0.8243181284259984
- MHCFlurry:     0.8394962803445576
- NetMHCpan-BA:  0.8393071652310102
- NetMHCpan-EL:  0.7591869616288176
