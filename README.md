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

Найдите полный хеш и комментарий коммита, хеш которого начинается на aefea.
aefead2207ef7e2aa5dc81a34aedf0cad4c32545
Update CHANGELOG.md




Какому тегу соответствует коммит 85024d3?
(tag: v0.12.23)


Сколько родителей у коммита b8d720? Напишите их хеши.
56cd7859e05c36c06b56d013b55a252d0bb7e158 9ea88f22fc6269854151c571162c5bcf958bee2b





Перечислите хеши и комментарии всех коммитов которые были сделаны между тегами v0.12.23 и v0.12.24.
33ff1c03bb960b332be3af2e333462dde88b279e (tag: v0.12.24) v0.12.24

b14b74c4939dcab573326f4e3ee2a62e23e12f89 [Website] vmc provider links

3f235065b9347a758efadc92295b540ee0a5e26e Update CHANGELOG.md

6ae64e247b332925b872447e9ce869657281c2bf registry: Fix panic when server is unreachable

5c619ca1baf2e21a155fcdb4c264cc9e24a2a353 website: Remove links to the getting started guide's old location

06275647e2b53d97d4f0a19a0fec11f6d69820b5 Update CHANGELOG.md

d5f9411f5108260320064349b757f55c09bc4b80 command: Fix bug when using terraform login on Windows

4b6d06cc5dcb78af637bbb19c198faff37a066ed Update CHANGELOG.md

dd01a35078f040ca984cdd349f18d0b67e486c35 Update CHANGELOG.md

225466bc3e5f35baa5d07197bbc079345b77525e Cleanup after v0.12.23 release





Найдите коммит в котором была создана функция func providerSource, 
ее определение в коде выглядит так func providerSource(...) (вместо троеточия перечислены аргументы).
8c928e83589d90a031f811fae52a81be7153e82f




Найдите все коммиты в которых была изменена функция globalPluginDirs.
78b1220558 Remove config.go and update things using its aliases

52dbf94834 keep .terraform.d/plugins for discovery

41ab0aef7a Add missing OS_ARCH dir to global plugin paths

66ebff90cd move some more plugin search path logic to command

8364383c35 Push plugin discovery down into command package



Кто автор функции synchronizedWriters?
Martin Atkins
