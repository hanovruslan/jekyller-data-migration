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

**Изменения системных данных**

## Данные

- {:.next}Пользовательские данные
- {:.next}Системные данные

## Пользовательские данные

- {:.next}Порождаемые пользователем
- {:.next}Разные версии БД - разные данные

## Инструменты

- {:.next}Doctrine migrations
- {:.next}Phinx
- {:.next}Doctrine Fixtures
- {:.next}Поведенческий плагин
    - {:.next}KnpLabs DoctrineBehaviors
    - {:.next}gedmo doctrine extensions

## Заключение

**Знать возможности используемого инструмента со всеми его плюсами и минусами**

**Найти эффективные стыки инструментов исходя из первого пункта**

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
