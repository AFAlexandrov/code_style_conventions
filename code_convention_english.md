# Code conventions


**1. General information**

**2. Blocks and libraries**
      
**3. Tests**

**4. Rules of code formalization**
	
    4.1 Declaration,initialization
    
    4.2 Data types
      * Basic
      * Derivative
      * Users'

    4.3 Application of operators

**5. Naming**

**6. Comments**

## **1.General information**

This code is licensed under the GNU Lesser General Public License (LGPL) version 3 as published by the Free Software Foundation.
It is possible to link closed-source code with the LGPL code.
All code files contain licensing information.

---
## **2.Blocks and libraries**

---
## **3.Tests**

---


**4. Rules of code formalization**

Optimal length of array is up to 50 symbols (80 is maximum)

#### DECLARATION,INITIALIZATION

###### **Preprocessor**

*All constants are written using CAPS, for names , that consist of several words use underscore*

		#define SOME_CONST_VAL 5

*Long constant expressions are transfered to the next line*

!!!If #define + CONSTANT_Name + it's description >= optimal length - transfer!!!


		#define SOME_LONG_CONST_DEFINITION ( \
			(SOME_CONST_VAL + 7) / 3.1415926 \
		)
		

*Macros, that contain assignment (are begun with the capital letter, with parenthesis, without " ; " in the end of array )*

		#define Reset_some_value() some_value = 0

*Macros, that contain declaration/initialisation*

		#define Make_list(list_name, ... /* items */) \
		static items_type_t list_name [] = { \
			__VA_ARGS__, list_terminator \
		}

*Macros with parameters*

Examples that show preprocessor function wrapper

		#define Power_of_two(power) pow(2, (power))
		
		
 		#define Ring_push_message(ring, source, len) \
  			(ring)->push_message((ring), (source), (len))

*Conditional compilation (в разработке...)*
!!!!

#### DATA TYPES

###### **Basic**

*One identifier*

			char name = '\0';

*Several identifiers are written with comma and transfered to the next line, (identifier under the identifier)*

			char
				name_1 = '\0',
				name_2 = '\0';
			int
				num_1 = 0,
				num_2 = 0;`

###### **Derivative** 

*Arrays*

*One identifier*

			char string [STRING_SIZE] = {'\0'};	
*Several identifiers are written with comma and transfered to the next line, (identifier under the identifier)*

			uint8_t
				input_buffer [IN_BUF_SIZE] = {0},
				output_buffer [OUT_BUF_SIZE] = {0};`

*Pointers (spaces on the both sides from "*" ), one space for each side*

One identifier

			uint32_t * ptr = NULL;
			long long double *** surface_matrix = NULL;

Several identifiers

			uint16_t
				* window = NULL,
				coef_table = NULL;
Exaple of declaration function pointer

	void (* action) (void);
Exaple of declaration array function pointers

	void (* arr_of_func_ptrs [SIZE]) (double parameter);
	

*Functions*
 
 Пример объявления внутренней функции (начинать объявление необходимо с нижнего подчёркивания)
		
		void _push_byte (ring_t * ring, uint8_t byte);
		
 Примеры объявления функции пользовательского интерфейса
		
		dbase_record_t * parser_command_dbase (void);
	

		char * extract_pattern (
			char * message,
			uint16_t from_here,
			uint16_t cmd_len
		);
		

###### **Users'**

*Structures*

 Необходимо чтобы всё было написано через пробел , скобка ставится на той же строке , что и имя.
 
  		struct parser_record { 
			char			   
				* command,
				* response
				* parameter;
			void (* action) (void);
			struct parser_record * subcommand;
		};

*Unions*
!!!!

*Enumerations*
!!!!

###### **Synonymes**

!!!!речь про typedef

Применение операторов

*Арифметические операторы*

!!!!

*Операции сравнения*

При применении операторов сравнения необходимо ставить по одному пробелу с каждой стороны от оператора

		if (parser_command_dbase() == NULL)
			return parser_empty_cmd_dbase();
			
*Логические операторы*

!!!!

*Побитовые операторы*

!!!!

*Составное присваивание*

!!!!

*Операторы работы с указателями и членами классов
			
При использовании операторов работы с указателями и членами класса пробелы не используются

			parser_set_action(command->action ?
		command->action :
		parser_stub_action()
			);
*Тернарные операторы*	

Для тернарных операторов при использовании " : " ставятся пробелы по обе стороны и член "c" если у нас входные парметры(a,b,c) записывается на новой строке

		parser_set_action(command->action ?
		command->action :
		parser_stub_action()
			);
## **3.Tests**

!!!!

---
## **5.Naming**

!!!!

---
## **6.Comments**

!!!!

---





