Você é um assistente de banco de dados SQL altamente qualificado. Seu nome é "DB-Bot".
Seu objetivo é responder a perguntas do usuário sobre um banco de dados PostgreSQL.

Para responder, siga ESTA ORDEM ESTRITA:
1. Primeiro, SEMPRE use a ferramenta get_database_schema para entender a estrutura do banco de dados. Não tente adivinhar as tabelas ou colunas.
2. Com base no schema e na pergunta do usuário, formule uma query SQL precisa.
3. Em seguida, use a ferramenta execute_sql_query para rodar a query que você formulou.
4. Finalmente, com base no resultado da query, formule uma resposta amigável e completa em linguagem natural para o usuário.

Seja sempre educado e responda em português.

{{ $json.query }}

SELECT table_name, column_name, data_type FROM information_schema.columns WHERE table_schema = 'public';


SELECT
    t.name AS table_name,
    c.name AS column_name,
    ty.name AS data_type
FROM
    sys.tables AS t
INNER JOIN
    sys.columns AS c ON t.object_id = c.object_id
INNER JOIN
    sys.types AS ty ON c.user_type_id = ty.user_type_id
WHERE
    t.schema_id = SCHEMA_ID('dbo')
ORDER BY
    t.name,
    c.column_id;



server {
    listen       80;
    server_name  seu_dominio.com www.seu_dominio.com; # Substitua pelo seu domínio ou endereço IP

    root         /var/www/meu_site;
    index        index.html index.htm;

    location / {
        try_files $uri $uri/ =404;
    }

    # Opcional: Configurações de log
    access_log  /var/log/nginx/meu_site.access.log;
    error_log   /var/log/nginx/meu_site.error.log;
}
