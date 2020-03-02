# Conventions
**1. General: License,compiler,language,opensource**

**2. Blocks and libraries
 *2.1 Declaration,initialisation*
 *2.2 Data types*
    *~Basic*
    *~Derivative*
    *~Users'*

**3. Tests**
**4. The rules of code formalization **
**5. Naming**
**6. Comments**

***
## **1.General**
This code is licensed under the GNU Lesser General Public License (LGPL) version 3 as published by the Free Software Foundation.
It is possible to link closed-source code with the LGPL code.
All code files contain licensing information.
---
## **2.Blocks and libraries**
==DECLARATION, INITIALISATION==
###### ++Prepocessor++

-- All the constants are written with CAPS , we use underscore with names, consisting of several words

`#define SOME_CONST_VAL 5`

--Long constant expressions are wrapped to the next line 

`#define SOME_LONG_CONST_DEFINITION ( \
	(SOME_CONST_VAL + 7) / 3.1415926 \
)`

--Macros that have assignment are written with a capital letter, using parenthesis , without ";" in the end of the line )

`#define Reset_some_value() some_value = 0`

--Macros, that have declaration/initialisation

		#define Make_list(list_name, ... /* items */) \
		static items_type_t list_name [] = { \
			__VA_ARGS__, list_terminator \
		}

--Macros with parametrs\\ и что?

`#define Power_of_two(power) pow(2, (power))
 #define Ring_push_message(ring, source, len) \
  (ring)->push_message((ring), (source), (len))`

--Conditional compilation 
==DATA TYPES==
###### ++Basic++

--One identifier

	`char name = '\0';`

--Several identifiers are written with comma on the following line, ( identifier under the indentifier

	`char
		name_1 = '\0',
		name_2 = '\0';
	int
		num_1 = 0,
		num_2 = 0;`

###### ++Derivative++ 

--Arrays
--One identifier
	`char string [STRING_SIZE] = {'\0'};`
--Several identifiers are written with comma on the following line, ( identifier under the indentifier

	`uint8_t
		input_buffer [IN_BUF_SIZE] = {0},
		output_buffer [OUT_BUF_SIZE] = {0};`

--Pointers (spaces at the both sides of "*")// using one space for the each side
//--One identifier
	`uint32_t * ptr = NULL;`
	`long long double *** surface_matrix = NULL;`
//--Several identifiers
	`uint16_t`
		`* window = NULL,`
		`coef_table = NULL;`

	`void (* action) (void);`

	`void (* arr_of_func_ptrs [SIZE]) (double parameter);`

--Functions

`void _push_byte (ring_t * ring, uint8_t byte);`

`dbase_record_t * parser_command_dbase (void);
char * extract_pattern (
	char * message,
	uint16_t from_here,
	uint16_t cmd_len
);`

###### ++Users'++ 

--Structures

  `struct parser_record {
	char
		* command,
		* response
		* parameter;
	void (* action) (void);
	struct parser_record * subcommand;
}`

--Unions
--Enums

###### ++Synonyms//??++


## **3.Tests**

---
## **4.The rules of code formalization **

---
## **5.Naming**

---
## **6.Comments**

---


