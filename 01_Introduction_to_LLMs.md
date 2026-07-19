**Introduction to Large Language Models (LLMs)**

These notes cover the basic ideas behind LLMs and related concepts.
Written for internship reference.

**What is an LLM?**

LLM stands for Large Language Model. It is a type of artificial
intelligence model that is trained on a very large amount of text data.
The model learns patterns in language so it can generate text, answer
questions, translate languages, write code, and do many other tasks.

The word "large" refers to two things. First, the amount of training
data is huge, sometimes hundreds of billions of words. Second, the model
itself has billions of parameters, which are internal numbers that it
adjusts during training.

Some well-known LLMs are GPT-4, Claude, Gemini, and LLaMA. These models
are not databases. They do not look up answers. They generate text based
on what they learned during training.

**How LLMs Work (High Level)**

At a high level, an LLM takes text as input and predicts what text
should come next. This sounds simple but it requires understanding
context, grammar, facts, and meaning all at once.

The training process involves showing the model massive amounts of text
and asking it to predict the next word over and over. Each time it makes
a wrong prediction, the model adjusts its parameters slightly to do
better next time. After billions of these adjustments, the model becomes
good at producing useful and coherent text.

During this training, the model also learns things like facts, reasoning
patterns, and how to follow instructions without being explicitly taught
those things separately.

**Tokens**

A token is a small piece of text. It is not always a full word. For
example, the word "running" might be split into two tokens: "run"
and "ning". Short common words like "the" or "is" are usually one
token.

LLMs do not process raw text directly. They first convert text into
tokens using a tokenizer, then convert those tokens into numbers, and
feed those numbers into the model.

Tokens matter because LLMs have a limit called a context window. This is
the maximum number of tokens the model can handle at once. GPT-4 Turbo,
for example, has a context window of 128,000 tokens. Claude 3.5 has a
context window of 200,000 tokens. The larger the context window, the
more text the model can read and respond to at once.

**Embeddings**

An embedding is a way of representing a word or a token as a list of
numbers, called a vector. This vector captures the meaning of the word
in a numerical form.

Words that have similar meanings end up with similar vectors. For
example, the vectors for "king" and "queen" will be closer to each
other than the vectors for "king" and "pizza". This is how the model
understands meaning, not by looking at letters but by working with these
numerical representations.

Embeddings are used at the start of the model when text is converted
into vectors. They are also used in search systems and recommendation
engines where you need to find similar items.

**Attention**

Attention is one of the most important ideas in modern LLMs. It was
introduced in the 2017 paper "Attention Is All You Need" by Vaswani et
al.

The idea behind attention is that when the model is processing a word,
it should be able to look at all other words in the input and decide
which ones are most relevant. For example, in the sentence "the cat sat
on the mat because it was tired", the word "it" refers to "cat".
The attention mechanism helps the model figure out this connection.

Each word creates three things: a query (what am I looking for?), a key
(what do I represent?), and a value (what information do I hold?). The
model computes a score between the query of one word and the keys of all
other words. High scores mean high relevance. The final representation
of a word is a weighted combination of all values, based on these
scores.

This is called self-attention because the sequence is attending to
itself. Multi-head attention means the model does this process multiple
times in parallel with different learned weights, so it can focus on
different types of relationships at the same time.

**Transformers**

The Transformer is the architecture that almost all modern LLMs are
based on. It was introduced in 2017 by a team at Google in the paper
mentioned above.

Before Transformers, the most common architectures were RNNs (Recurrent
Neural Networks) and LSTMs. These processed text word by word in order,
which was slow and made it hard to handle long documents. The
Transformer replaced this with self-attention, which can look at all
words at the same time. This made training much faster because it could
use parallel computation.

A Transformer has two main parts. The encoder reads the input and
creates a representation. The decoder generates the output token by
token. Many modern LLMs like GPT use only the decoder part.

A Transformer block includes a self-attention layer, a feed-forward
neural network layer, and normalization layers. These blocks are stacked
on top of each other, sometimes dozens of times. GPT-3, for example, has
96 layers.

**Training vs Inference**

**Training:**

