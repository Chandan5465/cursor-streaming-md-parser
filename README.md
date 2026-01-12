Streaming Markdown Parser

This project implements a streaming Markdown parser that incrementally renders Markdown content as it is received in small, irregular chunks—similar to how large language models stream output.

The parser focuses on optimistic parsing and incremental DOM updates, ensuring that already-rendered content remains selectable and copyable while new content streams in.

✨ Features

✅ Character-by-character streaming parser

✅ Optimistic rendering (styles applied immediately when syntax starts)

✅ Supports:

Inline code blocks using single backticks (inline code)

Fenced code blocks using triple backticks (```)

✅ Handles:

Tokens split arbitrarily (including split backticks)

Multiple state transitions within a single token

✅ Incremental DOM updates (no full re-render)

🧠 Parsing Approach

The parser is implemented as a state machine with three states:

TEXT – normal markdown text

INLINE_CODE – content between single backticks

CODE_BLOCK – content between triple backticks

Markdown is processed character by character, allowing correct parsing even when backticks are split across streamed tokens.

State Transitions

` → toggles INLINE_CODE

``` → toggles CODE_BLOCK

DOM nodes (span for inline code, pre for code blocks) are created immediately when entering a new state.

🧩 Why Streaming Parsing?

Traditional Markdown parsers require the full input upfront.
This project simulates real-world streaming scenarios where:

Input arrives in unpredictable chunks

The UI must update progressively

Previously rendered content must remain interactive

🚀 How to Run
Install dependencies
npm install

Build the project
npm run build

Open the app

Open the following file in your browser:

dist/index.html


Click the STREAM button to begin streaming and parsing the Markdown content.
