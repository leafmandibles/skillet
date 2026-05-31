# skillet

![Skillet logo](docs/images/logo.png)

A small test harness for developing and testing local `agent` skills using pi-agent as a test runner.

## Getting Started

Develop your skill — for example, `IronSteak` — in:

```txt
<GIT_ROOT>/skill/IronSteak
```

Then initialize a test namespace:

```bash
./bin/skill-test init randomtests
```

This scaffolds:

```txt
test/randomtests/
  fixtures/
  prompts/
  .agents/
    skills -> ../../../skill
```

Run the skill with an ad hoc prompt:

```bash
./bin/skill-test randomtests "launch my ironsteak skill and init"
```

Or run from a prompt file:

```txt
test/randomtests/prompts/init.txt
```

```bash
./bin/skill-test randomtests prompts/init.txt
```

## Output formats

By default, `skill-test` prints a concise session summary to stdout:

```txt
session:
- assistant message (1.23s)
  Done.
```

For YAML output:

```bash
./bin/skill-test -o yaml randomtests prompts/init.txt
```

Example:

```yaml
input:
  namespace: "randomtests"
  file: "./test/randomtests/prompts/init.txt"

session:
  - type: "message"
    role: "assistant"
    content:
      |
        Done.

output:
  content-type: text/plain
  data:
    |
      Done.
```

`skill-test` creates isolated test workspaces under `test/<namespace>`.
