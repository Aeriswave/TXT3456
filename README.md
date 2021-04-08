# STRAB   
Формат последовательности текстовых символов разной длины. Название форматов состоит из трех частей:
- STR (сокращенно от string)
- A = число бит в 1 последовательности символов (включая биты для обозначения режима отображения последовательности текстовых символа)
- B = число текстовых символов в одной последовательности    

# Назначение   
Универсальный формат текстовых данных, предназначенный для удобной работы с простыми текстовыми данными.   

# Причина создания   
Отсутствуют (не нашел) универсальные решения, позволяющие корректно и просто хранить, передавать, обрабатывать и отображать текстовую информацию.   

# Форматы последовательности текстовых символов
## (31) Формат последовательности текстовых символов STR31   
Размер символа 8 бит (2^3), включает в себя только значение самого текстового символа.   
Одное из значений = обозначению "пустого", "несуществующего", "незаданного" или "неотображаемого" текстового символа.   
Используемая кодировка символов **UTF8** или другая, подходящая по размеру.   

## (41) Формат последовательности текстовых символов STR41   
Размер символа 16 бит (2^4), включает в себя:   
### (41-0)
0...7 бит- обозначение режима отображения текстового символа:   
-- 0й бит для обозначения регистра:       нижний регистр (=0) или верхний регистр (=1)   
-- 1й бит для обозначения выделения:      без выделения (=0) или жирный (=1)   
-- 2й бит для обозначения стиля:          без курсива (=0) или курсив (=1)   
-- 3й бит для обозначения подчеркивания:  без подчеркивания (=0) или с подчеркиванием (=1)   
-- 4й бит для обозначения зачеркивания:   без зачеркивания (=0) или с зачеркиванием (=1)   
-- 5й бит для обозначения шрифта:         обычный (=0) или заглавный (=1)   
-- 6й и 7й биты для обозначения:          цвета символа или расширенного кода используемого шрифта
> обычный (=00) или GYR (зеленый=01, желтый=10, красный=11)   
> 

### (41-8)
8...15 бит - значение самого текстового символа, размером 8 бит   

## (51) Формат последовательности текстовых символов STR51   
Размер символа 32 бит (2^5), включает в себя:   
### (51-0)
0...7 бит   - обозначение режима отображения текстового символа (аналогично формату **STR41**).   
### (51-8)
8...31 бит  - значение самого текстового символа, размером 24 бит.   

## (53) Формат последовательности текстовых символов STR53   
Состоит из 3х (трех) последовательных текстовых символов.   
Если символов меньше 3х, то вместо недостающих значений устанавливаются значение "несуществующего" или "пустого" символа.   
Размер символа 32 бит (2^5), включает в себя обозначение режимов отображения текстовых символов и 3 символа размером 8 бит каждый:   
### (53-0)
0...7 бит   - обозначение режима отображения текстового символа (аналогично формату **STR41**)   
### (53-8)
8...15 бит  - значение 0-го текстового символа, размером 8 бит   
16...23 бит - значение 1-го текстового символа, размером 8 бит   
24...31 бит - значение 2-го текстового символа, размером 8 бит   

## (67) Формат последовательности текстовых символов STR67   
Размер 64 бит (2^6) (предназначен для ускорения работы на 64 битных процессорах и экономии памяти):   
Состоит из 7х (семи) последовательных текстовых символов.   
Если символов меньше 7, то вместо недостающих значений устанавливаются значение "несуществующего" или "пустого" символа.   
Размер одного символа в последовательности 8 бит,   
включает в себя обозначение режимов отображения текстовых символов и 7 символов размером 8 бит каждый:   
### (67-0)
0...7 бит   - обозначение режима отображения текстового символа (аналогично формату **STR41**)   
### (67-8)
8...15 бит  - значение 0-го текстового символа, размером 8 бит   
16...23 бит - значение 1-го текстового символа, размером 8 бит   
24...31 бит - значение 2-го текстового символа, размером 8 бит   
32...39 бит - значение 3-го текстового символа, размером 8 бит   
40...47 бит - значение 4-го текстового символа, размером 8 бит   
48...55 бит - значение 5-го текстового символа, размером 8 бит   
56...63 бит - значение 6-го текстового символа, размером 8 бит   
