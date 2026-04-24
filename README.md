# Prompt Engineering Case Studies

This repository demonstrates practical applications of prompt engineering and iterative refinement using Large Language Models (LLMs).

Focus areas:
- Structured prompt design  
- Identifying and correcting model output issues  
- Iterative improvement of responses  
- Reducing hallucinations in LLM systems  

---

## Case Study 1: Improving Code Debugging with Prompt Iteration

### Problem
Given a Python function with logical errors, generate accurate debugging feedback and suggestions using an LLM.

---

### Example Code
```python
def sum_numbers(n):
    total = 0
    for i in range(n):
        total = i
    return total
Initial Prompt
Analyze the following Python code and provide feedback.
Issues with Initial Output
Output was partially correct but included incorrect reasoning (e.g., mentioning "integer overflow")
Explanation was not fully reliable
Lacked structured, step-by-step analysis
Suggestions were somewhat generic
Improved Prompt
Analyze the following Python code step-by-step. 
Identify logical errors, explain why they occur, and avoid incorrect assumptions. 
Provide a clear and accurate explanation. 
Suggest specific fixes and focus only on actual issues in the code.
Final Output Improvements
Removed incorrect reasoning (e.g., no mention of integer overflow)
Clearly identified the real issue: overwriting instead of accumulation
Provided accurate and structured explanation
Suggested correct fix using total += i
Output became more reliable and easier to understand
Actual Model Output (Phi via LM Studio)

The issue with the provided Python function lies in its logic, not syntax.
Inside the loop, total = i overwrites the value instead of accumulating it.
To fix this, replace it with total += i and adjust the loop range accordingly.

Key Learning

LLMs can generate partially correct but misleading explanations.

Prompt refinement plays a critical role in improving output quality by:

Eliminating incorrect assumptions
Improving reasoning accuracy
Increasing reliability of responses

Adding explicit constraints like "avoid incorrect assumptions" significantly improves results.

## Case Study 2: Reducing Hallucinations in RAG-Based Q&A
Problem

Generate accurate answers from documents using a Retrieval-Augmented Generation (RAG) system while avoiding hallucinated or unsupported information.

Scenario

The model is provided with retrieved document chunks as context and asked to answer a question.

Initial Prompt
Answer the question based on the given context.
Issues with Initial Output
Model included information not present in the context
Responses were partially correct but contained fabricated details
No indication when the answer was not found in the context
Output lacked consistency and grounding
Improved Prompt
Answer the question using only the provided context. 
If the answer is not present in the context, say "I don't know." 
Do not include any external knowledge. 
Provide a clear and concise answer based strictly on the context.
Final Output Improvements
Responses strictly grounded in retrieved context
Hallucinations significantly reduced
Model correctly responded with "I don't know" when context was insufficient
Output became more reliable and consistent
Example Behavior

Before Prompt Improvement:

The model generated additional details not present in the document.

After Prompt Improvement:

The answer was limited to the provided context or returned "I don't know" when insufficient information was available.

Key Learning

In RAG systems, prompt design is critical for controlling hallucinations.

Key improvements came from:

Explicitly restricting the model to use only retrieved context
Allowing the model to admit uncertainty ("I don't know")
Reducing ambiguity in instructions

Well-defined constraints significantly improve trustworthiness and reliability in LLM-based systems.

Tools Used
Python
Phi model (via LM Studio)
ChatGPT
Prompt Engineering Techniques
Retrieval-Augmented Generation (RAG)
