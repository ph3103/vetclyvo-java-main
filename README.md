# Vetclyvo Java API
API RESTful feita em Java com Spring Boot para acompanhamento da saúde do pet
— FIAP Challenge 2026 em parceria com a Clyvo VET.

## Integrantes
-Pedro Henrique rm:563062
-Luis Guilherme rm:566548
-Leonardo Guilherme rm:562992
-Vinicios L. rm:563340


## Descrição do Projeto

A vetclvo API resolve o problema na saúde animal. Hoje, tutores só consuta clínicas em situações de extrema urgência. Nossa solução oferece uma solução digital para organizar, persolanilar e lembrar o cuidado preventivo e terapêutico do pet.

## Tecnologias 

- Java 17
- Spring Boot 3.3.5
- Spring Data JPA
- Banco H2 (in-memory)
- Swagger / OpenAPI (springdoc)
- Maven

# Estrutura 
src/main/java/br/com/fiap/clyvovet/
├── controller/
│   ├── TutorController.java
│   ├── PetController.java
│   ├── ConsultaController.java
│   └── VacinaController.java
├── model/
│   ├── Tutor.java
│   ├── Pet.java
│   ├── Consulta.java
│   └── Vacina.java
├── repository/
│   ├── TutorRepository.java
│   ├── PetRepository.java
│   ├── ConsultaRepository.java
│   └── VacinaRepository.java
└── exception/
└── GlobalExceptionHandler.java

## Rotas da API

### Tutores
| Método | Rota | Descrição |
|--------|------|-----------|
| GET | /api/tutores | Lista todos os tutores |
| GET | /api/tutores/{id} | Busca tutor por ID |
| GET | /api/tutores/email/{email} | Busca tutor por email |
| GET | /api/tutores/{id}/pets | Lista pets do tutor |
| POST | /api/tutores | Cadastra novo tutor |
| PUT | /api/tutores/{id} | Atualiza tutor |
| DELETE | /api/tutores/{id} | Remove tutor |

### Pets
| Método | Rota | Descrição |
|--------|------|-----------|
| GET | /api/pets | Lista todos os pets |
| GET | /api/pets/{id} | Busca pet por ID |
| GET | /api/pets/especie/{especie} | Busca por espécie |
| GET | /api/pets/raca/{raca} | Busca por raça |
| GET | /api/pets/tutor/{tutorId} | Busca pets do tutor |
| POST | /api/pets | Cadastra novo pet |
| PUT | /api/pets/{id} | Atualiza pet |
| DELETE | /api/pets/{id} | Remove pet |

### Consultas
| Método | Rota | Descrição |
|--------|------|-----------|
| GET | /api/consultas | Lista todas as consultas |
| GET | /api/consultas/{id} | Busca consulta por ID |
| GET | /api/consultas/veterinario/{nome} | Busca por veterinário |
| GET | /api/consultas/periodo?inicio=&fim= | Busca por período |
| GET | /api/consultas/pet/{petId} | Consultas do pet |
| POST | /api/consultas | Cadastra nova consulta |
| PUT | /api/consultas/{id} | Atualiza consulta |
| DELETE | /api/consultas/{id} | Remove consulta |

### Vacinas
| Método | Rota | Descrição |
|--------|------|-----------|
| GET | /api/vacinas | Lista todas as vacinas |
| GET | /api/vacinas/{id} | Busca vacina por ID |
| GET | /api/vacinas/pendentes | Lista vacinas pendentes |
| GET | /api/vacinas/nome/{nome} | Busca por nome |
| GET | /api/vacinas/proximas?dias=30 | Próximas vacinas |
| GET | /api/vacinas/pet/{petId} | Vacinas do pet |
| POST | /api/vacinas | Cadastra nova vacina |
| PUT | /api/vacinas/{id} | Atualiza vacina |
| DELETE | /api/vacinas/{id} | Remove vacina |

## Como Rodar o Projeto

### Pré-requisitos
- Java 17
- Maven

### Instalação

**1. Clone o repositório:**
```bash
git clone https://github.com/ph3103/vetclyvo-java-main.git
cd vetclyvo-java-main
```

**2. Execute o projeto:**
```bash
./mvnw spring-boot:run
```

**3. Acesse o Swagger:**
http://localhost:8080/swagger-ui/index.html

**4. Acesse o console H2:**
http://localhost:8080/h2-console
JDBC URL: jdbc:h2:mem:clyvovetdb
User: sa
Password: (vazio)

## Exemplos de Requisições

### Cadastrar um Tutor
```json
POST /api/tutores
{
  "nome": "Neymar Junior",
  "email": "neymar@email.com",
  "telefone": "11999999999"
}
```

### Cadastrar um Pet
```json
POST /api/pets
{
  "nome": "Thor",
  "especie": "Cachorro",
  "raca": "Labrador",
  "dataNascimento": "2020-03-15",
  "tutor": { "id": 1 }
}
```

### Cadastrar uma Consulta
```json
POST /api/consultas
{
  "data": "2026-05-10T10:00:00",
  "descricao": "Consulta de rotina",
  "veterinario": "Dr. Henrique",
  "observacoes": "Pet saudável",
  "pet": { "id": 1 }
}
```

### Cadastrar uma Vacina
```json
POST /api/vacinas
{
  "nome": "Antirrábica",
  "dataAplicacao": "2026-05-10",
  "proximaDose": "2027-05-10",
  "aplicada": true,
  "pet": { "id": 1 }
}
```
