# Git

### 1. VCS

1. **VCS (Version Control System)** - система контроля версий, регистрирующая изменения в одной или нескольких файлах с тем, чтобы в дальнейшем была возможность вернуться к определенным старым версиям этих файлов. <sup>[\[1.1\]][1.1]</sup>
  - Позволяет разработчкам работать одновременно над одним проектом.
  - Предотвращает случайные изменения в файлах.
  - Управляет историей проекта.
  - Существует два типа VCS: CVCS и DVCS.
  - VCS может хранить изменения локально или удаленно.

2. **CVCS (Central Version Control System)** - централизованная система контроля версий, которая подразумевает, что существует сервер, на котором хранятся все файлы под контролем VCS, и ряд клиентов получают копии файлов из него. <sup>[\[1.2\]][1.2]</sup>
  - Имеет преимущество над локальными VCS.
  - Администрирование единой VCS намного легче, чем локальные базы на каждом клиенте.
  - Однако такой подход является не безопасным, т.к. CVCS в единственном экземпляре.

3. **DVCS (Distributed Version Control System)** - распределенная система контроля версий подразумевает, что у клиентов находится полная копия репозитория с сервера, что позволяет легко восстановить рабочий прототип, если с ним что-то случится. <sup>[\[1.3\]][1.3]</sup>
  - Любое ответвление автоматически является бекапом проекта.
  - В больше части этих систем можно работать с несколькими удаленными репозиториями, таким образом, можно одновременно работать по-разному с разными группами людей в рамках одного проекта.

***

### 2. Общее

1. **Принцип хранения** - многие VCS хранят свои данные в виде списка изменений, Git же хранит полные копии файлов, только заменяя неизмененные файлы на ссылки. <sup>[\[2.1\]][2.1]</sup>
  - Таким образом Git является своего рода небольшой файловой системой.
  - Такой подход предоставляет ряд преимуществ при восстановлении данных, работе с комитами и т.д., но требует больше места.

2. **Локальные операции** - для совершения большинства операций в Git'е необходимы только локальные файлы и ресурсы, т.е. обычно информация с других компьютеров в сети не нужна. <sup>[\[2.2\]][2.2]</sup>
  - Данная особенность позволяет спокойно делать коммиты, а затем отправить их, как только станет доступна сеть (в некоторых других VCS это невозможно или же крайне неудобно).
  - Поскольку вся история проекта хранится локально у вас на диске, большинство операций кажутся практически мгновенными.

3. **Состояние файла** - в Git'е файлы могут находиться в одном из трёх состояний: fixed, changed и staged. <sup>[\[2.3\]][2.3]</sup>
  - fixed - файл уже сохранен в локальной базе.
  - changed - файл изменен, но изменение не зафиксировано (`git add`).
  - staged - файл изменен, и изменение было зафиксирвано (`git add`).
  
4. **Repository** - это место, где Git хранит метаданные и базу данных объектов вашего проекта.
  - Это наиболее важная часть Git'а, и именно она копируется, когда вы клонируете репозиторий с другого компьютера.
  - Git хранит все изменения в скрытой папке .git, которая есть в каждом проекте, находящемся под контролем VCS.

5. **Working Directory** - это извлечённая из базы копия определённой версии проекта.

6. **Staging Area** - это обычный файл, хранящийся в репозитории Git'а, который содержит информацию о том, что должно войти в следующий коммит.



[1.1]: https://git-scm.com/book/ru/v1/%D0%92%D0%B2%D0%B5%D0%B4%D0%B5%D0%BD%D0%B8%D0%B5-%D0%9E-%D0%BA%D0%BE%D0%BD%D1%82%D1%80%D0%BE%D0%BB%D0%B5-%D0%B2%D0%B5%D1%80%D1%81%D0%B8%D0%B9
[1.2]: https://git-scm.com/book/ru/v1/%D0%92%D0%B2%D0%B5%D0%B4%D0%B5%D0%BD%D0%B8%D0%B5-%D0%9E-%D0%BA%D0%BE%D0%BD%D1%82%D1%80%D0%BE%D0%BB%D0%B5-%D0%B2%D0%B5%D1%80%D1%81%D0%B8%D0%B9#%D0%A6%D0%B5%D0%BD%D1%82%D1%80%D0%B0%D0%BB%D0%B8%D0%B7%D0%BE%D0%B2%D0%B0%D0%BD%D0%BD%D1%8B%D0%B5-%D1%81%D0%B8%D1%81%D1%82%D0%B5%D0%BC%D1%8B-%D0%BA%D0%BE%D0%BD%D1%82%D1%80%D0%BE%D0%BB%D1%8F-%D0%B2%D0%B5%D1%80%D1%81%D0%B8%D0%B9
[1.3]: https://git-scm.com/book/ru/v1/%D0%92%D0%B2%D0%B5%D0%B4%D0%B5%D0%BD%D0%B8%D0%B5-%D0%9E-%D0%BA%D0%BE%D0%BD%D1%82%D1%80%D0%BE%D0%BB%D0%B5-%D0%B2%D0%B5%D1%80%D1%81%D0%B8%D0%B9#%D0%A0%D0%B0%D1%81%D0%BF%D1%80%D0%B5%D0%B4%D0%B5%D0%BB%D1%91%D0%BD%D0%BD%D1%8B%D0%B5-%D1%81%D0%B8%D1%81%D1%82%D0%B5%D0%BC%D1%8B-%D0%BA%D0%BE%D0%BD%D1%82%D1%80%D0%BE%D0%BB%D1%8F-%D0%B2%D0%B5%D1%80%D1%81%D0%B8%D0%B9

[2.1]: https://git-scm.com/book/ru/v1/%D0%92%D0%B2%D0%B5%D0%B4%D0%B5%D0%BD%D0%B8%D0%B5-%D0%9E%D1%81%D0%BD%D0%BE%D0%B2%D1%8B-Git#%D0%A1%D0%BB%D0%B5%D0%BF%D0%BA%D0%B8-%D0%B2%D0%BC%D0%B5%D1%81%D1%82%D0%BE-%D0%BF%D0%B0%D1%82%D1%87%D0%B5%D0%B9
[2.2]: https://git-scm.com/book/ru/v1/%D0%92%D0%B2%D0%B5%D0%B4%D0%B5%D0%BD%D0%B8%D0%B5-%D0%9E%D1%81%D0%BD%D0%BE%D0%B2%D1%8B-Git#%D0%9F%D0%BE%D1%87%D1%82%D0%B8-%D0%B2%D1%81%D0%B5-%D0%BE%D0%BF%D0%B5%D1%80%D0%B0%D1%86%D0%B8%D0%B8-%E2%80%94-%D0%BB%D0%BE%D0%BA%D0%B0%D0%BB%D1%8C%D0%BD%D1%8B%D0%B5
[2.3]: https://git-scm.com/book/ru/v1/%D0%92%D0%B2%D0%B5%D0%B4%D0%B5%D0%BD%D0%B8%D0%B5-%D0%9E%D1%81%D0%BD%D0%BE%D0%B2%D1%8B-Git#%D0%A2%D1%80%D0%B8-%D1%81%D0%BE%D1%81%D1%82%D0%BE%D1%8F%D0%BD%D0%B8%D1%8F