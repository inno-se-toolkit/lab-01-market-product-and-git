# Coding agents

You may use any [coding agent](https://docs.aws.amazon.com/prescriptive-guidance/latest/agentic-ai-patterns/coding-agents.html) with any LLM.

`OpenRouter` provides [free models](https://openrouter.ai/collections/free-models).

Below, we explain how to set up coding agents based on the [`Qwen3-Coder`](https://github.com/QwenLM/Qwen3-Coder) LLM.

## Set up `Qwen Code`

`Qwen Code` [provides](https://github.com/QwenLM/qwen-code#why-qwen-code) 2000 free requests per day.

- [Install](https://github.com/QwenLM/qwen-code#installation) `Qwen Code`.
- [Authenticate](https://github.com/QwenLM/qwen-code#qwen-oauth-recommended).
- Check that you have `Qwen` credentials at `~/.qwen/oauth_creds.json`.

## Set up `Qwen Code Companion` with `Qwen3-Coder`

1. [Set up `Qwen Code`](#set-up-qwen-code).
1. Open the `Chat` panel using one of these methods:
    1. Method 1:
       1. Go to the [`Editor Toolbar`](../appendix/vs-code.md#editor-toolbar).
       2. Click the `Qwen` icon.
    2. Method 2:
       - [Open the `Command Palette`](../appendix/vs-code.md#open-the-command-palette).
       - Run `Qwen Code: Open`.
1. Write `/login` in the chat.
1. Write `@<file-name>` to refer to the file `<file-name>`.

## Set up `GitHub Copilot Chat` with `Qwen3-Coder`

1. [Set up `Qwen Code`](#set-up-qwen-code).
1. [Install](https://code.visualstudio.com/docs/configure/extensions/extension-marketplace#_browse-for-extensions) the `github.copilot-chat` and `denizhandaklr.vscode-qwen-copilot` extensions.
1. [Open the `Command Palette`](../appendix/vs-code.md#open-the-command-palette).
1. Run `Qwen Copilot: Authenticate`.
1. Complete the authentication procedure.
1. Open the `Command Palette`.
1. Run `Chat: Manage Language Models`.
1. Click `Add Models`.
1. Click `Qwen Code`.
1. Double click `Qwen 3 Coder Plus` to make the model visible.
1. [Open the `Command Palette`](../appendix/vs-code.md#open-the-command-palette).
1. Run `Chat: Open Chat`.
1. In the `Chat`, click `Auto` (`Pick Model`) and then click `Qwen 3 Coder Plus`.
