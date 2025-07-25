# Определение
**Big O** - это верхняя граница сложности алгоритма, в зависимости от входных данных.

**Оценка по времени** - сколько времени займет исполнение алгоритма.

**Оценка по памяти** - сколько памяти уйдет на исполнение алгоритма.
# Как считать сложность
```python
def(users: List[users]):
	# n^2
	for user1 in users:
		for user2 in users	
			user.name = "test"
	# n
	for user in users:
		user.status = "ok"
	# const = 1
	commit()
```
Всего операций для users 
```
n^2 + n + 1, где n - длина массива users.
```
## Пример 1
```python
for i = 0; i < 100*n; i++:
	op()
	op()
# n = 10 -> 2000 операций 
# O(n) = 100*n*2 = 200n - линейная
```
## Пример 2
```python
for i = 0; i < n; i++:
	for j = 0; j < m; j++:
		op()
# O(n*m) - линейная
```
## Пример 3
```python
for i = 0; i < n; i++:
	for j = i; j < n; j++:
		op()                     
#                                арифмет.прогр.
# 1 + 2 + 3 + 4 + 5 + ... + n = (n * (n+1))/2 = n^2
# O(n^2) - квадратичная
```
# Общая сложность
Если сложность алгоритма 
```
300n^2 + 600n + 1000
```
то общая сложность будет n^2. Меньшие степени и константы **отбрасываются**.
# Амортизационный анализ
## Определение
Средняя производительность операций **в худшем случае** на протяжении длинной последовательности операций.
## Пример
```
 i   | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |  9 | 10 |    ...    | 17 | ...
-----|---|---|---|---|---|---|---|---|----|----|-----------|----|----
size | 1 | 2 | 4 | 4 | 8 | 8 | 8 | 8 | 16 | 16 |    ...    | 32 | ...
-----|---|---|---|---|---|-----------|----|----|-----------|----|----
cost | 1 | 2 | 3 | 1 | 5 |     1     |  9 |    |     1     | 17 | ...
|      ^           ^           ^                     ^
|      |           |           |                     |
|------|-----------|-----------|---------------------|
```
Амортизационная сложность вставки в динамический массив (слайс в Go) - **О(1)**. 
При переполнении cap - выделяется новый массив w/ cap в 2 раза больше. 
Окна, когда вставка осуществляется за О(1) становятся все шире с увеличением cap.

Рассчитаем сложность одной операции:
```     
        кол-во вставок   кол-во копий
              n             log2n                геом.прогрессия          
       (1+1+1+...+1)  + (1+2+4+8+16+...)    n + (1 * (2^log2n - 1))/(2-1)     
O(N) = --------------------------------- = ---------------------------
					n                                 n
```
```
             1*(2^log2n - 1)
         n + -------------
				    1         n + 2^log2n - 1         n + n - 1        
O(N) = ------------------- = ----------------- = ------------------- = 2 = const
                n                   n                     n

```

# Как решать задачи
1. Спросить можно ли модифицировать данные: если да, то не нужно аллоцировать.
2. Обратить внимание на условие задачи: отсортирован массив или нет.
3. ...
# Шпаргалка O(n)
![[Pasted image 20250619144413.png]]