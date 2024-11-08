# IHostApplicationBuilder vs IHostBuilder

This repository contains self-contained [LINQPad](https://www.linqpad.net/) files that showcase some differences and gotchas between `IHostApplicationBuilder` and `IHostBuilder`.

----

`IHostApplicationBuilder` is part of the [new hosting model](https://learn.microsoft.com/en-us/aspnet/core/migration/50-to-60?view=aspnetcore-8.0&tabs=visual-studio#new-hosting-model) introducied in .NET 6 and it's the nowadays recommended approach to host building in .NET.

One of the main differences to take into account when reviewing this PR: the new model is based in linear code execution rather than in callbacks that are executed whenever the `IHost` is built.

Quoting David Fowler [here](https://github.com/dotnet/runtime/discussions/81090#discussioncomment-4784551):
> We moved away from the ceremony of a generic host in the default templates and to the scenario specific WebApplicationBuilder. The general idea was to move away from calbacks and move to linear code for configuring everything, this was part of .NET 6. In .NET 7, we added var builder = Host.CreateApplicationBuilder() as the backbone of WebApplication.CreateBuilder so we could have a smoother integration of the API styles (building the linear API on top of the callback API was error prone).

More info and comparison between hosting models can be found in [this blog post](https://andrewlock.net/exploring-dotnet-6-part-2-comparing-webapplicationbuilder-to-the-generic-host/).
