# langchain-daytona-data-analysis

This package provides the `DaytonaDataAnalysisTool` - LangChain tool integration that enables agents to perform secure Python data analysis in a sandboxed environment. It supports multi-step workflows, file uploads/downloads, and custom result handling, making it ideal for automating data analysis tasks with LangChain agents.

## Installation

```bash
pip install -U langchain-daytona-data-analysis
```
The `daytona` package must also be installed to use `DaytonaDataAnalysisTool`:
```bash
pip install -U daytona
```

You must configure credentials for Daytona. You can do this in one of three ways:

1. Set the `DAYTONA_API_KEY` environment variable:
	```bash
	export DAYTONA_API_KEY="your-daytona-api-key"
	```

2. Add it to a `.env` file in your project root:
	```env
	DAYTONA_API_KEY=your-daytona-api-key
	```

3. Pass the API key directly when instantiating `DaytonaDataAnalysisTool`:
	```python
	from langchain_daytona_data_analysis import DaytonaDataAnalysisTool

	tool = DaytonaDataAnalysisTool(daytona_api_key="your-daytona-api-key")
	```

## Instantiation

Import and instantiate the tool:

```python
from langchain_daytona_data_analysis import DaytonaDataAnalysisTool
from daytona import ExecutionArtifacts

 # Optionally, you can pass an on_result callback.
 # This callback lets you apply custom logic to the data analysis result.
 # For example, you can save outputs, display charts, or trigger other actions.
def process_data_analysis_result(result: ExecutionArtifacts):
	print(result)

tool = DaytonaDataAnalysisTool(
	daytona_api_key="your-daytona-api-key",
	on_result=process_data_analysis_result
)
```

## Usage

`DaytonaDataAnalysisTool` can be used in three ways:


### Direct Invocation with Args

```python
tool.invoke({'data_analysis_python_code': "print('Hello World')"})
```

### Invocation with ToolCall

```python
model_generated_tool_call = {
    "args": {'data_analysis_python_code': "print('Hello World')"},
    "id": "1",
    "name": tool.name,
    "type": "tool_call",
}

tool.invoke(model_generated_tool_call)
```

### Usage Inside an Agent

```python
from langchain.agents import create_agent
from langchain_anthropic import ChatAnthropic

model = ChatAnthropic(
    model_name="claude-haiku-4-5-20251001",
    temperature=0,
    max_tokens_to_sample=1024,
    timeout=None,
    max_retries=2,
    stop=None
)

agent = create_agent(model, tools=[tool])
```
