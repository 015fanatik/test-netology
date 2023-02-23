# Local .terraform directories
#**/.terraform/*

Будут проигнорированны все файлы в каталоге/каталогах .terraform  
в не зависимости от расположения самого каталога .terraform  

# .tfstate files
# *.tfstate
# *.tfstate.*

Будут проигнорированны все файлы с расширением .tfstate и все файлы в имени которых присутствует .tfstate.

# Crash log files
# crash.log
# crash.*.log

Будет проигнорирован файл crash.log  и файлы crash.*.log с любыми символами вместо *

# Exclude all .tfvars files, which are likely to contain sensitive data, such as
# password, private keys, and other secrets. These should not be part of version 
# control as they are data points which are potentially sensitive and subject 
# to change depending on the environment.
# *.tfvars
# *.tfvars.json

Будут проигнорированы  файлы с расширением .tfvars и файлы содержащие в названии .tfvars.json

# Ignore override files as they are usually used to override resources locally and so
# are not checked in
# override.tf
# override.tf.json
# *_override.tf
# *_override.tf.json

Будут проигнорированны файлы override.tf и override.tf.json  
и файлы содержащие любые символы в названии до  _override.tf и _override.tf.json  
например 123_override.tf  




# Include override files you do wish to add to version control using negated pattern
# !example_override.tf
# Include tfplan files to ignore the plan output of command: terraform plan -out=tfplan
# example: *tfplan*
# Ignore CLI configuration files
# .terraformrc
# terraform.rc

Будут проигнорированны файлы .terraform и terraform.rc


# Инструменты Git


# 1 Найдите полный хеш и комментарий коммита, хеш которого начинается на aefea.

git show aefea

Update CHANGELOG.md  
aefead2207ef7e2aa5dc81a34aedf0cad4c32545  


# 2 Какому тегу соответствует коммит 85024d3?  

git show 85024d3  
v0.12.23  

# 3 Сколько родителей у коммита b8d720? Напишите их хеши.  

git show b8d720f8^1  
56cd7859e05c36c06b56d013b55a252d0bb7e158  

git show b8d720f8^2  
9ea88f22fc6269854151c571162c5bcf958bee2b  

# 4 Перечислите хеши и комментарии всех коммитов которые были сделаны между тегами v0.12.23 и v0.12.24  

git log --oneline v0.12.23...v0.12.24

33ff1c03bb (tag: v0.12.24) v0.12.24  
b14b74c493 [Website] vmc provider links  
3f235065b9 Update CHANGELOG.md  
6ae64e247b registry: Fix panic when server is unreachable  
5c619ca1ba website: Remove links to the getting started guide's old location  
06275647e2 Update CHANGELOG.md  
d5f9411f51 command: Fix bug when using terraform login on Windows  
4b6d06cc5d Update CHANGELOG.md  
dd01a35078 Update CHANGELOG.md  
225466bc3e Cleanup after v0.12.23 release  

# 5 Найдите коммит в котором была создана функция func providerSource, ее определение в коде выглядит так func providerSource(...)  
# (вместо троеточия перечислены аргументы).  

git log -S"func providerSource(" --oneline  
8c928e8358 main: Consult local directories as potential mirrors of providers

git show 8c928e8358  
8c928e83589d90a031f811fae52a81be7153e82f

# 6 Найдите все коммиты в которых была изменена функция globalPluginDirs.  

Ищем файл  
git grep "func globalPluginDirs("

