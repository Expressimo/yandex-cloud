---
title: "Управление доступом в {{ dataproc-full-name }}"
description: "Управление доступом в сервисе по созданию и управлению кластерами Apache Hadoop® и Apache Spark™. Чтобы разрешить доступ к ресурсам сервиса {{ dataproc-name }} (кластерам или подкластерам), назначьте пользователю нужные роли из приведенного списка."
---

# Управление доступом в {{ dataproc-name }}

Пользователь {{ yandex-cloud }} может выполнять только те операции над ресурсами, которые разрешены назначенными ему ролями. Пока у пользователя нет никаких ролей, почти все операции ему запрещены.

Чтобы разрешить доступ к ресурсам сервиса {{ dataproc-name }} (кластерам или подкластерам), назначьте пользователю нужные роли из приведенного ниже списка. На данный момент роль может быть назначена только на родительский ресурс (каталог или облако), роли которого наследуются вложенными ресурсами.

{% note info %}

Подробнее о наследовании ролей читайте в разделе [{#T}](../../resource-manager/concepts/resources-hierarchy.md#access-rights-inheritance) документации сервиса {{ resmgr-full-name }}.

{% endnote %}

## Назначение ролей {#grant-role}

Чтобы назначить пользователю роль:

{% include [grant-role-console](../../_includes/grant-role-console.md) %}

## Роли {#roles}

Ниже перечислены все роли, которые учитываются при проверке прав доступа в сервисе {{ dataproc-name }}.

{% include [mdb.dataproc.agent](../../_includes/iam/roles/dataproc-agent.md) %}

{% include [data-proc-roles](../../_includes/iam/roles/data-proc-roles.md) %}

### {{ roles-mdb-auditor }} {#mdb-auditor}

Роль `{{ roles-mdb-auditor }}` предоставляет минимально необходимые права для просмотра информации о кластерах {{ dataproc-name }} (без доступа к данным и логам работы).

### {{ roles-mdb-viewer }} {#mdb-viewer}

Роль `{{ roles-mdb-viewer }}` позволяет просматривать информацию о кластерах {{ dataproc-name }} и логах их работы.

### {{ roles-mdb-admin }} {#mdb-admin}

Пользователь с ролью `{{ roles-mdb-admin }}` может управлять кластерами {{ dataproc-name }}, например создать кластер, создать или удалить подкластер в кластере.

Включает в себя роль `{{ roles-mdb-viewer }}`.

### {{ roles-viewer }} {#viewer}

Пользователь с ролью `{{ roles-viewer }}` может подключаться к хостам в кластере {{ dataproc-name }}, если его [SSH-ключи](../../glossary/ssh-keygen.md) привязаны к этому кластеру.

### {{ roles-editor }} {#editor}

Пользователь с ролью `{{ roles-editor }}` может управлять любыми ресурсами, например создать кластер, создать или удалить подкластер в кластере.

Включает в себя роль `{{ roles-viewer }}`.

### {{ roles-admin }} {#admin}

Пользователь с ролью `{{ roles-admin }}` может управлять правами доступа к ресурсам, например разрешить другим пользователям создавать кластеры {{ dataproc-name }} или просматривать информацию о правах пользователей.

Включает в себя роль `{{ roles-editor }}`.

{% include [cloud-roles](../../_includes/cloud-roles.md) %}
