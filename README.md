# Сравнение синтаксиса jQuery и JavaScript

Ниже я представил сравнение библиотеки jQuery и JavaScript в маленьких участках кода.

## Для начала установим jQuery через npm:

	npm jquery --save

Не забудем сделать import в основной файл script.js:

	import $ from 'jquery';

Появляется вопрос: что почему в импорте мы прописываем знак $?

Мы указываем знак $ т.к. в самой библиотеке jQuery знак $ ялвяется функцией. При использовании библиотеки без неё не обойтись. Импортируем её. 

Основным ресурсом для изучения jQuery может быть page2page.lohmach.info/index.php5

Удостоверимся, что наша DOM структура уже сформирована и готова к работе. В jQuery это выглядит так:

$(document).ready(function () {
 
  const btn = $('#btn');

  console.log(btn);

});

Где в первой строчке, мы обращаемся к document, используем метод ready (чтобы проверить, что наш document готов), после чего мы будем запускать callback функцию, где будет весь наш функционал.

Вариант с чистым JavaScript: 


$(document).ready(function () {

  const btn = $('#btn');

  console.log(btn);

});



`$(document).ready(function () {

  $('.list-item:first').hover(function () {
    $(this).toggleClass('active');
  });

});`



$(document).ready(function () {
  $('.list-item:eq(2)').on('click', function () {
    $('.image:even').fadeToggle('slow');
  });
});



$(document).ready(function () {
  $('.list-item:eq(4)').on('click', function () {
    $('.image:odd').animate({
      opacity: 'toggle',
      height: 'toggle'
    }, 1000);
  });
});