Training is when the model learns. The model is shown huge amounts of
text and adjusts its parameters to get better at predicting the next
token. This process takes weeks or months on thousands of powerful GPUs.
It is very expensive. Training GPT-4 reportedly cost over \$100 million
in compute. Training happens only once per model version.

**Inference:**

Inference is when the trained model is used to generate a response. You
give it a prompt, and it produces output. This is much cheaper and
faster than training. When you use ChatGPT or Claude in a browser, you
are doing inference. Inference still needs powerful hardware but at a
much smaller scale compared to training.

A good way to think about it: training is like going to school for
years, and inference is like using what you learned to answer a
question.

**What is an API?**

API stands for Application Programming Interface. It is a way for one
software program to talk to another. When you use the OpenAI API or the
Anthropic API, your application sends a request to their servers with a
prompt, and the server sends back a response with the model\'s output.

APIs use a standard format. You send an HTTP request with your message,
your API key, and some settings like which model to use. You get back a
JSON response with the generated text.

This matters because most companies do not run their own LLM. They use
APIs from OpenAI, Anthropic, or Google and pay per token used. Building
on top of an API is much faster and cheaper than running your own model.

**Famous LLM Companies and Models**

**OpenAI -- GPT Series**

OpenAI was founded in 2015. Its most famous models are the GPT series.
GPT-4o is currently the most capable publicly available model from
OpenAI. OpenAI also released GPT-3.5 which powered the first version of
ChatGPT. OpenAI offers API access and the ChatGPT consumer product.
Microsoft has invested heavily in OpenAI and uses their models in Bing
and Copilot.

**Anthropic -- Claude Series**

Anthropic was founded in 2021 by former OpenAI researchers including
Dario Amodei and Daniela Amodei. Their model family is called Claude.
The current generation is Claude 3.5 and later Claude 3.7 and Claude 4
series. Anthropic focuses on AI safety and developed a technique called
Constitutional AI to make models more aligned with human values. Claude
is known for being very good at long documents, coding, and nuanced
reasoning.

**Google -- Gemini Series**

Google has been working on LLMs for a long time. They released LaMDA,
then PaLM, and now the Gemini series. Gemini 1.5 Pro and Gemini Ultra
are their top models. Gemini is natively multimodal, meaning it was
trained on text, images, audio, and video together. Google integrates
Gemini into Search, Workspace, and the Gemini app for consumers.

**Meta -- LLaMA Series**

Meta released the LLaMA series of open-source models. LLaMA 2 and LLaMA
3 can be downloaded and run locally, which makes them very popular with
researchers and developers. Meta does not charge for the weights. The
trade-off is that you need your own hardware to run them. LLaMA 3 70B is
competitive with many commercial models.

**Mistral**

Mistral AI is a French startup founded in 2023. They released several
efficient open-weight models like Mistral 7B and Mixtral 8x7B. Their
models are known for being fast and small while remaining very capable.
Mixtral uses a technique called Mixture of Experts (MoE) where only part
of the model activates for each token, which improves efficiency.

**Groq**

Groq is a hardware company, not a model company. This is what makes it
different from all the others listed above. Groq does not create its own
LLMs. Instead, it builds custom chips called Language Processing Units
(LPUs) that are specifically designed to run LLM inference very fast.

Normal AI companies run their models on GPUs made by NVIDIA. GPUs are
flexible and good at parallel operations, but they were originally
designed for graphics, not language. Groq\'s LPU is built from the
ground up for the sequential token-by-token generation that LLMs do
during inference.

The result is extremely fast output. Groq can serve Llama 3 70B at
around 284 tokens per second, compared to 30-40 tokens per second on
NVIDIA H100 GPUs. This is roughly 7 to 10 times faster. For applications
that need real-time responses, like voice AI, this matters a lot.

Groq offers a cloud service called GroqCloud where developers can call
models like Llama, Gemma, and Mistral through an API. The API is
compatible with OpenAI\'s format, so it is easy to switch. In December
2025, NVIDIA entered into a \$20 billion licensing deal with Groq, which
shows how significant their technology has become.

In summary: OpenAI, Anthropic, Google, Meta, and Mistral compete on
model quality. Groq competes on inference speed and efficiency. They are
solving different problems.
