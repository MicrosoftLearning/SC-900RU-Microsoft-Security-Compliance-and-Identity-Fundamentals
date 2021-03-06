---
lab:
    title: 'Изучение управления удостоверениями в Azure AD с управлением привилегированными пользователями.'
    module: 'Модуль 2. Урок 4. Описание защиты удостоверений и возможностей управления ими в Azure AD: описание защиты удостоверений в Azure.'
---


# Практическое занятие. Изучение управления удостоверениями в Azure AD с управлением привилегированными пользователями.

## Сценарий практического занятия
В рамках этого практического занятия вы изучите некоторые базовые функциональные возможности управления привилегированными пользователями. Для управления привилегированными пользователями требуется Azure AD Premium P2.  В рамках этого практического занятия вы как администратор настроите одного из своих пользователей Diego Siciliani, предоставив ему роль администратора пользователей Azure AD через управление привилегированными пользователями.   Имея привилегии администратора, Диего сможет создавать пользователей и группы, управлять лицензиями и многое другое.  Являясь и администратором, и пользователей, Диего должен иметь лицензию Azure AD Premium P2.

**Примерное время**: 30–45 мин.

#### Задача 1. В рамках этой задачи вы как администратор сбросите пароль пользователя Diego Siciliani. Этот шаг необходим, чтобы вы в дальнейших задачах могли выполнять вход от имени пользователя.

1. Откройте Microsoft Edge.  В адресной строке введите **portal.azure.com**.

2. Войдите под своими учетными данными администратора.
    1. В окне входа введите **admin@WWLxZZZZZZ.onmicrosoft.com** (где ZZZZZZ — уникальный идентификатор клиента, предоставленный поставщиком размещения практических занятий), затем нажмите кнопку **Далее**.
    1. Введите пароль администратора, который должен быть предоставлен поставщиком размещения практических занятий. Выберите **Вход**.
    1. При появлении предложения не выходить из системы выберите **Да**.

3. Выберите **Azure Active Directory**.  

4. На панели навигации слева выберите **Пользователи**.

5. Выберите **Diego Siciliani** в списке пользователей.

6. Выберите **Сбросить пароль** в верхней части страницы. Поскольку вы еще не выполняли вход от имени Диего и не знаете его пароль, необходимо сбросить пароль.

7. При открытии окна сброса пароля выберите **Сбросить пароль**.  ВАЖНО! Запишите новый пароль, так как он понадобится далее, чтобы выполнить вход в качестве пользователя.

8. Закройте окно сброса пароля, выбрав **X** в правом верхнем углу страницы.

9. Закройте окно профиля Диего, выбрав **X** в правом верхнем углу страницы.

10. Закройте окно «Все пользователи», выбрав **X** в правом верхнем углу страницы. Должна открыться страница Contoso Azure Active Directory.

11. Не закрывайте эту страницу браузера, так как она понадобится в последующих задачах.


#### Задача 2. В рамках этой задачи вы как администратор назначите Диего роль Azure AD через управление привилегированными пользователями.

1. Откройте вкладку браузера с меткой Contoso — Microsoft Azure.   Если вы ранее закрыли вкладку браузера, откройте Microsoft Edge и в адресной строке введите portal.azure.com, затем выполните вход с использованием учетных данных администратора и выберите Azure Active Directory.  

2. На панели навигации слева выберите **Управление удостоверениями**.

3. Убедитесь, что в главном окне подчеркнуто **Приступая к работе**, затем выберите **Управление назначением ролей** в правой части экрана.  Кроме того, на панели навигации слева в разделе «Управление привилегированными пользователями» выберите **Роли Azure AD**.

4. Откроется окно быстрого начала работы с управлением привилегированными пользователями.  Выберите **Управление доступом**.

5. Откроется страница «Роли Contoso».  На панели поиска в верхней части страницы введите **пользователь**.  В результатах поиска выберите **Администратор пользователей**.

6. В верхней части страницы выберите **+ Назначения**.

7. На странице «Добавление назначений» убедитесь, что подчеркнута надпись **Членство**.  Здесь можно настроить параметры членства для роли администратора пользователей в управлении привилегированными пользователями.

