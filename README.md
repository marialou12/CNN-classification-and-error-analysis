# CNN-classification-and-error-analysis
This project builds a Convolutional Neural Network (CNN) to recognize handwritten digits using the MNIST dataset (70,000 grayscale images). Its core focus is deep error analysis, exploring where the model makes mistakes and how a single architectural modification shifts those errors.

## Project Structure

* **Part A: Setup and Data** — Downloads, prepares, normalizes, and splits the MNIST dataset (70,000 images, 28x28 pixels).
* **Part B: Build and Train Your Network** — Implementation of the baseline CNN architecture with a validation split and `EarlyStopping`.
* **Part C: Read the Mistakes** — Test set evaluation and detailed error analysis using a confusion matrix to find visually similar digit pairs (e.g., 4 vs 9, 7 vs 9).
* **Part D: Model Optimization & Reflection** — Comparative analysis introducing a single change (Deeper Layers or Stronger Dropout) to study how mistakes shift.

## Running the Notebook

1. Open the Jupyter Notebook:
   ```bash
   jupyter notebook "Final Project, Option 1.ipynb"
   ```
2. Run all cells in **Part A** to fetch the dataset from OpenML.
3. Complete the task blocks marked with `# TODO` in parts B, C, and D to build, evaluate, and compare your models.

##  Model Architectures & Workflow

### Model 1 (Baseline CNN)
The initial network structure consists of:
- **Input Layer:** `(28, 28, 1)` grayscale images.
- **Convolutional Layer:** 32 filters, 3x3 kernel, ReLU activation.
- **Pooling Layer:** Max Pooling 2x2.
- **Regularization:** Dropout (0.3).
- **Flattening & Dense Layers:** Flatten followed by a 64-unit ReLU layer.
- **Output Layer:** 10 units with Softmax activation.
- **Training:** Compiled with `adam` optimizer and `sparse_categorical_crossentropy` loss. Monitored with an `EarlyStopping` callback (patience=3) against validation loss.

### Model 2 (Option A: Deeper Network)
* To test our central question, Model 2 introduces architectural depth by adding a second convolutional block (**`Conv2D(64)`** + **`MaxPooling2D`**) right before the dropout and flattening phase. This allows the network to learn more abstract, detailed geometric features.


##  Key Results

### Metrics Comparison
* **Baseline Model Test Accuracy:** 98.63% *
* **Deeper Model (Option A) Test Accuracy:** 98.94% *

### Error & Confusion Matrix Analysis
* **Baseline Model Confusions:** The primary off-diagonal errors occurred when the model misclassified the digit **4 as a 9** and **7 as a 9**. This is common because handwritten variations often close the top loop of a 4 or curve the stem of a 7, making them structurally similar to a 9.
* **Deeper Model Confusions:** Adding the second convolutional block significantly reduced the confusion between **4 and 9**. The extra feature abstraction allowed the deeper network to successfully capture the subtle boundary lines separating the top loops of 4s and 9s, proving that architectural changes directly reshape error distributions.
  
## Ethical Considerations

Digit readers do not perform equally well for everyone. Handwriting conventions vary heavily across generational cohorts, regional schooling systems, and cultural backgrounds. A model trained heavily on one style (like standard Western MNIST) may read another less reliably. Confident misreadings on physical mail routing can lead to lost financial documents or delayed medical notices, disproportionately affecting under-represented demographics.

  
##  Project Reflection

* **What Worked Well:** The `EarlyStopping` callback functioned perfectly, halting training exactly when validation loss plateaued and saving computational time. The stratified split also kept our evaluation fair and balanced.
* **What Was Difficult:** Dissecting the confusion matrix highlighted how fragile standard feature maps can be when processing highly distorted human handwriting. Predicting how a deeper architecture would redistribute specific errors required close index scanning.
* **What Could Be Improved:** 
  * **Data Augmentation:** Introducing artificial rotations, minor scaling, and shifts during preprocessing would expose the model to wider handwriting variations.
  * **Error Profiling:** Rather than just counting errors, explicitly plotting the exact images where the model was highly confident yet wrong would provide better debugging insights before production.

