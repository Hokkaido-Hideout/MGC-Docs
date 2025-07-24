# 🎮 Magic Node Plugin for Unreal Engine

---

## ✨ Overview

Magic Node is a powerful plugin for Unreal Engine that allows developers to **write C++-like code directly within Blueprint nodes**. It provides a scriptable node system where you can dynamically write, compile, and run custom logic inline with the Blueprint visual scripting system.

🔹 **Script on the Fly**  
🔹 **C++-Styled Syntax**  
🔹 **Dynamic Runtime Execution**  
🔹 **Editor Integration**  

Ideal for prototyping or fine-tuned logic without leaving the Blueprint Editor.

---

## 🧱 Features

### ✅ Scriptable Blueprint Nodes
- Create nodes that accept inline source code.
- Support for logic encapsulation in runtime-compiled nodes.
- Dynamic pin generation based on script function signature.

### 🧠 Runtime Node Object
`UMagicNode` is the base object that acts like a mini-script component at runtime:
- Lifecycle methods: `Awake()`, `Start()`, `Update()`, `Stop()`
- Access to `UWorld` context
- Debugging support
- Tickable logic via timers

### 🧩 Blueprint-Embedded Scripts
`UMagicNodeScript` stores source code and metadata:
- Custom node colors
- Script locking for editor safety
- Inherits from selected `UMagicNode` class

### 🧮 Visual Node Integration
`UKMGC_MagicNode` is the K2 node implementation:
- Handles UI representation via custom Slate widget
- Compiler integration with Blueprint
- Dynamic UI and pin updates
- Tooltip, icon, and category configuration

---

## 🔧 Usage

### Adding a Magic Node
1. Open your Blueprint Editor.
2. Right-click → Search for **Magic Node Script**.
3. Drag it into the graph and double-click to open the script editor.

### Writing a Script
- Code directly inside the editor window.
- Use syntax similar to C++ for logic.
- Input/output pins will automatically generate based on your function parameters.

### Lifecycle Functions
Override the following virtual functions in your script:
```cpp
void Awake();     // Called once when node is created
void Start();     // Called before first Update
void Update(float DeltaTime); // Called every tick
void Stop();      // Called when node is finished
```

---

## 🛠️ Developer API

### `UMagicNode`
- `void Finish()` – Ends the node's execution.
- `void RegisterWorld(UWorld* World)` – Manually set the node’s world context.

### `UMagicNodeScript`
- `UClass* GetRuntimeScriptClass()` – Returns the class to spawn at runtime.
- `bool RefreshRuntimeScriptClass()` – Refreshes the class from source code.

### `UKMGC_MagicNode`
- `void CompileScript()` – Compiles the source code.
- `void ReloadRuntimeScript()` – Reloads the runtime object.
- `FText GetScriptText()` – Gets raw script string.
- `UEdGraphPin* GetExecPin()` / `GetThenPin()` – Get node execution pins.

---

## 🎨 Editor Integration

- Custom Slate widget for node visuals (`SKMGC_MagicNodeWidget`)
- Pin handling and dynamic script parsing
- Real-time source code editor
- Runtime compilation and validation

---

## 🧩 Dependencies

This plugin utilizes several Unreal Engine modules:
- `Slate`, `SlateCore`, `KismetSystemLibrary`
- `UGameplayStatics`, `TimerManager`

It also uses:
- Custom parser: `IKMGC_ScriptParser`
- Code representation: `FMGC_SourceCode`
- Compiler feedback: `EMGC_CompilerResult`

---

## 📸 Screenshot

![Magic Node Blueprint Editor](https://www.dropbox.com/scl/fi/qql7cna2dzw7ahkzw6ew6/95tQwSX.png?rlkey=i02popgwv7lnrjyq6a3zy1d25&st=p7rb8z2j&raw=1)

---
