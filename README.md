# First_proj
Модуль предназначен для получения из PDF-A файлов основных параметров документов и цельных абзацев до 4-го уровня вложенности, с сохранением, а при необходимости дополнением их нумерации.
Выявление отдельных абзацев основывается на пунктуации и некоторых ключевых словах.
В данной реализации выявлялись:
1.	Параметры: название, подписной номер, дата вступления в силу, -актуальность, издатель, тип НПА.
2.	Абзацы: полномочия, обязанности, функции, задачи.

Модуль делится на следующие блоки:
1.	Импорт.
2.	Переменные.
3.	Функции выделения отдельных абзацев. Громоздкое ветвление связано с большой вариативностью чередования типов абзацев на всех уровнях вложенности. Под типом абзаца подразумеваются комбинации начальных и конечных символов абзацев. Например: "1) в части касающейся ..... :". При наличии единого подхода к нумерации на уровнях вложенности, ветвление можно значительно сократить.
4.	Основная функция, обрабатывающая документ:

4.1) Считывание текста из документа. Была выбрана библиотека PyMuPDF (fitz), т.к. она показала наилучшие скорость и качество распознавания текста.

4.2) Обработка текста и частных случаев. Убираются мусорные символы и выражения. Также, при необходимости, отработка частных случаев для корректировки работы алгоритма.

4.3) Разделение на блоки. Документ делится на: "Первый лист", "Титульная информация", "Общие положения", "Полномочия", "Обязанности", "Задачи", "Функции", "Руководство". Такое разделение позволяет адресно применять функции и получать нужную информацию.

4.4) Выявление основных параметров документа. Выявляемые параметры указаны выше.

4.5) Выделение абзацев и вывод результатов. Предусмотрено два варианта использования результатов: - вызов основной функции другим модулем и сохранение в базу данных (результаты работы сохраняются в файлах.log - вывод в консоль для проверки работы алгоритма обособленно от основного приложения.

Разделение текста на абзацы основывается на пунктуации, ошибки в ней приведут к ошибкам в результатах.
Самый проблемный случай - ";" в тексте, и в конце абзаца. Вариант решения: в блоке обработки текста и частных случаев заменять проблемный символ. Лучшего решения пока не реализовано.


Модуль написан при отсутствии практического опыта разработки и базовой теоретической подготовке в области функционального программирования.
