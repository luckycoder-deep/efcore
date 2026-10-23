
### Installation

EF Core is available on [NuGet](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore). Install the provider package corresponding to your target database. See the [list of providers](https://docs.microsoft.com/ef/core/providers/) in the docs for additional databases.

```sh
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
dotnet add package Microsoft.EntityFrameworkCore.Sqlite
dotnet add package Microsoft.EntityFrameworkCore.Cosmos
```

Use the `--version` option to specify a [preview version](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore/absoluteLatest) to install.

### Daily builds

We recommend using the [daily builds](docs/DailyBuilds.md) to get the latest code and provide feedback on EF Core. These builds contain latest features and bug fixes; previews and official releases lag significantly behind.

### Basic usage

The following code demonstrates basic usage of EF Core. For a full tutorial configuring the `DbContext`, defining the model, and creating the database, see [getting started](https://docs.microsoft.com/ef/core/get-started/) in the docs.

```cs
using var db = new BloggingContext();

// Inserting data into the database
db.Add(new Blog { Url = "http://blogs.msdn.com/adonet" });
db.SaveChanges();

// Querying
var blog = db.Blogs
    .OrderBy(b => b.BlogId)
    .First();

// Updating
blog.Url = "https://devblogs.microsoft.com/dotnet";
blog.Posts.Add(
    new Post
    {
        Title = "Hello World",
        Content = "I wrote an app using EF Core!"
    });
db.SaveChanges();

// Deleting
db.Remove(blog);
db.SaveChanges();
```

### Build from source

Most people use EF Core by installing pre-built NuGet packages, as shown above. Alternatively, [the code can be built and packages can be created directly on your development machine](./docs/getting-and-building-the-code.md).

### Contributing

We welcome community pull requests for bug fixes, enhancements, and documentation. See [How to contribute](./.github/CONTRIBUTING.md) for more information.

### Getting support

If you have a specific question about using these projects, we encourage you to [ask it on Stack Overflow](https://stackoverflow.com/questions/tagged/entity-framework-core*?tab=Votes). If you encounter a bug or would like to request a feature, [submit an issue](https://github.com/dotnet/efcore/issues/new/choose). For more details, see [getting support](.github/SUPPORT.md).


### Installation

The latest stable version is available on [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite).

```sh
dotnet add package Microsoft.Data.Sqlite
```

Use the `--version` option to specify a [preview version](https://www.nuget.org/packages/Microsoft.Data.Sqlite/absoluteLatest) to install.

### Daily builds

We recommend using the [daily builds](docs/DailyBuilds.md) to get the latest code and provide feedback on Microsoft.Data.Sqlite. These builds contain the latest features and bug fixes; previews and official releases lag significantly behind.

### Basic usage

This library implements the common [ADO.NET](https://docs.microsoft.com/dotnet/framework/data/adonet/) abstractions for connections, commands, data readers, and so on. For more information, see [Microsoft.Data.Sqlite](https://docs.microsoft.com/dotnet/standard/data/sqlite/) on Microsoft Docs.

```cs
using var connection = new SqliteConnection("Data Source=Blogs.db");
connection.Open();

using var command = connection.CreateCommand();
command.CommandText = "SELECT Url FROM Blogs";

using var reader = command.ExecuteReader();
while (reader.Read())
{
    var url = reader.GetString(0);
}
```

### Build from source

Most people use Microsoft.Data.Sqlite by installing pre-built NuGet packages, as shown above. Alternatively, [the code can be built and packages can be created directly on your development machine](./docs/getting-and-building-the-code.md).

### Contributing

We welcome community pull requests for bug fixes, enhancements, and documentation. See [How to contribute](./.github/CONTRIBUTING.md) for more information.

### Getting support

If you have a specific question about using these projects, we encourage you to [ask it on Stack Overflow](https://stackoverflow.com/questions/tagged/microsoft.data.sqlite). If you encounter a bug or would like to request a feature, [submit an issue](https://github.com/dotnet/efcore/issues/new/choose). For more details, see [getting support](.github/SUPPORT.md).

