# Convert JUnit test results to Markdown

## Usage

This code is designed to run in Java source-file mode (requires Java 11 or later):

```
curl https://raw.githubusercontent.com/couchbaselabs/junit-markdown/refs/heads/main/JunitMarkdown.java --output JunitMarkdown.java
java JunitMarkdown.java test-result-root-dir
```

### Formats

By default, names are interpreted using Java conventions: a testsuite/class name is
a dot-delimited fully-qualified class name, so results are grouped by package and each test
is shown as `Class.method`.

For test frameworks or languages where this is not appropriate (e.g. Go), pass `--format=passthrough` to group by
the raw `classname` reported in the Junit file and show the test name as-is:

```
java JunitMarkdown.java --format=passthrough test-result-root-dir
```

### From a GitHub Action

```yaml
  - name: Publish test results
    run: |
      curl https://raw.githubusercontent.com/couchbaselabs/junit-markdown/refs/heads/main/JunitMarkdown.java --output ${{ runner.temp }}/JunitMarkdown.java
      java ${{ runner.temp }}/JunitMarkdown.java . >> $GITHUB_STEP_SUMMARY
```