8. Оставьте для типа области значение по умолчанию — «Каталог».  

9. В разделе «Выбор участников» выберите **Нет выбранных участников**. Откроется окно «Выбор участника». 

10. В поле поиска введите **Diego**.  В результатах поиска выберите **Diego Siciliani**, затем нажмите **Выбрать** в нижней части страницы.  

11. В разделе «Выбор участников» вы увидите выбранного 1 участника, а также имя и адрес эл. почты выбранного участника Diego Siciliani. В нижней части страницы «Добавление назначений» выберите **Далее**.  

12. Вы окажетесь на странице настроек.  Оставьте для типа назначения значение по умолчанию «Соответствует».

13. Если установлен флажок «Постоянно соответствует», щелкните **Постоянно соответствует**, чтобы снять флажок.

14. В полях «Начало назначения» оставьте дату и время по умолчанию, то есть текущее время сегодняшнего дня.

15. В полях «Окончание назначения» измените дату на сегодняшний день (обратите внимание, что настройка по умолчанию — один год с сегодняшнего дня, поэтому вам придется изменить год). Что касается времени, установите время на два часа вперед от текущего.  После установки значения времени для даты окончания назначения нажмите клавишу Tab на клавиатуре и выберите **Назначить** в нижней части страницы.  

16. Вы вернетесь в окно «Назначения».  Через несколько секунд Diego Siciliani появится в таблице администраторов пользователей вместе со сведениями о назначении.  Если через несколько секунд вы не увидите обновления, выберите **Обновить** в верхней части страницы.

17. В верхней части страницы выберите **Параметры**.

18. В сведениях о настройке роли администратора пользователей обратите внимание на различные параметры.  Обратите внимание, что для параметра «Требовать обоснования активации» задано значение «Да», а для параметра «При активации требовать многофакторную проверку подлинности Azure» также задано значение «Да».  Эти параметры вы увидите в следующей задаче, когда Диего активирует свою роль.  Кроме того, обратите внимание, что для параметра «Требовать разрешение для активации» задано значение «Нет». Оставьте для всех параметров значения по умолчанию.  Закройте страницу, выбрав **X** в правом верхнем углу экрана.

19. Выйдите из системы, нажав значок пользователя рядом с адресом эл. почты в правом верхнем углу экрана и выбрав **Выход**. Затем закройте все окна браузера.


#### Задача 3. Задача 3.  В рамках этой задачи вы от имени Diego Siciliani выполните вход на портал Azure чтобы получить доступ к возможностям управления привилегированными пользователями в Azure Active Directory для активации вашего назначения в качестве администратора пользователей.  После активации необходимо внести некоторые изменения конфигурации существующего пользователя. Примечание. В рамках этой задачи вам необходим доступ к мобильному устройству, на котором вы сразу же сможете принять текстовые сообщения.

1. Откройте Microsoft Edge.  В адресной строке браузера введите **portal.azure.com**.

1. Выполните вход как Diego Siciliani.
    1. В окне входа введите **DiegoS@WWLxZZZZZZ.onmicrosoft.com** (где ZZZZZZ — уникальный идентификатор клиента, предоставленный поставщиком размещения практических занятий), затем нажмите кнопку **Далее**.
    1. Введите временный пароль, который вы записали при выполнении предыдущей задачи, затем выберите **Вход**. Выберите **Вход**.
    1. Поскольку введенный пароль был только временным, необходимо обновить его на данном этапе. Введите текущий пароль.  В полях нового пароля и подтверждения пароля введите **SC900-Lab**.
    1. При появлении предложения не выходить из системы выберите **Да**.

