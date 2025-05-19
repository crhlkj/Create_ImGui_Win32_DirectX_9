# 🧊 ImGui + GLFW + OpenGL

Простой пример того, как создать графическое окно с меню ImGui, используя GLFW и OpenGL. Этот репозиторий поможет вам быстро настроить проект с помощью `CMake`.

---

## 📁 Структура проекта

```plaintext
your-project/
├── CMakeLists.txt
├── include/
│   └── imgui/        # Сюда помещаем ImGui
├── src/
│   └── main.cpp      # Точка входа
```

---

## ⚙️ Шаг 1: Создание базовых файлов

### `CMakeLists.txt`

```cmake
cmake_minimum_required(VERSION 3.31)
project(YourProjectName)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_executable(${PROJECT_NAME} src/main.cpp)
```

### `main.cpp`

```cpp
#include <iostream>
using namespace std;

int main(int argc, char* argv[]) {
    cout << "Hello, ImGui + GLFW + OpenGL!" << endl;
    return 0;
}
```

---

## 📦 Шаг 2: Установка зависимостей

### 🔹 ImGui

Клонируем официальный репозиторий:

```bash
git clone https://github.com/ocornut/imgui.git include/imgui
```

Удалите ненужные файлы, оставив только:

* `imgui.cpp`, `imgui_draw.cpp`, `imgui_tables.cpp`, `imgui_widgets.cpp`, `imgui_demo.cpp`
* `backends/imgui_impl_glfw.cpp`, `backends/imgui_impl_opengl3.cpp`
* Все соответствующие заголовки (`*.h`)

---

## 🔧 Финальный `CMakeLists.txt`

```cmake
cmake_minimum_required(VERSION 3.31)
project(YourNameProject)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

set(IMGUI_DIR ${CMAKE_SOURCE_DIR}/include/imgui)
set(IMGUI_SOURCES
        ${IMGUI_DIR}/imgui.cpp
        ${IMGUI_DIR}/imgui_draw.cpp
        ${IMGUI_DIR}/imgui_tables.cpp
        ${IMGUI_DIR}/imgui_widgets.cpp
        ${IMGUI_DIR}/imgui_demo.cpp
        ${IMGUI_DIR}/backends/imgui_impl_dx9.cpp
        ${IMGUI_DIR}/backends/imgui_impl_win32.cpp
)

add_library(imgui STATIC ${IMGUI_SOURCES})

target_include_directories(imgui
        PUBLIC
        ${IMGUI_DIR}
        ${IMGUI_DIR}/backends
)

add_executable(${PROJECT_NAME} src/main.cpp)
target_link_libraries(${PROJECT_NAME}
        PRIVATE
        imgui
        d3d9
        dwmapi
)
```

---

## ▶️ Запуск

1. Склонируйте репозиторий:

   ```bash
   git clone https://github.com/Baradinskiy/Create_ImGui_Win32_DirectX_9.git
   cd Create_ImGui_Win32_DirectX_9
   ```

2. Создайте папку сборки и соберите проект:

   ```bash
   mkdir build && cd build
   cmake ..
   cmake --build .
   ```

---

## 🧠 Результат

После запуска вы получите окно с базовым GUI от ImGui, работающим на OpenGL + GLFW. Отличная стартовая точка для вашего проекта!

---

## 📜 Лицензия

Этот проект распространяется под лицензией MIT. Подробнее см. [LICENSE](LICENSE).

