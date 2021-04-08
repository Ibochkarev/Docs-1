---
title: "Управления таблицами"
description: "Управления таблицами для TinyMCE"
translate: "extras/tinymce/tinymce.table-controls"
---

Чтобы добавить управление таблицами в редактор TinyMCE, вам нужно будет изменить две настройки. Вы можете найти их в разделе «Система» -> «Системные настройки» и выбрать `tinymce` в раскрывающемся списке Пространства имен - по умолчанию это `core` в верхней части списка.

Там найдите и добавьте следующее:

-   `tiny.custom_plugins`: добавьте где-нибудь там 'table', убедившись, что он остается правильным списком, разделенным запятыми.
-   `tiny.custom_buttonsN`: Любая из 5 настроек, в которых вы хотите отображать элементы управления таблицей, например, tiny.custom_buttons3, и добавить 'tablecontrols', следя за тем, чтобы он оставался правильным списком, разделенным запятыми.

Источник: <https://forums.modx.com/index.php/topic,65609.msg370576.html#msg370576>

## Смотрите также

1. [Проверка орфографии](extras/tinymce/tinymce.spellchecker)
2. [Шаблон](extras/tinymce/tinymce.template)
3. [TinyMCE](extras/tinymce)