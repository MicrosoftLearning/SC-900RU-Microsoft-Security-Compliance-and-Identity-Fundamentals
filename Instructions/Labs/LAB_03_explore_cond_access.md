﻿---
lab:
    title: 'Изучение управления доступом в Azure AD с условным доступом'
    module: 'Модуль 2. Урок 3. Описание возможностей решений Майкрософт по управлению удостоверениями и доступом: Изучение возможностей Azure AD по управлению доступом'
---


# Практическое занятие. Изучение управления доступом в Azure AD с условным доступом

## Сценарий практического занятия
На этом практическом занятии вы изучите условный доступ с многофакторной проверкой подлинности с точки зрения администратора и пользователя.  В качестве администратора вы создадите политику, которая будет требовать многофакторной проверки подлинности пользователя при доступе к облачному приложению Microsoft Azure Management.  С точки зрения пользователя вы увидите воздействие политики условного доступа, включая процесс регистрации для многофакторной проверки подлинности.

**Примерное время**: 10–15 мин

#### Задача 1. В рамках этой задачи вы как администратор сбросите пароль пользователя Debra Berger.  Этот шаг необходим, чтобы вы в дальнейших задачах могли выполнять вход от имени пользователя.

1. Откройте Microsoft Edge.  В адресной строке введите **portal.azure.com**.

2. Войдите под своими учетными данными администратора.
    1. В окне входа введите **admin@WWLxZZZZZZ.onmicrosoft.com** (где ZZZZZZ — уникальный идентификатор клиента, предоставленный поставщиком размещения практических занятий), затем нажмите кнопку **Далее**.
    1. Введите пароль администратора, который должен быть предоставлен поставщиком размещения практических занятий. Выберите **Вход**.
    1. При появлении предложения не выходить из системы выберите **Да**.

3. Выберите **Azure Active Directory**.  

4. На панели навигации слева выберите **Пользователи**.

5. Выберите **Debra Berger** в списке пользователей.

6. Выберите **Сбросить пароль** в верхней части страницы. Поскольку вы еще не выполняли вход под пользователем Debra Berger и не знаете ее пароль, необходимо сбросить пароль.

7. При открытии окна сброса пароля выберите **Сбросить пароль**.  ВАЖНО! Запишите новый пароль, так как он понадобится далее, чтобы выполнить вход в качестве пользователя.

8. Закройте окно сброса пароля, выбрав **X** в правом верхнем углу страницы.

9. Закройте окно «Пользователи», выбрав **X** в правом верхнем углу страницы.

10. Не закрывайте это окно.


#### Задача 2.  В рамках этой задачи вам необходимо будет создать политику условного доступа в Azure AD.

1. Откройте вкладку браузера с меткой Contoso — Microsoft Azure.   Если вы ранее закрыли вкладку браузера, откройте Microsoft Edge и в адресной строке введите portal.azure.com, затем выполните вход с использованием учетных данных администратора и выберите Azure Active Directory.  

2. На панели навигации слева выберите **Безопасность**.

3. На панели навигации слева выберите **Условный доступ**.

4. Отображается экран «Политики условного доступа». Здесь приведены любые политики условного доступа. Выберите**Новая политика**.

5. В поле «Имя» введите **Тестовая политика MFA**.

6. В разделе «Пользователи и группы» выберите **выбрано 0 пользователей и групп**.

7. Появится возможность включения или исключения пользователей и групп.  Убедитесь, что выбран параметр **Включить** (подчеркнут).

8. Выберите параметр **Выберите пользователи и группы** и выберите **Пользователи и группы**.  Откроется окно «Выбор пользователей и групп».  

9. В поле поиска введите **Debra**.  Выберите пункт **Debra Berger** под строкой поиска, затем нажмите кнопку **Выбрать** в нижней части страницы.  Обратите внимание, что обычно политика назначается пользователям в группе.  В целях более быстрого выполнения этого практического занятия мы назначим политику определенному пользователю. 

10. В разделе «Облачные приложения или действия» выберите **Нет выбранных облачных приложений или действий**.

11. Появится возможность включения или исключения облачных приложений или пользовательских действий.  Убедитесь, что выделен пункт **Облачные приложения** и выбран пункт **Включить** (подчеркнут), затем выберите **Выбрать приложения**.  Открывается окно «Выбрать облачные приложения».

12. В поле поиска введите **Azure**.  В результатах поиска, которые отображаются в поле поиска, выберите **Microsoft Azure Management**, затем нажмите **Выбрать** в нижней части страницы.  Обратите внимание на предупреждение.  

13. В разделе «Условия» выберите **0 условий выбрано**.  Обратите внимание на различные параметры, которые можно настроить.  В рамках этой политики вы можете управлять доступом пользователя на основе сигналов от таких условий, как риск, платформа устройства, местоположение, клиентские приложения или состояние устройства.  Например, вы можете включить условие применение политики к любому местоположению, кроме выбранных или доверенных мест, например сети головного офиса.  Для этой политики не задавайте какие-либо условия.

14. Теперь необходимо определить управление доступом.  В разделе «Предоставление разрешения» выберите **0 условий выбрано**.

