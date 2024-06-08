# Many-shot Jailbreaking
[Link to paper](https://www.anthropic.com/research/many-shot-jailbreaking)

### One-line elevator pitch

Can you get an LLM to ignore its safety guideline by prompting it with a large number of examples that violate the guideline

### Do they build their own model or do they use existing models?

They evaluate currently existing user-facing LLM products. Namely, the models they test are
1. Llama 2 70B
2. Mistral 7B
3. GPT-3.5
4. GPT-4
5. Claude 2.0

### A 500 word summary of what they are doing in the paper

### Open questions
1. The mechanism of Cautionary Warning Defence, and the failure of In-Context Defence indicates that in a model with a long context length, there is a fall-off in the ability for the first few tokens to control the output. This observation comes from the fact that CWD, which appends a cautionary phrase significantly outperforms ICD which initially starts with examples of non-cooperation, which indicates that with the growing size of the prompt, the model starts to ignore ICD examples. Is this a general observation about the behaviour of self-attention? Why would that happen? Or is it more of an implementation issue?
