---
lab:
    title: 'Изучение групп безопасности сетей Azure (NSG)'
    module: 'Модуль 3. Урок 1. Описание возможностей решений безопасности Майкрософт. Описание основных возможностей обеспечения безопасности в Azure.'
---


# Практическое занятие. Изучение групп безопасности сетей Azure (NSG).

## Сценарий практического занятия
В рамках этого практического занятия вы изучите функцию групп безопасности сети в Azure.  Это следует сделать путем создания виртуальной машины (ВМ) без группы безопасности сети (NSG).  Без наличия какой-либо группы NSG для фильтрации трафика все порты ВМ подвержены воздействию из Интернета.  Затем вы создадите группу NSG и назначите этой группе интерфейс ВМ.  После настройки вы проверите подключение к ВМ с помощью правил NSG по умолчанию, а также правил, которые вы создадите самостоятельно.
  

**Примерное время**: 15–20 мин.

#### Задача 1.  В рамках этой задачи вы создадите виртуальную машину Windows 10.    
1.	Откройте Microsoft Edge.  В адресной строке введите **portal.azure.com**.

1. Войдите под своими учетными данными администратора.
    1. В окне входа введите **admin@WWLxZZZZZZ.onmicrosoft.com** (где ZZZZZZ — уникальный идентификатор клиента, предоставленный поставщиком размещения практических занятий), затем нажмите кнопку **Далее**.

    1. Введите пароль администратора, который должен быть предоставлен поставщиком размещения практических занятий. Выберите **Вход**.
    1. При появлении предложения не выходить из системы выберите **Да**.
1. В левом верхнем углу экрана рядом с надписью Microsoft Azure выберите значок отображения меню портала (три горизонтальных линии, которые также называются значком гамбургера), затем выберите **Все службы**.  
1. В разделе «Подборка» главного окна выберите «Виртуальные машины».  Если здесь не указаны виртуальные машины, введите эту строку в поле поиска и выберите соответствующий пункт в результатах поиска.
1. В левой верхней части страницы выберите **+Создать**, затем выберите **+Виртуальная машина**.
1. На вкладке «Основные» заполните приведенные ниже сведения (если что-то не указано, оставьте настройки по умолчанию):
    1. Подписка: проверьте, что по умолчанию указано «Azure Pass – Спонсорские отношения».

    1. Группа ресурсов:  выберите **Создать**, затем в поле «Имя» ведите **LabsSC900-RG** и нажмите кнопку **OK**.
    1. Имя виртуальной машины:  введите **SC900-WinVM**.
    1. Образ:  в раскрывающемся списке выберите **Windows 10 Pro, версия 20H2 — пок. 1**.
    1. Размер:  выберите в раскрывающемся списке **видеть все размеры**, затем выберите **B2s** и нажмите **Выбрать** в нижней части страницы.
    1. Имя пользователя:  введите **AzureUser**.
    1. Пароль:  введите **SC900AzureLabs**.
    1. Общедоступные входящие порты:  выберите **Нет**.
    1. Лицензирование:  установите флажок **Подтверждаю, что имею действующую лицензию Windows 10 c правами размещения на нескольких клиентах**.
    1. Выберите **Далее: диски**. 
1. Откроется вкладка «Диски» конфигурации ВМ.  Оставьте значение по умолчанию для всех настроек и выберите **Далее: сеть >.**
1. Откроется вкладка «Сеть» конфигурации ВМ.  Заполните приведенные ниже сведения (если что-то не указано, оставьте настройки по умолчанию):
    1. Группа безопасности сети сетевого адаптера:  выберите **Нет**.

    1. Выберите **Далее:  Управление >**.
1. Откроется вкладка «Управление» для конфигурации ВМ.  Оставьте значение по умолчанию для всех настроек и выберите **Далее: Дополнительно>**.
1. Откроется вкладка «Дополнительно» для конфигурации ВМ.  Оставьте значение по умолчанию для всех настроек и выберите **Далее: Теги >**.
1. Откроется вкладка «Теги» для конфигурации ВМ.  Оставьте значение по умолчанию для всех настроек и выберите **Далее: Проверить и создать>**.
1. Обзор конфигурации для вашей ВМ.  Следует обратить внимание на несколько аспектов. Эта ВМ имеет общедоступный IP-адрес и не имеет группы безопасности сети, назначенной для сетевого адаптера.  С точки зрения безопасности эта ВМ подвержена угрозам.  Мы рассмотрим этот аспект в последующей задаче. Нажмите кнопку "Создать".  На развертывание ВМ может уйти несколько минут.
1. Обратите внимание на имя сетевого интерфейса **sc900-winvmXXX** (XXX относится непосредственно к сетевому интерфейсу вашей ВМ).
1. По завершении развертывания ВМ выберите **Перейти к ресурсу**.
1. Вы попадете на страницу SC900-WinVM.  Обратите внимание на общедоступный IP-адрес. 
1. В верхней части страницы выберите **Подключить**, затем в раскрывающемся списке выберите **RDP**.
1. Убедитесь, что задан общедоступный IP-адрес, оставьте номер порта по умолчанию и выберите **Загрузить DRP-файл**. 
1. Откройте загруженный файл и выберите **Подключить**. 
1. Вам будет предложено ввести учетные данные.  В качестве имени пользователя введите **AzureUser**.  В качестве пароля введите **SC900AzureLabs**. 
1. Открывается окно подключения к удаленному рабочему столу с сообщением, что идентификация удаленного компьютера не может быть проверена.  Продолжить в любом случае?  Выберите **Да**.
1. Теперь вы подключены к только что созданной ВМ Windows. Следуйте запросам для завершения настройки Windows. Несмотря на то, что вы подключены к ВМ через часто используемый порт RDP, на этой ВМ открыты все порты и трафик никак не фильтруется. 
1. Закройте подключение к удаленному рабочему столу, выбрав **X** в центре верхней части страницы, где отображается IP-адрес.  Появляется всплывающее окно с сообщением об отключении удаленного сеанса. Нажмите кнопку **ОК**.
1. Теперь вы можете вернуться на страницу SC900-WinVM портала Azure.  Оставьте эту вкладку браузера открытой для следующей задачи.