15. Откроется окно «Предоставление разрешения».  Убедитесь, что выбран пункт **Предоставить доступ**, затем выберите **Требовать многофакторную проверку подлинности**.  В разделе «Для нескольких элементов управления» оставьте значение по умолчанию **Требовать все выбранные элементы управления**.  Нажмите **Выбрать** в нижней части страницы.

16. Под надписью «Включить политику» в нижней части страницы выберите **Вкл**, затем нажмите кнопку **Создать**.

17. Через несколько секунд пилотная политика многофакторной проверки подлинности должна появиться в списке политик условного доступа (при необходимости выберите **Обновить** в верхней части страницы).

18. Завершите сеанс Azure и закройте окна браузера.

#### Задача 3. В рамках этой задачи вы увидите воздействие политики условного доступа с точки зрения пользователя Debra Berger. Сначала необходимо выполнить вход в приложение, которое не охвачено политикой условного доступа.  Затем вы повторите эту процедуру для приложения, которое включено в политику условного доступа.  Вспомните, что эта политика требует, чтобы пользователь прошел многофакторную проверку подлинности при доступе к приложению Microsoft Azure Management.  Чтобы использовать многофакторную проверку подлинности пользователь должен сначала зарегистрировать метод проверки подлинности, который будет использоваться для многофакторной проверки подлинности, например код, отправленный на мобильное устройство, или приложение Authenticator.

1. Откройте Microsoft Edge.  В адресной строке браузера введите **https://login.microsoftonline.com/**.

1. Выполните вход под пользователем Debra Burger,
    1. В окне входа введите **DebraB@WWLxZZZZZZ.onmicrosoft.com** (где ZZZZZZ — уникальный идентификатор клиента, предоставленный поставщиком размещения практических занятий), затем нажмите кнопку **Далее**.
    1. Введите пароль, который вы записали при выполнении предыдущей задачи. Выберите **Вход**.
    1. Поскольку пароль, предоставленный во время сброса вами пароля от лица администратора, является временным, необходимо обновить пароль (это не является частью многофакторной проверки подлинности).  Введите текущий пароль, затем в полях «Новый пароль» и «Подтвердите пароль» введите **SC900-Lab**.
    1. При появлении предложения не выходить из системы выберите **Да**

1. Вы должны успешно выполнить вход в учетную запись Microsoft 365.  Многофакторная проверка подлинности не требовалась для этого приложения и не является частью политики.

1. Теперь вы попытаетесь выполнить вход в приложение, которое соответствует требованиям многофакторной проверки подлинности.  Откройте Microsoft Edge и в адресной строке введите https://portal.azure.com.

1. Вы увидите окно «Требуется больше информации».  Выберите **Далее**.  Обратите внимание, что это запустит процедуру регистрации многофакторной проверки подлинности, так как это первое получение доступа к облачному приложению, которое было определено в политике условного доступа.  Регистрацию необходимо выполнить только один раз.   Альтернативой прохождения пользователем регистрации является настройка администратором метода проверки подлинности.

1. В окне «Защитить свою учетную запись» у вас есть возможность выбрать метод многофакторной проверки подлинности.  Одним из вариантов является Microsoft Authenticator. Для ускоренного выполнения этого практического занятия выберите другой метод.  Выберите **Мне необходимо настроить другой метод**.  Во всплывающем окне «Выберите другой метод» выберите **стрелку раскрывающегося списка** и нажмите **Телефон**, затем выберите **Подтвердить**.

1. В открывшемся окне убедитесь, что выбрана страна, затем введите номер мобильного телефона, который следует использовать, убедитесь, что выбран пункт **Отправить код в текстовом сообщении**, затем нажмите кнопку **Далее**.  На экране появится надпись «Проверено по SMS. Ваш телефон успешно зарегистрирован».  Выберите **Далее**, затем **Готово**.  На этом завершается процедура регистрации, которую нужно выполнить один раз.

1. Скорее всего, появится сообщение о таймауте входа.  Просто введите пароль **SC900-Lab** и выберите **Вход**.

1. Появится окно с запросом на ввод кода, который был отправлен на ваш телефон.  Введите код и нажмите кнопку **Далее**.  Именно это будете видеть вы в качестве пользователя Gerhart каждый раз при входе в облачное приложение Microsoft Azure Management, например на портал Azure, в соответствии с политикой многофакторной проверки подлинности.

1. Появится окно с запросом на ввод кода, который был отправлен на ваш телефон.  Введите код и нажмите кнопку **Подтвердить**.  При появлении предложения не выходить из системы выберите **Нет**.

1. Теперь вы должны зайти на портал Azure.  Портал Azure — это приложение Microsoft Azure Management, поэтому нуждается в многофакторной проверки подлинности в соответствии с созданной политикой условного доступа.  

1. Выйдите из системы, нажав значок пользователя рядом с адресом эл. почты в правом верхнем углу экрана и выбрав «Выход». Затем закройте все окна браузера.

#### Обзор
На этом практическом занятии вы настроили политику условного доступа, которая требовала от пользователей проходить многофакторную проверку подлинности при входе в облачное приложение Microsoft Azure Management.  Затем в качестве пользователя вы зарегистрировали многофакторную проверку подлинности и увидели воздействие политики условного доступа, которая требует использования многофакторной проверки подлинности при входе на портал Azure.