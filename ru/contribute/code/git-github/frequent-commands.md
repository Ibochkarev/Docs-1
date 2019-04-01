---
title: "Git FAC (Frequently Accessed Commands)"
translation: "contribute/code/git-github/frequent-commands"
---

### Как мне создать и держать свежей локальную ветку develop?

Во-первых, с помощью модели сотрудничества и ветвления MODX вы не будете делать коммиты в свою ветку Major-версии, поэтому легко поддерживать ее в актуальном состоянии. Предположим, вы работаете с `2.x`:

 ``` php 
$ git fetch upstream
$ git checkout 2.x
Switched to branch "2.x"
$ git merge --ff-only upstream/2.x
```

Это означает, что modxcms или другой репозиторий установлен как `upstream` в remote. (git remote manpage: <http://www.kernel.org/pub/software/scm/git/docs/git-remote.html>)

### Как мне создать тематическую ветку?

Если вы только что влили свежие изменения из ветки develop из upstream репозитория, тогда это очень просто:

 ``` php 
$ git checkout -b myFeatureBranchName 2.x
```

Если вы не получили последние изменения из апстрима и слили их локально, вам следует [сделать это сначала](#GitFAC%28FrequentlyAccessedCommands%29-HowdoIgetandkeepmylocaldevelopbranchinsync%3F).

### Существует ли соглашение об именах для ветвей функций?

Если вы вносите изменения, связанные с заявкой, в трекере проблем (пожалуйста, сначала отправьте заявку на любые ошибки, если ее нет), тогда вы можете назвать свою ветку "issue-xxxx", где xxxx - номер проблемы из трекера ошибок.

 ``` php 
$ git checkout -b issue-1234 2.4.x
```

Обратите внимание, что это не является обязательным требованием, но может помочь вам организовать ваши локальные ветки, если у вас их много.

 Если вы работаете с новой функцией, у которой нет номера, вы можете назвать ее как угодно, но избегайте имен, которые выглядят как номера версий релиза.

 ``` php 
$ git checkout -b myAwesomeFeature 2.x
```

### Нужна ли мне новая тематическая ветка для каждой проблемы, над которой я работаю?

 Yes.

 ``` php 
$ echo 'Yes'
```

### Как мне сохранять свежесть мой ветки относительно develop ветки в upstream?

Если вы работаете над новой функцией, для которой требуется некоторое время, может оказаться полезным синхронизировать изменения в основной ветке разработки. Git позволяет вам «воспроизводить» ваши коммиты поверх изменений в ветке разработки с помощью команды rebase.

На самом деле, это, как правило, хорошая идея сделать перед тем, как сделать окончательный коммит на ваш форк и сделать Pull Request.

 ``` php 
$ git fetch upstream
$ git checkout 2.x
Switched to branch "2.x"
$ git merge --ff-only upstream/2.x
$ git checkout my-bc-feature
Switched to branch "my-bc-feature"
$ git rebase 2.x
```

 Чтобы узнать больше, вот страница помощи git rebase: <http://www.kernel.org/pub/software/scm/git/docs/git-rebase.html>

### Мне действительно нужно беспокоиться о ветке минорной версии?

 Нет, не совсем. Но если вы исправляете ошибки, которые должны быть включены в выпуск патча, как можно скорее, вы можете рассмотреть возможность ветвления и нацеливания на ветви с второстепенным выпуском, а не на основные, в случае необходимости их переноса из-за конфликтов в изменениях между основными и незначительный. Но это совсем не критично для рабочего процесса участника.

 ``` php 
$
```