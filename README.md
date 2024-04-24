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

# Usage


# License

The scripts and documentation in this project are released under the [MIT License](LICENSE)