PHP CommerceML 2
==============

### О библиотеке
Данная библиотека предназначена для поточного разбора выгруженных из 1с файлов по стандарту Commerce ML 2.

Сам парсер представляет собой диспетчер событий, т.е. при нахождении в структуре Commerce ML 2 объекта нужной структуры, диспетчером вызывается определенной событие и в него передается уже сформированные по модельной структуре объект.

На данный момент существует 5 основных событий:

* получение Категории;
* получение Предложения;
* получение Категории Цен;
* получение Товара;
* получение Свойства товара.

### Простое использование парсера:

```php
$parser = new \CommerceMLParser\Parser(); // Создание экземпляра класса парсера
$parser->addListener("CategoryEvent", function (\CommerceMLParser\Event\CategoryEvent $categoryEvent) {
    $categories = $categoryEvent->getCategory()->fetch(); // array of Category
}); // добавление функции обработки события CategoryEvent
$parser->parse($pathToImportXmlFile); // полный путь до файла import.xml (Commerce ML 2) выгрузки из 1с
```