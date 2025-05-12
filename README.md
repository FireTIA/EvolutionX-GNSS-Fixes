> 📘 **English version available!**  
> Please refer to `readme_en.md` for the English translation of this README.  
> Choose the file and happy reading!

# GNSS & GPS Fix Modules for EvolutionX 10.2 (Android 15) on Poco F4 5G (munch)

Набор KSU-модулей для исправления работы GNSS HAL и улучшения A-GPS/стандарного GPS на кастомной прошивке EvolutionX 10.2 от @AnkitSavani для Poco F4 5G (кодовое имя: `munch`).

---

## 📦 Модули в составе

- `FixGPS_KSU.zip` — конфигурация GNSS (включает `gps.conf`, SUPL/XTRA, A-GPS-настройки)
- `FixGNSS_SELinux_KSU_v3.zip` — SELinux-правила для разблокировки GNSS HAL

> ⚠️ **Внимание:** модуль `FixGPS_KSU.zip` оптимизирован под регион **Россия / СНГ**.  
> Используются российские NTP- и SUPL-серверы для максимально быстрой GPS-настройки.  
> Для других регионов рекомендуется отредактировать `gps.conf` вручную.

---

## 📱 Поддерживаемые версии и ядра

- **Прошивка**: EvolutionX 10.2 (Android 15) от @AnkitSavani  
- **Ядра** (тестировалось и работает):  
  - `perf+` (предустановленное в EvoX 10.2)  
  - FusionX-SUSFS-AOSP-EFF-1.7-Eclipse-0501 (с SuSFS и KSU-Next)  

---

## ⚙️ Требования

- **KernelSU Next** (версия ≥ 1.0.6) с поддержкой SuSFS (Желателен SuSFS но можно и без него, но тестировалось с ним)
- Ядро с поддержкой KernelSU Next

---

## 🔧 Установка

1. Скопируйте оба ZIP-файла в любое доступное место на устройстве (например, `/sdcard/Download/`).  
2. Откройте приложение **KernelSU Next** → **Модули**.  
3. Нажмите **“Установить”** и выберите по очереди:
   - `FixGPS_KSU.zip`  
   - `FixGNSS_SELinux_KSU_v3.zip`  
4. После установки **перезагрузите** устройство.  
5. Для лучшего первого фикса (TTFF) запустите любое A-GPS-приложение (например, GPS Test) → меню → **AGPS Data** → Reset & Download.

---

## 🚀 Что исправляет

- Пробивает **SELinux-блокировки** для GNSS HAL и `hal_power_default` (отладочный prop-файл и capability).  
- Подключает и улучшает работу **A-GPS / XTRA**, гарантируя быструю Time-To-First-Fix.  
- Восстанавливает стабильный **3D-Fix** и удержание фикса даже при кратковременных провалах сигнала.  
- Позволяет задействовать **GPS + GLONASS** (и при поддержке прошивки — BeiDou/Galileo/QZSS).

---

## 📈 Результаты тестов

- **В помещении**: стабильный фикc, 4–6 спутников в использовании, точность 20–50 м (зависит от условий).  
- **На улице / около окна**: ожидается точность до 3–10 м и до 10+ спутников.  
- **Логи SELinux** (`dmesg | grep denied`) очищены от критичных блокировок GNSS.  

🎥 **Видео тестирования в помещении в близи окна:** [Смотреть на YouTube](https://youtu.be/F7PhC6nSPhc)

---

## 📝 Лицензия

MIT © 2025 [FireTIA](https://github.com/FireTIA) & o4-mini  

---

> **Демо-скриншоты и подробные логи** можно найти в репозитории в папке `/examples`.  
> Если увидите новые `avc: denied` в `dmesg` или `logcat`, создайте issue — мы добавим правило в следующий патч.
