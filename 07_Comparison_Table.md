# Comparison Table – LLM Summarization Task

Paper summarized: "Attention Is All You Need" – Vaswani et al. (2017)

All three models used the same prompt. See 03_Prompt_Used.md for the exact wording.

---

## Scores

| Criteria | ChatGPT (GPT-4o) | Gemini 1.5 Pro | Claude 3.5 Sonnet |
|---|---|---|---|
| Summary Quality | 8/10 | 7.5/10 | 8.5/10 |
| Accuracy | 9/10 | 8/10 | 9/10 |
| Conciseness | 8/10 | 7/10 | 8/10 |
| Hallucinations | None found | None found | None found |
| **Overall Score** | **8.3/10** | **7.5/10** | **8.5/10** |

---

## Observations

**ChatGPT (GPT-4o) – 8.3/10**

GPT-4o gave a clear and well-structured summary. It used a good analogy with the trophy and suitcase example, which made the concept of attention easy to understand. The summary hit all the main points: the problem with RNNs, what self-attention does, the translation results, and why the paper is important. One small issue was that it felt slightly more casual than the other two, which may not suit all academic contexts. No factual errors were found.

**Gemini 1.5 Pro – 7.5/10**

Gemini produced an accurate summary that covered the key ideas. It explained multi-head attention and gave the correct BLEU scores. However, the writing felt a bit more mechanical compared to GPT and Claude. It listed facts well but did not explain the significance of the paper as naturally. The English-to-French BLEU score it mentioned was 41.0, whereas the paper says 41.8. This is a minor inaccuracy but worth noting. Overall still a useful and honest summary.

**Claude 3.5 Sonnet – 8.5/10**

Claude gave the most technically detailed summary among the three. It mentioned positional encoding using sine and cosine functions, which the other two models skipped. It also correctly noted that the Transformer beat ensemble methods, not just single models, which shows better attention to the paper's actual claims. The writing was clear and the structure was logical. It stayed within the word limit and did not repeat itself. Scored highest overall.

---

## Score Notes

Hallucinations column: all three models produced factually accurate summaries. No made-up claims or wrong numbers were found in GPT or Claude. Gemini had one minor score difference (41.0 vs 41.8 BLEU) which could be rounding or a small error.

Scores are based on manual review comparing each summary against the original abstract and paper content.
