# Papers
Research papers I find interesting, and other ideas. 


## Combining Masked Input and Autoregression 

- [Look Ahead or Look Around?
A Theoretical Comparison Between Autoregressive and Masked Pretraining](https://arxiv.org/pdf/2407.00935)

- [MEAP: Pay Less Attention to Learn More](https://arxiv.org/abs/2502.07490v1)


### Summary of MEAP from chat gpt o1:

The paper “Mask-Enhanced Autoregressive Prediction: Pay Less Attention to Learn More”  introduces a novel training paradigm—MEAP—that blends ideas from masked language modeling (MLM) into the conventional next-token prediction (NTP) framework used by decoder-only Transformers.

Key Ideas

-	Motivation:
Large language models often struggle to accurately retrieve key information from long contexts. MEAP is designed to improve in-context retrieval and long-context reasoning without changing the model architecture or incurring extra computational costs.
-	Method:
MEAP works by randomly masking a small fraction of input tokens and then applying the standard autoregressive (next-token) prediction on the resulting partially masked sequence. Unlike traditional MLM (which typically requires bidirectional attention or an encoder-decoder setup), MEAP leverages the same causal (unidirectional) Transformer used in NTP. This means that during both training and inference, no additional overhead is introduced.
-	Experimental Findings:
The authors report that MEAP significantly outperforms the standard NTP objective on tasks that require accurate retrieval of key information and effective long-context reasoning. Moreover, on commonsense reasoning tasks, MEAP performs on par or even better. Notably, when applied in a supervised fine-tuning setting—especially in scenarios where important information is “lost in the middle” of sequences—MEAP shows an improvement of up to 11.77 percentage points compared to conventional NTP.
-	Analysis:
The paper attributes these improvements to MEAP’s ability to foster more distinguishable attention scores. By masking a few tokens, the model is forced to focus on a reduced set of non-masked (and thus highly relevant) tokens, which helps it to concentrate on critical contextual signals while diminishing the noise from less relevant parts of the input.

Conclusion

Overall, MEAP presents a simple yet effective modification to the traditional autoregressive training method. By integrating a lightweight masking strategy into NTP, the approach enhances the model’s retrieval and reasoning capabilities without modifying the underlying Transformer architecture or adding extra computational burden.

This work positions MEAP as a promising training paradigm for large language models, combining the strengths of both masked and autoregressive methods in a unified and efficient framework.


### My Thoughts:

This might be interesting to use in fine tuning a model to perform well on coding and debugging, using generated outputs for solving coding
challenges with a rich text output language like Rust. Rust's compiler error messages are industry leading, although llm code gen for rust isn't
always great because the language often has very "fluid" type inferencing that makes it hard for the model to know how to type expressions.
