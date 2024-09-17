# Sprint_3_Net

## Integrantes 

552421 - Flavio Sousa Vasconcelos

552368 - WELLINGTON DE OLIVEIRA URCINO DA SILVA

97887 - João Carlos França Figueiredo

550200 - Leonardo Oliveira Esparza


# Currículo API

Uma API desenvolvida em ASP.NET Core para gerenciar currículos. Esta aplicação utiliza o Oracle como banco de dados e implementa padrões de projeto para uma arquitetura de software escalável.

## 📋 Índice
- [Introdução](#introdução)
- [Pré-requisitos](#pré-requisitos)
- [Instalação](#instalação)
- [Configuração](#configuração)
- [Uso](#uso)
- [Estrutura do Projeto](#estrutura-do-projeto)
- [Tecnologias Utilizadas](#tecnologias-utilizadas)
- [Contribuindo](#contribuindo)
- [Licença](#licença)

## 🌟 Introdução
Esta API fornece endpoints CRUD (Create, Read, Update, Delete) para gerenciar currículos e inclui funcionalidades como:
- Paginação dos currículos.
- Log de ações e tratamento de exceções.
- Documentação automatizada utilizando Swagger.
  
## 🛠️ Pré-requisitos
Antes de iniciar, você precisa ter instalado em sua máquina:
- [.NET 8.0 SDK]
- [Oracle Database](https://www.oracle.com/database/)
- [Visual Studio](https://visualstudio.microsoft.com/) ou [Visual Studio Code](https://code.visualstudio.com/)
- [Oracle Managed Data Access](https://www.nuget.org/packages/Oracle.ManagedDataAccess/)
- [Git](https://git-scm.com/)

## 🚀 Instalação
1. Clone o repositório:
    ```bash
    git clone https://github.com/seu-usuario/seu-repositorio.git
    cd seu-repositorio
    ```

2. Instale as dependências necessárias:
    - Abra o terminal no diretório do projeto e execute:
    ```bash
    dotnet restore
    ```

3. Instale o pacote NuGet para o Oracle:
    ```bash
    dotnet add package Oracle.ManagedDataAccess --version <versão-desejada>
    ```

## 🔧 Configuração
1. Abra o arquivo `appsettings.json` e configure a string de conexão para o banco de dados Oracle:
    ```json
    {
      "ConnectionStrings": {
        "OracleConnection": "Data Source=(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=oracle.fiap.com.br)(PORT=1521))(CONNECT_DATA=(SERVICE_NAME=ORCL)));User Id=rm97887;Password=130303;"
      },
      "Logging": {
        "LogLevel": {
          "Default": "Information",
          "Microsoft": "Warning",
          "Microsoft.Hosting.Lifetime": "Information"
        }
      },
      "AllowedHosts": "*"
    }
    ```
    > **Nota:** Atualize os valores da string de conexão conforme necessário. Nunca deixe credenciais sensíveis em produção.

2. Atualize o método `ConfigureServices` em `Startup.cs` ou `Program.cs` para utilizar a `ConnectionString` configurada:
    ```csharp
    services.AddDbContext<AppDbContext>(options =>
        options.UseOracle(Configuration.GetConnectionString("OracleConnection")));
    ```

## 📦 Uso
1. Execute a aplicação:
    ```bash
    dotnet run
    ```
2. Acesse a documentação da API gerada pelo Swagger em:
    ```
    https://localhost:5001/swagger
    ```
3. Teste os endpoints utilizando o Swagger ou ferramentas como [Postman](https://www.postman.com/).

### Endpoints Principais
- **GET /api/curriculos** - Lista todos os currículos.
- **GET /api/curriculos/{id}** - Obtém um currículo pelo ID.
- **POST /api/curriculos** - Adiciona um novo currículo.
- **PUT /api/curriculos/{id}** - Atualiza um currículo existente.
- **DELETE /api/curriculos/{id}** - Exclui um currículo.
- **GET /api/curriculos/paged** - Lista os currículos com paginação.

## 🗂️ Estrutura do Projeto
├── Controllers │ ├── CurriculosController.cs # Controlador da API ├── Models │ ├── Curriculo.cs # Modelo de dados do currículo ├── Repositories │ ├── CurriculoRepository.cs # Repositório para comunicação com o banco de dados │ ├── ICurriculoRepository.cs # Interface do repositório ├── Services │ ├── CurriculoService.cs # Serviço que implementa a lógica de negócios │ ├── ICurriculoService.cs # Interface do serviço ├── Data │ ├── AppDbContext.cs # Configuração do banco de dados └── Program.cs # Configuração principal da aplicação

## 🛠️ Tecnologias Utilizadas
- **ASP.NET Core** - Framework para construção da API.
- **Oracle Database** - Banco de dados utilizado para armazenamento de dados.
- **Entity Framework Core** - ORM para trabalhar com o banco de dados.
- **Swagger** - Para documentação automática da API.
- **Serilog** - Para registro e tratamento de logs.

## 📚 Recursos Adicionais
- [Documentação do ASP.NET Core](https://docs.microsoft.com/aspnet/core)
- [Documentação do Oracle](https://www.oracle.com/database/technologies/)
- [Entity Framework Core](https://docs.microsoft.com/ef/core/)
