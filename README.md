# Инструкция по работе с GIT и GITHUB  

---  
Для начала нужно создать папку на компьютере. Это и будет наш GIT-репозиторий.  
Для инициальзации Git-репозитория нужно выполнить команду ```git init```, находясь в этой папке.  
Для того, чтобы "разгитить" папку нужно выполнить команду ```rm -rf .git```  
Команда ```git status``` позволяет проверить состояние репозитория.  
Она выведет:  
* название текущей ветки: **On branch master** или **On branch main**;
* сообщение о том, что в репозитории еще нет коммитов: **No commits yes**;
* сообщение, которое говорит: «чтобы что-нибудь закоммитить (то есть зафиксировать), нужно сначала это создать» — **nothing to commit (create/copy files and use "git add" to track)**.  

## Добавляем файлы в репозиторий  

Добавим в репозиторий два файла. Например, todo.txt и readme.md  
Команда **git add** позволяет подготовить файл к созранению. Используем ее.  
```
git add --all
```  
Флаг ```--all``` указывает на то, что мы хотим подготовить все файлы, находящиеся в папке.  
С помощью ```git add .``` можно добавить в репозиторий текущую папку со всеми файлами  


## Первый коммит  
**Комит** - это одна из сущностей в Git. Коммит гарантирует, что изменения будут сохранены в истории и при необходимости  
можно будет откатиться к ним.  

Сделать коммит можно командой ```git commit``` с флагом ```-m``` он присваивает комментарий к коммиту.  


Просмотреть историю коммитов можно с помощью команды ```git log```  

## Про GitHub  

GitHub позволяет создать удаленный репозиторий и делиться им с кем угодно, это необходимый инструмент в командой разратоке.  
Мы как бы создаем удаленную версию своего локального репозитория.  
Создать удаленный репозиторий можно по [инструкции](https://docs.github.com/ru/repositories/creating-and-managing-repositories/creating-a-new-repository)  


#SSH ключ  

Для связывания локального и удаленного репозиториев нужен так называемый SSH ключ.  
Он бывает публичный и приватный.
* Публичный ключ доступен всем и используется для шифрования данных.
* Приватный ключ хранится только локально на компьютере и используется для расшифровки. Его нельзя никому передавать!!!  

## Инструкция по генерации SSH-ключа  

Для генерации можно использовать программу ssh-keygen. Для этого нужно открыть терминал и ввести следующую команду:  
```ssh-keygen -t ed25519 -C "электронная почта, к которой привязан ваш аккаунт на GitHub"```  

Теперь проверим сработало ли:  
```ls -a ~/.ssh```  
На экране должны появится два файла .pub а другой без расширения.  
.pub - публичный ключ, им можно делиться.  
Файл без расширения - приватный, его нельзя никому передавать!!!  
Далее нужно связать ключ с GitHub  

## Связываем локальный и удалённый репозитории  

Переходим на удаленный репозиторий и копируем URL тип SSH.  
Открываем консоль, переходим в каталог с репозиторием и вводим:  
```git remote add origin [SSH]```  
Чтобы убедиться, что репозиторий создан нужно использовать ```git remote -v```  

## git push - отправить изменения на удаленный репозиторий   

В первый раз ```git push``` нужно вводить с флагом ```-u``` и параметром ```origin```  
Флаг ```-u``` свяжет локальную ветку с одноменной удаленной.  
```git push -u origin master```  

Далее можно отследить изменения на самом GitHub в репозитории.  

# Хеш - идентификатор коммита  
---  

**Хешерование** - это способ преобразовать набор данных и получить их "отпечаток"  

Информация о коммите — это набор данных: когда был сделан коммит, содержимое файлов в репозитории на момент коммита и ссылка на предыдущий, или родительский (англ. parent), коммит.  

Git хеширует информацию о коммите с помощью алгоритма **SHA-1** и получает хеш для каждого коммита  

## Хеш - основной идентификатор коммита  

Git хранит таблицу соответствий **хеш - информация о коммите**. Если известен хеш, можно узнать все остальное: автора дату и тд.  

Все хеши и таблицу **хеш - информация о коммите** Git сохраняет в служебные файлы, которые находятся в папке .git репозитория.  


