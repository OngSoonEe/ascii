---
name: ascii
description: Find the single Unicode character that best matches a short visual or semantic description by searching Compart Unicode. Use when the user invokes /ascii or asks for a symbol, arrow, box-drawing character, punctuation mark, shape, dingbat, technical sign, or similar character by description.
compatibility: Requires web/search access to https://www.compart.com/en/unicode/ for reliable lookup.
metadata:
  source: https://www.compart.com/en/unicode/
  version: "1.0.0"
---

# ASCII

Find the Unicode character that best matches the user's description.

Despite the skill name `ascii`, the output may be any Unicode character available in Compart.

## Invocation

Typical form:

`/ascii <description>`

Example:

`/ascii a L shape pointing down arrow`

Output exactly:

`↴  `

The example is U+21B4, RIGHTWARDS ARROW WITH CORNER DOWNWARDS.

## Procedure

1. Treat everything after `/ascii` as the character description.
2. Search Compart Unicode first:
   - `https://www.compart.com/en/unicode/search?q=<keywords>`
3. Convert the user's visual wording into likely Unicode-name keywords.
   - Examples: `L shape pointing down arrow` -> `arrow corner down`
   - `double line vertical` -> `box drawings double vertical`
   - `small filled triangle right` -> `black right-pointing triangle`
4. Prefer a Compart result whose official Unicode name semantically matches the requested shape or meaning.
5. If several candidates are close, choose the single best match. Prefer:
   - exact direction and geometry,
   - plain/basic variants over decorative variants unless decoration was requested,
   - precomposed characters over combining sequences,
   - a single code point over multiple characters.
6. Return only the selected character followed by exactly two ASCII space characters.
7. Do not add quotes, Markdown fences, labels, Unicode names, code points, links, explanations, or punctuation.
8. Do not return emoji presentation variants unless the request explicitly asks for an emoji-style symbol.
9. If no good match is found on Compart, return the closest single Unicode character you can verify there.
10. Never invent a character that was not verified against Compart when web access is available.

## Output contract

The response MUST be:

`<one Unicode character><space><space>`

Nothing else.

## More examples

Input:
`/ascii arrow down`

Output:
`↓  `

Input:
`/ascii arrow pointing down then left like return`

Output:
`↵  `

Input:
`/ascii l corner arrow going right then down`

Output:
`↴  `
