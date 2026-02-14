# AI Coding Assistant (Claude Code Clone)

A terminal-based AI coding assistant built in TypeScript that autonomously performs coding tasks. This agent connects to Large Language Models (LLMs) to understand instructions, read codebase context, apply file edits, and execute shell commands iteratively until the task is complete.

## Features

- **Autonomous Agent Loop**: Maintains conversation context and executes multiple steps to solve complex problems.
- **File System Operations**: 
  - **Read**: access file contents to understand the codebase.
  - **Write**: create and modify files to implement changes.
- **Shell Integration**: Execute bash commands directly to run tests, manage files, or gather system information.
- **LLM Integration**: Built to work with OpenAI-compatible APIs (configured for Anthropic models via OpenRouter).

## Prerequisites

- [Bun](https://bun.sh) runtime (v1.2+)
- An API Key (e.g., from OpenRouter)

## Setup

1.  **Clone the repository**
2.  **Install dependencies**:
    ```bash
    bun install
    ```
3.  **Configure Environment**:
    Create a `.env` file in the root directory and add your API credentials:
    ```env
    OPENROUTER_API_KEY=your_api_key_here
    OPENROUTER_BASE_URL=https://openrouter.ai/api/v1
    ```

## Usage

Run the assistant by passing a prompt with the `-p` flag:

```bash
bun run app/main.ts -p "Read README.md and summarize its contents."
```

Or using the provided shell script:

```bash
./your_program.sh -p "Create a new file called hello.ts that prints 'Hello World'"
```

## How It Works

The assistant operates in a continuous loop:
1.  **Think**: Sends the current conversation history and available tools (Read, Write, Bash) to the LLM.
2.  **Act**: If the LLM requests a tool call, the agent parses the arguments and executes the corresponding function (file I/O or shell command).
3.  **Observe**:The tool's output is fed back into the conversation history.
4.  **Repeat**: The process continues until the LLM determines the task is complete or provides a final answer.
