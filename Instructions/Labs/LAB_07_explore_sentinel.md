---
lab:
    title: 'Обзор Microsoft Sentinel'
    module: 'Модуль 3. Урок 3. Описание возможностей решений безопасности Майкрософт: описание возможностей обеспечения безопасности в Microsoft Sentinel'
---


# Практическое занятие: Обзор Microsoft Sentinel 

## Сценарий практического занятия
В рамках этого практического занятия вы рассмотрите процесс создания экземпляра Microsoft Sentinel.  Вы также настроите разрешения, чтобы обеспечить доступ к ресурсам, которые будут развернуты для поддержки Microsoft Sentinel.  После этой базовой настройки вы выполните все действия по подключению Microsoft Sentinel к вашим источникам данных, используя встроенную аналитику для получения уведомлений о любых подозрительных действиях. Наконец, вы изучите возможности автоматизации.  

  

**Примерное время**: 30–45 мин

#### Задача 1.  Создание экземпляра Microsoft Sentinel.

1. Откройте Microsoft Edge. В адресной строке введите **portal.azure.com**.

2. Войдите под своими учетными данными администратора.
    1. В окне входа введите **admin@WWLxZZZZZZ.onmicrosoft.com** (где ZZZZZZ — уникальный идентификатор клиента, предоставленный поставщиком размещения практических занятий), затем нажмите кнопку **Далее**.
    
    1. Введите пароль администратора, который должен быть предоставлен поставщиком размещения практических занятий. Выберите **Вход**.
    1. При появлении предложения не выходить из системы выберите **Да**.

3. В левом верхнем углу экрана рядом с надписью Microsoft Azure выберите значок отображения меню портала (три горизонтальных линии, которые также называются значком гамбургера), затем выберите **Все службы**.  

4. В поле «Фильтровать службы» введите **Microsoft Sentinel**, затем выберите в списке **Microsoft Sentinel**.

5. На странице Microsoft Sentinel выберите **Создать Microsoft Sentinel**.

6. На странице «Добавить Microsoft Sentinel в рабочую область» выберите **Создать новую рабочую область**.

7. На вкладке «Основные» рабочей области страницы «Создание рабочей области Log Analytics» введите следующее:
    1. Подписка:  **Azure Pass – Спонсорское предложение**
   
    1. Группа ресурсов: выберите **Создать**, затем введите имя **SC900-ResourceGroup** и нажмите кнопку **OK**.
    1. Имя: **SC900-LogAnalytics-workspace**.
    1. Регион: **Восток США** (оставьте значение по умолчанию)
    1. Выберите **Далее: Ценовая категория >**

8. Для ценовой категории оставьте настройки по умолчанию. **Оплата по мере использования (за ГБ 2018)**, затем выберите **Далее: Теги >**.

9. Можно оставить поле «Теги» пустым. Выберите **Просмотр и создание**.

10. Проверьте введенные сведения, затем выберите **Создать**.

11. Если в списке не отображается новая рабочая область, выберите **Обновить**, затем выберите **Добавить**.

12. После добавления новой рабочей области откроется страница «Новости и руководства | Azure Sentinel».  Обратите внимание на три действия, приведенные на странице «Начало работы».

13. Оставьте эту страницу открытой, так как она будет использоваться в следующей задаче.

#### Задача 2.  При создании экземпляра Microsoft Sentinel необходимо убедиться, что у вас есть необходимый доступ к ресурсам, которые развертываются для поддержки Microsoft Sentinel.  В рамках этой задачи вы получите доступ к странице управления доступом (IAM) для группы ресурсов, созданной с экземпляром Microsoft Sentinel, просмотрите доступные роли и назначьте себе (администратору MOD) необходимую роль. Назначение роли на уровне группы ресурсов обеспечит применение этой роли ко всем ресурсам, развернутым для поддержки Microsoft Sentinel.

1. В левом верхнем углу страницы Microsoft Sentinel над надписью Microsoft Sentinel выберите **Все службы**.

2. В поле «Фильтровать службы» введите группы ресурсов, затем в предоставленном списке выберите **Группы ресурсов**.

3. На странице групп ресурсов выберите группу ресурсов, созданную с помощью Microsoft Sentinel, под названием **SC900-ResourceGroup**.

4. На странице SC900-ResourceGroup выберите **Управление доступом (IAM)** на панели навигации слева.

5. На странице управления доступом выберите **Просмотреть мой доступ**.  Обратите внимание, что текущая роль — администратор безопасности.  Закройте окно назначений администратора MOD, выбрав **X** в правом верхнем углу окна.

6. На странице управления доступом выберите **+Добавить**, затем выберите **Добавить назначение ролей**.

