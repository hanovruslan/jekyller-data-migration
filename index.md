---

layout: yandex2

style: |
    .pre-small pre code { font-size: 24px!important; line-height: 48px!important; }
    .pre-big pre code { font-size: 54px !important; line-height: 108px !important; } #  9 lines x 52 symbols
    .big-list { font-size: 80px!important; line-height: 160px!important; }
    .images-w { background-color: #fff !important; }
    .slide-red { border-left: 9px solid #f00 !important; }
    figure.short { width: 480px !important; }
    .text-center { text-align: center !important; }
    img.center { margin: auto !important; }
    img.title { width: 1000px !important; }
    .symfoniacs { background-color: white !important; }
---

# Symfoniacs SPB \#4
{:.section.symfoniacs}

### PropellerAds 30 oct 2018

## {{ site.presentation.title }}
{:.title}

### Symfoniacs SPB #4

<div class="authors">
{% if site.author %}
<p>{{ site.author.name }}{% if site.author.position %}, {{ site.author.position }}{% endif %}</p>
{% endif %}
</div>

## О докладчике

* Разработчик php, java, symfony 1-4
* Докладчик и организатор митапов Symfoniacs, Москва и Санкт-Петербург
* Программист по образованию - Новосибирский государственный Университет

## Цель

**Изменение системных данных**

## Критерии отбора

**Простота подключения**{:.next}
**Богатство настроек**{:.next}
**Версионирование**{:.next}
**Интеграция в приложение и тесты**{:.next}

## Что будет в докладе

**Перечисление популярных решений**{:.next}

**Плюсы и минусы**{:.next}

## Что НЕ будет в докладе

**Live demo**{:.slide-red.next}

**Цитирование документации**{:.slide-red.next}

## Данные
{:.title.symfoniacs}
## Данные

- {:.next}Пользовательские данные
- {:.next}Системные данные

## Пользовательские данные

- {:.next}Порождаемые пользователем
- {:.next}Разные версии БД - разные данные

## Схема данных и данные - это две большие разницы
{:.blockquote}

## Инструменты
{:.title.symfoniacs}
## Инструменты

- {:.next}Phinx
- {:.next}Doctrine migrations
- {:.next}Doctrine Fixtures
- {:.next}Поведенческий плагин
    - {:.next}KnpLabs DoctrineBehaviors
    - {:.next}gedmo doctrine extensions

## Phinx
{:.title.symfoniacs}
## Phinx

- Продукт CakePHP
- SQL Builder
- Платформонезависимо
- Версионирование
- Phinx Seed
- Аналог Doctrine migrations и Doctrine fixtures

## Phinx Seed
{:.fullscreen}
```php
<?php

class UserSeeder extends Phinx\Seed\AbstractSeed {
    public function run() {
        $data = [[
            'body'    => 'foo',
            'created' => date('Y-m-d H:i:s'),
        ]];
        $posts = $this->table('posts');
        $posts->insert($data)
              ->save();
        // empty the table
        $posts->truncate();
    }
}
```

## Установка

```bash

composer require robmorgan/phinx
./vendor/bin/phinx init

```

## Особенности

Плюсы

**Простая реализация**{:.next}
**Зависимость миграций**{:.next}
**Интеграция с Faker library**{:.next}

Минусы

**Простая реализация %)**{:.slide-red.next}
**Нет symfony recipe**{:.slide-red.next}
**Нет symfony command (./vendor/bin/phinx ... )**{:.slide-red.next}

## Doctrine migrations
{:.title.symfoniacs}
## Doctrine migrations
{:.fullscreen}
```php
# class AddVKCOM_IDToUser     extends AbstractMigration {
  class Version20100416130459 extends AbstractMigration {
    public function up(Schema $schema) {
        $this->addSql(
          'ALTER TABLE users ADD vkcom_id VARCHAR(255) NOT NULL'
        );
    }
    public function down(Schema $schema) {
        $this->addSql(
          'ALTER TABLE users DROP vkcom_id'
        );
    }
}
```
## Заключение
{:.title.symfoniacs}
## Данные - это сложно
{:.blockquote}
## Заключение

**Знать возможности используемого инструмента со всеми его плюсами и минусами**

**Найти эффективные стыки инструментов исходя из первого пункта**

**Комбинация известных инструментов**

## Данные - это сложно
{:.blockquote}

## Вопросы?
{:.contacts}

{% if site.author %}

<figure markdown="1">

### {{ site.author.name }}

{% if site.author.position %}
{{ site.author.position }}
{% endif %}

</figure>

{% endif %}

{% if site.author2 %}

<figure markdown="1">

### {{ site.author2.name }}

{% if site.author2.position %}
{{ site.author2.position }}
{% endif %}

</figure>

{% endif %}

<!-- разделитель контактов -->
-------

<!-- left -->
- {:.github}hanovruslan
- {:.telegram}hanovruslan


<!-- right -->
- {:.mail}hanov.ruslan@gmail.com
- {:.twitter}@hanovruslan
- {:.facebook}hanov.ruslan
