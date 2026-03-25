<picture>
  <source media="(prefers-color-scheme: dark)" srcset="/docs/images/TOTEM_logo_dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="/docs/images/TOTEM_logo_bright.svg">
  <img alt="TOTEM logo font" src="/docs/images/TOTEM_logo_bright.svg">
</picture>

# ZMK CONFIG для сплит клавиатуры TOTEM

[Здесь](https://github.com/GEIGEIGEIST/totem) вы можете найти файлы аппаратной части и руководство по сборке.\
[Здесь](https://github.com/GEIGEIGEIST/qmk-config-totem) вы можете найти конфиг QMK для TOTEM.

TOTEM — это сплит-клавиатура на 38 клавиш с колоночным смещением, работающая на [ZMK](https://zmk.dev/) или [QMK](https://docs.qmk.fm/). Она предназначена для использования с SEEED XIAO BLE или RP2040.

![TOTEM layout](/docs/images/TOTEM_layout.svg)

## ВАЖНО О ВЕРСИИ ZMK

Текущая ветка `master` использует последнюю поддерживаемую версию ZMK.
Если вам нужна зафиксированная версия ZMK `v0.3`, переключитесь на ветку `v0.3-branch`.

## ВАЖНО О РАСКЛАДКЕ

TOTEM использует компактную матрицу `3x5`, поэтому полноценная русская раскладка обычно не помещается без сильных компромиссов.

Рекомендуется использовать:

- [Universal Layout](https://github.com/braindefender/universal-layout)
- [Wellum](https://github.com/braindefender/wellum)

## Режимы работы

**Без донгла (standalone):**

Одна половинка — главная (по Bluetooth к ПК). Вторая подключается по Bluetooth к ней.
Состоит из двух частей:

- `totem_central_left-xiao_ble`
- `totem_peripheral_right-xiao_ble`

**С донглом (dongle mode):**

Донгл — главный (USB/Bluetooth к ПК). Обе половинки — периферия (Bluetooth к донглу).
Состоит из трей частей:

- `totem_dongle-xiao_ble`, `totem_dongle-nice_nano` или `totem_dongle_prospector-xiao_ble`
- `totem_peripheral_left-xiao_ble`
- `totem_peripheral_right-xiao_ble`

**Варианты донглов:**

- nice!nano v2 / Seeeduino XIAO BLE — просто плата с USB
- Prospector Dongle — экран: слой, батарея, статус, модификаторы; на базе XIAO BLE

## Как использовать

- Сделайте форк этого репозитория
- Выполните `git clone` вашего репозитория, чтобы создать локальную копию на ПК (можно использовать [командную строку](https://www.atlassian.com/git/tutorials) или [GitHub Desktop](https://desktop.github.com/))
- Настройте файл totem.keymap (все keycode можно найти в [документации ZMK](https://zmk.dev/docs/codes/))
- Выполните `git push` в ваш форк
- На странице вашего форка на GitHub перейдите в раздел "Actions" и дождитесь завершения последнего workflow
- Откройте его артефакты и скачайте `firmware.zip`, затем распакуйте архив

### Прошивка

Чтобы перевести половинку или донгл в режим прошивки, нужно нажать кнопку Reset дважды или, если ее нет, замкнуть пины RST и GND дважды.

Стабильная процедура первичной привязки половинок к донглу. Используйте ее, когда половинки еще не привязаны или есть проблемы с подключением:

1. Подключите донгл и прошейте в него файл `settings_reset.uf2`
2. Отключите донгл от провода и отложите в сторону
3. Подключите левую половинку и прошейте в неё сначала `settings_reset.uf2`, затем `peripheral_left.uf2`
4. Подключите правую половинку и прошейте в неё сначала `settings_reset.uf2`, затем `peripheral_right.uf2`
5. Подключите донгл и прошейте в него `dongle.uf2`
6. Включите донгл, затем левую половину, затем правую половину (именно в таком порядке)

Когда нет донгла, левая половина является основной:

1. Подключите правую половинку и прошейте в неё сначала `settings_reset.uf2`, затем `peripheral_right.uf2`
2. Подключите левую половинку и прошейте в неё сначала `settings_reset.uf2`, затем `central_left.uf2`

Если половины уже привязаны к донглу и была изменена только `dongle.uf2`, то достаточно прошить только ее.

# ZMK CONFIG FOR THE TOTEM SPLIT KEYBOARD

[Here](https://github.com/GEIGEIGEIST/totem) you can find the hardware files and build guide.\
[Here](https://github.com/GEIGEIGEIST/qmk-config-totem) you can find the QMK config for the TOTEM.

TOTEM is a 38 key column-staggered split keyboard running [ZMK](https://zmk.dev/) or [QMK](https://docs.qmk.fm/). It's meant to be used with a SEEED XIAO BLE or RP2040.

## ZMK VERSION NOTE

The current `master` branch uses the latest supported ZMK version.
If you need the pinned ZMK `v0.3` version, switch to the `v0.3-branch` branch.

## LAYOUT NOTE

TOTEM uses a compact `3x5` matrix, so a full Russian layout usually does not fit without significant compromises.

Recommended options:

- [Universal Layout](https://github.com/braindefender/universal-layout)
- [Wellum](https://github.com/braindefender/wellum)

## Operating modes

**Without dongle (standalone):**

One half is the main one (Bluetooth to PC). The second half connects to it via Bluetooth.
It consists of two parts:

- `totem_central_left-xiao_ble`
- `totem_peripheral_right-xiao_ble`

**With dongle (dongle mode):**

The dongle is the main device (USB/Bluetooth to PC). Both halves are peripherals (Bluetooth to dongle).
It consists of three parts:

- `totem_dongle-xiao_ble`, `totem_dongle-nice_nano`, or `totem_dongle_prospector-xiao_ble`
- `totem_peripheral_left-xiao_ble`
- `totem_peripheral_right-xiao_ble`

**Dongle options:**

- nice!nano v2 / Seeeduino XIAO BLE: simple USB board
- Prospector Dongle: display for layer, battery, status, and modifiers; based on XIAO BLE

## HOW TO USE

- fork this repo
- `git clone` your repo, to create a local copy on your PC (you can use the [command line](https://www.atlassian.com/git/tutorials) or [GitHub Desktop](https://desktop.github.com/))
- adjust the totem.keymap file (find all the keycodes on [the ZMK docs pages](https://zmk.dev/docs/codes/))
- `git push` your repo to your fork
- on the GitHub page of your fork, open "Actions" and wait for the latest workflow to finish
- open its artifacts, download `firmware.zip`, and unzip it

### Flashing

To put a half or a dongle into flashing mode, press Reset twice or, if there is no button, short RST and GND twice.

Stable first-time pairing procedure for halves with the dongle. Use it when halves are not paired yet or when there are connection issues:

1. Connect the dongle and flash `settings_reset.uf2`.
2. Unplug the dongle and set it aside.
3. Connect the left half and flash `settings_reset.uf2` first, then `peripheral_left.uf2`.
4. Connect the right half and flash `settings_reset.uf2` first, then `peripheral_right.uf2`.
5. Connect the dongle and flash `dongle.uf2`.
6. Power on the dongle, then the left half, then the right half (in this exact order).

When there is no dongle, the left half is the main one:

1. Connect the right half and flash `settings_reset.uf2` first, then `peripheral_right.uf2`.
2. Connect the left half and flash `settings_reset.uf2` first, then `central_left.uf2`.

If halves are already paired to the dongle and only `dongle.uf2` changed, flashing only the dongle is enough.
