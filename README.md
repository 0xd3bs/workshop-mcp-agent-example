# Orchestrator workflow example

This example shows an Orchestrator workflow which dynamically plans across a number of agents to accomplish a multi-step task.

It parallelizes the task executions where possible, and continues execution until the objective is attained.

This particular example is a student assignment grader, which requires:

- Finding the student's assignment in a short_story.md on disk (using MCP filesystem server)
- Using proofreader, fact checker and style enforcer agents to evaluate the quality of the report
- The style enforcer requires reading style guidelines from the APA website using the MCP fetch server.
- Writing the graded report to disk (using MCP filesystem server)

<img width="1650" alt="Image" src="https://github.com/user-attachments/assets/12263f81-f2f8-41e2-a758-13d764f782a1" />

## Changes from Original Repository

This fork includes several modifications to improve the project's usability and reduce external dependencies:

### Configuration Changes
- Removed Brave Search server dependency to eliminate the need for a Brave API key
- Modified agent configurations to work exclusively with `fetch` and `filesystem` servers
- Updated the configuration in `mcp_agent.config.yaml` to reflect these changes

### Agent Modifications
- Refactored the searcher agent to focus on analyzing provided URLs instead of performing web searches
- Updated the fact checker agent to work with local and fetched content
- Maintained the report writer agent's functionality with simplified server dependencies

### Code Improvements
- Added configuration validation checks in `main.py`
- Enhanced error handling for configuration file loading
- Improved logging for better debugging and monitoring

### Documentation
- Added detailed configuration instructions
- Updated agent descriptions to reflect their current capabilities
- Included information about removed dependencies

## Setup Instructions

1. Clone this repository
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Configure your API keys in `mcp_agent.secrets.yaml`:
   ```yaml
   anthropic:
     api_key: your-anthropic-api-key
   openai:
     api_key: your-openai-api-key
   ```
4. Run the example:
   ```bash
   python main.py
   ```

Note: This version does not require a Brave Search API key, making it easier to set up and run.
