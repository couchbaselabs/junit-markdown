# Convert JUnit test results to Markdown

## Usage

This code is designed to run in Java source-file mode (requires Java 11 or later):

```
curl https://raw.githubusercontent.com/couchbaselabs/junit-markdown/refs/heads/main/JunitMarkdown.java --output JunitMarkdown.java
java JunitMarkdown.java test-result-root-dir
```

### From a GitHub Action

```yaml
  - name: Publish test results
    run: |
      curl https://raw.githubusercontent.com/couchbaselabs/junit-markdown/refs/heads/main/JunitMarkdown.java --output ${{ runner.temp }}/JunitMarkdown.java
      java ${{ runner.temp }}/JunitMarkdown.java . >> $GITHUB_STEP_SUMMARY
```