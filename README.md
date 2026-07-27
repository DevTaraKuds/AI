# AI Projects

I have put together a number of curated resources related to implementation of AI.

# Sub-Folders

## LLM Probe
This project applies the taxonmy of social engineering tactics used by security operations and red team to test whether a conversational LLM acting as a customer support agent respects simple operational rules under adversarial prompting.

### Pre-requisite
- Language: Python 3x
- Model client: google-genai (Gemini)
- Model used: gemini-3.5-flash
- A valid API key
- Network Access

### What was done
- Run 15 adversarial prompts (Single and Multi turn) that emulate common social engineering strategies.
- Constrains the model with a system instructionrepresenting simple customer-support rules.
- Log raw model responses for manual review.

### Commands used

``` pip install google-genai ```
``` export GEMINI_API_KEYv= "API-Key" ```
``` python LLM_Probe/run_eval.py ```

# Stack

**Language**: Python 3x

