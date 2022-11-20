# ------------------------------------LISTS---------------------------------- #
eng_upper_alphabet = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'
eng_lower_alphabet = 'abcdefghijklmnopqrstuvwxyz'
rus_upper_alphabet = "АБВГДЕЁЖЗИЙКЛМНОПРСТУФХЦЧШЩЪЫЬЭЮЯ"
rus_lower_alphabet = "абвгдеёжзийклмнопрстуфхцчшщъыьэюя"
# -------------------------------------DEFS---------------------------------- #


def russian_letter(message, step):
    result = ''
    for i in message:
        if i.isupper():
            mesto = rus_upper_alphabet.find(i)
            new_mesto = mesto + step
            if new_mesto > len(rus_upper_alphabet) - 1:
                new_mesto = step - (33 - rus_upper_alphabet.index(i))
                result += rus_upper_alphabet[new_mesto]
            elif new_mesto < 0:
                new_mesto = mesto + step
                result += rus_upper_alphabet[new_mesto]
            else:
                result += rus_upper_alphabet[new_mesto]
        elif i.islower():
            mesto = rus_lower_alphabet.find(i)
            new_mesto = mesto + step
            if new_mesto > len(rus_lower_alphabet) - 1:
                new_mesto = step - (33 - rus_lower_alphabet.index(i))
                result += rus_lower_alphabet[new_mesto]
            elif new_mesto < 0:
                new_mesto = mesto + step
                result += rus_lower_alphabet[new_mesto]
            else:
                result += rus_lower_alphabet[new_mesto]
        else:
            result += i
    return result


def english_letter(message, step):
    result = ''
    for i in message:
        if i.isupper():
            mesto = eng_upper_alphabet.find(i)
            new_mesto = mesto + step
            if new_mesto > len(eng_upper_alphabet) - 1:
                new_mesto = step - (26 - eng_upper_alphabet.index(i))
                result += eng_upper_alphabet[new_mesto]
            elif new_mesto < 0:
                new_mesto = mesto + step
                result += eng_upper_alphabet[new_mesto]
            else:
                result += eng_upper_alphabet[new_mesto]
        elif i.islower():
            mesto = eng_lower_alphabet.find(i)
            new_mesto = mesto + step
            if new_mesto > len(eng_lower_alphabet) - 1:
                new_mesto = step - (26 - eng_lower_alphabet.index(i))
                result += eng_lower_alphabet[new_mesto]
            elif new_mesto < 0:
                new_mesto = mesto + step
                result += eng_lower_alphabet[new_mesto]
            else:
                result += eng_lower_alphabet[new_mesto]
        else:
            result += i
    return result
# ----------------------------------------CORE-------------------------------- #


print('🔒 Добро пожаловать в шифратор , он пользутеся шифром цезаря')
print('🗺 Введите язык "ru" или "eng"')
while True:
    language = input().lower()
    if language == 'ru' or language == 'eng':
        print('✅ Accept')
        break
    else:
        print('❌Decline', 'Введите еще раз', sep='\n')
print('Введите шаг сдвига')
while True:
    step = input()
    if step.isdigit():
        step = int(step)
        print('✅ Accept')
        break
    else:
        print('❌Decline', 'Введите еще раз', sep='\n')
print('Для шифвроки введите "+" для дешифровки введите "-"')
while True:
    sign = input()
    if sign == "+" or sign == "-":
        print('✅Accept')
        break
    else:
        print('❌Decline', 'Введите еще раз', sep='\n')
print('Введите текст')
message = input()
# ----------------------------------------FINISH----------------------------------- #
if sign == "-":
    step = step * -1
if language == 'ru':
    print(russian_letter(message, step))
else:
    print(english_letter(message, step))
