---
title: Пайка хардмода в Old 3DS #
permalink: making-hardmod-old3ds.html
---
{% include toc title="Разделы" %}

{% include inc/hardmod.txt 

	console="Old 3DS" 

	screwdriver="" 
%}

### Часть II - Разбираем консоль

1. Отключите все периферийные устройства (зарядку, SD-карту, прочее) от консоли и положите их в безопасное место.
1. Переверните консоль и открутите два винта, что крепят заднюю крышку. 

	**Примечание:** Винты не откручиваются полностью, они остаются прикрепленными к задней крышке. Открепите заднюю крышку, потянув её наверх.
	{: .notice--info}

    ![]({{ base_path }}/3ds/images/ifixit/3ds/1.png){:target='_blank'}
	{: .text-center}
    {: .notice--info}
	
1. После этого вам необходимо вытащить батарею из консоли

    ![]({{ base_path }}/3ds/images/ifixit/3ds/2.png){:target='_blank'}
	{: .text-center}
    {: .notice--info}

1. Теперь открутите винты, которые удерживают заднюю панель и положите их в безопасное место.

    ![]({{ base_path }}/3ds/images/ifixit/3ds/3.png){:target='_blank'}
	{: .text-center}
    {: .notice--info}

1. Когда вы открутите все винты и начнете открывать крышку, вы увидите печатную плату (PCB), **НЕ ПРИМЕНЯЙТЕ СИЛУ ДЛЯ ОТКРЫТИЯ ПАНЕЛИ**. Под крышкой находятся два шлейфа от боковых кнопок. Аккуратно отсоедините их от материнской платы и продолжайте разбор.

    ![]({{ base_path }}/3ds/images/ifixit/3ds/4.png){:target='_blank'}
	{: .text-center}
    {: .notice--info}
	
1. Аккуратно отсоедините WiFi- и ИК-модуль. 

    ![]({{ base_path }}/3ds/images/ifixit/3ds/5.png){:target='_blank'}
	{: .text-center}
    {: .notice--info}
	
1. Открутите винты, удерживающие аналоговый джойстик и плату картридера. Осторожно открепите защелку, которая удерживает шлейф аналога и аккуратно отложите его в сторону. Будьте предельно осторожны - защелки очень хрупкие! 
Отогните кардридер. Нет нужды его снимать полностью. Достаточно просто приподнять его, открыв как крышку (одной частью он накрепко примонтажен к плате). При желании можно снять его совсем, отсоединив его от металлической пластины, к которой он приклеен двусторонним скотчем.

    ![]({{ base_path }}/3ds/images/ifixit/3ds/6.png){:target='_blank'}
	{: .text-center}
    {: .notice--info}

1. Открутите оставшиеся винты и аккуратно отстегните отмеченные синим защелки и уберите шлейфы.

    ![]({{ base_path }}/3ds/images/ifixit/3ds/7.png){:target='_blank'}
	{: .text-center}
    {: .notice--info}
	
1. Осоторжно переверните плату.

    ![]({{ base_path }}/3ds/images/ifixit/3ds/8.png){:target='_blank'}
	{: .text-center}
    {: .notice--info}
	
### Часть III - Впаиваем провода переходника в приставку 
	
{% capture notice-2 %}
Вы будете паять близко к чипу NAND. Припаивать мы будем 4 основных контакта. **DAT0 (Data Zero)**, **CMD** и **CLK (CLOCK)** находятся на нижней части платы. **GND (Ground или заземление)**, мы будем припаивать к металлическому корпусу слота для картриджей или SD-карты, который находится на верхней части материнской платы. Другие DAT-контакты (DAT1, DAT2 и DAT3) вам не потребуются, и в этом гайде вы их не найдете, однако, вы можете припаять провода и к ним, если вам нужна более высокая скорость передачи для записи и чтения NAND'а. Это опциональная операция и в этом гайде не используется, поскольку чип и так дампится достаточно быстро. Выигрыш в пару минут не стоит времени, затраченного на пайку дополнительных контактов.

![]({{ base_path }}/3ds/images/ifixit/3ds/o3ds_tp.png){:target='_blank'}
{: .text-center}

{% endcapture %}

<div class="notice--info">{{ notice-2 | markdownify }}</div>

1. Нанесите флюс на кончик провода и используйте его как кисточку, нанеся флюс на контакты, к которым необходимо припаять.
1. Начните припаивать 4 провода к каждому из контактов: DAT0, CMD и CLK, а также к GND. Убедитесь, что вы припаяли всё чисто, аккуратно и к нужным точкам.

	Убедитесь, что провода, выходящие из SD-адаптера припаяны к соответствующим точкам, иначе ничего работать не будет. Для пущей надежности прозвоните их мультиметром, или любым другим прибором.
	{: .notice--warning}

1. Соберите вашу приставку. Можете не закручивать болты, либо закрутить всего несколько. Аккуратно верните все шлейфы на место. Защелки очень хрупкие, поэтому действуйте пинцетом и будьте предельно осторожны! Можете пока не подключать аналоговый джойстик и камеру. 
1. Вставьте батарею в приставку и включите ее, чтобы удостоверится в её работоспособности. На этом этапе приставка все ещё должна работать в обычном режиме.

	Могут возникнуть следующие проблемы: 
	+ **При включении приставки загорается синий диод, раздается щелчок из динамика, затем приставка выключается** - неправильно подключены шлейфы экранов (или одного из них), переподключите их и попробуйте снова
	+ **При включении на экране приставки оба экрана светятся синим** - где-то замыкают провода; проверяйте пайку. 
	+ **Курсор быстро перемещается по экрану ВПРАВО** - это из-за отключенного аналога; игнорируйте

{% include inc/read_nand.txt content="2DS" %}

___

## [Установка boot9strap (Hardmod)](installing-boot9strap-hardmod)
{: .notice--success}