#### Задача 2.  Создайте группу безопасности сети и назначьте этой группе сетевой интерфейс ВМ.

1. Откройте вкладку «SC900-WinVM – Microsoft Azure» в вашем браузере.

1. В левом верхнем углу страницы рядом с надписью Microsoft Azure выберите значок меню «Показать портал» (три горизонтальных линии, которые также называются значком гамбургера), затем выберите **Все службы**.
1. В поле «Фильтровать службы» рядом с надписью «Все службы» введите **Группы безопасности сети**, затем в результатах выберите **Группы безопасности сети** (не выбирайте классические группы безопасности сети).
1. В верхней части страницы групп безопасности сети выберите **+ Создать**.
1. На вкладке «Основные» страницы «Создание группы безопасности сети» укажите следующие параметры.
    1. Подписка:  Azure Pass – Спонсорское предложение

    1. Группа ресурсов:  **LabsSC900**
    1. Имя:  **NSG-SC900**
    1. Регион:  оставьте значение по умолчанию **(США) Восток США**
    1. Выберите **Проверить и создать**, затем выберите **Создать**.
1. По завершении развертывания выберите **Перейти к ресурсу**.
1. Обратите внимание на правила входящего и исходящего трафика по умолчанию в NSG.  Несмотря на то, что группа NSG уже создана и имеются правила по умолчанию для фильтрации трафика, с этой NSG нет связанных интерфейсов, поэтому ВМ остается уязвимой, так как ко всем ее портам имеется выход из общедоступного Интернета.
1. В разделе «Параметры» на панели навигации в левой части страницы NSG-SC900 выберите **Сетевые интерфейсы**.
1. Выберите пункт **+ Сопоставить** над строкой поиска.
1. На странице соответствующего сетевого интерфейса выберите **sc900-winvmXXX** (где XXX относится непосредственно к сетевому интерфейсу вашей ВМ).  При сопоставлении интерфейса вы увидите уведомление в правом верхнем углу экрана.
1. После сопоставления интерфейса с NSG этот интерфейс появится в списке.
1. Теперь, когда интерфейс ВМ сопоставлен с группой безопасности сети и правилами этой группы по умолчанию, любая попытка подключиться к ВМ закончится с ошибкой.  
1. В левом верхнем углу страницы выберите **Все службы**, затем в разделе «Подборка» выберите **Виртуальные машины**.
1. На странице «Виртуальные машины» выберите **SC900-WinVM**.
1. В верхней части страницы **SC900-WinVM** выберите **Подключить**, затем выберите **RDP**.
1. Убедитесь, что задан общедоступный IP-адрес, оставьте номер порта по умолчанию и выберите **Загрузить DRP-файл**.
1. Откройте загруженный файл и выберите **Подключить**.
1. Через несколько секунд при выполнении попытки подключения появится сообщение об ошибке, указывающее, что удаленный рабочий стол не может подключиться к удаленному компьютеру.  Нажмите кнопку **ОК**.

#### Задача 3. В рамках этой задачи вы создадите правило NSG, чтобы разрешить входящий трафик RDP на порт 3389.  Затем вы проверите это правило, попытавшись подключиться к ВМ через RDP. 

1. Откройте вкладку «SC900-WinVM – Microsoft Azure» в вашем браузере.

1. В разделе «Параметры» на панели навигации слева выберите **Сеть**.
1. После выбора вкладки «Правила для порта входящего трафика» вы увидите на ней правила для входящего трафика по умолчанию. Правила по умолчанию нельзя удалить, но можно их переопределить, создав правила с более высоким приоритетом. В правой части страницы выберите **Добавить правило для порта входящего трафика**:
1. На странице «Добавить правило безопасности входящего трафика» укажите следующие параметры:
    1. Источник:  **Любой**

    1. Диапазоны исходных портов: *
    1. Место назначения:  **Любой**
    1. Служба:  **RDP**
    1. Действие:  **Разрешить**
    1. Приоритет:  **300**. Примечание. Правила с более низкими номерами имеют более высокий приоритет и обрабатываются первыми.
    1. Имя:  **AllowRDP**
