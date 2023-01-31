# Local .terraform directories
**/.terraform/*
Будут проигнорированны все файлы в каталоге/каталогах .terraform 
в не зависимости от расположения самого каталога .terraform

# .tfstate files
*.tfstate
*.tfstate.*
Будут проигнорированны все файлы с расширением .tfstate и все файлы в имени которых присутствует .tfstate.

# Crash log files
crash.log
crash.*.log
Будет проигнорирован файл crash.log  и файлы crash.*.log с любыми символами вместо *

# Exclude all .tfvars files, which are likely to contain sensitive data, such as
# password, private keys, and other secrets. These should not be part of version 
# control as they are data points which are potentially sensitive and subject 
# to change depending on the environment.
*.tfvars
*.tfvars.json
Будут проигнорированы  файлы с расширением .tfvars и файлы содержащие в названии .tfvars.json

# Ignore override files as they are usually used to override resources locally and so
# are not checked in
override.tf
override.tf.json
*_override.tf
*_override.tf.json
Будут проигнорированны файлы override.tf и override.tf.json
и файлы содержащие любые символы в названии до  _override.tf и _override.tf.json
например 123_override.tf



# Include override files you do wish to add to version control using negated pattern
# !example_override.tf

# Include tfplan files to ignore the plan output of command: terraform plan -out=tfplan
# example: *tfplan*

# Ignore CLI configuration files
.terraformrc
terraform.rc
Будут проигнорированны файлы .terraform и terraform.rc 