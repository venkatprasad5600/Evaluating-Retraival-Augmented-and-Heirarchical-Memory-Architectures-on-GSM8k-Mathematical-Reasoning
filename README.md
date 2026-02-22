# Evaluating-Retraival-Augmented-and-Heirarchical-Memory-Architectures-on-GSM8k-Mathematical-Reasoning

# Research Objective

Large Language Models often struggle with multi-step mathematical reasoning.
This project evaluates whether:
Flat retrieval augmentation
Hierarchical memory (episodic + failure tracking)
can improve mathematical reasoning accuracy on GSM8K compared to a standard LLM baseline.

# Experimental Setup

1) Model: LLaMA 3.1 8B (via API)
2) Dataset: GSM8K (test subset = 180)
3) Retrieval DB: 250 training examples
4) Embedding Model: all-MiniLM-L6-v2 (384-dim)
5) Similarity Metric: Inner Product (FAISS)
6) Temperature: 0.1
7) Max Tokens: 200

# Architectures Compared
1️) Baseline LLM

Direct prompt-based reasoning.

2️) Flat Retrieval

FAISS semantic search
Top-K similar examples injected into prompt
Few-shot augmentation

3️) Hierarchical Memory

Episodic store (correct high-confidence reasoning)
Failure memory (error hints)
Dynamic memory updates during evaluation

# Results
   
System          	    Accuracy	        Avg Latency	          Avg Tokens
Baseline	            47.22%	            1.95s	              289.9
Flat Retrieval	      55.00%	            1.76s	              720.0
Hierarchical Memory	  46.67%	            2.02s	              684.8

# Key Findings

✔ Flat retrieval improved accuracy by +7.78% absolute
✔ Retrieval significantly increased token usage (~2.5× baseline)
✔ Hierarchical memory did NOT outperform baseline in this configuration
✔ Simple retrieval > naive memory accumulation

# Core Insight

Retrieval provides immediate contextual grounding.
Hierarchical memory requires better:
Memory selection
Confidence estimation
Failure reasoning modeling
Naively storing past reasoning is insufficient.

# Conclusion

Flat retrieval significantly improves reasoning performance on GSM8K.
Hierarchical memory design requires more sophisticated confidence modeling to outperform baseline LLM reasoning.
This project demonstrates controlled evaluation of retrieval and memory architectures for mathematical reasoning.
