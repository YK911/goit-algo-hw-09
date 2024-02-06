##  Задача

Маємо набір монет `[50, 25, 10, 5, 2, 1]`. Уявіть, що ви розробляєте систему для касового апарату, яка повинна визначити оптимальний спосіб видачі решти покупцеві.

Порівняйте ефективність жадібного алгоритму та алгоритму динамічного програмування, базуючись на часі їх виконання або `Big О` нотації та звертаючи увагу на їхню продуктивність при великих сумах. Висвітліть, як вони справляються з великими сумами та чому один алгоритм може бути більш ефективним за інший у певних ситуаціях.

## Висновки

Алгоритм реалізований за допомогою функції `find_coins_greedy` має складність `O(n log n)` і належить до класу жадібних алгоритмів

Основна причина такої складності - сортування списку монет, яке виконується за допомогою методу `sorted()`. Сортування списку монет у порядку спадання має складність `O(n log n)`, де n - кількість монет.

Алгоритм реалізований за допомогою функції `find_min_coins` має складність `O(total * n)` і належить до класу алгоритмів реалізованих за методом динамічного програмування.

Складність алоритму становить `O(total * n)`, оскільки:

1. Ініціалізація dp: `O(total)`.
    - Створення списку довжиною `total + 1`, заповненого значеннями `float("inf")`.
2. Перший вкладений цикл: `O(total * n)`
    - Перебір через кожну суму від 1 до total.
    - У внутрішньому циклі перебираємо кожну монету (n монет).
    - На кожній ітерації робимо порівняння та присвоєння, що займає `O(1)`.
3. Другий вкладений цикл: `O(n)`
    - Перебір через кожну монету у зворотньому порядку.
    - У цьому циклі також можуть виконуватися порівняння та присвоєння, що займає `O(1)`.

### Benchmark results

| Total sum  | Greedy algorithm, combinations | Greedy algorithm,sec | Dynamic programming, combinations | Dynamic programming, sec |
|     ---    |              :-:               |         :-:          |                :-:                |             :-:          |
| 67         |   {50: 1, 10: 1, 5: 1, 2: 1}   |       0.001441       |     {50: 1, 10: 1, 5: 1, 2: 1}    |          0.063244        |
| 470        |        {50: 9, 10: 2}          |       0.001513       |          {10: 2, 50: 9}           |          0.573818        |
| 8852       |        {50: 177, 2: 1}         |       0.001428       |          {2: 1, 50: 177}          |          10.865443       |


## Підсумки

Отже, як видно з результатів представлених в таблиці використання жадібного алгоритму є ефективнішим, при цьому точність результатів для обох алгоритмів є однаковою. Також можна зробити висновок про те, що кількість комбінацій монет можуть суттєво впливати на час роботи алгоритмів, особливо використовуючи алгоритм динамічного програмування.

Показовою є різниця при пошуку комбінацій для розміну суми в 50 монет, де час виконання програми склав `0.001394 sec` та `0.044415 sec` відповідно для жадібного алгритму і алгоритму динамічного програмування.

Відповідь на таку суттєву різницю в часі виконання можемо знайти в реалізації самих алгоритмів і оцінці їх за асимптотичною складністю, оскільки, алгоритм зі складністю `O(n log n)` є ефективнішим за `O(total * n)`.

  