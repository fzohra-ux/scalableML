# Fine-Tuning Llama 3.2 1B for Code Generation

This project fine-tunes **Llama 3.2 1B** to become a better coding assistant using both **model-centric** and **data-centric** approaches.

---

##  Model-Centric Improvements

To improve the model itself, we used a **hyperparameter optimization** workflow with **Ray Tune**.  
We searched over key LoRA and training hyperparameters such as:

- Learning rate  
- LoRA rank (`r`)  
- LoRA alpha  

Ray Tune automatically tested multiple configurations and selected the best one based on training loss.  
This allowed us to systematically improve performance instead of manually guessing parameters.

---

##  Data-Centric Improvements

To make the model better at coding tasks, we changed the **training data**:

- We used the **CodeAlpaca dataset**, which contains coding instructions and solutions.
- We reformatted the dataset into a chat structure compatible with Llama models.
- This shift to coding-focused data improved the model’s ability to solve Python problems.

Future improvements could include:
- Adding more datasets (MBPP, HumanEval, CodeContests)
- Filtering or cleaning incorrect examples
- Creating more diverse function-based tasks

---

## Evaluation

We evaluated the fine-tuned model on **MBPP-style coding tasks** by:

1. Generating Python code for each prompt  
2. Executing the code against provided test cases  
3. Counting how many tasks passed all tests  

This gives a realistic measure of **functional correctness** rather than just text similarity.

---

##  Demo / URL

**HuggingFace Space:**  
https://huggingface.co/spaces/FatimaZh/iris
---

##  Summary

- **Model-centric:** Hyperparameter tuning improves how the model learns  
- **Data-centric:** Better, domain-specific datasets improve what the model learns  
- Together, these approaches significantly improved coding accuracy for our fine-tuned Llama model.
