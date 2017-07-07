# bootstrap-scrolltable-adaptive
Решение проблемы с появлением вертикального скролла при выпадающем меню в таблице<br>
The solution to the problem with the appearance of a vertical scroller with a drop-down menu in the table

Была необходимость в место стандартных yii2 ActionColumn поставить свой виджет с выпадающем меню<br>
There was a need for a place for the standard yii2 ActionColumn to put its widget from the drop-down menu<br>
https://github.com/ekilei/yii2-gridview-actionbuttons

На мобильном хотелось иметь горизонтальную прокрутку таблицы, и при этом чтобы не страдало меню.
Тут возникли первые трудости:
- появляется вертикальное меню при клике на выпадашку,
- скрыл вертикальный скролл, теперь выпадашка уходит за пределы видимости блока.
В итоге помогла одна хитрость полученная методом народного тыка.
padding-bottom увеличиваем на нужно число пикселей чтобы влезла выпадашка, а потом margin-bottom уменьшаем на тоже количество пикселей. В итоге контент после таблицы остается на своем месте, а выпадашка появляется как надо.

On the mobile it would be desirable to have a horizontal scrolling of the table, and thus that the menu did not suffer.
Here the first labor arose:
- there is a vertical menu when clicking on the dump,
- Hid the vertical scroll, now the fallout goes beyond the visibility of the block.
As a result, one cunning obtained by the method of people's tyke helped.
Padding-bottom increase the need for the number of pixels to climb out, and then reduce the margin-bottom to the same number of pixels. As a result, the content after the table remains in its place, and the pop-up appears as it should.

в site.css прописываем новый класс,<br>
In site.css we assign a new class

```$xslt
.table-scroll {
    width: 100%;
    max-width: 100%;
    overflow-x: auto;
    overflow-y: hidden;
    padding-bottom: 75px;
    margin-bottom: -75px;
}
```

а в шаблоне с таблицей родительскому контейнеру устанавливаем этот класс<br>
And in the template with the table, the parent container is set this class
```$xslt
        <div class="box table-scroll">
            <?= GridView::widget([
            ....
```

Пример:<br>
Sample:<br>
https://youtu.be/6I97yVUvAqc
