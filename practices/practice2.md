# Задание 1
## Вывести служебную информацию о пакете matplotlib (Python). Разобрать основные элементы содержимого файла со служебной информацией из пакета. Как получить пакет без менеджера пакетов, прямо из репозитория?
```
pip install matplotlib
pip show matplotlib
```

![image](https://github.com/user-attachments/assets/311f38fe-3a01-469b-82c4-1dc5e91e5273)
![image](https://github.com/user-attachments/assets/365ae43c-0bc0-4481-8482-6d71da3efe96)


# Задание 2
```
git clone https://github.com/expressjs/express.git
cd express
cat package.json
```

![image](https://github.com/user-attachments/assets/1fbb15f4-9127-4b2c-83c4-4f0c8de8b5d8)

# Задание 3
```
pip install pipdeptree
pipdeptree --packages matplotlib
```
![image](https://github.com/user-attachments/assets/9eeb2275-cfaa-4af4-9c57-02d5ed40300a)

```
cat package.json
```
![image](https://github.com/user-attachments/assets/90798742-abcd-49c8-ab56-035d3e9e22f8)

```
digraph G {
    node [shape=box];

    express -> "accepts";
    express -> "body-parser";
    express -> "content-disposition";
    express -> "content-type";
    express -> "cookie";
    express -> "cookie-signature";
    express -> "debug";
    express -> "depd";
    express -> "encodeurl";
    express -> "etag";
    express -> "finalhandler";
    express -> "fresh";
    express -> "http-errors";
    express -> "merge-descriptors";
    express -> "methods";
    express -> "mime-types";
    express -> "on-finished";
    express -> "once";
    express -> "parseurl";
    express -> "qs";
    express -> "range-parser";
    express -> "router";
    express -> "safe-buffer";
    express -> "send";
    express -> "serve-static";
    express -> "setprototypeof";
    express -> "statuses";
    express -> "type-is";
    express -> "utils-merge";
    express -> "vary";
}
```
## для express
![tets](https://github.com/user-attachments/assets/47e26236-27b0-4383-a1d6-c9d15878d235)

## для matplotlib
```
digraph G {
    node [shape=box];


    matplotlib -> "contourpy" -> "numpy";
    matplotlib -> "cycler";
    matplotlib -> "fonttools";
    matplotlib -> "kiwisolver";
    matplotlib -> "numpy";
    matplotlib -> "packaging";
    matplotlib -> "pillow";
    matplotlib -> "pyparsing";
    matplotlib -> "python-dateutil" -> six;
}
```

![tets](https://github.com/user-attachments/assets/78e34546-90d3-4809-92e4-431cc80534a1)


# Задание 4

```
include "globals.mzn";  % Импорт библиотеки с all_different

% Массив для представления 6-значного билета
array[1..6] of var 0..9: ticket;

% Все цифры должны быть различны
constraint all_different(ticket);

% Сумма первых трёх цифр должна быть равна сумме последних трёх цифр
constraint ticket[1] + ticket[2] + ticket[3] = ticket[4] + ticket[5] + ticket[6];

% Минимизируем сумму трёх цифр (чтобы найти минимальный билет)
var int: sum_3_digits = ticket[1] + ticket[2] + ticket[3];

% Найти минимальную сумму
solve minimize sum_3_digits;
```
![image](https://github.com/user-attachments/assets/91ab5564-1a05-4526-afc3-b296bbf6edcb)

# Задание 5

```
enum VersionsMenu = { menu_v1_0_0, menu_v1_1_0, menu_v1_2_0, menu_v1_3_0, menu_v1_4_0, menu_v1_5_0 };
enum VersionsDropdown = { dropdown_v1_8_0, dropdown_v2_0_0, dropdown_v2_1_0, dropdown_v2_2_0, dropdown_v2_3_0 };
enum VersionsIcons = { icons_v1_0_0, icons_v2_0_0 };

var VersionsMenu: menu_version;
var VersionsDropdown: dropdown_version;
var VersionsIcons: icons_version;

constraint
    if menu_version = menu_v1_5_0 then dropdown_version in {dropdown_v2_3_0, dropdown_v2_2_0} /\ icons_version = icons_v2_0_0

    elseif menu_version = menu_v1_4_0 then dropdown_version in {dropdown_v2_2_0, dropdown_v2_1_0} /\ icons_version = icons_v2_0_0
    elseif menu_version = menu_v1_3_0 then dropdown_version in {dropdown_v2_1_0, dropdown_v2_0_0} /\ icons_version = icons_v1_0_0
    elseif menu_version = menu_v1_2_0 then dropdown_version in {dropdown_v2_0_0, dropdown_v1_8_0} /\ icons_version = icons_v1_0_0
    elseif menu_version = menu_v1_1_0 then dropdown_version = dropdown_v1_8_0 /\ icons_version = icons_v1_0_0
    else dropdown_version = dropdown_v1_8_0 /\ icons_version = icons_v1_0_0
    endif;

solve minimize menu_version;
```
![image](https://github.com/user-attachments/assets/b58b7a76-dd2e-445d-8242-f107ddb5a7db)

# Задание 6
```
int: root = 100;
var 100..300: foo;
var 100..300: target;
var 100..300: left;
var 100..300: right;
var 100..300: shared;


constraint if root = 100 then foo >= 100 /\ foo < 200 /\ target >= 200 /\ target < 300 endif;
constraint if foo = 110 then left >= 100 /\ left < 200 /\ right >= 100 /\ right < 200 endif;
constraint if left = 100 then shared >= 100 endif;
constraint if right = 100 then shared < 200 endif;
constraint if shared = 100 then target >= 100 /\ target < 200 endif; 
```

![image](https://github.com/user-attachments/assets/69ae1736-96f4-45c2-ae93-7094d44f0068)



# Задание 7

```
# Структура данных для хранения пакетов и их зависимостей
packages = {
    'root': {
        '1.0.0': {
            'dependencies': {
                'foo': '^1.0.0',
                'target': '^2.0.0'
            }
        }
    },
    'foo': {
        '1.1.0': {
            'dependencies': {
                'left': '^1.0.0',
                'right': '^1.0.0'
            }
        },
        '1.0.0': {
            'dependencies': {}
        }
    },
    'left': {
        '1.0.0': {
            'dependencies': {
                'shared': '>=1.0.0'
            }
        }
    },
    'right': {
        '1.0.0': {
            'dependencies': {
                'shared': '<2.0.0'
            }
        }
    },
    'shared': {
        '2.0.0': {
            'dependencies': {}
        },
        '1.0.0': {
            'dependencies': {
                'target': '^1.0.0'
            }
        }
    },
    'target': {
        '2.0.0': {
            'dependencies': {}
        },
        '1.0.0': {
            'dependencies': {}
        }
    }
}


# Функция проверки совместимости версии пакетов
def check_dependencies(package, version, resolved, packages):
    # Если пакет уже добавлен в решение, пропускаем
    if package in resolved:
        return True

    # Получаем зависимости для указанной версии
    dependencies = packages[package][version]['dependencies']

    for dep_pkg, dep_version in dependencies.items():
        # Проверка совместимости версии зависимостей
        if not resolve_version(dep_pkg, dep_version, packages, resolved):
            return False

    # Добавляем текущий пакет в решенные
    resolved[package] = version
    return True


# Функция выбора совместимой версии
def resolve_version(package, version_range, packages, resolved):
    # Для простоты обрабатываем только некоторые форматы версий
    if version_range.startswith('^'):
        min_version = version_range[1:]  # Минимальная версия для диапазона "^"
        for version in packages[package]:
            if version >= min_version and package not in resolved:
                if check_dependencies(package, version, resolved, packages):
                    return True
    return False


# Основная функция для решения задачи
def solve(packages):
    resolved = {}
    root_version = '1.0.0'  # Задаем корневую версию
    if check_dependencies('root', root_version, resolved, packages):
        print("Решение найдено:", resolved)
    else:
        print("Решение не найдено")


solve(packages)
```

![image](https://github.com/user-attachments/assets/98f174f9-21b2-4b15-a655-01466d61d827)
