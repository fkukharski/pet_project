## Предыстория

Примерно год назад у меня была большая проблема с тем, чтобы найти квартиру для съема. Начинал я с ручного поиска, но зачастую, если мне и попадался хороший вариант, то он слетал по какой-либо причине.

Поиск затянулся больше, чем на месяц. Приближался сентябрь, а в конце августа - сентябре спрос на квартиры сильно взлетает. Мною было решено оптимизировать скорость поиска и отклика на объявления о сдаче жилья и я на коленке собрал мини-проект, который:

- раз в несколько минут ходил на популярные сайты объявлений о сдаче жилья в аренду (было сделано через while True + sleep);
- по заданным параметрам парсил свежие объявления;
- отправлял в телеграмм-чат свежие объявления.

Сейчас доступ к проекту вместе с сервером утерян, но там был только нехитрый парсинг + отправка в телеграмм, так что не страшно.

## Идея

Идейно этот проект можно развить, например, так:

- ходить в несколько источников, забирая информацию об объявлениях (по API). Можно начать с батчевой обработки раз в какое-то время, но можно будет сделать квази-стриминговую обработку, сделав между сайтом объявления и моей программой стриминговый прокси-источник. Здесь я пока не могу точнее сказать, насколько это реализуемо, потому что со стримингом не работал;
- забранные данные складывать в какую-нибудь БД, например, в постгрес;
- свежие объявления отправлять в канал в телеграмме. Можно, например, захардкодить параметры поиска, а можно попробовать реализовать загрузку желаемых параметров пользователем из телеграмма;
- раз в день данные можно складывать в какую-нибудь витрину, поверх которой можно построить дашборд с дневным/недельным/месячным обзором.

## Инструменты

Получается, можно попробовать следующие инструменты/технологии:

- Python как основной язык;
- SQL + PostgreSQL;
- API-парсинг;
- Kafka/другое для создания проки-источника и стриминговой обработки данных;
- Airflow для регуляризации;
- DataLens/Tableau/другое для визуализации;
- Yandex Cloud/другое для того, чтобы все это дело развернуть.

## Мысли

Меня смущает этическая сторона такого проекта. Насколько этично парсить сайты других компаний для такого проекта? Как будто бы для личных целей это нормально, но бизнес-ценность выудить из такого проекта было бы тяжело. С другой стороны, есть же куча всяких агрегаторов, которые на этом построили целый бизнес. Не знаю... Что-то смущает

Буду рад любым комментариям :)
