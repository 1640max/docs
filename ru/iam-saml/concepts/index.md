# {{ iam-full-name }}

{% include notitle [iam-def](../../_includes/iam-def.md) %}

С помощью {{ iam-short-name }} вы сможете:

* [предоставить доступ к ресурсам](#access);
* [управлять аккаунтами в Яндекс.Облаке](#accounts);
* [управлять ключами для авторизации](#keys);
* [авторизоваться в Яндекс.Облаке](#auth).


## Доступ {#access}

Чтобы предоставить пользователю доступ к ресурсу, вы назначаете ему [роли](access-control/roles.md) на ресурс. Каждая роль состоит из набора разрешений, описывающих допустимые операции с ресурсом.

Перед тем, как выполнить операцию с ресурсом, например создать виртуальную машину, Яндекс.Облако отправляет в IAM запрос на проверку, разрешена ли эта операция. {{ iam-short-name }} сравнивает список необходимых разрешений со списком разрешений пользователя, выполняющего операцию. Если какого-то из разрешений у пользователя нет, операция не будет выполнена и Яндекс.Облако вернет ошибку. Подробнее читайте в разделе [{#T}](access-control/index.md).


## Аккаунты {#accounts}

Для идентификации пользователей, выполняющих операции с ресурсами, используются [аккаунты Яндекс.Паспорта](#passport), [сервисные аккаунты](#sa) или [федеративные аккаунты](#saml-federation).

{% note info %}

Платежный аккаунт не используется для управления ресурсами в Яндекс.Облаке и не относится к сервису {{ iam-short-name }}. Подробнее читайте в разделе [{#T}](../../billing/concepts/billing-account.md) документации по биллингу.

{% endnote %}

### Аккаунт Яндекс.Паспорта {#passport}

_Аккаунт Яндекс.Паспорта_ — ваш аккаунт на Яндексе или [Яндекс.Коннекте]({{ link-yandex-connect }}). Аккаунт Яндекс.Паспорта необходим для управления ресурсами через [консоль управления]({{ link-console-main }}).

{% note info %}

{% include [yandex-account-2fa-warning.md](../../_includes/iam/yandex-account-2fa-warning.md) %}

{% endnote %}

### Сервисный аккаунт {#sa}

{% include [sa-def](../_includes_service/sa-def.md) %}

Использование сервисных аккаунтов позволяет гибко настраивать права доступа к ресурсам для написанных вами программ. Подробнее читайте в разделе [{#T}](users/service-accounts.md).

### Федеративный аккаунт {#saml-federation}

_Федеративный аккаунт_ — это аккаунт пользователя из SAML-федерации, например из Active Directory.

{% include [about-saml-federations](../../_includes/iam/about-saml-federations.md) %}

## Ключи для авторизации {#keys}

Для авторизации в Яндекс.Облаке используется три типа ключей:

* [API-ключи](authorization/api-key.md) — для упрощенной авторизации вместо IAM-токена;
* [Авторизованные ключи](authorization/key.md) — для получения IAM-токена для сервисного аккаунта;
* [Статические ключи доступа](authorization/access-key.md) — для авторизации в сервисах с AWS-совместимым API.

Сейчас все эти ключи используются только для сервисных аккаунтов.

## Авторизация {#auth}

Чтобы {{ iam-short-name }} смог проверить, обладает ли пользователь необходимыми правами, пользователь должен авторизоваться. Авторизация происходит по-разному в зависимости от типа аккаунта и используемого интерфейса. Подробнее читайте в разделе [{#T}](authorization/index.md).