 low-level code optimizations to make memory usage as efficient as possible.


GRPO
https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5080865


Takeaway:
- DeepSeek has proven that groundbreaking AI doesn’t have to come with an outrageous price tag
- making the best use of what’s available

High-Level:

- Training only what matters: Focusing on the most important parts of the model to reduce computation.
- Smart memory compression: Using less storage without losing performance.
- Efficient hardware use: Getting the most out of available resources instead of relying on cutting-edge chips.


## Architecture:

V3 not R1:

Mixture of experts (MoE) basics: The MoE architecture uses different subsets of its parameters to process different inputs. Each MoE layer contains a group of neural networks, or experts, preceded by a gating module that learns to choose which one(s) to use based on the input. In this way, different experts learn to specialize in different types of examples. Because not all parameters are used to produce any given output, the network uses less energy and runs faster than models of similar size that use all parameters to process every input.

DeepSeek-V3 is a mixture-of-experts (MoE) transformer that comprises 671 billion parameters, of which 37 billion are active at any moment. 


## Techniques:


1. Auxiliary-Loss-Free Load Balancing

- Each token (piece of text) is sent to a small set of experts, instead of engaging the entire model
- Only 5% of the model’s parameters were trained per token.
- This led to a 95% reduction in GPU usage compared to companies like Meta.
- Faster training at significantly lower costs, without losing accuracy.

2. Low-Rank Key-Value (KV) Joint Compression.

- The model compresses key and value vectors using a down-projection matrix
- During inference, only the compressed version is stored, significantly reducing memory requirements.


3. RL

A) Focused data
- focused on tasks that have clear, verifiable answers, such as math and coding problems.
- improve accuracy with fewer resources by focusing only on challenges that provided immediate, measurable feedback

B) GRPO
- 

4. Multi-head Latent Attention (MLA)

## Compute



V3 not R1:

The team trained the model in 2.79 million GPU hours — less than 1/10 the time required to train Llama 3.1 405B, which DeepSeek-V3 substantially outperforms — at an extraordinarily low cost of $5.6 million.