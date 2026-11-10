# Review agent

`review.py` checks your answer to a concept's quiz against the concept and its study materials, using Claude Sonnet through the Anthropic API. The feedback is advisory: it helps you decide what to reread, and it never grades you.

## What it costs

> **This uses a paid API key. Every `check` is a separate charge to your Anthropic account.**

- A check costs roughly **$0.05 to $0.10**. Most of that is the study pages the model fetches and reads (up to five per check, at most 15,000 tokens each). A concept with no linked materials is cheaper, because the model judges from general knowledge.
- The token counts print at the end of each review, so you can check against the [pricing page](https://www.anthropic.com/pricing).
- Only `check` sends anything. `list`, `new`, `--dry-run` and `--prompt` are free and make no network calls.
- A Claude.ai subscription does **not** cover API calls. The API is billed separately, from prepaid credits.

## Set it up

1. **Python.** You need Python 3.10 or newer and PyYAML. Nothing else.

   ```bash
   python3 -m pip install pyyaml
   ```

2. **An Anthropic account.** Sign up at [console.anthropic.com](https://console.anthropic.com), and add credits under Billing. A few dollars covers dozens of checks.

3. **A spend limit (recommended).** In the Console, create a workspace for this, say `curriculum-review`, and set a low monthly limit on it, such as $10. A runaway loop or a leaked key then can't cost more than that.

4. **An API key.** In that workspace, under API keys, create a key. Copy it once and keep it in your password manager; the Console won't show it again.

5. **Give the key to the script**, for the current terminal only:

   ```bash
   export ANTHROPIC_API_KEY=sk-ant-...           # macOS / Linux
   ```
   ```powershell
   $env:ANTHROPIC_API_KEY = "sk-ant-..."         # Windows PowerShell
   ```

   The script reads the key from that variable and never writes it anywhere. Don't put the key in a file inside this repo, and never commit it. If a key leaks, delete it in the Console and make a new one.

## Use it

```bash
python3 review/review.py list                         # every concept, its week, and whether it has a quiz and materials
python3 review/review.py new state-estimation         # creates notes/state-estimation.md, one heading per quiz question
#   ... write your answers under the headings ...
python3 review/review.py check state-estimation       # paid: writes notes/state-estimation.review.md and prints it
```

Options for `check`:

| Option | What it does |
|---|---|
| `--note PATH` | Review a different file instead of `notes/<concept-id>.md`. |
| `--dry-run` | Print the exact API request and send nothing. |
| `--prompt` | Print the same instructions as one prompt, to paste into a Claude chat instead (see below). |
| `--model NAME` | Use another model. The default is `claude-sonnet-5-5`. |

Write your answer under the `### 1`, `### 2`, … headings, so the review can judge each question on its own. A note without the headings is reviewed as a whole.

## What the feedback says

- **Checked against:** which materials the model actually read. A link it couldn't open is listed as not available.
- **Depth:** the level your answer reaches (`describe`, `explain` or `evaluate`) against the concept's target, and the one step that would reach it.
- **Per question:** what's correct; anything that *contradicts the material* (always with a quote from it), is *overstated*, *imprecise* or *unsupported*; and what the question asked that your answer leaves out.
- **Differs from common usage:** a remark, not an error. You followed the materials, but usage elsewhere differs.

A short answer isn't marked down for being short. It simply reaches a lower depth.

## Without an API key

`--prompt` prints the full instructions, the concept, the material links and your answer as one block of text. Paste it into a Claude chat that can browse the web, and you get the same review under your subscription, with no per-use charge. The reply comes as JSON; ask for Markdown if you prefer.