7. Откроется окно «Добавить назначение ролей».  Нажмите стрелку раскрывающегося списка в поле «Выберите роль» для отображения доступных ролей.  В рамках этого практического занятия выберите **Владелец**.  ПРИМЕЧАНИЕ.  Рекомендуется назначить наименьшую привилегию, необходимую для этой роли.  Для справки просмотрите разрешения в Microsoft Sentinel:  https://docs.microsoft.com/ru-ru/azure/sentinel/roles

8. В отображаемом списке пользователей выберите **Администратор MOD**.

9. Выберите **Сохранить** в нижней части страницы.

10. На странице управления доступом выберите **Просмотреть мой доступ**, чтобы подтвердить добавление роли, затем закройте окно, выбрав **X** в правом верхнем углу окна.

11. Вернитесь на страницу «Все службы» платформы Azure, выбрав **Все службы** в левом верхнем углу страницы над надписью «Группы ресурсов».

#### Задача 3.  В рамках этой задачи вы изучите процесс подключения Microsoft Sentinel к вашему источнику данных для запуска сбора данных. Примечание. Возможно, уйдет некоторое время на отображение подключенного состояния соединителя (около 30 минут в зависимости от клиента).

1. В поле «Фильтровать службы» страницы «Все службы» введите **Microsoft Sentinel**, затем выберите в результаты списке **Microsoft Sentinel**. 

2. На странице Microsoft Sentinel выберите созданную рабочую область с экземпляром Microsoft Sentinel под названием **SC900-LogAnalytics-workspace**.

3. Первый шаг с Microsoft Sentinel — получить возможность сбора данных. На панели навигации слева выберите пункт **Соединители данных**, который отображается под конфигурацией.

4. На странице «Соединители данных» прокрутите до главного окна, чтобы просмотреть расширенный список доступных соединителей. В поле «Поиск» на странице «Соединители данных» введите **Azure**, затем в списке выберите **Azure Active Directory**.

5. Откроется окно «Соединитель Azure Active Directory».  Выберите **Открыть страницу соединителя**.

6. На странице соединителя Azure Active Directory просмотрите описание и обратите внимание на связанное содержимое, которое включает книги, запросы и шаблоны правил аналитики.  

7. На вкладке инструкций основного окна приведены предварительные требования для интеграции Microsoft Sentinel с Azure Active Directory.   В разделе конфигурации выберите **Журналы входа**, затем выберите «Применить изменения» (можно выбрать несколько соединителей).

8. На вкладке «Следующие действия» обратите внимание на список рекомендуемых книг.   В рекомендованных книгах выберите **Журналы входа в Azure** (можно выбрать дополнительные книги).

9. На выбранной вкладке «Шаблоны» страницы книг выберите **Журналы входа в Azure** (подчеркнуто). 

10. В открывшемся окне журналов входа в Azure AD просмотрите описание и выберите **Просмотреть шаблон**.  Закройте шаблон, выбрав **X** в правом верхнем углу экрана.  Выберите **Сохранить** в нижней части страницы, затем выберите **OK**, чтобы сохранить книгу в месте по умолчанию.

11. В левом верхнем углу страницы «Книги» выберите **Microsoft Sentinel** над надписью «Книги». Вы вернетесь на страницу «Соединители данных Microsoft Sentinel».

12. В верхней части страницы «Соединители данных» отображается 1 подключенный, что означает ваше подключение к Azure Active Directory.

13. На панели навигации слева выберите **Книги**.

14. На странице «Книги» выберите вкладку **Мои книги** над полем поиска.  Только что сохраненная книга появляется в списке и доступна для просмотра и мониторинга ваших данных.

15. Оставьте эту страницу открытой, так как она будет использоваться в следующей задаче.

#### Задача 4.  В рамках этой задачи вы выполните процедуру с использованием встроенного шаблона правила аналитики для создания правила уведомления при наличии каких-либо подозрительных событий.

1. На панели навигации слева выберите **Аналитика**.

2. Страница «Аналитика» отображает активные правила (расширенное многоуровневое определение атак включено по умолчанию), а также обеспечивает доступ к шаблонам правил.  Выберите вкладку **Шаблоны правил**.  Обратите внимание на список доступных шаблонов и различные способы фильтрации списка.  Используя встроенные аналитические оповещения рабочей области Microsoft Sentinel, вы будете получать уведомления в случае возникновения подозрительных событий.

3. В поле поиска введите **Портал Azure**.  Выберите **Неудачные попытки входа на портал Azure**.  

