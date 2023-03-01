



[Инструменты Git](#иструменты-git)













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


## Инструменты Git


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

 Vagrant.configure("2") do |config|
 
 config.vm.box = "bento/ubuntu-20.04"
 
 end
 
# Выполнение в этой директории vagrant up установит провайдер VirtualBox для Vagrant, скачает необходимый образ и запустит виртуальную машину.
# vagrant suspend выключит виртуальную машину с сохранением ее состояния (т.е., при следующем vagrant up будут запущены все процессы внутри, которые работали на момент # вызова suspend), vagrant halt выключит виртуальную машину штатным образом.

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

скобки {} -  применяется для создания составных комманд, указанных в man bash line 179

![screenshot8](https://github.com/015fanatik/devops-netology/blob/main/Screenshot_8.jpg)

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
 
# Домашнее задание к занятию «Работа в терминале. Лекция 2»

# 1 Какого типа команда cd? Попробуйте объяснить, почему она именно такого типа: опишите ход своих мыслей и поясните, если считаете, что она могла бы быть другого типа.

cd - это shell builtin команда, то есть команда, которая вызывается напрямую в shell, а не как внешняя исполняемая.

сd во всех случаях является встроенной командой, так как смена текущей директории в рамках дочернего процесса не приведет ни к каким последствиям на уровне командной
оболочки. 

Смена текущей директории в рамках дочерней командной оболочки также не влияет на текущую директорию родительской командной оболочки



type cd 

root@vagrant:~# type cd

cd is a shell builtin




# 2 Какая альтернатива без pipe для команды grep <some_string> <some_file> | wc -l?

grep -c -w

# 3 Какой процесс с PID 1 является родителем для всех процессов в вашей виртуальной машине Ubuntu 20.04?


root           1  0.0  0.6 169456 13000 ?        Ss   08:38   0:02 /sbin/init

# 4 Как будет выглядеть команда, которая перенаправит вывод stderr ls на другую сессию терминала?

 ls "не существующий каталог" 2> /dev/pts/* *-номер нужного терминала

# 5 Получится ли одновременно передать команде файл на stdin и вывести её stdout в другой файл? Приведите работающий пример.

~~~ 
root@vagrant:/home/vagrant/11# touch test 

root@vagrant:/home/vagrant/11# ls 

test

root@vagrant:/home/vagrant/11# cat <test > test2 

root@vagrant:/home/vagrant/11#

root@vagrant:/home/vagrant/11# ls

test  test2
~~~

# 6 Получится ли, находясь в графическом режиме, вывести данные из PTY в какой-либо из эмуляторов TTY? Сможете ли вы наблюдать выводимые данные?

Да 

echo "test" > /dev/pts/* *-номер нужного терминала


# 7 Выполните команду bash 5>&1. К чему она приведёт? Что будет, если вы выполните echo netology > /proc/$$/fd/5? Почему так происходит?


bash 5>&1 - создаем новый дескриптор 5 и перенаправляем его в первый ( stdout ) 

echo netology > /proc/$$/fd/5 отправляет netology в 5 дескриптор , блягодаря перенаправлению сделаному ранее netology появится в текущей консоли .


root@vagrant:~# bash 5>&1

root@vagrant:~# echo netology > /proc/$$/fd/5

netology

root@vagrant:~#

# 8 Получится ли в качестве входного потока для pipe использовать только stderr команды, не потеряв отображение stdout на pty?
Напоминаем: по умолчанию через pipe передаётся только stdout команды слева от | на stdin команды справа. Это можно сделать, поменяв стандартные потоки местами через промежуточный новый дескриптор, который вы научились создавать в предыдущем вопросе.

Можно при помощи конструкции  3>&1 1>&2 2>&3 ( 3 промежуточный дискриптор ) 



root@vagrant:/home/vagrant/11# cat test{1..5} 3>&1 1>&2 2>&3 | grep No
123
123
123
123
123
134
dir123
123
123123
123
132
234cat: test5: No such file or directory
root@vagrant:/home/vagrant/11#

В данном случа  grep No найдёт "No" из ошибки No such file or directory.


# 9  Что выведет команда cat /proc/$$/environ? Как ещё можно получить аналогичный по содержанию вывод?


Выводится список переменных окружения для процесса, под которым выполняется текущая оболочка bash

с помощью команды env

# 10 Используя man, опишите, что доступно по адресам /proc/<PID>/cmdline, /proc/<PID>/exe.
 
 
/proc/<PID>/cmdline
 
cmdline
 
Этот файл содержит полную командную строку запуска процесса, кроме тех процессов, что полностью ушли в своппинг, а также тех, что превратились в зомби.
 
 В этих двух случаях в файле ничего нет, то есть чтение этого файла вернет 0 символов. Аргументы командной строки в этом файле указаны как список строк, каждая из 
 
 которых завешается нулевым символом, с добавочным нулевым байтом после последней строки.


/proc/<PID>/exe
 
 Под Linux 2.2 и 2.4 exe является символьной ссылкой, содержащей фактическое полное имя выполняемого файла.
 
 Символьная ссылка exe может использоваться обычным образом - при попытке открыть exe будет открыт исполняемый файл.
 
 Вы можете даже ввести /proc/[number]/exe чтобы запустить другую копию процесса такого же как и процесс с номером [число].
 
Под Linux 2.0 и в более ранних версиях exe является указателем на запущенный файл и является символьной ссылкой. Вызов readlink(2) на этот специальный файл exe под Linux 2.0 и более ранних версий возвращает строку формата:

[устройство]:индексный_дескриптор

Например, строка [0301]:1502 означает индексный дескриптор 1502 на устройстве со старшим номером устройства 03 (IDE, MFM и т. д.) и младшим номером устройства 01 (первый раздел на первом диске).

 
 # 11 Узнайте, какую наиболее старшую версию набора инструкций SSE поддерживает ваш процессор с помощью /proc/cpuinfo.
 
 root@vagrant:/home/vagrant/11# grep sse /proc/cpuinfo
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx rdtscp lm constant_tsc rep_good nopl xtopology nonstop_tsc cpuid tsc_known_freq pni pclmulqdq ssse3 cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt aes xsave avx rdrand hypervisor lahf_lm abm 3dnowprefetch invpcid_single pti fsgsbase bmi1 avx2 bmi2 invpcid rdseed clflushopt md_clear flush_l1d
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx rdtscp lm constant_tsc rep_good nopl xtopology nonstop_tsc cpuid tsc_known_freq pni pclmulqdq ssse3 cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt aes xsave avx rdrand hypervisor lahf_lm abm 3dnowprefetch invpcid_single pti fsgsbase bmi1 avx2 bmi2 invpcid rdseed clflushopt md_clear flush_l1d

Ответ: sse4_2 .
 
 # 12 При открытии нового окна терминала и vagrant ssh создаётся новая сессия и выделяется pty.
Это можно подтвердить командой tty, которая упоминалась в лекции 3.2.

Однако:

vagrant@netology1:~$ ssh localhost 'tty'
not a tty
Почитайте, почему так происходит и как изменить поведение.
 
 
 В случае выполения одиночной команды ssh на удаленном сервере не выделяется TTY
Исправить это можно опцией -t, принудительное выделение псевдотерминала: ssh -t localhost 'tty'
 
 
 # 13 Бывает, что есть необходимость переместить запущенный процесс из одной сессии в другую. Попробуйте сделать это, воспользовавшись reptyr.
 Например, так можно перенести в screen процесс, который вы запустили по ошибке в обычной SSH-сессии.
 
 
 
Записать 0 в  /proc/sys/kernel/yama/ptrace_scope
 
 Start a long running process, e.g. top
 
Background the process with CTRL-Z

Resume the process in the background: bg

Display your running background jobs with jobs -l, this should look like this:

[1]+  4711 Stopped (signal)        top

(The -l in jobs -l makes sure you'll get the PID)

Disown the jobs from the current parent with disown top. After that, jobs will not show the job any more, but ps -a will.

Start your terminal multiplexer of choice, e.g. tmux

Reattach to the backgrounded process: reptyr 4711

Detach your terminal multiplexer (e.g. CTRL-A D) and close ssh

Reconnect ssh, attach to your multiplexer (e.g. tmux attach), rejoice!

 
 
 
 
 
 
 # 14 sudo echo string > /root/new_file не даст выполнить перенаправление под обычным пользователем, так как перенаправлением занимается процесс shell, который запущен без sudo под вашим пользователем. Для решения этой проблемы можно использовать конструкцию echo string | sudo tee /root/new_file. Узнайте, что делает команда tee и почему в отличие от sudo echo команда с sudo tee будет работать.
 
 
tee - читает из стандартного ввода и записывает как в стандартный вывод, в один или несколько файлов одновременно.
Так как shell работает в том переменном окружении пользователя в котором он запущен то перенаправить вывод в файл принадлежащий другому пользователю нельзя было.
Во втором случае команда tee запущена от root, поэтому были права на запись.


















