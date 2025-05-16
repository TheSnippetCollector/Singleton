Here are **multiple examples** of converting a **normal class to a singleton class** in Dart.

### 🔹 Example 1: Basic Singleton using `factory` constructor

#### ✅ Normal Class:

```
class MyService {
  void fetchData() {
    print('Fetching data...');
  }
}

```
#### 🔁 Singleton Version:

```
class MyService {
  // Step 1: Private constructor
  MyService._privateConstructor();

  // Step 2: Static instance
  static final MyService _instance = MyService._privateConstructor();

  // Step 3: Factory constructor
  factory MyService() {
    return _instance;
  }

  void fetchData() {
    print('Fetching data...');
  }
}

```

### 🔹 Example 2: Singleton with Lazy Initialization

#### ✅ Normal Class:

```
class Logger {
  void log(String message) {
    print('Log: $message');
  }
}

```


#### 🔁 Singleton Version:

```
class Logger {
  static Logger? _instance;

  Logger._internal(); // private constructor

  factory Logger() {
    _instance ??= Logger._internal();
    return _instance!;
  }

  void log(String message) {
    print('Log: $message');
  }
}

```

### 🔹 Example 3: Singleton with Static Getter (Alternative Style)

```
class Config {
  Config._();

  static final Config _singleton = Config._();

  static Config get instance => _singleton;

  String get apiUrl => 'https://example.com';
}

```

Usage:

``` 
final config = Config.instance;
print(config.apiUrl);
```

### 🔹 Example 4: Thread-Safe Singleton (Optional for web/multithreading)

Dart is single-threaded in most Flutter use-cases, but here's a thread-safe version conceptually:
```
class Database {
  static final Database _instance = Database._internal();

  Database._internal();

  factory Database() => _instance;

  void query(String sql) {
    print("Executing: $sql");
  }
}
```

| Technique | Pros | Note |
| - | - | - |
| `factory` constructor | Simple, reliable| Most common in Dart |
| Lazy init | Useful if creation is expensive| Slightly more code |
| Static getter | Clear intent, flexible | Good for dependency injection |

Let me know if you want an example with async initialization, dependency injection, or using a service locator like `get_it`.
