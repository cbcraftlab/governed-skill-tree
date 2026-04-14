# Intent Patterns

Use these patterns to translate subjective wording into useful engineering intent.

## Smoothness Language

Examples:

- not smooth
- not silky
- too jumpy
- still feels weird

Likely layers:

- animation timing
- batch update rhythm
- layout reflow
- scroll follow behavior

## Reference Comparison Language

Examples:

- not like GPT
- unlike the reference app
- should feel more like product X

Likely next step:

- compare captures
- isolate the strongest visible difference
- avoid code guesses before comparison

## Expectation Language

Examples:

- I thought it would go to the latest message
- I expected it to stay at the bottom
- this should not happen after I click send

Likely layers:

- interaction rule
- state transition
- gating condition

## Confidence Rule

When the user's wording is fuzzy, do not force a detailed root cause.

Instead produce:

- best current interpretation
- likely layer
- smallest next check
