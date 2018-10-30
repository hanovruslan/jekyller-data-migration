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
* Программист по образованию - Новосибирский Государственный Университет

## Что будет в докладе

**Перечисление популярных решений**{:.next}

**Плюсы и минусы**{:.next}

## Чего НЕ будет в докладе

**Live demo**{:.slide-red.next}

**Цитирование документации**{:.slide-red.next}

**Мемасиков**{:.slide-red.next}

## Задача

**Изменение системных данных**

Примеры:
- Навигация
- Системные пользователи
- Произвольные реквизиты доступа

## Данные
{:.title.symfoniacs}
## Данные

**Пользовательские данны**

Могут быть разными на разных инсталляциях*

**Системные данные**

Должны быть одинаковыми на всех инсталляциях*

### * Один и тот же заказчик, одинаковая версия

## Чего хотим?

**Автоматически изменять системные данные**

## Как схема данных?
{:.blockquote}
## Критерии отбора

**Простота подключения (.5)**{:.next}
**Версионирование (1)**{:.next}
**Зависимость миграций (1)**{:.next}
**Доступные драйверы (2)**{:.next}
**Простота реализации (.5)**{:.next}
**Богатство настроек + документация (.5)**{:.next}
**Интеграция в приложение (.5)**{:.next}
**Транзитивные зависимости (.5)**{:.next}

## Варианты
{:.title.symfoniacs}
## Варианты

- {:.next}Phinx
- {:.next}Doctrine Migrations
- {:.next}Doctrine Fixtures
- {:.next}Поведенческий плагин
    - {:.next}KnpLabs DoctrineBehaviors
    - {:.next}Gedmo doctrine extensions

## Phinx
{:.title.symfoniacs}
## Phinx

- Продукт CakePHP
- SQL Builder
- Аналог Doctrine Migrations и Doctrine fixtures
- Релиз (?) - конец 2012 года
- Phinx Seed
- @packagist 6.6M, 3 596

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

## Phinx

Плюсы (4)

**Простота подключения (.5)**{:.next}
**Версионирование (1)**{:.next}
**Зависимость миграций (1)**{:.next}
**Простота реализации (.5)**{:.next}
**Богатство настроек + документация (.5)**{:.next}
**Транзитивные зависимости (.5)**{:.next}

Минусы (2.5)

**Доступные драйверы (2)**{:.slide-red.next}
**Интеграция в приложение (.5)**{:.slide-red.next}

## Doctrine
{:.title.symfoniacs}
## Doctrine Migrations и Doctrine Fixtrures @packagist

Migrations

- 20M, 1 584 (80) lib
- 16M, 1 304 (81) bundle

Fixtures

- 18.5M, 985 (53) lib
- 16.0M, 824 (52) bundle

Phinx - 6.6M, 3 596, (555)

## Doctrine Migrations
{:.title.symfoniacs}
## Doctrine Migrations

- Doctrine ORM
- Входит в TOP30 самых популярных symfony пакетов
- Релиз ALPHA - конец 2012 года
- Релиз - середина 2015 года

## Doctrine Migrations
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

## Doctrine Migrations

Плюсы (4.5)

**Версионирование (1)**{:.next}
**Доступные драйверы (2)**{:.next}
**Простота реализации (.5)**{:.next}
**Богатство настроек + документация (.5)**{:.next}
**Интеграция в приложение (.5)**{:.next}

Минусы (2)

**Простота подключения (.5)**{:.slide-red.next}
**Зависимость миграций (1)**{:.slide-red.next}
**Транзитивные зависимости (.5)**{:.slide-red.next}

## Doctrine Fixtures
{:.title.symfoniacs}
## Doctrine Fixtures

- Doctrine ORM
- Входит в TOP30 самых популярных symfony пакетов
- Релиз ALPHA - конец 2012 года
- Релиз - середина 2013 года

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

## Doctrine Fixtures

Плюсы (4)

**Простота подключения (.5)**{:.next}
**Зависимость миграций (1)**{:.next}
**Доступные драйверы (2)**{:.next}
**Интеграция в приложение (.5)**{:.next}

Минусы (2.5)

**Версионирование (1)**{:.slide-red.next}
**Простота реализации (.5)**{:.slide-red.next}
**Богатство настроек + документация (.5)**{:.slide-red.next}
**Транзитивные зависимости (.5)**{:.slide-red.next}

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

## Поведенческий плагин

Плюсы (4.5)

**Версионирование (1)**{:.next}
**Доступные драйверы (2)**{:.next}
**Богатство настроек + документация (.5)**{:.next}
**Интеграция в приложение (.5)**{:.next}
**Транзитивные зависимости (.5)**{:.next}

Минусы (2)

**Простота подключения (.5)**{:.slide-red.next}
**Зависимость миграций (1)**{:.slide-red.next}
**Простота реализации (.5)**{:.slide-red.next}

## Свой поведенческий плагин?
{:.title.symfoniacs}
## Плюсы/Минусы

- Простота подключения ?
- Версионирование ?
- Зависимость миграций ?
- Доступные драйверы (doctrine dbal) ?
- Богатство настроек + документация ?
- Интеграция в приложение ?
- Транзитивные зависимости ?

Минусы

**Простота реализации!**{:.slide-red.next}

## Выбор

- {:.next}Phinx - 4
- {:.next}Doctrine Fixtures - 4
- {:.next}Doctrine Migrations - 4.5
- {:.next}Поведенческий плагин - 4.5
- {:.next}Свой поведенческий плагин - 6 (или 0 :))

## Сейчас - Doctrine Migrations или Phinx?
{:.blockquote}
## Светлое будущее - Свой поведенческий плагин?
{:.blockquote}
## Заключение

**Знать возможности используемых инструментов**

**Найти эффективные стыки инструментов исходя из первого пункта**

**Создавать свои пакеты и бандлы**

## Спасибо за внимание!
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
