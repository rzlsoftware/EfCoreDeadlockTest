# EfCoreDeadlockTest

Sample Project for [EfCore Issue 12407](https://github.com/aspnet/EntityFrameworkCore/issues/12407)   
Ef Core 2.1 causes a deadlock when using in a WPF Application and calling `.Wait()` on an async operation.

```csharp
var query = context.Authors.Include(a => a.Books);

var t = query.ToListAsync();
t.Wait();           // Deadlock
return t.Result;
```
Deadlock in [MainWindow.xaml.cs](https://github.com/JakobFerdinand/EfCoreDeadlockTest/blob/master/EfCoreDeadlockTest/MainWindow.xaml.cs)
