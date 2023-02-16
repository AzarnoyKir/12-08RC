# 12-08RC

# Финансовая компания решила увеличить надежность работы БД и их резервного копирования.
# Необходимо описать, какие варианты резервного копирования подходят в случаях:

# 1.1 Необходимо восстанавливать данные в полном объеме за предыдущий день.

# 1.2 Необходимо восстанавливать данные за час до предполагаемой поломки.

# 1.3* Возможен ли кейс, когда при поломке базы происходило моментальное переключение на работающую/починеную БД?

# Приведите ответ в свободной форме.
# ___


# В процессе обычно используются утилиты для восстановления, поставляемые в комплекте с СУБД.

# 1.1 Необходимо восстанавливать данные в полном объеме за предыдущий день.
# Дифференциальная резервная копия подойдет.
# Дифференциальная резервная копия позволяет быстрее восстанавливать данные по сравнению с инкрементным резервным копированием, поскольку для этого требуется всего две части резервной копии: полная резервная копия и последняя дифференциальная резервная копия.
# Данное резервное копирование быстрее, чем полное, но медленнее, чем инкрементное .
 
# 1.2 Необходимо восстанавливать данные за час до предполагаемой поломки.
# Инкрементное резервное копирование подойдет.
# Инкрементное резервное копирование использует полную копию, как начальную точку. Затем выполняется резервное копирование только блоков данных, которые были изменены с момента последнего резервного задания, с заданным периодом выполнения задания. В зависимости от политики хранения резервных копии, через определенный период создается новая полная копия для повторения цикла.
# Инкрементное резервное копирование можно выполнять так часто, как требуется, так как сохраняются только копии последних изменений. Нам это подходит.
 
# 1.3  Возможен ли кейс, когда при поломке базы происходило моментальное переключение на работающую/починеную БД?**
 
# Репликация master-slave 
 


# Задание 2. PostgreSQL
# 2.1 С помощью официальной документации приведите пример команды резервирования данных и восстановления БД (pgdump/pgrestore).

# Приведите ответ в свободной форме.
# ____________________________________________________________________________


# PostgreSQL

# 2.1 С помощью официальной документации приведите пример команды резервирования данных и восстановления БД (pgdump/pgrestore).

# Следующая команда делает дамп базы данных, используя специальный формат дампа:

# pg_dump -Fc bd_name > dump.sql

# Специальный формат дампа не является скриптом для psql и должен восстанавливаться с помощью команды 
# pg_restore, например:

# pg_restore –d bd_name dump.sql
# ____________________________________________________________________________



# Задание 3. MySql

# 3.1 С помощью официальной документации приведите пример команды инкрементного резервного копирования базы данных MySql.


# Приведите ответ в свободной форме.
# ___

# MySql

# 3.1 С помощью официальной документации приведите пример команды инкрементного резервного копирования базы данных MySql.

# --incremental-base=history:last_full_backup

