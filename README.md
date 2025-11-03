# langchain-daytona-data-analysis

This package contains the LangChain integration with DaytonaDataAnalysis

## Installation

```bash
pip install -U langchain-daytona-data-analysis
```

And you should configure credentials by setting the following environment variables:

* TODO: fill this out

## Chat Models

`ChatDaytonaDataAnalysis` class exposes chat models from DaytonaDataAnalysis.

```python
from langchain_daytona_data_analysis import ChatDaytonaDataAnalysis

llm = ChatDaytonaDataAnalysis()
llm.invoke("Sing a ballad of LangChain.")
```

## Embeddings

`DaytonaDataAnalysisEmbeddings` class exposes embeddings from DaytonaDataAnalysis.

```python
from langchain_daytona_data_analysis import DaytonaDataAnalysisEmbeddings

embeddings = DaytonaDataAnalysisEmbeddings()
embeddings.embed_query("What is the meaning of life?")
```

## LLMs

`DaytonaDataAnalysisLLM` class exposes LLMs from DaytonaDataAnalysis.

```python
from langchain_daytona_data_analysis import DaytonaDataAnalysisLLM

llm = DaytonaDataAnalysisLLM()
llm.invoke("The meaning of life is")
```