1. Вы должны успешно выполнить вход на портал Azure.
1. На странице приветствия в разделе «Службы Azure» выберите **Azure Active Directory**.
1. На панели навигации слева выберите **Управление удостоверениями**.
1. На панели навигации слева в разделе «Управление привилегированными пользователями» выберите **Роли Azure AD**.
1. На панели навигации слева выберите **Мои роли**.  Отображаются сведения по вашим ролям Azure AD.  Вы увидите, что вам (то есть Диего), назначена роль администратора пользователей.  
1. В последнем столбце таблицы, который помечен как «действие», выберите **Активировать**.
1. Появится значок предупреждение, оповещающий о необходимости дополнительной проверки.  Выберите **Щелкните, чтобы продолжить**.  Вспомните, что для настроек управления привилегированными пользователями в рамках роли администратора пользователей требуется многофакторная проверка подлинности.  Кроме того, поскольку контактные данные Диего для использования с многофакторной проверкой подлинности (методы проверки подлинности) не были настроены ранее, он должен зарегистрировать эти сведения, чтобы воспользоваться многофакторной проверкой подлинности.  Несмотря на то, что ему придется пользоваться многофакторной проверкой подлинности при входе в качестве администратора пользователей в течение указанного периода времени, регистрацию многофакторной проверки подлинности следует выполнить только один раз.
1. Появляется уведомление, что требуется больше информации, нажмите **Далее**.
1. Введите пароль **SC900-Lab**.
1. В левой нижней части окна Microsoft Authenticator выберите **Мне необходимо настроить другой метод**.
1. Появляется запрос на выбор другого метода.  Рядом с указанием приложения Authenticator нажмите стрелку вниз.   Выберите **Телефон**, а затем **Подтвердить**.
1. Появляется запрос на ввод номера телефона, который следует использовать. Убедитесь, что для номера телефона указан правильный код страны.  Введите номер телефона, убедитесь, что выбран параметр **Отправить код в текстовом сообщении**, и нажмите кнопку **Далее**.
1. Введите 6-значный код, полученный на телефоне, и нажмите кнопку **Далее**. 
1. Появится уведомление, что ваш телефон успешно зарегистрирован. Выберите **Далее**, затем **Готово**.
1. Появится предложение не выходить из системы, нажмите **Да**.
1. Отображается окно активации администратора пользователей.  Вам необходимо ввести причину для активации.  В появившемся поле введите любую нужную причину (не более 500 символов), затем выберите **Активировать**.
1. По мере выполнения активации будет отображаться состояние (3 этапа хода выполнения).
1. По завершении активации вы вернетесь на страницу «Мои роли» | Страница «Роли Azure AD», где можно увидеть уведомление о том, что вы только что активировали роль.  Выберите **Щелкните здесь**, чтобы просмотреть активные роли.  Если вы увидели, что время окончания отличается от того, что было изначально настроено, нажмите кнопку «Обновить» в верхней части экрана (на обновление может уйти несколько минут). 
1. Закройте это окно, выбрав **X** в правом верхнем углу экрана.
1. Закройте окно быстрого запуска управления привилегированными пользователями, | выбрав **X** в правом верхнем углу экрана.
1. Закройте окно управления удостоверениями, выбрав **X** в правом верхнем углу экрана.
1. Вы вернетесь на страницу Contoso Azure Active Directory.  Вы в качестве администратора пользователей Azure AD можете создавать пользователей и группы, управлять лицензиями и многое другое.   На панели навигации слева выберите **Пользователи**.
1. В списке пользователей выберите **Bianca Pisani**.
1. На панели навигации слева, выберите **Лицензии**.
1. Обратите внимание, что пользователю Bianca не назначено лицензий.  В верхней части страницы выберите **+ Назначения**. 
1. В списке выбора лицензий выберите **Office 365 E3** и **Windows 10 Enterprise E3**.
1. В верхней части страницы выберите **Сохранить**.  Вы увидите краткое уведомление в правой верхней части страницы, указывающее, что лицензии были успешно назначены.
1. Закройте обновленную страницу назначения лицензий, выбрав **X** в правом верхнем углу страницы.
1. Выйдите из системы, нажав значок пользователя рядом с адресом эл. почты в правом верхнем углу экрана и выбрав **Выход**. Затем закройте все окна браузера.
1. Продолжительность действия роли администратора пользователей ограничена указанным временем.

#### Обзор
На этом практическом занятии вы изучили возможности управления привилегированными пользователями.  Вы в качестве администратора предоставили Диего (Diego) привилегии администратора пользователей на указанное время.  Затем в качестве Диего вы выполнили активацию привилегий администратора пользователей и настроили пользовательские параметры.  Вспомните, что для управления привилегированными пользователями требуется лицензирование Azure AD Premium P2.
