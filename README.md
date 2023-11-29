# practice_13
import pandas as pd
import matplotlib.pyplot as plt
from scipy.stats import linregress

# Загрузка данных
file_path = "Fashion_Retail_Sales (1).csv"
data = pd.read_csv(file_path)

# Выбор соответствующих столбцов
selected_columns = ["Review Rating", "Purchase Amount (USD)"]
df = data[selected_columns]

# Удаление пропущенных значений, если они есть
df = df.dropna()

# Извлечение переменных
x = df["Review Rating"]
y = df["Purchase Amount (USD)"]

# Выполнение линейной регрессии
slope, intercept, r, p, std_err = linregress(x, y)

# Определение функции регрессии
def myfunc(x):
    return slope * x + intercept

# Генерация значений y с использованием функции регрессии
mymodel = myfunc(x)

# Построение точечного графика и линии регрессии
plt.scatter(x, y, label="Данные")
plt.plot(x, mymodel, color='red', label=f'Линия регрессии: y = {slope:.2f}x + {intercept:.2f}')
plt.xlabel("Review Rating")
plt.ylabel("Purchase Amount (USD)")
plt.title("Линейная регрессия: Review Rating vs Purchase Amount")
plt.legend()
plt.show()

# Вывод параметров модели
print(f'Коэффициент (наклон): {slope:.2f}')
print(f'Пересечение с осью y: {intercept:.2f}')
print(f'R-квадрат: {r:.2f}')
print(f'p-значение: {p:.4f}')
print(f'Стандартная ошибка: {std_err:.2f}')
#2
import pandas as pd
import statsmodels.api as sm

# Загрузка вашего датасета
file_path = "Fashion_Retail_Sales (1).csv"
data = pd.read_csv(file_path)

# Выбор соответствующих столбцов
selected_columns = ["Review Rating", "Purchase Amount (USD)"]
df = data[selected_columns]

# Удаление пропущенных значений, если они есть
df = df.dropna()

# Выделение переменных
X = df["Review Rating"]
y = df["Purchase Amount (USD)"]

# Добавление константного члена к матрице независимых переменных
X = sm.add_constant(X)

# Построение модели регрессии
model = sm.OLS(y, X).fit()

# Создание таблицы регрессии
regression_table = model.summary()

# Вывод таблицы регрессии
print(regression_table)
#3
import pandas as pd
import statsmodels.api as sm

# Загрузка вашего датасета
file_path = "Fashion_Retail_Sales (1).csv"
data = pd.read_csv(file_path)

# Выбор соответствующих столбцов
selected_columns = ["Review Rating", "Purchase Amount (USD)"]
df = data[selected_columns]

# Удаление пропущенных значений, если они есть
df = df.dropna()

# Выделение переменных
X = df["Review Rating"]
y = df["Purchase Amount (USD)"]

# Добавление константного члена к матрице независимых переменных
X = sm.add_constant(X)

# Построение модели регрессии
model = sm.OLS(y, X).fit()

# Создание таблицы коэффициентов
coefficients_table = model.summary().tables[1]

# Вывод таблицы коэффициентов
print(coefficients_table)
#4
