---
title: Смена региона
permalink: /region-changing.html
author_profile: true
---
{% include toc title="Разделы" %}

Этот дополнительный раздел рассказывает о смене региона на вашей приставке с CFW, установленной в SysNAND. Это делается путем установки образа 9.2.0 CTRTransfer того региона, на который вы хотите перейти.

Смена региона абсолютно не обязательна с тех пор, как в Luma3DS поддерживает запуск игр других регионов и индивидуальную [эмуляцию региона для отдельных игр](lumalocales){:target="_blank"}.

Этот процесс отсоединит NNID от приставки, поскольку он больше не будет совместим с вашей консолью. NNID привязан к конкретному устройству и к его региону, поэтому перенос NNID между приставками с разными регионами невозможен без применения [крайне сложных операций](https://gist.githubusercontent.com/yifanlu/e80db121d38aceb8cca0e03cefd5853b/raw/3c4dd89869156ca0f945a2791e699acfdb32b510/gistfile1.txt){:target="_blank"}.
{: .notice--warning}

Практика показывает, что eShop почти наверняка перестанет работать, вне зависимости от типа вашей консоли. Все же, наибольший шанс есть у Old3DS и у New3DS, которая ни разу не была привязана к eShop.
{: .notice--warning}

Смена региона при помощи CTRTransfer (что используется в этом методе) по какой-то причине ломает reboot-патч. Причина этого неизвестна, но из-за этого владельцы Old 3DS теряют возможность играть в игры, требующие режим расширенной оперативной памяти (например, Monster Hunter, Super Smash Bros, и Pokémon Sun / Moon) до тех пор, пока не выполнят форматирование устройства (подробности в конце этой страницы).

Для продолжения, у вас уже ДОЛЖНА быть установлена Luma3DS и boot9strap.

Не обращайте внимание на версию установленного системного ПО. Всё будет хорошо, даже если версия вашего ПО выше, или ниже, чем версия ПО в образе CTRTransfer.
{: .notice--danger}

## Что понадобится

* Свежая версия [GodMode9](https://github.com/d0k3/GodMode9/releases/latest){:target="_blank"}
* Свежая версия [FBI](https://github.com/Steveice10/FBI/releases/latest){:target="_blank"} (`.3dsx-файл`)
* CTRTransfer-образ 11.5.0 для вашего устройства и региона, на который вы хотите перейти:
  +    <i class="fa fa-magnet" aria-hidden="true" title="Это magnet-ссылка. Воспользуйтесь торрент-клиентом, чтобы скачать этот файл."></i> - [New 3DS or 2DS - 11.5.0 - EUR - CTRTransfer](magnet:?xt=urn:btih:465f1048f81e8e5c651ce2a4d9df48fec88d1099&dn=11.5.0-38E_ctrtransfer_n3ds.zip&tr=udp%3A%2F%2F9.rarbg.to%3A2710%2Fannounce&tr=udp%3A%2F%2Fbt.xxx-tracker.com%3A2710%2Fannounce&tr=udp%3A%2F%2Fexodus.desync.com%3A6969%2Fannounce&tr=udp%3A%2F%2Fmgtracker.org%3A6969%2Fannounce&tr=udp%3A%2F%2Fopen.demonii.si%3A1337%2Fannounce&tr=udp%3A%2F%2Fpublic.popcorn-tracker.org%3A6969%2Fannounce&tr=udp%3A%2F%2Fthetracker.org%3A80%2Fannounce&tr=udp%3A%2F%2Ftracker.coppersurfer.tk%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.cypherpunks.ru%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.ds.is%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.internetwarriors.net%3A1337%2Fannounce&tr=udp%3A%2F%2Ftracker.mg64.net%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.open-internet.nl%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.opentrackr.org%3A1337%2Fannounce&tr=udp%3A%2F%2Ftracker.port443.xyz%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.qt.is%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.tiny-vps.com%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.torrent.eu.org%3A451%2Fannounce&tr=udp%3A%2F%2Ftracker.vanitycore.co%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker-2.msm8916.com%3A6969%2Fannounce)    
  +    <i class="fa fa-magnet" aria-hidden="true" title="Это magnet-ссылка. Воспользуйтесь торрент-клиентом, чтобы скачать этот файл."></i> - [New 3DS or 2DS - 11.5.0 - JPN - CTRTransfer](magnet:?xt=urn:btih:70f641c9f2a4933a07fac49eb7ad19451c7c8c96&dn=11.5.0-38J_ctrtransfer_n3ds.zip&tr=udp%3A%2F%2F9.rarbg.to%3A2710%2Fannounce&tr=udp%3A%2F%2Fbt.xxx-tracker.com%3A2710%2Fannounce&tr=udp%3A%2F%2Fexodus.desync.com%3A6969%2Fannounce&tr=udp%3A%2F%2Fmgtracker.org%3A6969%2Fannounce&tr=udp%3A%2F%2Fopen.demonii.si%3A1337%2Fannounce&tr=udp%3A%2F%2Fpublic.popcorn-tracker.org%3A6969%2Fannounce&tr=udp%3A%2F%2Fthetracker.org%3A80%2Fannounce&tr=udp%3A%2F%2Ftracker.coppersurfer.tk%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.cypherpunks.ru%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.ds.is%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.internetwarriors.net%3A1337%2Fannounce&tr=udp%3A%2F%2Ftracker.mg64.net%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.open-internet.nl%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.opentrackr.org%3A1337%2Fannounce&tr=udp%3A%2F%2Ftracker.port443.xyz%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.qt.is%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.tiny-vps.com%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.torrent.eu.org%3A451%2Fannounce&tr=udp%3A%2F%2Ftracker.vanitycore.co%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker-2.msm8916.com%3A6969%2Fannounce)    
  +    <i class="fa fa-magnet" aria-hidden="true" title="Это magnet-ссылка. Воспользуйтесь торрент-клиентом, чтобы скачать этот файл."></i> - [New 3DS or 2DS - 11.5.0 - KOR - CTRTransfer](magnet:?xt=urn:btih:c9e4de20d30b80032a5dd6f675fecb6d748f71b1&dn=11.5.0-34K_ctrtransfer_n3ds.zip&tr=udp%3A%2F%2F9.rarbg.to%3A2710%2Fannounce&tr=udp%3A%2F%2Fbt.xxx-tracker.com%3A2710%2Fannounce&tr=udp%3A%2F%2Fexodus.desync.com%3A6969%2Fannounce&tr=udp%3A%2F%2Fmgtracker.org%3A6969%2Fannounce&tr=udp%3A%2F%2Fopen.demonii.si%3A1337%2Fannounce&tr=udp%3A%2F%2Fpublic.popcorn-tracker.org%3A6969%2Fannounce&tr=udp%3A%2F%2Fthetracker.org%3A80%2Fannounce&tr=udp%3A%2F%2Ftracker.coppersurfer.tk%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.cypherpunks.ru%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.ds.is%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.internetwarriors.net%3A1337%2Fannounce&tr=udp%3A%2F%2Ftracker.mg64.net%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.open-internet.nl%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.opentrackr.org%3A1337%2Fannounce&tr=udp%3A%2F%2Ftracker.port443.xyz%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.qt.is%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.tiny-vps.com%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.torrent.eu.org%3A451%2Fannounce&tr=udp%3A%2F%2Ftracker.vanitycore.co%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker-2.msm8916.com%3A6969%2Fannounce)    
  +    <i class="fa fa-magnet" aria-hidden="true" title="Это magnet-ссылка. Воспользуйтесь торрент-клиентом, чтобы скачать этот файл."></i> - [New 3DS or 2DS - 11.5.0 - USA - CTRTransfer](magnet:?xt=urn:btih:2b0a71a2523328e447938fea7b4c02ebe0b72705&dn=11.5.0-38U_ctrtransfer_n3ds.zip&tr=udp%3A%2F%2F9.rarbg.to%3A2710%2Fannounce&tr=udp%3A%2F%2Fbt.xxx-tracker.com%3A2710%2Fannounce&tr=udp%3A%2F%2Fexodus.desync.com%3A6969%2Fannounce&tr=udp%3A%2F%2Fmgtracker.org%3A6969%2Fannounce&tr=udp%3A%2F%2Fopen.demonii.si%3A1337%2Fannounce&tr=udp%3A%2F%2Fpublic.popcorn-tracker.org%3A6969%2Fannounce&tr=udp%3A%2F%2Fthetracker.org%3A80%2Fannounce&tr=udp%3A%2F%2Ftracker.coppersurfer.tk%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.cypherpunks.ru%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.ds.is%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.internetwarriors.net%3A1337%2Fannounce&tr=udp%3A%2F%2Ftracker.mg64.net%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.open-internet.nl%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.opentrackr.org%3A1337%2Fannounce&tr=udp%3A%2F%2Ftracker.port443.xyz%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.qt.is%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.tiny-vps.com%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.torrent.eu.org%3A451%2Fannounce&tr=udp%3A%2F%2Ftracker.vanitycore.co%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker-2.msm8916.com%3A6969%2Fannounce)    
~
  +    <i class="fa fa-magnet" aria-hidden="true" title="Это magnet-ссылка. Воспользуйтесь торрент-клиентом, чтобы скачать этот файл."></i> - [Old 3DS or 2DS - 11.5.0 - EUR - CTRTransfer](magnet:?xt=urn:btih:df0836a731778ab6ffe9a8c658400c782f0225cd&dn=11.5.0-38E_ctrtransfer_o3ds.zip&tr=udp%3A%2F%2F9.rarbg.to%3A2710%2Fannounce&tr=udp%3A%2F%2Fbt.xxx-tracker.com%3A2710%2Fannounce&tr=udp%3A%2F%2Fexodus.desync.com%3A6969%2Fannounce&tr=udp%3A%2F%2Fmgtracker.org%3A6969%2Fannounce&tr=udp%3A%2F%2Fopen.demonii.si%3A1337%2Fannounce&tr=udp%3A%2F%2Fpublic.popcorn-tracker.org%3A6969%2Fannounce&tr=udp%3A%2F%2Fthetracker.org%3A80%2Fannounce&tr=udp%3A%2F%2Ftracker.coppersurfer.tk%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.cypherpunks.ru%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.ds.is%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.internetwarriors.net%3A1337%2Fannounce&tr=udp%3A%2F%2Ftracker.mg64.net%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.open-internet.nl%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.opentrackr.org%3A1337%2Fannounce&tr=udp%3A%2F%2Ftracker.port443.xyz%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.qt.is%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.tiny-vps.com%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.torrent.eu.org%3A451%2Fannounce&tr=udp%3A%2F%2Ftracker.vanitycore.co%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker-2.msm8916.com%3A6969%2Fannounce)     
  +    <i class="fa fa-magnet" aria-hidden="true" title="Это magnet-ссылка. Воспользуйтесь торрент-клиентом, чтобы скачать этот файл."></i> - [Old 3DS or 2DS - 11.5.0 - JPN - CTRTransfer](magnet:?xt=urn:btih:d8913b4c0da224e8852fa2f685c41ddbce5310bc&dn=11.5.0-38J_ctrtransfer_o3ds.zip&tr=udp%3A%2F%2F9.rarbg.to%3A2710%2Fannounce&tr=udp%3A%2F%2Fbt.xxx-tracker.com%3A2710%2Fannounce&tr=udp%3A%2F%2Fexodus.desync.com%3A6969%2Fannounce&tr=udp%3A%2F%2Fmgtracker.org%3A6969%2Fannounce&tr=udp%3A%2F%2Fopen.demonii.si%3A1337%2Fannounce&tr=udp%3A%2F%2Fpublic.popcorn-tracker.org%3A6969%2Fannounce&tr=udp%3A%2F%2Fthetracker.org%3A80%2Fannounce&tr=udp%3A%2F%2Ftracker.coppersurfer.tk%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.cypherpunks.ru%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.ds.is%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.internetwarriors.net%3A1337%2Fannounce&tr=udp%3A%2F%2Ftracker.mg64.net%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.open-internet.nl%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.opentrackr.org%3A1337%2Fannounce&tr=udp%3A%2F%2Ftracker.port443.xyz%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.qt.is%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.tiny-vps.com%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.torrent.eu.org%3A451%2Fannounce&tr=udp%3A%2F%2Ftracker.vanitycore.co%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker-2.msm8916.com%3A6969%2Fannounce)     
  +    <i class="fa fa-magnet" aria-hidden="true" title="Это magnet-ссылка. Воспользуйтесь торрент-клиентом, чтобы скачать этот файл."></i> - [Old 3DS or 2DS - 11.5.0 - USA - CTRTransfer](magnet:?xt=urn:btih:2708089605ca47387fa64e996a699eedd18031e8&dn=11.5.0-38U_ctrtransfer_o3ds.zip&tr=udp%3A%2F%2F9.rarbg.to%3A2710%2Fannounce&tr=udp%3A%2F%2Fbt.xxx-tracker.com%3A2710%2Fannounce&tr=udp%3A%2F%2Fexodus.desync.com%3A6969%2Fannounce&tr=udp%3A%2F%2Fmgtracker.org%3A6969%2Fannounce&tr=udp%3A%2F%2Fopen.demonii.si%3A1337%2Fannounce&tr=udp%3A%2F%2Fpublic.popcorn-tracker.org%3A6969%2Fannounce&tr=udp%3A%2F%2Fthetracker.org%3A80%2Fannounce&tr=udp%3A%2F%2Ftracker.coppersurfer.tk%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.cypherpunks.ru%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.ds.is%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.internetwarriors.net%3A1337%2Fannounce&tr=udp%3A%2F%2Ftracker.mg64.net%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.open-internet.nl%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.opentrackr.org%3A1337%2Fannounce&tr=udp%3A%2F%2Ftracker.port443.xyz%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.qt.is%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.tiny-vps.com%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.torrent.eu.org%3A451%2Fannounce&tr=udp%3A%2F%2Ftracker.vanitycore.co%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker-2.msm8916.com%3A6969%2Fannounce)    
 
## Инструкция

### Часть I - Подготовительные работы

1. Выключите консоль
1. Вставьте SD-карту в компьютер
1. Создайте папку `cias` в корне SD-карты
1. Создайте папку `3ds` в корне SD-карты
1. Скопируйте `GodMode9.firm` из `.zip-архива` GodMode9 в папку `/luma/payloads/` на SD-карте
1. Скопируйте папку `gm9` из `.zip-архива` `GodMode9` в корень SD-карты
1. Скопируйте файл `.bin` из `.zip-архива` с CTRTransfer-образом 11.5.0 в папку `/gm9/in` на SD-карте
1. Скопируйте `FBI.3dsx` в папку `/3ds/` в корне SD-карты
1. Вставьте SD-карту обратно в консоль

### Часть II - CTRTransfer

{% include inc/launch_godmode9.txt console="" %}
1. Выберите "**Scripts...**"
1. Выберите "**GM9Megascript**"
1. Выберите "**Scripts from Plailect’s Guide**"
1. Выберите "**CTRTransfer Ticket Copy**"
1. Нажмите {% include inc/btn.txt btn="A" %}, чтобы начать копирование тикетов
1. Нажмите {% include inc/btn.txt btn="A" %}, чтобы продолжить
1. Нажимайте {% include inc/btn.txt btn="B" %}, пока не вернётесь в главное меню скрипта
1. Выберите "**CTRNAND trnsfer...**"
1. Выберите из списка на нижнем экране образ, подготовленный для переноса, нажав кнопку {% include inc/btn.txt btn="A" %}
1. Нажмите {% include inc/btn.txt btn="A" %}
1. Нажмите {% include inc/btn.txt btn="A" %}, чтобы разрешить запись в SysNAND (lvl2) и введите указанную комбинацию кнопок
	+ Этот процесс займет некоторое время
1. Если появится запрос, выберите "**Transfer to SysNAND**"
	+ Этот запрос отображается только если у вас есть EmuNAND
1. По завершению процесса, нажмите {% include inc/btn.txt btn="A" %}
1. Нажимайте {% include inc/btn.txt btn="B" %}, пока не вернётесь в главное меню скрипта
1. Выберите "**Exit**"
1. Нажмите {% include inc/btn.txt btn="START" %} для перезагрузки
1. Обновите прошивку консоли, зайдя в Системные настройки (System Settings), затем "**Прочие настройки**" (Other Settings), затем листайте ВПРАВО до конца и выберите пункт "**Обновление**" (System Update)
  + Обновление консоли с установленным b9s + Luma (установлено у вас) безопасно
  + При появлении ошибки, поставьте в настройках подключения, в настройках DNS "Получать DNS автоматически" в положение "Да"

### Часть III - Запуск Homebrew Launcher

{% include /inc/hbl.txt content="Homebrew Launcher" %}

### Часть IV - Переустановка тикетов

Если скрипт, запускавшийся выше, не нашел пользовательских тикетов на консоли, и предложил вам пропустить эту часть - так и поступите
{: .notice--info}

1. Выберите FBI в списке Homebrew и запустите его
1. Перейдите в `SD` -> `cias`
1. Нажмите {% include inc/btn.txt btn="B" %}, чтобы вернуться в папку "SD"
1. Выберите "**gm9**"
1. Выберите "**out**"
1. Выберите "**ctrtransfer_tickets**"
1. Выполните шаги ниже либо для папки `eshop` либо для папки `unknown`, или для обоих
  + Перейдите в папку
  + Выберите "**\<current directory>**"
  + Выберите "**Install and delete all tickets**"
  + Ожидайте. Может показаться, что приставка зависла, просто дайте ей время.
  + Нажмите {% include inc/btn.txt btn="A" %} для подтверждения
1. Нажмите {% include inc/btn.txt btn="HOME" %} для выхода из FBI

Если после восстановления тикетов игры так и не появились, восстановите их с помощью программы [faketik](https://github.com/ihaveamac/faketik/releases/latest){:target="_blank"}. 
1. Поместите программу в папку `3ds`
1. Запустите [Homebrew Launcher](launch-hbl){:target="_blank"}
1. Запустите faketik 
	* Интернет на приставке должен быть включен 
	
### Часть V - Региональные настройки

1. Откройте **Системные настройки (System settings)**
1. Перейдите в "**Прочие настройки**" (Other Settings), затем "**Профиль**" (Profile), затем "**Настройки региона**" (Region Settings)
1. Выберите страну из вашего нового региона
1. При появлении запроса о штате указывать его не нужно

### Часть VI - Обновление системы

{% include /inc/sys_update.txt %}

___

{% capture notice-10 %}

Для Old 3DS и 2DS может потребоваться форматирование (используя TinyFormat или Системные настройки), иначе игры требующие режима расширенной памяти могут не заработать (Monster Hunter, Super Smash Bros, Pokemon Sun/Moon, и т. п.).

* [Если перестали запускать игры от DS](troubleshooting#dsids-%D0%B8%D0%B3%D1%80%D1%8B-%D0%BD%D0%B5-%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0%D1%8E%D1%82-%D0%BD%D0%B0-%D0%BF%D1%80%D0%BE%D1%88%D0%B8%D1%82%D0%BE%D0%B9-%D0%BF%D1%80%D0%B8%D1%81%D1%82%D0%B0%D0%B2%D0%BA%D0%B5){:target="_blank"}

{% endcapture %}

<div class="notice--info">{{ notice-10 | markdownify }}</div>