<!-- markdownlint-disable -->

# Hardening Report: preactjs--compressed-size-action/2.9.1

> This file was generated automatically by the hardening agent.

**Policy SHA:** `374911c4be584df24e6da57af2d990570ef0f859`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **preactjs--compressed-size-action/2.9.1** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### prior-fix (severity: high)

Carried forward from this version's previous harden, which fixed it; fix it again unless the code no longer has the problem. The previous harden changed action.yml without recording a finding for it, and this analysis reported nothing there. Re-apply its security changes unless the code no longer needs them. The previous patch:
```diff
diff --git a/action.yml b/action.yml
index aa4dae3..f871f48 100644
--- a/action.yml
+++ b/action.yml
@@ -46,7 +46,7 @@ inputs:
   sort-by:
     description: 'The column and direction to sort the results by. The format is "column:direction", where column is one of "Filename", "Size", or "Change" and direction is "asc" or "desc". For example, "Size:desc" sorts the table by file size in descending order.'
     default: 'Filename:asc'
-
 runs:
   using: 'node24'
-  main: 'index.js'
\ No newline at end of file
+  main: 'index.js'

```

Locations:

- `action.yml`

## Iteration Notes

### Iteration 1

**Fixes applied:** prior-fix

**Notes:**

The earlier patch only changed whitespace in action.yml: it deleted a blank line before 'runs:' and added the missing newline at the end of the file. I made the same edit again. Nothing in the action's behaviour or security changes. This is a node24 action with no 'uses:' references and no 'run:' steps, so there was no other security fix to make.

