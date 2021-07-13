# Отчёт о тестировании Credit Card Number Validator

## Краткое описание

**11.07.2021 - 13.07.2021** было проведено функциональное тестирование программы "Проверки функциональности валидации номера банковской карт".

На тестирование затрачено: **5 часов**

**В результате тестирования выявлены следующие дефекты:**       
[Credit-Card-Number-Validator](https://github.com/alexboom85/Credit-Card-Number-Validator/issues/1)       
[Credit-Card-Number-Validator #2](https://github.com/alexboom85/Credit-Card-Number-Validator/issues/2)

## Описание процесса тестирования

**В программном коде:**


    public class Main {
      public static void main(String[] args) {
    // TODO: подставлять номер карты нужно сюда между двойными кавычками, без пробелов
    String number = "5351719427810741";
    System.out.println(String.format("Result is %s", isValidCardNumber(number) ? "OK" : "FAIL"));
       }

     public static boolean isValidCardNumber(String number) {
    if (number == null) {
      return false;
    }

    if (number.length() != 16) {
      return false;
    }

    long result = 0;
    for (int i = 0; i < number.length(); i++) {
      int digit;
      try {
        digit = Integer.parseInt(number.charAt(i) + "");
      } catch (NumberFormatException e) {
        return false;
      }

      if (i % 2 == 0) {
        digit *= 2;
        if (digit > 9) {
          digit -= 9;
        }
      }
      result += digit;
    }

    return (result != 0) && (result % 10 == 0);
  }
}


Запускать программу с разными тестовыми данными ( в месте проверки номера, строка 20, банковской карты подставляем различные данные).



[Пример кода](https://github.com/netology-code/javaqa-homeworks/tree/master/intro)


**Тестирование производилось в следующем окружении:**

1. Ноутбук HP Pavilion,Windows 10, x64 
1. Openjdk version "11.0.11" 2021-04-20
