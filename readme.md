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

## КАК ИСПОЛЬЗОВАТЬ

- сделайте форк этого репозитория
- выполните `git clone` вашего репозитория, чтобы создать локальную копию на ПК (можно использовать [командную строку](https://www.atlassian.com/git/tutorials) или [GitHub Desktop](https://desktop.github.com/))
- настройте файл totem.keymap (все keycode можно найти в [документации ZMK](https://zmk.dev/docs/codes/))
- выполните `git push` в ваш форк
- на странице вашего форка на GitHub перейдите в раздел "Actions"
- прокрутите вниз и распакуйте архив `firmware.zip`, содержащий последнюю прошивку
- подключите левую половину TOTEM к ПК и дважды нажмите reset
- клавиатура должна появиться как накопитель
- перетащите файл `totem_left-xiao_ble__zmk-zmk.uf2` из архива на накопитель
- повторите процесс для правой половины и файла `totem_right-xiao_ble__zmk-zmk.uf2`.

# ZMK CONFIG FOR THE TOTEM SPLIT KEYBOARD

[Here](https://github.com/GEIGEIGEIST/totem) you can find the hardware files and build guide.\
[Here](https://github.com/GEIGEIGEIST/qmk-config-totem) you can find the QMK config for the TOTEM.

TOTEM is a 38 key column-staggered split keyboard running [ZMK](https://zmk.dev/) or [QMK](https://docs.qmk.fm/). It's meant to be used with a SEEED XIAO BLE or RP2040.

## ZMK VERSION NOTE

The current `master` branch uses the latest supported ZMK version.
If you need the pinned ZMK `v0.3` version, switch to the `v0.3-branch` branch.

## HOW TO USE

- fork this repo
- `git clone` your repo, to create a local copy on your PC (you can use the [command line](https://www.atlassian.com/git/tutorials) or [github desktop](https://desktop.github.com/))
- adjust the totem.keymap file (find all the keycodes on [the zmk docs pages](https://zmk.dev/docs/codes/))
- `git push` your repo to your fork
- on the GitHub page of your fork navigate to "Actions"
- scroll down and unzip the `firmware.zip` archive that contains the latest firmware
- connect the left half of the TOTEM to your PC, press reset twice
- the keyboard should now appear as a mass storage device
- drag'n'drop the `totem_left-xiao_ble__zmk-zmk.uf2` file from the archive onto the storage device
- repeat this process with the right half and the `totem_right-xiao_ble__zmk-zmk.uf2` file.
