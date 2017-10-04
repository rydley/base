# Our first AWS configuration for Terraform

An initial configuration for Terraform.

## Usage
```
$ terraform plan
$ terraform apply
```
## License

MIT

## Best Practices

The state file contains everything in your configuration, including any secrets.  Add this file to your .gitignore configuration.

```
$ echo "terraform.tfstate*" > > .gitignore 
$ git add .gitignore 
$ git commit -m "Adding .gitignore file"
```
Pre-commit hooks
```
#!/usr/bin/env bash
set -e

# Formats any *.tf files according to the hashicorp convention
files=$(git diff --cached --name-only)
for f in $files
do
  if [ -e "$f" ] && [[ $f == *.tf ]]; then
    #terraform validate `dirname $f`
    terraform fmt $f
    git add $f
  fi
done
```
