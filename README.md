# Домашнее задание к занятию 6 «Создание собственных модулей»

## Подготовка к выполнению

1. Создайте пустой публичный репозиторий в своём любом проекте: `my_own_collection`.
> [Репозиторий my_own_collection](https://github.com/YTimashev/my_own_collection)
2. Скачайте репозиторий Ansible: `git clone https://github.com/ansible/ansible.git` по любому, удобному вам пути.
3. Зайдите в директорию Ansible: `cd ansible`.
4. Создайте виртуальное окружение: `python3 -m venv venv`.
5. Активируйте виртуальное окружение: `. venv/bin/activate`. Дальнейшие действия производятся только в виртуальном окружении.
6. Установите зависимости `pip install -r requirements.txt`.
7. Запустите настройку окружения `. hacking/env-setup`.
8. Если все шаги прошли успешно — выйдите из виртуального окружения `deactivate`.
9. Ваше окружение настроено. Чтобы запустить его, нужно находиться в директории `ansible` и выполнить конструкцию `. venv/bin/activate && . hacking/env-setup`.

<details>
<summary>Настроенное виртуальное окружение</summary>
```bash
tim@tim:~/nl/devops-netology/ansible/08-ansible-06-module$ git clone https://github.com/ansible/ansible.git
Клонирование в «ansible»…
remote: Enumerating objects: 607524, done.
remote: Counting objects: 100% (606/606), done.
remote: Compressing objects: 100% (384/384), done.
remote: Total 607524 (delta 228), reused 507 (delta 171), pack-reused 606918
Получение объектов: 100% (607524/607524), 237.38 МиБ | 3.48 МиБ/с, готово.
Определение изменений: 100% (404354/404354), готово.
tim@tim:~/nl/devops-netology/ansible/08-ansible-06-module$ cd ansible
tim@tim:~/nl/devops-netology/ansible/08-ansible-06-module/ansible$ python3 -m venv venv
The virtual environment was not created successfully because ensurepip is not
available.  On Debian/Ubuntu systems, you need to install the python3-venv
package using the following command.

    apt install python3.10-venv

You may need to use sudo with that command.  After installing the python3-venv
package, recreate your virtual environment.

Failing command: /home/tim/nl/devops-netology/ansible/08-ansible-06-module/ansible/venv/bin/python3

tim@tim:~/nl/devops-netology/ansible/08-ansible-06-module/ansible$ sudo apt install python3.10-venv
[sudo] пароль для tim: 
Чтение списков пакетов… Готово
Построение дерева зависимостей… Готово
Чтение информации о состоянии… Готово         
Будут установлены следующие дополнительные пакеты:
  python3-pip-whl python3-setuptools-whl
Следующие НОВЫЕ пакеты будут установлены:
  python3-pip-whl python3-setuptools-whl python3.10-venv
Обновлено 0 пакетов, установлено 3 новых пакетов, для удаления отмечено 0 пакетов, и 229 пакетов не обновлено.
Необходимо скачать 2 473 kB архивов.
После данной операции объём занятого дискового пространства возрастёт на 2 882 kB.
Хотите продолжить? [Д/н] y
Пол:1 http://ru.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 python3-pip-whl all 22.0.2+dfsg-1ubuntu0.3 [1 679 kB]
Пол:2 http://ru.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 python3-setuptools-whl all 59.6.0-1.2ubuntu0.22.04.1 [788 kB]
Пол:3 http://ru.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 python3.10-venv amd64 3.10.12-1~22.04.2 [5 724 B]
Получено 2 473 kB за 0с (8 763 kB/s)    
Выбор ранее не выбранного пакета python3-pip-whl.
(Чтение базы данных … на данный момент установлено 294910 файлов и каталогов.)
Подготовка к распаковке …/python3-pip-whl_22.0.2+dfsg-1ubuntu0.3_all.deb …
Распаковывается python3-pip-whl (22.0.2+dfsg-1ubuntu0.3) …
Выбор ранее не выбранного пакета python3-setuptools-whl.
Подготовка к распаковке …/python3-setuptools-whl_59.6.0-1.2ubuntu0.22.04.1_all.deb …
Распаковывается python3-setuptools-whl (59.6.0-1.2ubuntu0.22.04.1) …
Выбор ранее не выбранного пакета python3.10-venv.
Подготовка к распаковке …/python3.10-venv_3.10.12-1~22.04.2_amd64.deb …
Распаковывается python3.10-venv (3.10.12-1~22.04.2) …
Настраивается пакет python3-setuptools-whl (59.6.0-1.2ubuntu0.22.04.1) …
Настраивается пакет python3-pip-whl (22.0.2+dfsg-1ubuntu0.3) …
Настраивается пакет python3.10-venv (3.10.12-1~22.04.2) …
tim@tim:~/nl/devops-netology/ansible/08-ansible-06-module/ansible$ python3 -m venv venv
tim@tim:~/nl/devops-netology/ansible/08-ansible-06-module/ansible$ . venv/bin/activate
(venv) tim@tim:~/nl/devops-netology/ansible/08-ansible-06-module/ansible$ pip install -r requirements.txt
Collecting jinja2>=3.0.0
  Using cached Jinja2-3.1.2-py3-none-any.whl (133 kB)
Collecting PyYAML>=5.1
  Downloading PyYAML-6.0.1-cp310-cp310-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (705 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 705.5/705.5 KB 616.1 kB/s eta 0:00:00
Collecting cryptography
  Downloading cryptography-41.0.5-cp37-abi3-manylinux_2_28_x86_64.whl (4.4 MB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 4.4/4.4 MB 176.2 kB/s eta 0:00:00
Collecting packaging
  Downloading packaging-23.2-py3-none-any.whl (53 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 53.0/53.0 KB 352.4 kB/s eta 0:00:00
Collecting resolvelib<1.1.0,>=0.5.3
  Downloading resolvelib-1.0.1-py2.py3-none-any.whl (17 kB)
Collecting MarkupSafe>=2.0
  Downloading MarkupSafe-2.1.3-cp310-cp310-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (25 kB)
Collecting cffi>=1.12
  Downloading cffi-1.16.0-cp310-cp310-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (443 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 443.9/443.9 KB 498.3 kB/s eta 0:00:00
Collecting pycparser
  Downloading pycparser-2.21-py2.py3-none-any.whl (118 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 118.7/118.7 KB 519.7 kB/s eta 0:00:00
Installing collected packages: resolvelib, PyYAML, pycparser, packaging, MarkupSafe, jinja2, cffi, cryptography
Successfully installed MarkupSafe-2.1.3 PyYAML-6.0.1 cffi-1.16.0 cryptography-41.0.5 jinja2-3.1.2 packaging-23.2 pycparser-2.21 resolvelib-1.0.1
(venv) tim@tim:~/nl/devops-netology/ansible/08-ansible-06-module/ansible$ . hacking/env-setup
running egg_info
creating lib/ansible_core.egg-info
writing lib/ansible_core.egg-info/PKG-INFO
writing dependency_links to lib/ansible_core.egg-info/dependency_links.txt
writing entry points to lib/ansible_core.egg-info/entry_points.txt
writing requirements to lib/ansible_core.egg-info/requires.txt
writing top-level names to lib/ansible_core.egg-info/top_level.txt
writing manifest file 'lib/ansible_core.egg-info/SOURCES.txt'
reading manifest file 'lib/ansible_core.egg-info/SOURCES.txt'
reading manifest template 'MANIFEST.in'
warning: no files found matching 'changelogs/CHANGELOG*.rst'
adding license file 'COPYING'
writing manifest file 'lib/ansible_core.egg-info/SOURCES.txt'

Setting up Ansible to run out of checkout...

PATH=/home/tim/nl/devops-netology/ansible/08-ansible-06-module/ansible/bin:/home/tim/nl/devops-netology/ansible/08-ansible-06-module/ansible/venv/bin:/home/tim/.local/bin:/home/tim/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/snap/bin
PYTHONPATH=/home/tim/nl/devops-netology/ansible/08-ansible-06-module/ansible/test/lib:/home/tim/nl/devops-netology/ansible/08-ansible-06-module/ansible/lib
MANPATH=/home/tim/nl/devops-netology/ansible/08-ansible-06-module/ansible/docs/man:/usr/local/man:/usr/local/share/man:/usr/share/man

Remember, you may wish to specify your host file with -i

Done!

(venv) tim@tim:~/nl/devops-netology/ansible/08-ansible-06-module/ansible$ deactivate
tim@tim:~/nl/devops-netology/ansible/08-ansible-06-module/ansible$ . venv/bin/activate && . hacking/env-setup
running egg_info
creating lib/ansible_core.egg-info
writing lib/ansible_core.egg-info/PKG-INFO
writing dependency_links to lib/ansible_core.egg-info/dependency_links.txt
writing entry points to lib/ansible_core.egg-info/entry_points.txt
writing requirements to lib/ansible_core.egg-info/requires.txt
writing top-level names to lib/ansible_core.egg-info/top_level.txt
writing manifest file 'lib/ansible_core.egg-info/SOURCES.txt'
reading manifest file 'lib/ansible_core.egg-info/SOURCES.txt'
reading manifest template 'MANIFEST.in'
warning: no files found matching 'changelogs/CHANGELOG*.rst'
adding license file 'COPYING'
writing manifest file 'lib/ansible_core.egg-info/SOURCES.txt'

Setting up Ansible to run out of checkout...

PATH=/home/tim/nl/devops-netology/ansible/08-ansible-06-module/ansible/bin:/home/tim/nl/devops-netology/ansible/08-ansible-06-module/ansible/venv/bin:/home/tim/.local/bin:/home/tim/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/snap/bin
PYTHONPATH=/home/tim/nl/devops-netology/ansible/08-ansible-06-module/ansible/test/lib:/home/tim/nl/devops-netology/ansible/08-ansible-06-module/ansible/lib:/home/tim/nl/devops-netology/ansible/08-ansible-06-module/ansible/test/lib:/home/tim/nl/devops-netology/ansible/08-ansible-06-module/ansible/lib
MANPATH=/home/tim/nl/devops-netology/ansible/08-ansible-06-module/ansible/docs/man:/usr/local/man:/usr/local/share/man:/usr/share/man

Remember, you may wish to specify your host file with -i

Done!

(venv) tim@tim:~/nl/devops-netology/ansible/08-ansible-06-module/ansible$ 
```
</details>


## Основная часть

Ваша цель — написать собственный module, который вы можете использовать в своей role через playbook. Всё это должно быть собрано в виде collection и отправлено в ваш репозиторий.

**Шаг 1.** В виртуальном окружении создайте новый `my_own_module.py` файл.
> Mодули Ansible размещаются по пути lib/ansible/modules, в котором и создан файл `my_own_module.py`.

**Шаг 2.** Наполните его содержимым:
>Содержание файла наполнено из предложенной в задание [статьи](https://docs.ansible.com/ansible/latest/dev_guide/developing_modules_general.html#creating-a-module).

**Шаг 3.** Заполните файл в соответствии с требованиями Ansible так, чтобы он выполнял основную задачу: module должен создавать текстовый файл на удалённом хосте по пути, определённом в параметре `path`, с содержимым, определённым в параметре `content`.
> [my_own_module.py](ansible/modules/my_own_module.py)

**Шаг 4.** Проверьте module на исполняемость локально.
>Проверку запускаем через json файл:
```json
{
    "ANSIBLE_MODULE_ARGS": {
        "path": "my_test",
        "content": "Hello, World!"
    }
}
```
```bash
(venv) tim@tim:~/nl/devops-netology/ansible/08-ansible-06-module/ansible$ python -m ansible.modules.my_own_module my_own_module.json 

{"changed": true, "original_message": "Hello, World!", "message": "file recorder", "invocation": {"module_args": {"path": "my_test", "content": "Hello, World!"}}}
(venv) tim@tim:~/nl/devops-netolog
```

**Шаг 5.** Напишите single task playbook и используйте module в нём.
```yaml
---
#site.yml
- name: Test module
  hosts: localhost
  tasks:
    - name: Call my_own_module
      my_own_module:
        path: "/home/tim/my_own_module.txt"
        content: "Привет, Мир"
```

При первом запуске файл my_own_module.txt отсутствует.
```bash
(venv) tim@tim:~/nl/devops-netology/ansible/08-ansible-06-module/ansible$ ansible-playbook site.yml -v
[WARNING]: You are running the development version of Ansible. You should only run Ansible from "devel" if you are modifying the
Ansible engine, or trying out features under development. This is a rapidly changing source of code and can become unstable at any
point.
No config file found; using defaults
[WARNING]: No inventory was parsed, only implicit localhost is available
[WARNING]: provided hosts list is empty, only localhost is available. Note that the implicit localhost does not match 'all'

PLAY [Test module] *******************************************************************************************************************

TASK [Gathering Facts] ***************************************************************************************************************
ok: [localhost]

TASK [Call my_own_module] ************************************************************************************************************
changed: [localhost] => {"changed": true, "message": "file recorder", "original_message": "Привет, Мир"}

PLAY RECAP ***************************************************************************************************************************
localhost                  : ok=2    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   

(venv) tim@tim:~/nl/devops-netology/ansible/08-ansible-06-module/ansible$ 
```
**Шаг 6.** Проверьте через playbook на идемпотентность.
>При повторном запуске файл расположен в указанном месте.
```bash
(venv) tim@tim:~/nl/devops-netology/ansible/08-ansible-06-module/ansible$ ansible-playbook site.yml -v
[WARNING]: You are running the development version of Ansible. You should only run Ansible from "devel" if you are modifying the
Ansible engine, or trying out features under development. This is a rapidly changing source of code and can become unstable at any
point.
No config file found; using defaults
[WARNING]: No inventory was parsed, only implicit localhost is available
[WARNING]: provided hosts list is empty, only localhost is available. Note that the implicit localhost does not match 'all'

PLAY [Test module] *******************************************************************************************************************

TASK [Gathering Facts] ***************************************************************************************************************
ok: [localhost]

TASK [Call my_own_module] ************************************************************************************************************
ok: [localhost] => {"changed": false, "message": "file exists", "original_message": "Привет, Мир"}

PLAY RECAP ***************************************************************************************************************************
localhost                  : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   

(venv) tim@tim:~/nl/devops-netology/ansible/08-ansible-06-module/ansible$ 
```

**Шаг 7.** Выйдите из виртуального окружения.
```bash
(venv) tim@tim:~/nl/devops-netology/ansible/08-ansible-06-module/ansible$ deactivate
tim@tim:~/nl/devops-netology/ansible/08-ansible-06-module/ansible$ 
```

**Шаг 8.** Инициализируйте новую collection: `ansible-galaxy collection init my_own_namespace.yandex_cloud_elk`.
>Инициализацию новой коллекциии выполнил с другим именем `my_own_namespace.ytim`
```bash
tim@tim:~/08-ansible-06-module/my_own_collection$ ansible-galaxy collection init my_own_namespace.ytim
[WARNING]: You are running the development version of Ansible. You should only run Ansible from "devel" if you are modifying the Ansible
engine, or trying out features under development. This is a rapidly changing source of code and can become unstable at any point.
- Collection my_own_namespace.ytim was created successfully
tim@tim:~/08-ansible-06-module/my_own_collection$
```
**Шаг 9.** В эту collection перенесите свой module в соответствующую директорию.
>Модуль размещен в директории /plagins/modules/ согласно рекомендации в README.md.

**Шаг 10.** Single task playbook преобразуйте в single task role и перенесите в collection. У role должны быть default всех параметров module.
>Создана роль `my_own_role`, в которую перенесена task и обозначены переменные параметров module через default.
```bash
tim@tim:~/08-ansible-06-module/my_own_collection$ ansible-galaxy role init my_own_namespace/ytim/roles/my_own_role
[WARNING]: You are running the development version of Ansible. You should only run Ansible from "devel" if you are modifying the Ansible
engine, or trying out features under development. This is a rapidly changing source of code and can become unstable at any point.
- Role my_own_namespace/ytim/roles/my_own_role was created successfully
```
> [Ссылка на my_own_role](my_own_role)

**Шаг 11.** Создайте playbook для использования этой role.
> [Ссылка на playbook role](playbook/site.yml)
```bash
tim@tim:~/08-ansible-06-module/my_own_collection$ ansible-playbook playbook/site.yml -v
[WARNING]: You are running the development version of Ansible. You should only run Ansible from "devel" if you are modifying the Ansible
engine, or trying out features under development. This is a rapidly changing source of code and can become unstable at any point.
No config file found; using defaults
[WARNING]: No inventory was parsed, only implicit localhost is available
[WARNING]: provided hosts list is empty, only localhost is available. Note that the implicit localhost does not match 'all'

PLAY [Test module] ***************************************************************************************************************************

TASK [Gathering Facts] ***********************************************************************************************************************
ok: [localhost]

TASK [my_own_role : Call my_own_module] ******************************************************************************************************
ok: [localhost] => {"changed": false, "message": "file exists", "original_message": "Привет, Мир"}

PLAY RECAP ***********************************************************************************************************************************
localhost                  : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
```

**Шаг 12.** Заполните всю документацию по collection, выложите в свой репозиторий, поставьте тег `1.0.0` на этот коммит.

**Шаг 13.** Создайте .tar.gz этой collection: `ansible-galaxy collection build` в корневой директории collection.

**Шаг 14.** Создайте ещё одну директорию любого наименования, перенесите туда single task playbook и архив c collection.

**Шаг 15.** Установите collection из локального архива: `ansible-galaxy collection install <archivename>.tar.gz`.

**Шаг 16.** Запустите playbook, убедитесь, что он работает.

**Шаг 17.** В ответ необходимо прислать ссылки на collection и tar.gz архив, а также скриншоты выполнения пунктов 4, 6, 15 и 16.

## Необязательная часть

1. Реализуйте свой модуль для создания хостов в Yandex Cloud.
2. Модуль может и должен иметь зависимость от `yc`, основной функционал: создание ВМ с нужным сайзингом на основе нужной ОС. Дополнительные модули по созданию кластеров ClickHouse, MySQL и прочего реализовывать не надо, достаточно простейшего создания ВМ.
3. Модуль может формировать динамическое inventory, но эта часть не является обязательной, достаточно, чтобы он делал хосты с указанной спецификацией в YAML.
4. Протестируйте модуль на идемпотентность, исполнимость. При успехе добавьте этот модуль в свою коллекцию.
5. Измените playbook так, чтобы он умел создавать инфраструктуру под inventory, а после устанавливал весь ваш стек Observability на нужные хосты и настраивал его.
6. В итоге ваша коллекция обязательно должна содержать: clickhouse-role (если есть своя), lighthouse-role, vector-role, два модуля: my_own_module и модуль управления Yandex Cloud хостами и playbook, который демонстрирует создание Observability стека.

---

### Как оформить решение задания

Выполненное домашнее задание пришлите в виде ссылки на .md-файл в вашем репозитории.

---