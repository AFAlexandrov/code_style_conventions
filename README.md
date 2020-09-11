# Конвенции кодирования


**1. Основная информация**

**2. Блоки и библиотеки**
      
**3. Тесты**

**4. Правила оформления кода**
	
    4.1 Объявления,инициализация
    
    4.2 Типы данных
      * Базовые
      * Производные
      * Пользовательские

    4.3 Применение операторов

--------


## **1.Основная информация**

This code is licensed under the GNU Lesser General Public License (LGPL) version 3 as published by the Free Software Foundation.
It is possible to link closed-source code with the LGPL code.
All code files contain licensing information.

---
## **2.Блоки и библиотеки**

Под библиотекой понимаем связку двух и более файлов с расширениями .c и .h
Подключённых линейно, то есть:

header_1.h ---> sourse_1.c
header_2.h --/

либо

header_1.h ---> header_2.h ---> source_1.c

Под блоком понимаем две пары файлов file.c и file.h  c явно разделёнными открытым и закрытым интерфейсами
При этом объявления строго в заголовках (иногда кроме inline)
А реализации строго в file.c

TODO
1. варианты связи блоков

1.1. через открытые интерфейсы

1.2. через закрытые

1.3. кольцом

---
## **3.Тесты**

Процесс разработки построен по методологии TDD.
Для тестирования используется unity фрэймворк от ThrowTheSwitch.
Тесты хранятся отдельно от кода.
Для генерации структуры проекта на основе идеологии блоков используется скрипт *ссылку сюда*

---


## **4. Правила оформления кода**

Оптимальная длина строки 80 - 90 символов

#### ОБЪЯВЛЕНИЕ, ИНИЦИАЛИЗАЦИЯ

###### **Препроцессор**

*Все константы пишутся черед CAPS , используя нижнее подчеркивание для названия ,состоящего из нескольких слов*

		#define SOME_CONST_VAL 5

*Длинные константные выражения (переносятся на следующую строку)*

*Если #define + ИМЯ_КОНСТАНТЫ + её описание >= оптимальной длины - переносим*


		#define SOME_LONG_CONST_DEFINITION ( \
			(SOME_CONST_VAL + 7) / 3.1415926 \
		)
		
*Макросы, оборачивающие действие начинаются с большой буквы, слова разделяются нижними подчёркиваниями. ";" в конце строки не ставится*

*Если нет параметров, в конце ставятся круглые скобки, чтобы подчеркнуть что это действие.*

		#define Reset_some_value() some_value = 0

*Макросы, содержащие объявление/инициализацию*

		#define Make_list(list_name, ... /* items */) \
			static items_type_t list_name [] = { \
				__VA_ARGS__, list_terminator \
			}

*Макросы с параметрами*

		#define Ring_push_message(ring, source, len) \
			(ring)->push_message((ring), (source), (len))
			
		#define Power_of_two(power) pow(2, (power))

*Условная компиляция (в разработке...)*

*Уровни вложенности оформляются следующим образом*
		
		#define A
		#define E
		#ifdef A
		#	define B
		#else
		#	define C
		#	if defined E
		# 		define X
		#	endif
		#endif

#### ТИПЫ ДАННЫХ

###### **Базовые**

*Один идентификатор*

			char name = '\0';

*Несколько идентификаторов пишутся через запятую на следующей строке, ( идентификатор под идентификатором)*

			char
				name_1 = '\0',
				name_2 = '\0';
			int
				num_1 = 0,
				num_2 = 0;`

###### **Производные** 

*Массивы*

Один идентификатор

			char string [STRING_SIZE] = {'\0'};	
			
Несколько идентификаторов пишутся через запятую на следующей строке, ( идентификатор под идентификатором)

			uint8_t
				input_buffer [IN_BUF_SIZE] = {0},
				output_buffer [OUT_BUF_SIZE] = {0};`

*Указатели (пробелы с обеих сторон от "*"), по одному пробелу с каждой стороны*

Один идентификатор

			uint32_t * ptr = NULL;
			long long double *** surface_matrix = NULL;

Несколько идентификаторов

			uint16_t
				* window = NULL,
				coef_table = NULL;
Пример объявления указателя на функцию

	void (* action) (void);
Пример объявления массива указателей на функции

	void (* arr_of_func_ptrs [SIZE]) (double parameter);
	



*Функции*
 
 Пример объявления внутренней функции (начинать объявление необходимо с нижнего подчёркивания)
		
		void _push_byte (ring_t * ring, uint8_t byte);
		
 Примеры объявления функции пользовательского интерфейса
		
		dbase_record_t * parser_command_dbase (void);
	

		char * extract_pattern (
			char * message,
			uint16_t from_here,
			uint16_t cmd_len
		);
		

###### **Пользовательские**

*Cтруктуры*

 Необходимо чтобы всё было написано через пробел , скобка ставится на той же строке , что и имя
 
  		struct parser_record { 
			char			   
				* command,
				* response
				* parameter;
			void (* action) (void);
			struct parser_record * subcommand;
		};

*объединения*
!!!!

*перечисления*
!!!!

###### **Синонимы**

Любой синоним типа оканчивается суффиксом _t

		typedef void (* action_t) (void);

		typedef struct struct_name {
			char
				status : 3,
				buf [BUF_SIZE];
			struct struct_name * next; 
		} struct_name_t;

Применение операторов

*Арифметические операторы*

!!!!

*Логические операторы*

Унарные ставятся вплотную к операнду

		if (!entity) return NULL;

Вокруг бинарных ставятся пробелы 


		if (parser_command_dbase() == NULL)
			return parser_empty_cmd_dbase();

Для тернарных операторов при использовании " : " ставятся пробелы по обе стороны и член "c" если у нас входные парметры(a,b,c) записывается на новой строке

		parser_set_action(command->action ?
			command->action :
			parser_stub_action()
		);

Таблица сравнений на тернарном операторе

		result =
			(a == b) ? 1 :
			(a == c) ? 2 :
			(a == d) ? 3 :
		0;

*Побитовые операторы*

Те же принципы для унарных и бинарных операторов

		uint8_t zeros_in_mask &= ~msk;

*Операторы работы с указателями и членами классов*
			
При использовании операторов работы с указателями и членами класса пробелы не используются

		parser_set_action(command->action ?
			command->action :
			parser_stub_action()
		);
		
		ring.push_byte(ring, byte);



