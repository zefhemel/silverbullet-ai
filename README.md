# SilverBullet AI Plug

**WIP Notice**: This plug is still in early development and may not work as expected. Please report any issues you encounter, or feature ideas.  Currently an OpenAI api key is required, but support for local LLMs will be added in the future.

**Warning**: Please backup your notes before using this plug.  It inserts and replaces text at certain points and isn't well-tested yet, so back up your data!

This plug integrates OpenAI functionalities into SilverBullet, allowing users to perform various AI-related tasks directly within their notes. It requires the SilverBullet platform and an OpenAI API key to work.

## Features

- **Summarize Note**: Summarizes the content of a note or selected text.
- **Replace with Summary**: Replaces the selected text with its summary.
- **Insert Summary**: Inserts a summary of the selected text or note at the cursor position.
- **Call OpenAI with Note Context**: Sends the note or selected text to OpenAI based on a user-defined prompt.
- **Generate Tags for Note**: Generates tags for the current note using AI.
- **Generate and Insert Image using Dall-E**: Generates an image based on a prompt and inserts it into the note.

### Available commands

TODO: Better descriptions of what these do

<!-- start-commands-and-functions -->
- **AI: Summarize Note and open summary**: Uses a built-in prompt to ask the LLM for a summary of either the entire note, or the selected
text.  Opens the resulting summary in a temporary right pane.
- **AI: Replace with Summary**: Uses a built-in prompt to ask the LLM for a summary of either the entire note, or the selected
text.  Replaces the selected text with the summary.
- **AI: Insert Summary**: Uses a built-in prompt to ask the LLM for a summary of either the entire note, or the selected
text.  Inserts the summary at the cursor's position.
- **AI: Call OpenAI with Note context**: Prompts the user for a custom prompt to send to the LLM.  If the user has text selected, the selected text is used as the note content.
If the user has no text selected, the entire note is used as the note content.
The response is inserted at the cursor position.
- **AI: Generate tags for note**: Asks the LLM to generate tags for the current note.
Generated tags are added to the note's frontmatter.
- **AI: Generate and insert image using DallE**: Prompts the user for a custom prompt to send to DALL·E, then sends the prompt to DALL·E to generate an image.
The resulting image is then uploaded to the space and inserted into the note with a caption.

<!-- end-commands-and-functions -->

## Usage

After installing the plug, you can access its features through the command palette. Make sure to set `OPENAI_API_KEY` in the SECRETS page for the plug to function correctly.

If you do not have a SECRETS page, create a new page named `SECRETS` with content similar to the following:

```yaml
OPENAI_API_KEY: "openai key here"
```

### Configuration

To change the text generation model used by all commands, open your `SETTINGS` page and change the setting below:

```yaml
ai:
  # By default, gpt-3.5-turbo is used.  Change the model below if desired.
  defaultTextModel: gpt-4-0125-preview
```

## Build
To build this plug, make sure you have [SilverBullet installed](https://silverbullet.md/Install). Then, build the plug with:

```shell
deno task build
```

Or to watch for changes and rebuild automatically

```shell
deno task watch
```

Then, copy the resulting `.plug.js` file into your space's `_plug` folder. Or build and copy in one command:

```shell
deno task build && cp *.plug.js /my/space/_plug/
```

SilverBullet will automatically sync and load the new version of the plug (or speed up this process by running the {[Sync: Now]} command).

## Installation

Add the following to to your `PLUGS` file, run `Plugs: Update` command and off you go!

For in-development code from the main branch:
```yaml
- github:justyns/silverbullet-ai/silverbullet-ai.plug.js
```

For the latest "release" code, mostly also still in development for now:

```yaml
- ghr:justyns/silverbullet-ai/0.0.3
```

You can also use the `Plugs: Add` command and enter the above url to install.