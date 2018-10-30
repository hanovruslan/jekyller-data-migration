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

* Разработчик php, java
* Symfony 1-4
* Докладчик и организатор митапов Symfoniacs, Москва и Санкт-Петербург
* Программист по образованию - Новосибирский государственный Университет

## Цель

**Изменение системных данных**


## Что будет в докладе

**Перечисление популярных решений**{:.next}

**Плюсы и минусы**{:.next}

## Чего НЕ будет в докладе

**Live demo**{:.slide-red.next}

**Цитирование документации**{:.slide-red.next}

**Мемасиков**{:.slide-red.next}

## Данные
{:.title.symfoniacs}
## Данные

* Пользовательские могут быть *разными* на разных инсталляциях
* Системные должны быть *одинаковыми* на всех инсталляциях

## Чего хотим?

**Автоматически изменять набор (системных) данных**

## Как схема данных?
{:.blockquote}
## Критерии отбора

**Простота подключения**{:.next}

**Версионирование (без костылей)**{:.next}

**Зависимость миграций (без костылей)**{:.next}

**Доступные драйверы**{:.next}

**Богатство настроек + документация**{:.next}

**Интеграция в приложение и тесты**{:.next}

**Транзитивные зависимости**{:.next}

## Варианты
{:.title.symfoniacs}
## Варианты

- {:.next}Phinx
- {:.next}Doctrine migrations
- {:.next}Doctrine Fixtures
- {:.next}Поведенческий плагин
    - {:.next}KnpLabs DoctrineBehaviors
    - {:.next}Gedmo doctrine extensions

## Phinx
{:.title.symfoniacs}
## Phinx

- Продукт CakePHP
- SQL Builder
- Аналог Doctrine migrations и Doctrine fixtures
- Phinx Seed
- @packagist 6.5M, 3 596

## Phinx Seed
{:.fullscreen}
```php

class UserSeeder extends Phinx\Seed\AbstractSeed {
    public function run() {
        // empty the table
        $posts->truncate();
        $data = [[
            'body'    => 'foo',
            'created' => date('Y-m-d H:i:s'),
        ]];
        $posts = $this->table('posts');
        $posts->insert($data)
              ->save();
    }
}
```

## Особенности

Плюсы

**Простота подключения**{:.next}
**Версионирование**{:.next}
**Зависимость миграций**{:.next}
**Богатство настроек + документация**{:.next}
**Транзитивные зависимости**{:.next}

Минусы

**Доступные драйверы (mysql, postgres, sqlite, SQL Server)**{:.slide-red.next}
**Интеграция в приложение и тесты**{:.slide-red.next}

## Doctrine
{:.title.symfoniacs}
## Doctrine Migrations и Doctrine Fixtrure @packagist

Migrations

- 20M, 1 584 (79.9) lib
- 16M, 1 304 (80.9) bundle

Fixtures

- 18.5M, 985 (52.9) lib
- 16.0M, 824 (51.8) bundle

Phinx - 6.6M, 3 596 (*554.8*)

## Doctrine migrations
{:.title.symfoniacs}
## Doctrine migrations

 - Doctrine ORM
 - Входит в TOP30 самых популярных symfony пакетов
 - Релиз ALPHA - конец 2012 года
 - Релиз - середина 2015 года

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

## Особенности

Плюсы

**Версионирование**{:.next}
**Зависимость миграций**{:.next}
**Доступные драйверы (все популярные)**{:.next}
**Богатство настроек + документация**{:.next}
**Интеграция в приложение и тесты**{:.next}

Минусы

**Простота подключения**{:.slide-red.next}
**Транзитивные зависимости**{:.slide-red.next}

## Doctrine Fixtures
{:.title.symfoniacs}
## Doctrine migrations

 - Doctrine ORM
 - Входит в TOP30 самых популярных symfony пакетов
 - Релиз ALPHA - конец 2012 года
 - Релиз - середина **2013** года

## Doctrine Fixtures
{:.fullscreen}
```php

class AppFixtures extends Fixture {
    public function load(ObjectManager $manager) {
        for ($i = 0; $i < 20; $i++) {
            $product = new Product();
            $product->setName('product '.$i);
            $product->setPrice(mt_rand(10, 100));
            $manager->persist($product);
            $this->addReference('product_' . $i, $product);
        }
        $manager->flush();
    }
}
```

## Особенности

Плюсы

**Простота подключения**{:.next}
**Доступные драйверы (все популярные)**{:.next}
**Интеграция в приложение и тесты**{:.next}

Минусы

**Версионирование**{:.slide-red.next}
**Зависимость миграций**{:.slide-red.next}
**Богатство настроек + документация**{:.slide-red.next}
**Транзитивные зависимости**{:.slide-red.next}

## Поведенческий плагин
{:.title.symfoniacs}
## Поведенческий плагин

**KnpLabs DoctrineBehaviors**

**Gedmo doctrine extensions**

## Поведенческий плагин
{:.fullscreen}
```php

/**
 * @ORM\Table(name="article")
 * @ORM\Entity
 * @Gedmo\SoftDeleteable(fieldName="deletedAt", timeAware=false, hardDelete=true)
 */
class Article {
    /**
     * @Gedmo\Translatable
     * @ORM\Column(name="title", type="string", length=128)
     */
    private $title;

}
```

## Особенности

Плюсы

**Версионирование**{:.next}
**Зависимость миграций**{:.next}
**Доступные драйверы (все популярные)**{:.next}
**Богатство настроек + документация**{:.next}
**Интеграция в приложение и тесты**{:.next}
**Транзитивные зависимости**{:.next}

Минусы

**Простота подключения**{:.slide-red.next}

## Импорт из файла
{:.title.symfoniacs}

## Особенности

Плюсы/Минусы

 - Простота подключения
 - Версионирование
 - Зависимость миграций
 - Доступные драйверы (doctrine dbal?)
 - Богатство настроек + документация
 - Интеграция в приложение и тесты
 - Транзитивные зависимости

## Заключение

**Знать возможности используемого инструмента со всеми его плюсами и минусами**

**Найти эффективные стыки инструментов исходя из первого пункта**

**Создавать свои пакеты и бандлы**

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
