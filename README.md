# Rfam SQL Pipeline

Этот проект демонстрирует использование CI/CD для автоматического выполнения SQL-запросов к публичной базе данных Rfam (https://rfam.org).

## Описание

Пайплайн GitHub Actions автоматически запускается при изменении файла `query.sql`, выполняет SQL-запросы к публичной MySQL-базе Rfam и выводит результат в логах Actions.

## Как использовать

1. Клонируйте репозиторий:
   ```bash
   git clone https://github.com/<ваш_логин>/rfam-sql-pipeline.git
   cd rfam-sql-pipeline
   ```
2. Измените файл `query.sql`, добавив нужный SQL-запрос.
3. Зафиксируйте и отправьте изменения:
   ```bash
   git add query.sql
   git commit -m "Update SQL query"
   git push
   ```
4. Перейдите на вкладку **Actions** в вашем репозитории на GitHub, чтобы посмотреть результат выполнения запроса.

## Пример SQL-запроса

```sql
SELECT fr.rfam_acc, fr.rfamseq_acc, fr.seq_start, fr.seq_end
FROM full_region fr, rfamseq rf, taxonomy tx
WHERE rf.ncbi_id = tx.ncbi_id
  AND fr.rfamseq_acc = rf.rfamseq_acc
  AND tx.ncbi_id = 10116
  AND is_significant = 1;
```

## Доступ к базе данных Rfam

- **host:** mysql-rfam-public.ebi.ac.uk
- **user:** rfamro
- **password:** (нет пароля)
- **port:** 4497
- **database:** Rfam

## Лицензия

MIT
