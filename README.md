# secretlint with pre-commit

- [secretlint](https://github.com/secretlint/secretlint)
- [pre-commit](https://pre-commit.com/)

## Installation

You should install [pre-commit](https://pre-commit.com/#install).

## Usage

[.pre-commit-config.yaml](.pre-commit-config.yaml)
```
-   repo: local
    hooks:
    -   id: secretlint
        name: secretlint
        language: docker_image
        entry: secretlint/secretlint:latest secretlint
```

## Example

pre-commit's secretlint hook prevent to commit credential to your project.

```
$ echo "AWS_SECRET_ACCESS_KEY = wJalrXUtnFEMI/K7MDENG/bPxRfiCYSECRETSKEY" > SECRET
$ git add .
$ git commit -m commit
secretlint...............................................................Failed
- hook id: secretlint
- exit code: 1

SECRET
  1:0  error  found AWS Secret Access Key: wJalrXUtnFEMI/K7MDENG/bPxRfiCYSECRETSKEY  @secretlint/secretlint-rule-preset-recommend > @secretlint/secretlint-rule-aws

✖ 1 problem (1 error, 0 warnings)
```

## Contributing

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D

## License

MIT