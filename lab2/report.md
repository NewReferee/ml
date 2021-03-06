## ФИО, Группа
Иванов Данила Сергеевич, М8О-307Б-17
## Алгоритмы
1. Логистическая регрессия. Реализована в самом стандартном варианте без каких-либо регуляризаций. Можно выбрать шаг градиентного спуска и максимальное количество итераций.
2. КНН. В качестве расстояния взята Евклидова норма. Можно задать количество соседей.
3. Дерево. Взят коэффициент Джини при разбиении. Реализован механизм ограничения глубины дерева.
4. Лес. Деревья строятся по бутстрапированный выборке. Количество признаков на каждом дереве можно ограничить (сабсет оригинальных на уровне дерева).
##  Результаты
Оценка качества модели проводилось посредством кросс-валидации, а метркикой выступала f1-мера, так как в даных был дизбаланс.

1. Ожидаемо, линейная регрессия без каких-либо регуляризаций показывет худший результат. Время исполнения намного больше в сравнении с реализацией из Sklearn из-за однопоточности и отсутствия каких-либо оптимизаций.
2. Реализованный метод ближайших соседей дает такой же результат как и алгоритм из Sklearn, а время исполнения даже чуть меньше.
3. Решающее дерево так же дает аналогичный результат готовому алгоритму, однако время работы на порядки больше.
4. Качество работы случайного леса намного меньше готовой реализации, а со временем работы так и вовсе происходит сущий кошмар, что связано в первую очередь с отсутстивем параллельного исполнения, так как в коробочных реализациях как раз-таки имеется эта ключевая особенность в силу того что деревья можно строить независимо друг от друга.