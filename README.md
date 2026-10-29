# AI Gateway Benchmark

AIMultiple benchmark of OpenRouter, SambaNova, TogetherAI, Groq and AI/ML API on Llama 3.1 8B. The study measures first-token latency, total latency and output-token count for short and long prompts.

> [Read the benchmark on AIMultiple](https://aimultiple.com/ai-gateway)

## Workload

Groq and SambaNova serve models on their own hardware, TogetherAI acts as both provider and gateway, and OpenRouter and AI/ML API route requests to external providers.

Short prompts average about 18 input tokens. Long prompts average about 203 and ask for an analysis across eight thematic areas. Each test ran 50 times per gateway in streaming mode at temperature 0.7, with a 0.5-second delay between runs. Failed runs (non-200 HTTP responses, timeouts, incomplete or malformed outputs) were excluded.

The platforms serve different Llama 3.1 8B variants, such as Instruct, Turbo and Instant. Results were normalized to compare inference-level optimizations, not model variation.

## Benchmark results

First-token latency in seconds, by prompt length:

| Platform | Short prompts | Long prompts |
| --- | ---: | ---: |
| Groq | 0.13 | 0.14 |
| SambaNova | 0.13 | 0.19 |
| OpenRouter | 0.40 | 0.45 |
| TogetherAI | 0.43 | 0.45 |
| AI/ML API | 0.84 | 0.90 |

OpenRouter's first token arrives slightly sooner than TogetherAI's, but its long-prompt total latency is 25 seconds against 11 seconds, with the same output-token count. SambaNova generated the most long-prompt tokens (1,997) and finished in 3 seconds.

## Scope

Results apply to the Llama 3.1 8B variants each platform served. Runs were sequential, so the figures do not cover peak throughput, and excluding failed runs favors platforms with stable streaming. The cost section lists per-token prices for Llama 4 Scout (17Bx16E), not the benchmarked model.

## Ownership

The benchmark implementation was developed for AIMultiple and belongs to AIMultiple. This repository contains a documentation summary. Source code and benchmark datasets are not distributed here.
