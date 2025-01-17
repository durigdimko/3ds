---
title: Пайка хардмода в New 3DS XL #
permalink: making-hardmod-new3dsxl.html
---
{% include toc title="Разделы" %}

{% include inc/hardmod.txt 

	console="New 3DS XL" 

	screwdriver="" 
%}

### Часть II - Разбираем консоль

1. Отключите все периферийные устройства (зарядку, SD-карту, прочее) от консоли и положите их в безопасное место.
1. Переверните консоль и открутите два винта, что крепят заднюю крышку. 

	**Примечание:** Винты не откручиваются полностью, они остаются прикрепленными к задней крышке. Открепите заднюю крышку, потянув её наверх.
	{: .notice--info}

    ![]({{ base_path }}/3ds/images/ifixit/new3dsxl/1.png){:target='_blank'}
	{: .text-center}
    {: .notice--info}
	
1. После этого вам необходимо вытащить батарею из консоли и аккуратно убрать резиновые заглушки, отмеченные зеленым (я использую для этого пинцет, либо острую иглу). Под ними еще два винта. Открутите все винты и положите их в надежное место.

    ![]({{ base_path }}/3ds/images/ifixit/new3dsxl/2.png){:target='_blank'}
	{: .text-center}
    {: .notice--info}

1. Когда вы открутите все винты и начнете открывать крышку, вы увидите печатную плату (PCB), **НЕ ПРИМЕНЯЙТЕ СИЛУ ДЛЯ ОТКРЫТИЯ ПАНЕЛИ**. Под крышкой находятся два шлейфа. 

    ![]({{ base_path }}/3ds/images/ifixit/new3dsxl/3.png){:target='_blank'}
	{: .text-center}
    {: .notice--info}

1. Осторожно отсоедините отмеченные шлейфы (9 штук). Особое внимание обратите на те, что отмечены зеленым - **защелки такой конструкции не нужно открывать!!** Просто вытащите шлейф пинцетом прямо из защелки. Обратно он вставляется сходным образом - просто вставьте и затолкните до упора. Шлейф отмеченный синим - наиболее уязвим в этой материнской плате. В нем находится 50 контактных ножек, которые очень легко повредить. Будьте внимательны и осторожны! После всех манипуляций, переверните плату.

    ![]({{ base_path }}/3ds/images/ifixit/new3dsxl/4.png){:target='_blank'}
	{: .text-center}
    {: .notice--info}
	
### Часть III - Впаиваем провода переходника в приставку 
	
{% capture notice-2 %}
Вы будете паять близко к чипу NAND. Припаивать мы будем 4 основных контакта. **DAT0 (Data Zero)** и **CMD** находятся на нижней части платы. **GND (Ground или заземление)**, мы будем припаивать к металлическому корпусу слота для картриджей или SD-карты, который находится на верхней части материнской платы. **CLK (CLOCK)** находится там же, рядом с широким шлейфом. 

![]({{ base_path }}/3ds/images/ifixit/new3dsxl/new3dsxl_tp_1.png){:target='_blank'}
{: .text-center}
![]({{ base_path }}/3ds/images/ifixit/new3dsxl/new3dsxl_tp_2.png){:target='_blank'}
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