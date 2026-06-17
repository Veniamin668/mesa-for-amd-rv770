# Mesa R600 Custom Build for Radeon HD 4850 (RV770)

A custom-compiled Mesa driver optimized for **AMD Radeon HD 4850 (RV770)** on modern Linux systems. This build provides hardware-accelerated graphics for legacy hardware where standard system drivers may lack support or performance.

---

## 🇬🇧 English Installation Guide

### Prerequisites
* OS: Debian GNU/Linux (or compatible)
* GPU: AMD Radeon HD 4850 (RV770)

### Installation
1. Download the `.deb` package from the [Releases](https://github.com/Veniamin668/mesa-for-amd-rv770/releases) page.
2. Install the package:
  ```
   sudo dpkg -i mesa-r600-custom_26.2.0-1_amd64.deb

    #If you encounter dependency errors, fix them with:

    sudo apt-get install -f
 ```
Verification

Verify that the system is using the new driver:
 ```
glxinfo | grep "OpenGL renderer"
   ```
You should see: OpenGL renderer string: AMD RV770 (DRM 2.51.0 / ...)
Troubleshooting

If the system defaults to llvmpipe (software rendering):
 
    №Add the driver path to the library configuration:

    echo "/opt/mesa-r600/lib/x86_64-linux-gnu/" | sudo tee /etc/ld.so.conf.d/mesa-r600.conf

    №Update the cache
    sudo ldconfig

🇷🇺 Инструкция на русском языке (Russian)
Установка

    №Скачайте .deb пакет со страницы Releases.

    №Установите его командой:

    sudo dpkg -i mesa-r600-custom_26.2.0-1_amd64.deb

    №Если возникнут ошибки зависимостей, выполните:

    sudo apt-get install -f

Проверка

Убедитесь, что система использует ваш драйвер:
 ```

glxinfo | grep "OpenGL renderer"

Правильный результат: OpenGL renderer string: AMD RV770 ...
Решение проблем

Если система всё еще использует llvmpipe (программный рендер):

    Добавьте путь к драйверу в конфиг системы:

    echo "/opt/mesa-r600/lib/x86_64-linux-gnu/" | sudo tee /etc/ld.so.conf.d/mesa-r600.conf

    Обновите кэш библиотек:

    sudo ldconfig

🗑 Removal

To uninstall the custom driver, simply run:

sudo dpkg -r mesa-r600-custom
