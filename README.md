
# AGENT

A TypeScript-based AI agent that runs from the terminal, uses LLM tool calling, and can interact with files and the shell.

The project is designed as an experimental agent framework with a focus on **tool use, multi-turn interactions, and evaluating agent behavior**.

## ✨ Features

* 🤖 LLM-powered agent using the Vercel AI SDK
* 🔌 OpenAI model provider
* 🛠️ Tool calling with structured inputs
* 📁 File-system tooling
* 💻 Shell command tooling
* ✅ Runtime validation with Zod
* 🖥️ Interactive terminal UI using React + Ink
* 📊 Agent tracing and evaluation with LMNR
* 🧪 Dedicated evaluations for tools and multi-turn agent behavior
* 📦 Installable as an `agi` CLI command

## 🏗️ Architecture

                ┌─────────────────────┐
                │     CLI / User      │
                └──────────┬──────────┘
                           │
                           ▼
                ┌─────────────────────┐
                │  React + Ink CLI    │
                └──────────┬──────────┘
                           │
                           ▼
                ┌─────────────────────┐
                │      AI SDK         │
                │       `ai`          │
                └──────────┬──────────┘
                           │
                 ┌─────────┴──────────┐
                 ▼                    ▼
          OpenAI provider       Other provider
        @ai-sdk/openai          e.g. Anthropic
                 │
                 ▼
             LLM / Agent
                 │
        ┌────────┼────────┐
        ▼        ▼        ▼
      Shell    Files    Other tools
        │
        ▼
     shelljs

                 │
                 ▼
          Laminar / LMNR
       tracing + evaluation



## 🧰 Tech Stack

| Package          | Purpose                                              |
| ---------------- | ---------------------------------------------------- |
| `ai`             | LLM application framework and tool calling           |
| `@ai-sdk/openai` | OpenAI provider for the AI SDK                       |
| `zod`            | Runtime schema validation and structured tool inputs |
| `shelljs`        | Shell and filesystem operations                      |
| `ink`            | React-based terminal UI                              |
| `react`          | Component model used by Ink                          |
| `ink-spinner`    | Terminal loading indicators                          |
| `@lmnr-ai/lmnr`  | LLM tracing and agent evaluation                     |
| `typescript`     | Type-safe application development                    |
| `tsx`            | Running TypeScript directly during development       |
| `@biomejs/biome` | Formatting and linting                               |

## 🚀 Getting Started

### Prerequisites

* Node.js
* npm
* An OpenAI API key

### Installation

Clone the repository:

```bash
git clone <repository-url>
cd agi
```

Install dependencies:

```bash
npm install
```

Create an environment file:

```bash
cp .env.example .env
```

Add your API key to `.env`:

```env
OPENAI_API_KEY=your_api_key_here
```

> Never commit your `.env` file or API keys to Git.

## ▶️ Running the Agent

Start the agent:

```bash
npm start
```

For development with automatic reload:

```bash
npm run dev
```

## 🏗️ Building

Compile the TypeScript project:

```bash
npm run build
```

The compiled application is placed in `dist/`.

The package also exposes a CLI command:

```bash
agi
```

## 🛠️ Agent Tools

The agent can interact with external resources through tools.

### File tools

File tools allow the agent to inspect and work with files in the project environment.

Example tasks:

```text
"Find all TypeScript files in this repository."

"Read package.json and explain the dependencies."

"Find every TODO in the source code."
```

### Shell tools

Shell tools allow the agent to execute shell operations through `shelljs`.

Example tasks:

```text
"List the files in the current directory."

"Find all files containing the word TODO."

"Show me the current git status."
```

> ⚠️ Shell access gives an agent significant capabilities. Do not run an agent with unrestricted shell access against sensitive or untrusted environments.

## 🧪 Evaluations

Agent behavior is evaluated using LMNR.

Run the default evaluation:

```bash
npm run eval
```

Run the file-tool evaluations:

```bash
npm run eval:file-tools
```

Run the shell-tool evaluations:

```bash
npm run eval:shell-tools
```

Run the multi-turn agent evaluation:

```bash
npm run eval:agent
```

The evaluations are intended to test whether the agent correctly uses tools and produces the expected results across different interactions.

## 📂 Project Structure

```text
.
├── src/
│   ├── index.ts
│   └── ...
├── evals/
│   ├── file-tools.eval.ts
│   ├── shell-tools.eval.ts
│   └── agent-multiturn.eval.ts
├── dist/
├── package.json
├── tsconfig.json
├── tsconfig.build.json
├── .env
└── README.md
```

## 🔑 Environment Variables

| Variable         | Description                          |
| ---------------- | ------------------------------------ |
| `OPENAI_API_KEY` | API key used to access OpenAI models |

Additional environment variables may be required as tracing, evaluation, or additional providers are configured.

## 🔭 Roadmap

Potential areas for development:

* [ ] Additional LLM providers
* [ ] More agent tools
* [ ] Improved tool permission/sandboxing
* [ ] Persistent conversation memory
* [ ] Better terminal UX
* [ ] More comprehensive agent evaluations
* [ ] Streaming tool output
* [ ] Configurable models
* [ ] Agent planning and task decomposition

## 🤝 Contributing

Contributions, experiments, and improvements are welcome.

Before opening a pull request:

```bash
npm run build
npm run eval
```

Please include tests or evaluations when adding new agent behavior.

## ⚠️ Disclaimer

This project is experimental.

Agents with shell or filesystem access can perform potentially destructive operations. Run the project in an environment where you understand and control the permissions available to the agent.

## 📄 License

Add your chosen license here.
