## Cursor gpt-4o

### Prompt 1
 - Como un desarrollador Full-stack altamente capacitado, posees experiencia en varios lenguajes de programación y dominas como el mejor experto del mundo spring boot, angular , typescript, node, prisma y react. Tus fortalezas incluyen programación, documentación, seguridad e implementación de las mejores prácticas. Para recopilar información suficiente para el desarrollo del proyecto, harás preguntas hasta tener todo claro antes de ejecutar algo. comienza preguntándome que haremos hoy.

 ### Prompt 2
 - Necesito realizar una union/migracion y normalizacion de base de datos. Iremos paso a paso, aun no programes, estamos en fase de analisis.  Necesito por favor que analises todo el proyecto y leas el archivo @README.md para entender el contexto total del proyecto. aun no hagas nada, cuando estes listo avisame

 ### Prompt 3
 - Genial, nuestra mision es poder actualizar la base d datos con las nuevas entidades que nos permitan operar el flujo completo de la aplicacion para diversas posciciones. Te entregare un ERD en formato Mermaid para que sea migrado a SQL. Junto con esto Analiza la base de datos actual y el Script SQL y expande la estructura de datos usando las migraciones de Prisma.


ERD:

erDiagram
     COMPANY {
         int id PK
         string name
     }
     EMPLOYEE {
         int id PK
         int company_id FK
         string name
         string email
         string role
         boolean is_active
     }
     POSITION {
         int id PK
         int company_id FK
         int interview_flow_id FK
         string title
         text description
         string status
         boolean is_visible
         string location
         text job_description
         text requirements
         text responsibilities
         numeric salary_min
         numeric salary_max
         string employment_type
         text benefits
         text company_description
         date application_deadline
         string contact_info
     }
     INTERVIEW_FLOW {
         int id PK
         string description
     }
     INTERVIEW_STEP {
         int id PK
         int interview_flow_id FK
         int interview_type_id FK
         string name
         int order_index
     }
     INTERVIEW_TYPE {
         int id PK
         string name
         text description
     }
     CANDIDATE {
         int id PK
         string firstName
         string lastName
         string email
         string phone
         string address
     }
     APPLICATION {
         int id PK
         int position_id FK
         int candidate_id FK
         date application_date
         string status
         text notes
     }
     INTERVIEW {
         int id PK
         int application_id FK
         int interview_step_id FK
         int employee_id FK
         date interview_date
         string result
         int score
         text notes
     }

     COMPANY ||--o{ EMPLOYEE : employs
     COMPANY ||--o{ POSITION : offers
     POSITION ||--|| INTERVIEW_FLOW : assigns
     INTERVIEW_FLOW ||--o{ INTERVIEW_STEP : contains
     INTERVIEW_STEP ||--|| INTERVIEW_TYPE : uses
     POSITION ||--o{ APPLICATION : receives
     CANDIDATE ||--o{ APPLICATION : submits
     APPLICATION ||--o{ INTERVIEW : has
     INTERVIEW ||--|| INTERVIEW_STEP : consists_of
     EMPLOYEE ||--o{ INTERVIEW : conducts
 

Los cambios de modelo y migracion .sql deben ir en @prisma 

Si tienes dudas preguntalas antes de comenzar!

 ### Prompt 4
 - Aquí esta el @schema.prisma

si, necesito que nos pongamos en escenarios de funcionalidades que podrían ser recurrentes, para que? para saber como optimizar los indices de consultas. Ademas necesitamos normalizar la base de datos para que sea escalable y eficiente. Analicemos esto juntos

 ### Prompt 5
 - solo eso, ya podemos comenzar

 ### Prompt 6
 - Quiero que ahora, con este nuevo esquema, realices una revision de cada entidad y revises la relacion de cada una, para hacer mejoras enfocadas en:

Identificar entidades o atributos redundantes y sugerir formas de eliminarlos.
Recomendar la normalizacion de entidades que no cumplen con las formas normales.
Sugerir la creacion de indices en columnas frecuentemente utilizadas en queries para mejorar el rendimiento.
Identificar relaciones faltantes o incorrectas entre entidades.


 - 