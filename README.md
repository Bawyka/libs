## Feature
Класс [DBFeature](https://github.com/Bawyka/DBFeature) это библиотека `php` для работы с *Базой Данных* с использованием **PDO**.

Для того чтобы обращаться к методам вы должны сначала обратиться к Таблице, к которой эти Методы нужно применить

Например, если у вас есть Таблица `users`, то обращаться к ней нужно так ( *учитывая регистр имени таблицы!* ):

```php
// Подключим саму библиотеку
include('dbfeature.php');
// Создаем новый экземпляр класса Feature
$dbf = new DBFeature();
// users - это имя Вашей таблицы !!!
$dbf->users()->GetData();
```

### методы:

```php
// Получет все данные из Таблицы в виде ассоциативного массива
->GetData();
```

```php
// Удаляет Запись из Таблицы где Поле [$idn] равно Значению [$val]
->DelOne($idn,$val);
```

```php
// Проверка существует ли Запись с Полем [$clm], содержащим Значение [$rc] в Таблице
->ExistsRow($clm,$rc);
```

```php
// Обновить Поле [$clm] Значением [$upd] где Поле [$idn] равно Значению [$val]
->UpdOne($clm,$upd,$idn,$val); 
```

```php
// Получает данные Поля [$clm] из Таблицы где Поле [$idn] равно Значению [$val]
->GetOne($clm,$idn,$val);
```

```php
// Подсчет кол-ва записей Поля [$clm] в Таблице, где Поле [$idn] равно Значению [$val]
->CountRows($clm,$idn,$val);
```

```php
// Фетч всех Полей Записи где Поле [$idn] равно Значению [$val] в Ассоциативный массив из Таблицы
->GetRec($idn,$val);
```

```php
// Фетч всех Полей [$clm] Таблицы, где Поле [$idn] равно Значению [$val] в Ассоциатвиный массив
->GetEvery($clm,$idn,$val);
```

```php
// Вставка данных в Таблицу, Ключ массива это Поле, а значение массива это Данные, которые вставляются в это поле
->PutData($params = array());
```

```php
// Проверка, не пуста ли таблица
->isEmpty();
```

```php
// Установка текущей таблицы
->SetTable($t);
```

```php
// method Query - выолняет любой запрос
->Query("SELECT * FROM `users`");
```

#### Объект

Если в таблице `users` есть пользователь с `id=1`

```php
// Загрузим Объект
$user_object = $dbf->users(1)->Load();
// Выведем Его Email
echo $user_object->email;
```
