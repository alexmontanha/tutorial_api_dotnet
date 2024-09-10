# Tutorial: Criar uma API mínima em C# com .NET

Este tutorial foi criado para ajudar os estudantes de Ciência da Computação a criarem uma API mínima em C# com .NET. A API será criada utilizando o framework minimalista [ASP.NET Core Web API](https://docs.microsoft.com/pt-br/aspnet/core/web-api/?view=aspnetcore-5.0).

## Pré-requisitos

Antes de começar, você precisa ter o [.NET SDK](https://dotnet.microsoft.com/download) instalado na sua máquina. Você pode verificar se o .NET SDK está instalado executando o seguinte comando no terminal:

```bash
dotnet --version
```

Se o comando retornar a versão do .NET SDK, significa que o SDK está instalado corretamente.

## Passo a passo

### Passo 1: Criar um novo projeto

1. Abra o terminal e execute o comando para criar um novo projeto web:

    ```bash
    dotnet new web -o ApiAula1
    ```

2. Navegue até o diretório do projeto:

    ```bash
    cd .\ApiAula1\
    ```

3. Abra o projeto no Visual Studio Code:

    ```bash
    code .
    ```

### Passo 2: Configurar a aplicação

1. No arquivo `Program.cs`, adicione o seguinte código:

    ```csharp
    var builder = WebApplication.CreateBuilder(args);
    var app = builder.Build();

    app.MapGet("/", () => "Hello World!");

    app.Run();
    ```

### Passo 3: Executar a aplicação

1. No terminal, execute o comando:

    ```bash
    dotnet run
    ```

2. Você verá as seguintes informações no terminal:

    ```bash
    info: Microsoft.Hosting.Lifetime[14]
          Now listening on: http://localhost:{port}
    info: Microsoft.Hosting.Lifetime[0]
          Application started. Press Ctrl+C to shut down.
    info: Microsoft.Hosting.Lifetime[0]
          Hosting environment: Development
    info: Microsoft.Hosting.Lifetime[0]
          Content root path: F:\source\Repos\sistemas_distribuidos\ApiAula1
    ```

    {port} é a porta que a aplicação está escutando. Por padrão, a porta é 5000, mas pode ser diferente.
    Caso a porta seja 5013, por exemplo, a URL será `http://localhost:5013`.

3. Acesse a URL `http://localhost:{port}` no seu navegador para ver a mensagem "Hello World!".

### Passo 4: Adicionar uma nova rota

1. No arquivo `Program.cs`, adicione a seguinte rota:

    ```csharp
    app.MapGet("/hello", (string name) =>
    {
        var saudacao = DateTime.Now.Hour < 12 ? "Bom dia" : "Boa tarde";
        var retorno = $"{saudacao}, {name}";
        return retorno;
    });
    ```

2. Acesse a URL `http://localhost:{port}/hello?name=Montanha` no seu navegador para ver a saudação personalizada.

### Passo 5: Adicionar uma rota para retornar um objeto

1. No arquivo `Program.cs`, adicione a seguinte rota:

    ```csharp
    app.MapGet("/pessoa", () =>
    {
        var pessoa = new Pessoa
        {
            Nome = "Fulano de Tal",
            DataNascimento = new DateTime(1980, 1, 1),
            Email = "fulano@fulano.com",
            Telefone = "11 99999-9999",
            Endereco = "Rua das Flores",
            Cidade = "São Paulo",
            Estado = "SP",
            Pais = "Brasil",
            CEP = "00000-000",
            CPF = "000.000.000-00",
            RG = "00.000.000-0",
            CNH = "00000000000",
        };
        return pessoa;
    });
    ```

2. Adicione a classe `Pessoa` no mesmo arquivo ou em um arquivo separado:

    ```csharp
    namespace ApiAula1
    {
        public class Pessoa
        {
            public string Nome { get; set; } = string.Empty;
            public DateTime DataNascimento { get; set; }
            public string Email { get; set; } = string.Empty;
            public string Telefone { get; set; } = string.Empty;
            public string Endereco { get; set; } = string.Empty;
            public string Cidade { get; set; } = string.Empty;
            public string Estado { get; set; } = string.Empty;
            public string Pais { get; set; } = string.Empty;
            public string CEP { get; set; } = string.Empty;
            public string CPF { get; set; } = string.Empty;
            public string RG { get; set; } = string.Empty;
            public string CNH { get; set; } = string.Empty;
            public string TituloEleitor { get; set; } = string.Empty;
            public string Passaporte { get; set; } = string.Empty;
            public string CarteiraTrabalho { get; set; } = string.Empty;
        }
    }
    ```

3. Acesse a URL `http://localhost:{port}/pessoa` no seu navegador para ver os dados da pessoa.

O retorno será um objeto JSON com os dados da pessoa:

```json
{
    "nome": "Fulano de Tal",
    "dataNascimento": "1980-01-01T00:00:00",
    "email": "fulano@fulano.com",
    "telefone": "11 99999-9999",
    "endereco": "Rua das Flores",
    "cidade": "São Paulo",
    "estado": "SP",
    "pais": "Brasil",
    "cep": "00000-000",
    "cpf": "000.000.000-00",
    "rg": "00.000.000-0",
    "cnh": "00000000000",
    "tituloEleitor": "",
    "passaporte": "",
    "carteiraTrabalho": ""
}
```

## Conclusão

Parabéns! Você criou uma API mínima em C# com .NET. Agora você pode adicionar mais rotas e funcionalidades à sua API. Divirta-se!

## Referências

- [ASP.NET Core Web API](https://docs.microsoft.com/pt-br/aspnet/core/web-api/?view=aspnetcore-5.0)
- [Tutorial: Criar uma API Web com ASP.NET Core](https://learn.microsoft.com/pt-br/aspnet/core/tutorials/first-web-api?view=aspnetcore-8.0&preserve-view=true&tabs=visual-studio)

## Autor

- [Professor Alexandre Montanha](https://www.linkedin.com/in/professor-montanha/)
- [GitHub](https://github.com/alexmontanha)
