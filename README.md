Узнать, где вы сейчас, поможет команда pwd (от англ. print working directory — «показать рабочую папку»). Она выводит путь к текущей директории.

С помощью терминала вы всегда можете перейти к домашней директории. Для этого нужно ввести команду cd (от англ. change directory — «сменить директорию») 
и символ ~ — обозначение домашней директории. Не забудьте про Enter для выполнения.
$ cd ~ 

Вывести содержимое директории — ls
ls -a # вывели список, в котором отображаются скрытые файлы ., .. и .git

Сменить директорию — cd

Обратите внимание: если в названии папки есть пробелы, при вводе нужно использовать кавычки.

$ cd "Фотографии с дня рождения" 

Также cd позволяет перемещаться сразу через несколько директорий. Для этого нужно разделить их названия знаком /.
cd github/open-source-project # переходим через несколько директорий

Создание файлов и директорий — touch, mkdir

Можно создать целую структуру директорий одной командой с помощью флага -p.
$ mkdir -p dir1/dir-inside/dir-deeper-inside
# создали папку dir-deeper-inside в папке dir-inside, которая находится в папке dir1 

По умолчанию touch и mkdir создают файлы и папки в текущей рабочей директории. Например, если вы находитесь в директории abs, 
команда touch file.txt создаст файл именно там: abs/file.txt.

Копирование файлов — cp
cp index.html src/
# скопировали index.html в папку src 

$ mkdir first-project   
$ touch first-project/data.txt first-project/table.csv 

Перемещение файлов и папок — mv

$ mv table.csv ./very-important-files
# сначала указываем имя файла, который хотим переместить, потом путь — куда перемещаем 

$ cd very-important-files
$ ls
table.csv 
# перешли в папку very-important-files и проверили, что всё сработало 

Чтение файлов — cat
$ cat myfile.txt # распечатали содержимое файла myfile.txt
file-content-1
file-content-2 
Команда cat работает только с текстовыми файлами.

Удаление файлов и папок — rm, rmdir, rm -r
$ rm example.txt # удалили файл example.txt из текущей папки 
$ rmdir images # команда удалит папку images из текущей директории, 
               # если папка images пуста 
$ rm -r images # удалили папку images со всем её содержимым из текущей директории 

Необязательно заучивать все команды наизусть. Если нужно найти какую-нибудь из них, достаточно вспомнить, с каких букв она начинается. 
Можно набрать их в командной строке и дважды нажать клавишу Tab. 
Терминал покажет список всех команд, которые начинаются с этих символов.
Tab автоматически дописывает не только команды, но и пути. Начните печатать имя папки или файла (они должны быть в той же директории) 
и нажмите Tab. Терминал заполнит имя автоматически.

Сделать папку репозиторием — git init
«Разгитить» папку, если что-то пошло не так, — rm -rf .git
$ cd <папка с репозиторием> # перешли в папку
$ rm -rf .git # удалили подпапку .git 

Проверить состояние репозитория — git status

Подготовить файлы к сохранению — git add

Добавим в репозиторий два файла — файл todo.txt со списком дел и readme.txt с информацией о проекте.
Создайте файлы todo.txt и readme.txt в папке first-project и запустите git status, чтобы посмотреть, что изменилось.
$ touch todo.txt
$ touch readme.txt
# создали файлы todo.txt и readme.txt
$ git status # проверили статус 

Сейчас в first-project два файла. Мы хотим отслеживать состояние обоих, поэтому можем использовать команду git add --all 
(от англ. add — «добавить» + от англ. all — «всё»). Ключ, или флаг, --all позволяет подготовить к сохранению все файлы в репозитории.
$ git add --all # подготовили к сохранению все файлы в репозитории
$ git status # проверили статус 
Добавлять файлы можно и по одному, без ключа --all.
$ git add todo.txt
$ git add readme.txt
$ git status 
Также можно добавить текущую папку целиком — в этом случае все файлы в ней тоже будут добавлены. Обратиться к текущей папке в Bash позволяет точка (.).
$ git add . # добавить всю текущую папку
$ git status 

Выполнить коммит — git commit
Сделать коммит можно командой git commit c ключом -m (от англ. message — «сообщение»), который присваивает коммиту сообщение.
Например, перейдите в папку first-project и выполните коммит со следующим комментарием.
$ git commit -m 'Мой первый коммит!' 

Просмотреть историю коммитов — git log

Что такое GitHub
GitHub — платформа для хранения IT-проектов и их командной разработки с использованием Git. По сути, это сайт, 
куда можно загрузить файлы своего проекта для обмена с другими людьми.

Проверка наличия SSH-ключа
Обычно SSH-ключи находятся в директории .ssh/. Проверить наличие этой директории и файлов в ней можно с помощью следующей команды.
$ ls -la .ssh/ # вывели список созданных ключей 

Инструкция по генерации SSH-ключа
Для генерации SSH-пары можно использовать программу ssh-keygen. Откройте терминал и введите следующую команду.
 $ ssh-keygen -t ed25519 -C "электронная почта, к которой привязан ваш аккаунт на GitHub"

Инструкция по связыванию SSH-ключа и GitHub-аккаунта
    После выполнения ssh-keygen в директории ~/.ssh есть два файла — id_ed25519 и id_ed25519.pub 
(или id_rsa и id_rsa.pub — в зависимости от того, какой алгоритм вы использовали).
 # скопировать содержимое ключа в буфер обмена:
 # для ed25519:
 $ pbcopy < ~/.ssh/id_ed25519.pub

Привязать удалённый репозиторий к локальному — git remote add
Перейдите на страницу удалённого репозитория, выберите тип SSH и скопируйте URL. Кнопка справа позволит сделать это мгновенно.

$ cd ~/dev/first-project
$ git remote add origin git@github.com:%ИМЯ_АККАУНТА%/first-project.git 

origin (англ. «источник») — стандартный псевдоним, с помощью которого можно обращаться к главному удалённому репозиторию 
(обычно такой репозиторий один). Это значительно упрощает работу.

Убедиться, что репозитории связаны, — git remote -v
Отлично: вы связали локальный репозиторий с удалённым. Осталось убедиться, что всё работает, с помощью следующей команды.
$ git remote -v
origin    git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ-ПРОЕКТА%.git (fetch)
origin    git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ-ПРОЕКТА%.git (push) 

Отправить изменения на удалённый репозиторий — git push
В первый раз эту команду нужно вызвать с флагом -u и параметрами origin (имя удалённого репозитория) и main или master (название текущей ветки). 
Флаг -u свяжет локальную ветку с одноимённой удалённой. Как вы связывали локальный и удалённый репозитории, так же и здесь нужно дополнительно связать ветки.
$ git push -u origin main # Если команда приведёт к ошибке, попробуйте 
                          # заменить main на master. 

Клонировать репозиторий — git clone
$ git clone https://github.com/yandex-praktikum/git-clone-lesson
# укажите адрес репозитория, который нужно склонировать 
Убедитесь в том, что репозитории связаны, командой git remote -v.
$ cd git-clone-lesson
$ git remote -v
origin    git@github.com:yandex-praktikum/git-clone-lesson.git (fetch)
origin    git@github.com:yandex-praktikum/git-clone-lesson.git (push) 




