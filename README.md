# Model_Quantization_and_Optimization
Model optimization and quantization are both techniques used to make deep learning models faster and more efficient—especially important for deploying models on edge devices (e.g., phones, embedded systems). However, they focus on different aspects of model simplification.

📌 **1. Model Optimization**

**What it does:**  
Improves the computational efficiency of a neural network by restructuring or simplifying the computation graph.

**Techniques:**
- **Layer Fusion:** Combine consecutive operations (e.g., Conv + BatchNorm + ReLU).
- **Operator Folding:** Simplify or remove no-op operations.
- **Graph Pruning:** Remove unused parts of the network.
- **Constant Folding:** Precompute constant operations.

**Result:**  
Same numerical outputs but faster execution and lower memory usage.


📌 **2. Quantization**

**What it does:**  
Reduces the precision of weights and activations from floating-point (e.g., FP32) to lower bit representations (e.g., INT8 or FP16).

**Types:**
- **Post-Training Quantization:** Quantize a pre-trained model.
- **Quantization-Aware Training (QAT):** Simulate quantization during training to preserve accuracy.
- **Dynamic vs Static Quantization:** Whether scale/zero-point values are computed on-the-fly or precomputed.

**Result:**  
- Smaller model size  
- Faster inference (especially on hardware with INT8 support)  
- Slight loss in accuracy (often negligible with QAT)

📌 **3. Model Pruning**

**Summary in One Line:**  
Pruning removes unnecessary weights or neurons to make models smaller and faster without significantly affecting accuracy.

**What it does:**  
Eliminates less important connections or nodes in a neural network to reduce complexity and improve efficiency.

**Types:**
- **Unstructured Pruning:** Remove individual weights based on magnitude (e.g., smallest weights set to zero).
- **Structured Pruning:** Remove entire channels, filters, or neurons for better hardware compatibility.
- **Global vs Layer-wise Pruning:** Prune across the entire model or within each layer separately.
- **One-shot vs Iterative Pruning:** Perform pruning all at once or gradually over training steps.

**Result:**  
- Smaller model size  
- Lower computation cost  
- Potential drop in accuracy, often recoverable with fine-tuning

📌 **4. Knowledge Distillation**

**Summary in One Line:**  
Distillation transfers knowledge from a large, accurate model (teacher) to a smaller, faster one (student).

**What it does:**  
Trains a compact student model to mimic the output behavior of a larger, well-performing teacher model, aiming to retain accuracy while reducing size and latency.

**Types:**
- **Logit-Based Distillation:** Match the soft output probabilities (logits) from the teacher.
- **Feature-Based Distillation:** Match intermediate layer representations.
- **Response-Based Distillation:** Focus on final predictions or soft targets.
- **Self-Distillation:** The teacher and student share the same architecture (e.g., training one copy using another).

**Result:**  
- Smaller, faster models  
- Retained or even improved generalization  
- Works well in combination with pruning or quantization

