# DynamicNativeDllLoader

> _Note: This is fixed fork of [this](https://github.com/schellingb/DLLFromMemory-net) repo_

## What is it for?

Now you can load 86/64 native DLLs from a resource without writing them to disk.

## Usage

```CSharp
[UnmanagedFunctionPointer(CallingConvention.Cdecl)]
private delegate int functionDelegate(int x, int y);
private static functionDelegate function;


var resource = Assembly.GetExecutingAssembly().GetManifestResourceStream("NativeDllRes");
MemoryStream stream = new MemoryStream();
resource.CopyTo(stream);
data = stream.ToArray();
dll = new DLLFromMemory(data);
function = dll.GetDelegateFromFuncName<functionDelegate>("func_name");
```
