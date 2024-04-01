# HCK.Result

`HCK.Result` is a `.NET` library that simplifies the process of returning and handling operation results from methods, including success or failure information, error messages, and HTTP status codes. It's particularly useful in web applications and APIs but can be utilized in any `.NET` project to make result handling more structured and consistent.

## Features

- Generic `Result<T>` type for operation results with an optional data payload.
- Support for error messages as a list of strings.
- Includes HTTP status codes for integration with web projects.
- Simplifies method return types by encapsulating success, data, and error information.
- Supports implicit conversion from data or error information to `Result<T>` objects, making it easy to return from methods.

## Getting Started

### Installation

To use `HCK.Result` in your project, install it via NuGet package manager or the `dotnet` CLI:

```plaintext
Install-Package HCK.Result
```

Or through the .NET CLI:
```plaintext
dotnet add package HCK.Result
```

### Usage

- **Here's how to use `HCK.Result` in your `.NET` applications:**

#### Returning Success

```csharp
public Result<string> GetGreeting(string name)
{
    return $"Hello, {name}!";
}
```

- **Returning Failure**
```csharp
public Result<string> GetGreeting(string name)
{
    if (string.IsNullOrEmpty(name))
    {
        return (HttpStatusCode.BadRequest, "Name cannot be empty");
    }
    return $"Hello, {name}!";
}
```

- **Handling Results**
```csharp
var result = GetGreeting("John");

if (result.IsSuccessful)
{
    Console.WriteLine(result.Data);
}
else
{
    Console.WriteLine($"Error ({result.StatusCode}): {string.Join(", ", result.ErrorMessages)}");
}
```

## Contributing

We welcome contributions! Please submit any bug reports, suggestions, or pull requests to the project's issue tracker or repository.

## License
`HCK.Result` is licensed under the MIT License. See the LICENSE file in the source repositor for full details.

```rust
This Markdown formatted text can be directly used as a `README.md` file in your repository. Just make sure to update the placeholder `(LICENSE)` with a link to your actual license file, if applicable.
```