1. Нажмите **Добавить**
1. После подготовки правила оно появится в списке правил входящего трафика.
1. Теперь убедитесь, что вы можете подключиться к ВМ с помощью RDP.  Выберите **Подключить** на панели навигации слева.
1. Убедитесь, что задан общедоступный IP-адрес, оставьте номер порта по умолчанию и выберите **Загрузить DRP-файл**.
1. Откройте загруженный файл и выберите **Подключить**.
1. Вам будет предложено ввести учетные данные.  В качестве имени пользователя введите **AzureUser**.  В качестве пароля введите **SC900AzureLabs**.
1. Открывается окно подключения к удаленному рабочему столу с сообщением, что идентификация удаленного компьютера не может быть проверена.  Продолжить в любом случае?  Выберите **Да**.
1. Теперь вы подключены к ВМ. В этом случае вы смогли подключиться к ВМ, потому что созданное вами правило входящего трафика пропускает входящий трафик к ВМ через RDP.
1. Оставьте ВМ открытой, так как она будет использоваться в следующей задаче.

#### Задача 4.  Правила для исходящего трафика, которые по умолчанию применяются для группы, разрешают исходящий интернет-трафик, поэтому вы будете проверять возможность выхода в Интернет.  Затем вы создадите пользовательское правило исходящего трафика для блокировки исходящего трафика в Интернет и проверите это правило.

1. На ВМ выберите **Edge**, чтобы открыть браузер.  
1. Введите **https://www.bing.com** в адресной строке браузера и убедитесь, что вы можете подключиться к поисковой системе.
1. Закройте браузер на ВМ, но не завершайте ее работу, так как ВМ понадобится для дальнейших действий.
1. Вернитесь на портал Azure, откройте вкладку «SC900-WinVM – Microsoft Azure» в вашем браузере.
1. В разделе «Параметры» на панели навигации слева выберите **Сеть**.
1. Перейдите на вкладку **Правила исходящего порта**.  Вы увидите правила для исходящего трафика по умолчанию.  Обратите внимание на правило по умолчанию «AllowInternetOutBound». Это правило разрешает весь исходящий интернет-трафик. Вы не можете удалить правило по умолчанию, однако можно переопределить его, создав правило с более высоким приоритетом. В правой части страницы выберите **Добавить правило исходящего порта**.
1. На странице «Добавить правило безопасности исходящего трафика» укажите следующие параметры:
    1. Источник:  **Любой**

    1. Диапазоны исходных портов:  *
    1. Место назначения:  **Тег службы**
    1. Тег службы назначения:  **Интернет**
    1. Служба:  **Пользовательская** (оставьте значение по умолчанию)
    1. Диапазоны портов назначения:  * (обязательно поставьте звездочку в поле диапазонов портов назначения)
    1. Протокол: **Любой**
    1. Действие: **Запретить**
    1. Приоритет:  **4000**
    1. Имя:  **DenyInternet**
1. Нажмите **Добавить**
1. После подготовки правила оно появится в списке правил исходящего трафика.  Несмотря на отображение этого правила в списке оно вступит в силу только через несколько минут (подождите несколько минут, прежде чем переходить к дальнейшим действиям).  
1. Вернитесь на ВМ
1. Откройте браузер Edge в ВМ и введите **https://www.bing.com**.  Страница не должна отображаться.  Примечание. Если вы можете подключиться к Интернету и проверили, что все параметры для правил исходящего трафика правильно настроены, скорее всего, необходимо подождать несколько минут, чтобы правило вступило в силу.  Закройте браузер, подождите несколько минут и повторите попытку.
1. Закройте подключение к удаленному рабочему столу, выбрав **X** в центре верхней части страницы, где отображается IP-адрес.  Появляется всплывающее окно с сообщением об отключении удаленного сеанса. Нажмите кнопку **ОК**.
1. В рамках этой задачи вы успешно настроили правило для исходящего трафика в группе NSG для блокировки исходящего интернет-трафика.

#### Задача 5.  ВАЖНО! В рамках этой задачи вы удалите группу ресурсов и все содержащиеся в ней ресурсы.   Это важно во избежание дополнительных затрат.

1. Откройте вкладку «SC900-WinVM – Microsoft Azure» в вашем браузере.

1. В левом верхнем углу страницы выберите **Все службы**.
1. В поле «Фильтровать службы» рядом с надписью «Все службы» введите **Группы ресурсов**, затем в результатах выберите **Группы ресурсов**.
1. Выберите **LabsSC900**.
1. Вверху в центре страницы LabsSC900 выберите **Удалить группу ресурсов**.
1. В открывшемся окне введите имя группы ресурсов **LabsSC900** для подтверждения удаления группы ресурсов и всех содержащихся в ней ресурсов, затем выберите **Удалить** в нижней части страницы.
1. На удаление всех ресурсов и группы ресурсов может уйти несколько минут.

#### Обзор

В рамках этой лабораторной работы вы изучили процесс настройки ВМ с группой безопасности сети (NSG) и без нее, а также оценили воздействие правил NSG по умолчанию.  Кроме того, вы выполнили процесс создания правил NSG.