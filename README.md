Chain-of-Thought Distillation on Qwen-0.5B

This repository implements Parameter-Efficient Fine-Tuning (PEFT) to enhance the mathematical reasoning capabilities of small language models.

Research Objective
To investigate if low-rank adaptation (LoRA) is sufficient to induce Chain-of-Thought (CoT) reasoning patterns in sub-1B parameter models, making them viable for edge-device reasoning tasks.

Methodology
* **Model:** Qwen-2.5-0.5B-Instruct (Quantized to 4-bit via bitsandbytes)
* **Dataset:** GSM8K (Grade School Math)
* **Technique:** LoRA (Rank=16) targeting Q, K, V, and O projections.
* **Hardware:** Trained on NVIDIA T4 (via Google Colab).

Results
* **Behavioral Shift:** The fine-tuned model successfully adopted a step-by-step reasoning format ("First I calculate..."), replacing the baseline model's direct guessing behavior.
* **Accuracy:** Demonstrated correct arithmetic logic on unseen test questions.
* **Limitations:** The 0.5B parameter scale still limits complex arithmetic consistency.

Usage
The training notebook includes the full pipeline:
1. Loading the 4-bit quantized model.
2. Formatting the GSM8K dataset.
3. Training with `SFTTrainer`.
4. Inference testing.
