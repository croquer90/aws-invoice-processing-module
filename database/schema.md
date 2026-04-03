mysql> describe invoices;
+----------------------------+---------------------------------------------------------------------+------+-----+-------------------+-----------------------------------------------+
| Field                      | Type                                                                | Null | Key | Default           | Extra                                         |
+----------------------------+---------------------------------------------------------------------+------+-----+-------------------+-----------------------------------------------+
| id                         | bigint                                                              | NO   | PRI | NULL              | auto_increment                                |
| vendor_id                  | bigint                                                              | NO   | MUL | NULL              |                                               |
| invoice_number             | varchar(100)                                                        | NO   |     | NULL              |                                               |
| invoice_date               | date                                                                | YES  | MUL | NULL              |                                               |
| due_date                   | date                                                                | YES  |     | NULL              |                                               |
| subtotal                   | decimal(15,2)                                                       | YES  |     | NULL              |                                               |
| tax_amount                 | decimal(15,2)                                                       | YES  |     | NULL              |                                               |
| total_amount               | decimal(15,2)                                                       | NO   |     | NULL              |                                               |
| currency_code              | varchar(10)                                                         | NO   |     | USD               |                                               |
| paid_status                | enum('PAID','UNPAID')                                               | NO   | MUL | UNPAID            |                                               |
| status                     | enum('UPLOADED','EXTRACTED','VALIDATED','POSTED','REVIEW','FAILED') | NO   | MUL | UPLOADED          |                                               |
| source_file_name           | varchar(255)                                                        | NO   |     | NULL              |                                               |
| source_file_s3_key         | varchar(500)                                                        | NO   |     | NULL              |                                               |
| file_hash_sha256           | char(64)                                                            | YES  |     | NULL              |                                               |
| extracted_vendor_name      | varchar(255)                                                        | YES  |     | NULL              |                                               |
| extracted_confidence_score | decimal(5,2)                                                        | YES  |     | NULL              |                                               |
| validation_message         | text                                                                | YES  |     | NULL              |                                               |
| extracted_payload_json     | json                                                                | YES  |     | NULL              |                                               |
| journal_entry_id           | bigint                                                              | YES  | MUL | NULL              |                                               |
| created_at                 | timestamp                                                           | YES  |     | CURRENT_TIMESTAMP | DEFAULT_GENERATED                             |
| updated_at                 | timestamp                                                           | YES  |     | CURRENT_TIMESTAMP | DEFAULT_GENERATED on update CURRENT_TIMESTAMP |
+----------------------------+---------------------------------------------------------------------+------+-----+-------------------+-----------------------------------------------+

mysql> describe vendors;
+--------------------+--------------+------+-----+-------------------+-----------------------------------------------+
| Field              | Type         | Null | Key | Default           | Extra                                         |
+--------------------+--------------+------+-----+-------------------+-----------------------------------------------+
| id                 | bigint       | NO   | PRI | NULL              | auto_increment                                |
| vendor_name        | varchar(255) | NO   |     | NULL              |                                               |
| normalized_name    | varchar(255) | NO   | MUL | NULL              |                                               |
| tax_id             | varchar(100) | YES  | MUL | NULL              |                                               |
| email              | varchar(255) | YES  |     | NULL              |                                               |
| phone              | varchar(50)  | YES  |     | NULL              |                                               |
| address_line1      | varchar(255) | YES  |     | NULL              |                                               |
| address_line2      | varchar(255) | YES  |     | NULL              |                                               |
| city               | varchar(100) | YES  |     | NULL              |                                               |
| state              | varchar(100) | YES  |     | NULL              |                                               |
| postal_code        | varchar(30)  | YES  |     | NULL              |                                               |
| country            | varchar(100) | YES  |     | NULL              |                                               |
| default_account_id | int          | YES  | MUL | NULL              |                                               |
| created_at         | timestamp    | YES  |     | CURRENT_TIMESTAMP | DEFAULT_GENERATED                             |
| updated_at         | timestamp    | YES  |     | CURRENT_TIMESTAMP | DEFAULT_GENERATED on update CURRENT_TIMESTAMP |
+--------------------+--------------+------+-----+-------------------+-----------------------------------------------+

mysql> describe chart_of_accounts;
+----------------+--------------------------------------------------------+------+-----+---------+----------------+
| Field          | Type                                                   | Null | Key | Default | Extra          |
+----------------+--------------------------------------------------------+------+-----+---------+----------------+
| id             | int                                                    | NO   | PRI | NULL    | auto_increment |
| code           | varchar(20)                                            | NO   | UNI | NULL    |                |
| name           | varchar(100)                                           | NO   |     | NULL    |                |
| type           | enum('ASSET','LIABILITY','EQUITY','REVENUE','EXPENSE') | NO   |     | NULL    |                |
| statement_type | enum('BALANCE_SHEET','PROFIT_LOSS')                    | YES  |     | NULL    |                |
| is_active      | tinyint(1)                                             | YES  |     | 1       |                |
| parent_id      | int                                                    | YES  | MUL | NULL    |                |
+----------------+--------------------------------------------------------+------+-----+---------+----------------+

mysql> describe  journal_entries;
+----------------+--------------+------+-----+-------------------+-------------------+
| Field          | Type         | Null | Key | Default           | Extra             |
+----------------+--------------+------+-----+-------------------+-------------------+
| id             | bigint       | NO   | PRI | NULL              | auto_increment    |
| reference      | varchar(100) | YES  |     | NULL              |                   |
| description    | text         | YES  |     | NULL              |                   |
| date           | date         | NO   |     | NULL              |                   |
| effective_date | date         | NO   |     | NULL              |                   |
| period_start   | date         | YES  |     | NULL              |                   |
| period_end     | date         | YES  |     | NULL              |                   |
| created_at     | timestamp    | YES  |     | CURRENT_TIMESTAMP | DEFAULT_GENERATED |
+----------------+--------------+------+-----+-------------------+-------------------+

mysql> describe  journal_entries;
+----------------+--------------+------+-----+-------------------+-------------------+
| Field          | Type         | Null | Key | Default           | Extra             |
+----------------+--------------+------+-----+-------------------+-------------------+
| id             | bigint       | NO   | PRI | NULL              | auto_increment    |
| reference      | varchar(100) | YES  |     | NULL              |                   |
| description    | text         | YES  |     | NULL              |                   |
| date           | date         | NO   |     | NULL              |                   |
| effective_date | date         | NO   |     | NULL              |                   |
| period_start   | date         | YES  |     | NULL              |                   |
| period_end     | date         | YES  |     | NULL              |                   |
| created_at     | timestamp    | YES  |     | CURRENT_TIMESTAMP | DEFAULT_GENERATED |
+----------------+--------------+------+-----+-------------------+-------------------+
