--- 
layout: post 
title: "LLM Evaluation Benchmark"
date: 2024-07-06 
categories: LLMs, evaluation 
---

#AI #LLM 

**Table of Contents **
* [[#Math & Reasoning]]
	* [[#GSM8K]]   
	* [[#MATH]] 
	* [[#MathQA]] 
	* [[#CommonsenseQA]] 
	* [[#Multi-LogiEval]] 
	* [[#HOTPOT QA]] 
	* [[#STRATEGYQA]] 
* [[#Truthfulness]] 
	* [[#TruthfulQA]] 
	* [[#HaluEval]] 
* [[#Code]] 
	* [[#HumanEval]] 
	* [[#BigCodeBench]] 
	* [[#ODEX]] 
* [[#MMLU]]  
* [[#MMLU-Pro]] 
* [[#Instruction-Following]] 
	* [[#IFEval]]
* [[#Conclusion]] 

As the capabilities of Large Language Models (LLMs) continue to evolve, many traditional evaluation benchmarks may require updates. With the rapid progress of these models, researchers are increasingly introducing new evaluation datasets. However, the specific dimensions these datasets assess in the models are often unclear. In this blog, I will explore a series of commonly referenced evaluation datasets and highlight the particular aspects of model capabilities they were designed to assess even though I may not cover all available datasets.

## Math & Reasoning

### GSM8K

[GSM8K](https://arxiv.org/abs/2110.14168) (Cobbe et al., 2021), developed by OpenAI, is a dataset consisting of a variety of grade school math word problems. It's used to probe the informal reasoning ability of LLMs. These problems require between 2 and 8 steps to solve, and solutions mainly involve a sequence of basic arithmetic calculations. In fact, a proficient middle school student should be able to solve every problem.

There are 5 principles for this dataset:

- **High Quality** It relies on human workers to create problems, resulting in fewer than 2% of problems containing errors.
- **High Diversity** It encompasses a wide range of diverse problems and purposefully excludes problems that are derived from the same linguistic templates.
- **Moderate Difficulty** This evaluation dataset is of medium-level difficulty. Most problems can be solved without explicitly defining a variable.
- **Natural Language Solutions** The questions in this dataset are in natural language descriptions, not pure mathematical expressions. This natural language format is likely more universally applicable.

The examples of GSM8K are as follows:

![[Untitled 14.png]]

Fig 1. GSM8K Examples(Image Source: [Cobbe et., 2021](https://arxiv.org/abs/2110.14168))

### MATH

[MATH](https://arxiv.org/abs/2103.03874) (Hendrycks et al., 2021) comprises 12,500 problems, with 7,500 for training and 5,000 for testing, derived from high school math competitions. These problems encompass a variety of subjects and difficulty levels. The seven subjects include Prealgebra, Algebra, Number Theory, Counting and Probability, Geometry, Intermediate Algebra, and Precalculus. The dataset assigns each problem a difficulty level ranging from `1` to `5`, facilitating the assessment of performance across various subjects and difficulty levels. The examples of MATH are as follows:

![[Untitled 1.png]]

Fig 2. MATH Examples(Image Source: [Hendrycks et al., 2021](https://arxiv.org/abs/2103.03874))

### MathQA

[MathQA](https://arxiv.org/abs/1905.13319) (Amini et al., 2019) is a large-scale, diverse dataset of 37K English multiple-choice math word problems. It covers multiple math domain categories by modeling operation programs corresponding to word problems found in the AQuA dataset (Ling et al., 2017). The examples of MathQA looks as follows:

![[Untitled 2.png]]

Fig 3. MathQA Example(Image Source: [Amini et al., 2019](https://arxiv.org/abs/1905.13319))

### CommonsenseQA

[CommonsenseQA](https://arxiv.org/abs/1811.00937) (Talmor et al., 2018) is a dataset specifically created for commonsense question answering. This dataset consists of questions that typically require complex semantics and prior knowledge. With 12,247 questions in total, it's a robust tool for testing the commonsense reasoning abilities of LLMs and is structured in a multiple-choice format. Here are a few examples from CommonsenseQA:

![[Untitled 3.png]]

Fig 4. CommonsenseQA Examples(Image Source: [Talmor et al., 2018](https://arxiv.org/abs/1811.00937))

### Multi-LogiEval

[Multi-LogiEval](https://arxiv.org/abs/2406.17169) (Patel et al., 2024) is a comprehensive evaluation dataset. It encompasses multi-step logical reasoning with a variety of inference rules and depths. The dataset covers three logical types: propositional, first-order, and non-monotonic. It includes 1.6k high-quality instances that cover more than 30 inference rules and over 60 combinations of these rules at various depths.

The objective of this evaluation dataset is to present a preliminary analysis of the LLMs' ability to perform multi-step logical reasoning and to demonstrate their failures even with simple reasoning tasks. In Multi-LogiEval, the context represents a natural language story consisting of logical statements, and the models have to determine whether the story entails a conclusion given in the question.

The examples of datasets are as follows:

![[Untitled 4.png]]

Fig 5. Multi-LogiEval Examples (Image Source: [Patel et al., 2024](https://arxiv.org/abs/2406.17169))

### HOTPOT QA

[HOTPOT QA](https://arxiv.org/abs/1809.09600) (Yang et al., 2018) is designed to test a QA system’s ability to perform multi-hop reasoning. The system must reason with information from more than one document to arrive at the answer. This dataset includes 113k Wikipedia-based question-answer pairs featuring the following key points:

- The questions require finding and reasoning over multiple supporting documents to answer.
- The questions are diverse and not constrained to any pre-existing knowledge bases or schemas.
- The dataset includes sentence-level supporting facts necessary for reasoning, allowing QA systems to reason with strong supervision and explain their predictions.
- The dataset includes a new type of questions: comparison questions. These test LLMs' ability to extract relevant facts and perform necessary comparisons.

The example of HOTPOT QA is as follows:

![[Untitled 5.png]]

Fig 6. HOTPOT QA Example (Image Source: [Yang et al., 2018](https://arxiv.org/abs/1809.09600))

### STRATEGYQA

[STRATEGYQA](https://arxiv.org/abs/2101.02235) (Geva et al., 2021) is a question-answering benchmark where the required reasoning steps are implicit in the question and need to be inferred using a strategy. It is designed to test the reasoning ability of LLMs. The difference from other multi-hop reasoning datasets is that the required steps for answering the question in StrategyQA are not explicit.

The dataset contains 2,780 examples, each with a strategy question, its decomposition, and evidence paragraphs.

The examples of strategy questions are as follows:

![[Untitled 6.png]]

Fig 7. Strategy Questions Examples (Image Source: [Geva et al., 2021](https://arxiv.org/abs/2101.02235))

## Truthfulness

### TruthfulQA

[TruthfulQA](https://arxiv.org/abs/2109.07958)(Lin, et al., 2021) measures whether the responses from LLMs to questions are truthful. The benchmark consists of 817 questions across 38 categories, including law, finance, health, and politics. Most questions are one sentence long with a median length of 9 words. TruthfulQA is intended as a zero-shot benchmark and has two tasks: generation and multiple-choice.

For the generation task, LLMs generate a full-sentence answer given a prompt and question. For the multiple-choice task, it uses the same questions but tests LLMs on a multiple-choice variation. Some examples of TruthfulQA are as follows:

![[Untitled 7.png]]

Fig 8. TruthfulQA Benchmark Examples([Lin, et al., 2021](https://arxiv.org/abs/2109.07958))

### HaluEval

[HaluEval](https://arxiv.org/abs/2305.11747) (Li et al., 2023) is a benchmark for LLMs to evaluate hallucination. It covers 5,000 general user queries with ChatGPT responses and 30,000 task-specific examples from three tasks: question answering, knowledge-grounded dialogue, and text summarization. It is created in two ways: 1) automatic generation and 2) human annotation.

The examples of HaluEval are as follows :

![[Untitled 8.png]]

Fig 9. HaluEval Benchmark Examples ([Li et al., 2023](https://arxiv.org/abs/2305.11747))

## Code

### HumanEval

[HumanEval](https://arxiv.org/abs/2107.03374) (Chen et al., 2021) is an evaluation dataset consisting of 164 human-written problems to test the functional correctness of model-generated code. Each problem contains a function signature, docstring, body, and several unit tests, with an average of 7.7 tests per problem. The example of the dataset is as follows:

![[Untitled 9.png]]

Fig 10. HummanEval Examples(Image Source: [Chen et al., 2021](https://arxiv.org/abs/2107.03374))

### BigCodeBench

[BigCodeBench](https://arxiv.org/abs/2406.15877) (Zhuo et al., 2024) is used to challenge LLMs to invoke multiple function calls as tools from 139 libraries and 7 domains for 1,140 fine-grained programming tasks. This benchmark is constructed through three stages: Data Synthesis, Semi-automatic Program Refactoring and Testing Case Generation, and Human Curation. Let’s see some example data from the HF Dataset Viewer:

**Code Completion**

```Python
import itertools
from random import shuffle

def task_func(numbers=list(range(1, 3))):
    """
    Calculates the average of the sums of absolute differences between each pair of consecutive numbers 
    for all permutations of a given list. Each permutation is shuffled before calculating the differences.

    Args:
    - numbers (list): A list of numbers. Default is numbers from 1 to 10.

    Returns:
    float: The average of the sums of absolute differences for each shuffled permutation of the list.

    Requirements:
    - itertools
    - random.shuffle

    Example:
    >>> result = task_func([1, 2, 3])
    >>> isinstance(result, float)
    True
    """
```

**Natural Language Instruction**

````Markdown
Calculates the average of the sums of absolute differences between each pair of consecutive numbers for all permutations of a given list. Each permutation is shuffled before calculating the differences. Args: - numbers (list): A list of numbers. Default is numbers from 1 to 10.
The function should output with:
    float: The average of the sums of absolute differences for each shuffled permutation of the list.
You should write self-contained code starting with:
```
import itertools
from random import shuffle
def task_func(numbers=list(range(1, 3))):
```
````

### ODEX

[ODEX](https://arxiv.org/abs/2212.10481) (Wang et al., 2022) is an open-domain execution-based dataset with 1,707 test cases for 945 NL-Code pairs from the CoNaLa and MCoNaLa datasets. It covers 79 libraries, with 53.4% of the problems using at least one library. The queries in the dataset are diverse, containing four different languages. The examples of the dataset areas are shown as follows:

![[Untitled 10.png]]

Fig 11. ODEX Examples(Image Source: Wang et al., 2022)

## MMLU

[MMLU](https://arxiv.org/abs/2009.03300) (Hendrycks et al., 2020) is a benchmark for measuring an LLM's multitask performance. This evaluation dataset covers 57 tasks, including elementary mathematics, US history, computer science, law, and more. It consists of multiple-choice questions, totaling 15,908 questions. The questions are manually collected by graduate and undergraduate students from online sources. The examples of the dataset are as follows:

![[Untitled 11.png]]

Fig 12. MMLU Examples(Image Source: Hendrycks et al.,2020)

### MMLU-Pro

[MMLU-Pro](https://arxiv.org/abs/2406.01574) (Wang et al., 2024) is an advanced dataset that builds on the primarily knowledge-based MMLU benchmark. It introduces more complex, reasoning-intensive questions and increases the number of answer choices from four to ten. Examples of the dataset are as follows:

![[Untitled 12.png]]

Fig 13: MMLU-Pro Examples(Image Source: Wang et al.,2024) 

## Instruction-Following

### IFEval

[IFEval](https://arxiv.org/abs/2311.07911) (Zhou et al., 2023) is an approach for evaluating the proficiency of LLMs in instruction following. The metric focuses on a distinct category of instructions termed “verifiable instructions,” defined as instructions like “write 450 to 500 words” or “your entire output should be in JSON output.” The examples of IFEval are as follows:
![[Untitled 13.png]]
Fig14：IFEval Examples(Image Source: [Zhou et al.,2023](https://arxiv.org/abs/2311.07911))
## Conclusion

In this blog, I investigate many popular evaluation benchmarks, though I do not cover all of them. Some are recently released, while others are older but still used to evaluate today’s LLMs. Proper evaluation of LLMs is both important and difficult. I hope these benchmarks can inspire you to create more valuable evaluation datasets.

Future work may involve creating more nuanced benchmarks to better capture the diverse capabilities and limitations of LLMs. Continuous updates to these benchmarks will be essential to keep pace with the rapid advancements in AI.