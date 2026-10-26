## Variable declarations

- Declare function-local variables at the beginning of the function.
  Loop variables may be declared in the `for` statement.
- Order new consecutive declaration blocks within the same scope by
  descending declaration-line length: Reverse Christmas Tree ordering.
  Keep equal-length declarations in their original order.

  ```c
  uint32_t connection_timeout_ms;
  uint16_t retry_count;
  bool is_ready;
  int i;
  ```

- When adding or modifying a declaration in an existing block, preserve
  surrounding declarations and their order. Place new declarations to fit
  the descending order where possible; do not sort the existing block.
  This preservation rule takes precedence over perfect visual ordering.
- Follow the initial declaration block with exactly one empty line.
  In existing functions, enforce this spacing only when adding or modifying
  a declaration. Otherwise preserve existing spacing.
- Declaration placement and ordering must not change initialization order,
  side effects, or behavior. Separate declarations from later assignments
  when an initializer depends on preceding work.

## Code style

- Do not reformat, rename, refactor, or comment on unrelated code. Preserve
  untouched blocks, including their comments and spacing.
- Extract recurring or meaningful numbers and strings into descriptive
  macros, `const` constants or enums. Keep self-explanatory, one-off values inline.
  Always name specification-defined values, such as HTTP status codes.
- Keep new function names under 30 characters. Do not rename unrelated
  existing functions solely to meet this limit.
- Separate logical blocks with empty lines.
- Add comments only when the code alone is insufficient: explain missing
  context, intent, constraints, or non-obvious decisions. Keep them brief;
  use examples when helpful. Do not comment every block or restate the code.
  Prefix such comments by "NOTE:" or "NOTES:".
- Propose ASCII diagrams when they would clarify a complete system.
- Reduce nesting with early returns and `continue`. Avoid the Arrow
  Anti-Pattern; do not flatten unrelated code as incidental cleanup.

## Communication

- Use the fewest words that preserve meaning in replies, comments,
  documentation, and commit messages.
- State facts directly. Avoid praise, superlatives, flattery, and automatic
  agreement. Correct mistaken assumptions and state uncertainty plainly.

## Atomic commits

- Each commit must contain exactly one logical change that can be reviewed
  and reverted independently. Group by purpose, not by file.
- Separate independent features, fixes, refactors, formatting, and
  documentation. Include tests with the change they validate.
- Before committing, inspect the diff and staged diff. Split distinct
  changes; stage individual files or hunks as needed.
- Keep each commit valid and working whenever reasonably possible.
  Prefer small, coherent commits when uncertain.
- Describe only the change contained in the commit.

## Commit messages

- Inspect recent commit subjects and bodies for repository conventions.
  This is particularly import to understand which prefix use.
  Follow them where compatible with these rules.
- Use an imperative subject without a trailing period. It must complete:
  "If applied, this commit will <subject>".
- Target at most 50 characters in the subject; never exceed 72.
- Separate the subject from an optional body with one blank line.
- Explain context and why in the body, not implementation details already
  clear from the diff. Omit the body when the subject is sufficient.
- Manually wrap body text at 72 characters.
- If a Jira tag is provided, preserve its supplied syntax and put it on
  the final line of the body, separated from preceding text by one blank
  line. If there is no explanatory body, place it after the subject's
  blank line. Never invent a Jira tag.

  ```text
  <prefix>: fix route expiration after traffic

  Keep active routes available until their refreshed lifetime expires.

  WI_SUN-1234
  ```