plugins.go:func globalPluginDirs() []string {


Ищем коммиты с изменением этой функции  
git log -s -L :globalPluginDirs:plugins.go --oneline

78b1220558 Remove config.go and update things using its aliases  
52dbf94834 keep .terraform.d/plugins for discovery  
41ab0aef7a Add missing OS_ARCH dir to global plugin paths  
66ebff90cd move some more plugin search path logic to command  
8364383c35 Push plugin discovery down into command package  


# 7 Кто автор функции synchronizedWriters?

git log -S synchronizedWriters Смотрим самый ранний комит.

Martin Atkins



# Домашнее задание к занятию "Работа в терминале. Лекция 1"



# 1 С помощью базового файла конфигурации запустите Ubuntu 20.04 в VirtualBox посредством Vagrant:
# Создайте директорию, в которой будут храниться конфигурационные файлы Vagrant. В ней выполните vagrant init. Замените содержимое Vagrantfile по умолчанию следующим:

 # Vagrant.configure("2") do |config|
 # config.vm.box = "bento/ubuntu-20.04"
 # end
 
# Выполнение в этой директории vagrant up установит провайдер VirtualBox для Vagrant, скачает необходимый образ и запустит виртуальную машину.
# vagrant suspend выключит виртуальную машину с сохранением ее состояния (т.е., при следующем vagrant up будут запущены все процессы внутри, которые работали на момент вызова suspend), vagrant halt выключит виртуальную машину штатным образом.

![screenshot1](https://github.com/015fanatik/devops-netology/blob/main/Screenshot_1.jpg)

# 2 Ознакомьтесь с графическим интерфейсом VirtualBox, посмотрите как выглядит виртуальная машина, которую создал для вас Vagrant, какие аппаратные ресурсы ей выделены. Какие ресурсы выделены по-умолчанию?

![screenshot2](https://github.com/015fanatik/devops-netology/blob/main/Screenshot_2.jpg)
![screenshot3](https://github.com/015fanatik/devops-netology/blob/main/Screenshot_3.jpg)
![screenshot4](https://github.com/015fanatik/devops-netology/blob/main/Screenshot_4.jpg)

# 3 Ознакомьтесь с возможностями конфигурации VirtualBox через Vagrantfile: документация. Как добавить оперативной памяти или ресурсов процессора виртуальной машине?

Добавить в конфиг

config.vm.provider "virtualbox" do |v|
  v.memory = 1024
  v.cpus = 2
end

# 4 Команда vagrant ssh из директории, в которой содержится Vagrantfile, позволит вам оказаться внутри виртуальной машины без каких-либо дополнительных настроек. Попрактикуйтесь в выполнении обсуждаемых команд в терминале Ubuntu.

![screenshot5](https://github.com/015fanatik/devops-netology/blob/main/Screenshot_5.jpg)

# 5 Ознакомьтесь с разделами man bash, почитайте о настройках самого bash:

# какой переменной можно задать длину журнала history, и на какой строчке manual это описывается?

![screenshot6](https://github.com/015fanatik/devops-netology/blob/main/Screenshot_6.jpg)

# что делает директива ignoreboth в bash?

ignoreboth — использовать обе опции ‘ignorespace’ и ‘ignoredups’

ignorespace — не сохранять строки начинающиеся с символа <пробел>

ignoredups — не сохранять строки, совпадающие с последней выполненной командой

# 6 В каких сценариях использования применимы скобки {} и на какой строчке man bash это описано?

скобки {} - вариант использования составных команд, указанных в man bash line 195
в этих скобках мы можем передавать список shell-команд и использовать регулярные выражения, которые выполнятся последовательно в текущем переменном окружении
так же этот список мы можем присвоить переменной 

# 7 С учётом ответа на предыдущий вопрос, как создать однократным вызовом touch 100000 файлов? Получится ли аналогичным образом создать 300000? Если нет, то почему?

touch {1..100000}

создать 300000 файлов без изменения переменной ARG_MAX (увеличить ограничение на объём передаваемых аргументов комманде) 

![screenshot7](https://github.com/015fanatik/devops-netology/blob/main/Screenshot_7.jpg)

# 8 В man bash поищите по /\[\[. Что делает конструкция [[ -d /tmp ]]

Конструкция [[ -d /tmp ]] вернёт 0 при наличии каталога /tmp.

# 9 Сделайте так, чтобы в выводе команды type -a bash первым стояла запись с нестандартным путем, например bash is ... Используйте знания о просмотре существующих и создании новых переменных окружения, обратите внимание на переменную окружения PATH
# bash is /tmp/new_path_directory/bash
# bash is /usr/local/bin/bash
# bash is /bin/bash

 mkdir /tmp/new_path_directory
 
 cp /bin/bash /tmp/new_path_directory/
 
 PATH=/tmp/new_path_directory/:$PATH
 
 # 10 Чем отличается планирование команд с помощью batch и at?
 
 команда at используется для назначения одноразового задания на заданное время, а команда batch — для назначения одноразовых задач, которые должны выполняться, когда загрузка системы становится меньше 1,5.
 
 # 11 Завершите работу виртуальной машины чтобы не расходовать ресурсы компьютера и/или батарею ноутбука.
 exit
 exit
 halt
 



















