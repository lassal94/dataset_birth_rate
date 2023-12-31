# dataset_birth_rate
## Сбор датасета для модели прогноза рождаемости в РФ из данных ЕМИСС
Одна из типовых задач, решаемых мной в текущей работе. Выложил в открытый доступ по причине того, что использованы только открытые данные.

### Задача - сформировать датасет, на основе которого можно будет построить прогноз рождаемости первых, вторых, трех и последующих детей в РФ.

Вся работа ведется в файле birth_rate.ipynb

Перед началом работы были изучены ряд статей, опросов, а также других исследований.
Выяснил факторы, которые характеризуют рождаемость - это коэффициенты рождаемости
Составлен список факторов, которые могут влиять на рождаемость
В работе использованы только открытые данные с сайта ЕМИСС

В работе много работы с грязными данными, склейки датафреймов, расчета тех или иных показателей, построения сводных таблиц, транспонирования (перекидывал по необходимости строки и столбцы)
Работал с категориями и многое другое.

### Краткое описание хода решения поставленной задачи (подробные комментарии в файле birth_rate.ipynb):
1. Выгружены и объеденены данные о рождаемости женщин и мужчин
2. Сформированы данные по женщинам и мужчинам, разбиты на группы по возрасту и типу населения (сельское/городское), перешел от количественных данных к промилле
3. Аналогичная работа проделана с данными по числу родившихся первых, вторых, третьих, четвертых, 5+ детей, разбиты на группы по возрасту матерей, перешел от количественных данных к промилле
4. Далее проделана работа с целым рядом факторов, с высокой долей вероятности влияющих на рождаемость:
   married - число зарегистрированных браков на 1000 населения (его присоединение расписал отдельно - чтобы показать логику работы вообще)  
   birth_1 - коэффициент рождаемости первых детей  
   birth_2 - коэффициент рождаемости вторых детей  
   birth_3 - коэффициент рождаемости третьих детей  
   idx_price - базовый индекс потребительских цен  
   idx_med - индекс цен на медицинские товары  
   idx_school - индекс цен на одежду для детей школьного возраста  
   idx_preschool - индекс цен на одежду для детей дошкольного возраста  
   idx_baby - индекс цен на белье для детей ясельного возраста  
   idx_school_up - индекс цен на услуги дошкольного воспитания  
   per_zozh - доля населения ведущего зож  
   divorce - число разводов на 1000 населения  
   poverty_lvl - уровень бедности  
   Была написана функция, отвечающая за считывание, обработку и присоединение новых данных (это было возможно, потому что выгрузки, перечисленные выше имеют одинаковую структуру)  
   Далее она была применена в цикле к каждой переменной.
5. Затем был обработан итоговый датафрейм (на предмет пропущенных значений)
6. Все датафреймы, находящиеся в работе были объединены в единый итоговый, осуществлен переход от количественных данных к промилле во всех столбцах
7. Затем отбросили лишние столбцы (год и регион) и сохранили итоговый датасет в файле final_dataset.csv
