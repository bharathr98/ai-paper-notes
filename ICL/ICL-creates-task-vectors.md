# In-Context Learning Creates Task Vectors
[Link to paper](https://arxiv.org/abs/2310.15916)

### One-line elevator pitch

Paper shows that ICL seeks an element in a linear hypothesis class by calculating a task vector from examples that minimises empirical risk. 

### Do they build their own model or do they use existing models?

They evaluate currently existing user-facing LLM products. Namely, the models they test are
1. Pythia 2.8B
2. Pythia 6.9B
3. Pythia 12B
4. Llama 7B
5. Llama 13B
6. Llama 30B
7. GPT-J 6B

### A 500 word summary of what they are doing in the paper
It is yet an unsettled debate on how LLMs implement ICL. This paper advocates for ICL creating task vector theta from the in-context sample S such that the prompt x gets mapped to the response through some function f(x, theta(S)). 
In order for this to hold true, the task vector theta(S) should be independent of the prompt x. The most straightforward method to check for that is to mask attention to the token x. But they notice a significant drop in performance and thus instead they use a dummy prompt x' and then demonstrate that the task vector remains morally the same no matter what the dummy prompt x' is. 

The full "pipeline" of the experiment is as follows. The in-context sample S consists of token pairs separated by the separator "→". For example, pineapple→yellow. They prompt the LLM with a list of sample pairs (unclear on how many samples a prompt contains), followed by a dummy pair x'→. They let the transformer process this input however it does up to the Lth layer. At the Lth layer, they extract the vector representing the last token →. This forms the task vector theta(S,L). Now they prompt the LLM with only the target prompt as x→, let the LLM do its thing up to layer L, and at the Lth layer replace the vector representing → with theta(S,L), and then let the LLM do it thing and provide the output. 

_Prompt to myself - there is also some kind of an interference study they talk about in section 5. What is it about? Why is it needed?_

### Tasks for myself
1. Understand in detail how t-SNE works

### Unanswered questions about the paper
1. How many examples does the sample S contain? Do they keep it constant or is it varied? How does it perform as a function of the number of prompts?

### Open questions
1. Does this generalise to the case of multi-token associations?
2. Why is the last letter task significantly worse than other logical tasks?