4. В открывшемся окне прочитайте описание и просмотрите сведения, связанные с шаблоном.  В нижней части страницы выберите **Создать правило**.

5. В мастере правила аналитики просмотрите сведения и выберите **Далее: Задать логику правила >**.

6. Страница «Настройка логики правила» позволяет определить логику для вашего нового правила аналитики. Шаблон уже содержит определенную логику и предварительно заданные настройки.  Прокрутите эту страницу вниз, чтобы просмотреть доступные настройки.  Оставьте значение по умолчанию. Выберите **Далее: Настройки инцидента (предварительный просмотр)>**.

7. Благодаря настройкам инцидента оповещения Microsoft Sentinel можно сгруппировать в инцидент, который надлежит исследовать. Вы можете определить, должны ли оповещения, вызванные этим правилом аналитики, создавать инциденты.  Оставьте параметры по умолчанию и выберите **Далее: Автоматически ответ >**.

8. На вкладке «Автоматический ответ» обратите внимание, что можно добавить сборник схем для автоматизации ответа.  Аналогичным образом можно создать правило автоматизации инцидентов.  Выберите **+ Добавить** в разделе автоматизации инцидентов.  Открывается окно для создания нового правила автоматизации.  Любое правило автоматизации, созданное на этой странице, приводится в действие созданным правилом аналитики. Обратите внимание, что для этого правила можно добавить условия и задать действия.   Выберите **Отмена**, чтобы закрыть окно.

9. Выберите **Далее: Просмотреть >**, чтобы просмотреть все сведения, связанные с правилом и основанные на выбранном шаблоне. На этом этапе можно выбрать создание правила, нажав **Создать**, или выйти без создания правила, выбрав **X** в правом верхнем углу страницы.

10. Оставьте эту страницу открытой, так как она будет использоваться в следующей задаче.

#### Задача 5.  В предыдущей задаче вы создали правило аналитики, которое служит для оповещения о подозрительных действиях.  В этом мастере есть возможность автоматизации ответа на инцидент, которая основана на конкретном правиле.  Однако можно также создать правила автоматизации, открыв непосредственно параметр конфигурации автоматизации.

1. На панели навигации слева выберите **Автоматизация**.  

2. Выберите **+ Создать**. В раскрывающемся списке обратите внимание на то, как можно добавить новый сборник схем или добавить новое правило.  Выберите **Добавить новое правило**.  

3. Открывается окно для создания нового правила автоматизации.  Обратите внимание на то, что можно добавить условия и задать действия для правила.  Единственное различие заключается в том, что первое условие служит для сопоставления аналитических правил, к которым должно применяться правило автоматизации.  Оно было затенено в предыдущей задаче, поскольку автоматизация настраивалась для определенного правила.  Выберите **Отмена**, чтобы закрыть окно «Создание нового правила автоматизации».

4. Оставьте эту страницу открытой, так как она будет использоваться в следующей задаче.


#### Задача 6.  Удалите группу ресурсов Microsoft Sentinel.  Счета за Microsoft Sentinel выставляются на основе объема принятых на анализ в Microsoft Sentinel данных. Несмотря на то, что объем данных, принятых на анализ в рамках этого практического занятия, является минимальным, рекомендуется удалить группу ресурсов Microsoft Sentinel по завершении изучения функциональных возможностей Microsoft Sentinel.

1. В левом верхнем углу страницы Microsoft Sentinel над надписью Microsoft Sentinel выберите **Все службы**.

2. В поле «Фильтровать службы» введите группы ресурсов, затем в предоставленном списке выберите **Группы ресурсов**.

3. На странице групп ресурсов выберите группу ресурсов, созданную с помощью Microsoft Sentinel, под названием **SC900-ResourceGroup**.

4. Вверху по центру страницы выберите **Удалить группу ресурсов**.  Ознакомьтесь с предупреждением.  Введите имя группы ресурсов **SC900-ResourceGroup**, затем выберите **Удалить** в нижней части страницы.  На удаление группы ресурсов уйдет несколько минут.

5. После проверки удаления группы ресурсов закройте страницу браузера. 


#### Обзор

В рамках этого практического занятия вы рассмотрели процесс создания экземпляра Microsoft Sentinel.  Вы также настроили разрешения, чтобы обеспечить доступ к ресурсам, связанным с вашим экземпляром Microsoft Sentinel.  После создания экземпляра Microsoft Sentinel вы изучили действия по подключению Microsoft Sentinel к вашим источникам данных, используя встроенные правила аналитики для получения уведомлений о подозрительных событиях и возможности автоматизации. В заключительной части практического занятия вы удалили группу ресурсов, связанную с созданным экземпляром Microsoft Sentinel.
