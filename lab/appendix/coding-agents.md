# Coding agents

Coding agents let you use LLMs to help you complete your tasks.

- [Choose a coding agent](#choose-a-coding-agent)
- [Set up `Qwen Code`-based agent](#set-up-qwen-code-based-agent)
  - [Set up `Qwen Code`](#set-up-qwen-code)
  - [Set up a coding agent in `VS Code`](#set-up-a-coding-agent-in-vs-code)
    - [Set up `Qwen Code Companion` with `Qwen3-Coder`](#set-up-qwen-code-companion-with-qwen3-coder)
    - [Set up `GitHub Copilot Chat` with `Qwen3-Coder`](#set-up-github-copilot-chat-with-qwen3-coder)

## Choose a coding agent

You may use any [coding agent](https://docs.aws.amazon.com/prescriptive-guidance/latest/agentic-ai-patterns/coding-agents.html) with any LLM.

`OpenRouter` provides [free models](https://openrouter.ai/collections/free-models).

## Set up `Qwen Code`-based agent

Below, we explain how to set up coding agents based on the free [`Qwen3-Coder`](https://github.com/QwenLM/Qwen3-Coder) LLM.

Complete these steps:

1. [Set up `Qwen Code`](#set-up-qwen-code)
2. [Set up a coding agent in `VS Code`](#set-up-a-coding-agent-in-vs-code)

### Set up `Qwen Code`

`Qwen Code` [provides](https://github.com/QwenLM/qwen-code#why-qwen-code) 2000 free requests per day.

- [Install](https://github.com/QwenLM/qwen-code#installation) `Qwen Code`.
- [Authenticate](https://github.com/QwenLM/qwen-code#qwen-oauth-recommended).
- Check that you have `Qwen` credentials at `~/.qwen/oauth_creds.json`.

### Set up a coding agent in `VS Code`

Set up a coding agent in `VS Code` using one of these approaches:

<!-- no toc -->
- [Set up `Qwen Code Companion` with `Qwen3-Coder`](#set-up-qwen-code-companion-with-qwen3-coder)
- [Set up `GitHub Copilot Chat` with `Qwen3-Coder`](#set-up-github-copilot-chat-with-qwen3-coder)

#### Set up `Qwen Code Companion` with `Qwen3-Coder`

1. Open the `Chat` panel using one of these methods:
    1. Method 1:
       1. Go to the [`Editor Toolbar`](../appendix/vs-code.md#editor-toolbar).
       2. Click the `Qwen` icon.
    2. Method 2:
       - [Run using the `Command Palette`](../appendix/vs-code.md#run-a-command-using-the-command-palette): `Qwen Code: Open`.
2. Write `/login` in the chat.
3. Write `@<file-name>` to refer to the file `<file-name>`.

#### Set up `GitHub Copilot Chat` with `Qwen3-Coder`

1. [Install](https://code.visualstudio.com/docs/configure/extensions/extension-marketplace#_browse-for-extensions) the `github.copilot-chat` and `denizhandaklr.vscode-qwen-copilot` extensions.
2. [Run using the `Command Palette`](../appendix/vs-code.md#run-a-command-using-the-command-palette): `Qwen Copilot: Authenticate`.
3. Complete the authentication procedure.
4. [Run using the `Command Palette`](../appendix/vs-code.md#run-a-command-using-the-command-palette): `Chat: Manage Language Models`.
5. Click `Add Models`.
6. Click `Qwen Code`.
7. Double click `Qwen 3 Coder Plus` to make the model visible.
8. [Run using the `Command Palette`](../appendix/vs-code.md#run-a-command-using-the-command-palette): `Chat: Open Chat`.
9. The `CHAT` panel will open.
10. Go to `CHAT`.
11. Click `Auto` (`Pick Model`)
12. Click `Qwen 3 Coder Plus`.
