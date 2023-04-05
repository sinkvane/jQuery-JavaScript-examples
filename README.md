# Сравнение синтаксиса jQuery и JavaScript

Ниже я представил сравнение библиотеки jQuery и JavaScript в маленьких участках кода.

Основным ресурсом для изучения jQuery может быть [этот ресурс](https://page2page.lohmach.info/index.php5/%D0%97%D0%B0%D0%B3%D0%BB%D0%B0%D0%B2%D0%BD%D0%B0%D1%8F_%D1%81%D1%82%D1%80%D0%B0%D0%BD%D0%B8%D1%86%D0%B0.html).

## Для начала установим jQuery через npm:

`npm jquery --save`

Не забудем сделать import в основной файл script.js:

`import $ from 'jquery'`

Появляется вопрос: что почему в импорте мы прописываем знак $?

Мы указываем знак $ т.к. в самой библиотеке jQuery знак $ ялвяется функцией. При использовании библиотеки без неё не обойтись.

## Начнём работу


Удостоверимся, что наша DOM структура уже сформирована и готова к работе. В jQuery это выглядит так:

	$(document).ready(function () {

		const btn = $('#btn');

		console.log(btn);

	});

Где в первой строчке, мы обращаемся к document, используем метод ready (чтобы проверить, что наш document готов), после чего мы будем запускать callback функцию, где будет весь наш функционал.

Вариант с чистым JavaScript будет выглядеть так: 

	window.addEventListener('DOMContentLoaded', function () {

	  const btn = document.querySelector('#btn');

	  console.log(btn);

	});
	
Заодно увидели, как можно получить элемент страницы с помощью jQuery и JS.

Пойдем дальше: сделаем смену класса при наведении на элемент с помощью jQuery:

	$(document).ready(function () {

	  $('.list-item:first').hover(function () {
		$(this).toggleClass('active');
	  });

	});
	
Вариант с чистым JavaScript будет выглядеть так: 

	window.addEventListener('DOMContentLoaded', function () {

	  const buttons = document.querySelectorAll('.list-item');

	  buttons[0].addEventListener('mouseenter', () => {
	    buttons[0].classList.toggle('active');
	  });

	  buttons[0].addEventListener('mouseout', () => {
	    buttons[0].classList.toggle('active');
	  });

	});

Сделаем следующее: выберем определенную кнопку на странице и при клике скроем нечетное изображение

	$(document).ready(function () {
	  $('.list-item:eq(2)').on('click', function () {
	    $('.image:even').fadeToggle('slow');
	  });
	});
	
Вариант с чистым JavaScript будет выглядеть так: 

window.addEventListener('DOMContentLoaded', function () {

  const buttons = document.querySelectorAll('.list-item'),
        images = document.querySelectorAll('img');

  buttons[2].addEventListener('click', () => {
    for (let i = 0; i < images.length; i++) {
      const oddImg = images[i];
      if (i % 2 == 0) oddImg.classList.toggle('display-none');
    }
  });
});

Отредактируем функцию выше на такую: всё также выбираем определенный элемент страницы, при клике будем запускать свою анимацию, которая будет тоглить высоту и прозрачность четной фотографии

	$(document).ready(function () {
	  $('.list-item:eq(4)').on('click', function () {
		$('.image:odd').animate({
		  opacity: 'toggle',
		  height: 'toggle'
		}, 1000);
	  });
	});
	
Вариант с чистым JavaScript будет выглядеть так: 
