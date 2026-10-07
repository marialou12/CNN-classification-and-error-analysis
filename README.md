# CNN-classification-and-error-analysis
This project builds a Convolutional Neural Network (CNN) to recognize handwritten digits using the MNIST dataset (70,000 grayscale images). Its core focus is deep error analysis, exploring where the model makes mistakes and how a single architectural modification shifts those errors.

## Project Structure

* **Part A: Setup and Data** — Downloads, prepares, normalizes, and splits the MNIST dataset (70,000 images, 28x28 pixels).
* **Part B: Build and Train Your Network** — Implementation of the baseline CNN architecture with a validation split and `EarlyStopping`.
* **Part C: Read the Mistakes** — Test set evaluation and detailed error analysis using a confusion matrix to find visually similar digit pairs (e.g., 4 vs 9, 7 vs 9).
* **Part D: Model Optimization & Reflection** — Comparative analysis introducing a single change (Deeper Layers or Stronger Dropout) to study how mistakes shift.
  
* ### Running the Notebook

1. Open the Jupyter Notebook:
   ```bash
   jupyter notebook "Final Project, Option 1.ipynb"
   ```
2. Run all cells in **Part A** to fetch the dataset from OpenML.
3. Complete the task blocks marked with `# TODO` in parts B, C, and D to build, evaluate, and compare your models.

## Baseline Model Architecture

The initial network structure consists of:
- **Input Layer:** `(28, 28, 1)` grayscale images.
- **Convolutional Layer:** 32 filters, 3x3 kernel, ReLU activation.
- **Pooling Layer:** Max Pooling 2x2.
- **Regularization:** Dropout (0.3).
- **Flatenning & Dense Layers:** Flatten followed by a 64-unit ReLU layer.
- **Output Layer:** 10 units with Softmax activation.

## Key Insights & Ethical Considerations

* **Visual Confusions:** The project explores why certain pairs of numbers are naturally harder for computer vision models to distinguish due to overlapping geometric feature maps.
* **Ethical Risks:** Discussion on how regional handwriting styles, age gaps, and cultural variations under-represented in the MNIST dataset can lead to biased accuracy rates and real-world costs in critical automation systems (e.g., mail sorting or check processing).
