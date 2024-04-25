# Coverage Checker

This action validates if a pre generated coverage report with clover format is above a chosen treshold

# Usage

<!-- start usage -->
```yaml
- uses: convenia/coverage-checker@v1
  with:
    # Path to clover file
    # Default: '.coverage/xml/clover.xml'
    clover-xml-path: ''

    # Coverage Threshold
    # Default: 90
    min-coverage: 90
```
<!-- end usage -->

# Requirements
To run the coverage checker you must have PHP installed. The image `convenia/php-full:latest` would be a nice choice for your workflows.

# Usage

Almost all testing frameworks have an option to export a coverage report in clover xml format. This action uses this report to pass or fail the step when the coverage below a chosen treshold.

For exemplo lets allow the workflow to proceed only if the coverage generated for the PHPUnit is above 75%

```yaml
name: Validate treshold

on:
  push:

jobs:
  validation:
    container: 
      image: convenia/php-full:latest
    steps:
    - name: Checkout
      uses: actions/checkout@v4
    - name: Generate Coverage Report
      run: ./vendor/bin/phpunit --colors='always' --coverage-clover clover.xml
    - name: Check Coverage
      uses: convenia/coverage-checker@v1
      with:
        clover-xml-path: "clover.xml"
        min-coverage:  75
```

# License

The scripts and documentation in this project are released under the [MIT License](LICENSE)

# Credits

This action is just a wrapper around [this file](https://ocramius.github.io/blog/automated-code-coverage-check-for-github-pull-requests-with-travis/) from [Marco Pivetta(Ocramius)](https://twitter.com/Ocramius)
