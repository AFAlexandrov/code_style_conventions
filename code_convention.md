# Конвенции
**1. Основная информация : Лицензия,компилятор,язык,opensource**
**2. Блоки и библиотеки// добавить подпункты и уже от них будут идти главы**
    *2.1 Объявления,инициализация*
    *2.2 Типы данных*
      *~Базовые*
      *~Производные*
      *~Пользовательские*
**3. Тесты**
**4. Правила оформления кода**
**5. Именование**
**6. Комментарии**
Оптимальная длина строки не более 50 символов (максимум 80)// почему это тут и к чему это
***
## **1.Основная информация**
This code is licensed under the GNU Lesser General Public License (LGPL) version 3 as published by the Free Software Foundation.
It is possible to link closed-source code with the LGPL code.
All code files contain licensing information.
---
## **2.Блоки и библиотеки**
==ОБЪЯВЛЕНИЕ, ИНИЦИАЛИЗАЦИЯ==
###### ++Препроцессор++

-- Все константы пишутся черед CAPS , используя нижнее подчеркивание для названия ,состоящего из нескольких слов

`#define SOME_CONST_VAL 5`

--Длинные константные выражения (переносятся на следующую строку)// больше скольки символов считается длинным константным выражением (указать)

`#define SOME_LONG_CONST_DEFINITION ( \
	(SOME_CONST_VAL + 7) / 3.1415926 \
)`// как должен выглядеть этот пример?

--Макросы, содержащие присваивание (начинаются с большой буквы, с круглыми скобками, без ";" в конце строки )

`#define Reset_some_value() some_value = 0`

--Макросы, содержащие объявление/инициализацию

		#define Make_list(list_name, ... /* items */) \
		static items_type_t list_name [] = { \
			__VA_ARGS__, list_terminator \
		}

--Макросы с параметрами\\ и что?

`#define Power_of_two(power) pow(2, (power))
 #define Ring_push_message(ring, source, len) \
  (ring)->push_message((ring), (source), (len))`

--Условная компиляция (в разработке...)
==ТИПЫ ДАННЫХ==
###### ++Базовые++

--Один идентификатор

	`char name = '\0';`

--Несколько идентификаторов пишутся через запятую на следующей строке, ( идентификатор под идентификатором)

	`char
		name_1 = '\0',
		name_2 = '\0';
	int
		num_1 = 0,
		num_2 = 0;`

###### ++Производные++ 

--Массивы
//--Один идентификатор
	`char string [STRING_SIZE] = {'\0'};`
//--Несколько идентификаторов пишутся через запятую на следующей строке, ( идентификатор под идентификатором)

	`uint8_t
		input_buffer [IN_BUF_SIZE] = {0},
		output_buffer [OUT_BUF_SIZE] = {0};`

--Указатели (пробелы с обеих сторон от "*")// по одному пробелу с каждой стороны
//--Один идентификатор
	`uint32_t * ptr = NULL;`
	`long long double *** surface_matrix = NULL;`
//--Несколько идентификаторов
	`uint16_t`
		`* window = NULL,`
		`coef_table = NULL;`

	`void (* action) (void);`// что поясняет этот пример

	`void (* arr_of_func_ptrs [SIZE]) (double parameter);`

--Функции

`void _push_byte (ring_t * ring, uint8_t byte);`// все примеры вызывают вопросы, нужно пояснение

`dbase_record_t * parser_command_dbase (void);
char * extract_pattern (
	char * message,
	uint16_t from_here,
	uint16_t cmd_len
);`

###### ++Пользовательские++ 

--структуры // что именно мы говорим про оформление структур

  `struct parser_record {
	char
		* command,
		* response
		* parameter;
	void (* action) (void);
	struct parser_record * subcommand;
}`

--объединения
--перечисления

###### ++Синонимы//??++

применение операторов// почему это здесь а не в операторах
## **3.Тесты**

---
## **4.Правила оформления кода**

---
## **5.Именование**

---
## **6.Комментарии**

---


