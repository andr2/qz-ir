---
order: 2
title: Интерфейс оператора
---

Пользователь выбирает датасет соответствующий бренду и SKU из списка. Далее ему становятся видны все изображения из выбранной папки датасета, по которым пользователь еще не принял решение.

Нужен интерфейс в котором по конкретному SKU показывается картинки нарезанных фото товаров и оператор быстро отмечает товары, разобранные неверно.

### Основной сценарий

1. Оператор открывает специальную веб-страницу, на которой он должен обработать все фотографии.

2. В выпадающем списке выбирает SKU из выпадающего списка. Снизу видит порцию фотографий по этому SKU.

3. Пробегается глазами по всем фотографиям в порции и находит те, которые не соответствуют выбранному SKU.

4. Наводится на них мышкой и во всплывающем меню нажимает на иконку выбранного решения. Фотография становится блеклой как обработанная, поверх нее отображается иконка принятого решения.

5. Убеждается, что оставшиеся фотографии соответствуют выбранному SKU и подтверждает, что остальные определены корректно. Список фотографий обновляется и отображаются новые фотографии по которым еще не принято решение.

### Как это может выглядеть

-  **Панель фильтров**. Отображается в верхней части страницы. При изменении фильтров в этой области они автоматически применяются.

   -  **Выпадающий список SKU** имеющихся в датасете. По умолчанию выбирается первый из них. После названия SKU в скобках отображается кол-во фото обработанных / необработанных. Например: Nurofen для детей 20 шт. (20 / 1023).

   -  Ползунки от 0 до 1. По умолчанию выбран весь диапазон:

      -  **Размытие**.

      -  **Уверенность**.

   -  **Размер страницы**. Кол-во фотографий отображаемых на странице. Ползунок от 10 до 200.

-  **Тулбар**

   -  **Размер фото**. Максимальная ширина по ширине или высоте. Ползунок от 20 до 200 пикселей. При изменении ползунка фотографии в списке сразу же изменяют размер.

   -  **Пометить оставшиеся как корректные**. Пометить все товары на странице как распознанные верно. При нажатии запрашивать подтверждение “Вы уверены, что хотите пометить все оставшиеся на странице товары как распознанные корректно? Отмена будет невозможна.”. После подтверждения всем необработанным товарам проставляется решение.

-  **Область фотографий**. Список необработанных фото выбранного SKU в виде горизонтальных рядов.

   -  При изменении любого значения фильтра список фото сразу же обновляется.

   -  Фото отсортированы по пропорциям (т.е. ширину разделить на высоту). Чтобы горизонтальные фото располагались рядом с такими же горизонтальными, а вертикальные с вертикальными. Чтобы список был более однородным.

   -  При наведении мышкой на фото ниже показываются варианты решения. Варианты отображаются независимо принято ли по фото решение или нет.

   -  Фото, по которому уже принято решение (обработанные), отображаются блеклыми с opacity 0.5, цветной иконкой принятого решения и с границей цвета принятого решения.

#### Решение по фото

Фото считается обработанным, когда по нему принято решение. При обработке принимается одно из решений:

-  **Плохое** -- Для изображений, где очень много артефактов и не удается определить даже бренд. Например, за бликами и ценником самого товара не видно. Цвет: `warning`, иконка: `exclamation-diamond`, код решения `invalid_photo`.

-  **Неизвестное SKU**-- Пометить как изображение, где SKU не удается определить -- для изображений, где правильно определен бренд, но нет достаточной информации для определения SKU. Цвет: `secondary`, иконка: `question-circle`, код решения `unknown_sku`.

-  **Ошибка** -- Пометить как изображение, определенное с ошибкой -- неправильно определен бренд или SKU. Цвет: `danger`, иконка: `hand-thumbs-down-fill`, код решения `error`.

-  **Корректное** -- Пометить как правильно распознанное. Цвет: `success`, иконка: `hand-thumbs-up-fill`, код решения `ok`.

При наведении на решение должен отображаться тултип, поясняющий иконку решения.

### Дополнительная информация

Палитру для цветов можно взять отсюда: <https://getbootstrap.com/docs/5.3/customize/color/>

Иконки отсюда: <https://icons.getbootstrap.com/>