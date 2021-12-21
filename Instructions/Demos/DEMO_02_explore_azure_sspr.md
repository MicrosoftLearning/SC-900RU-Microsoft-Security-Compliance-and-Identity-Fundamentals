---
Demo:
    title: 'Самостоятельный сброс пароля в Azure Active Directory'
    module: 'Модуль 2. Урок 2. Описание возможностей решений Майкрософт по управлению удостоверениями и доступом: Описание различных методов проверки подлинности в Azure AD'
---

# Демонстрация. Самостоятельный сброс пароля в Azure Active Directory (SSPR)

### Сценарий демонстрации

В рамках этой демонстрации вы рассмотрите различные настройки, связанные с включением самостоятельного сброса пароля.

1. Перейдите на вкладку «Contoso – Microsoft Azure», которая уже открыта в вашем браузере. Если ранее вы закрыли эту вкладку, откройте страницу браузера и в адресной строке введите portal.azure.com, затем выберите Azure Active Directory. Вы должны выполнить вход на портал Azure в качестве администратора. Если это не так, выполните вход повторно.

1. На панели навигации слева выберите «Сброс пароля».

1. Выделится вкладка свойств.  В окне «Свойства» обратите внимание, что самостоятельный сброс пароля (SSPR) может быть включен для всех, выбранных пользователей или же не включен совсем.
    1. Наведите указатель на значок сведений рядом с надписью «Самостоятельный сброс пароля включен» и укажите, что вам нужно выбрать «Выбрано» для ограничения сброса пароля ограниченной группе пользователей, а не выбирать значения «Нет» или «Все».
    1. Наведите указатель мыши на значок сведений рядом с надписью «выберите группу» и скажите, что здесь следует указать группу пользователей, которым разрешено сбрасывать собственные пароли.   Вы должны включить пользователей в этой группе, но не можете выбирать отдельных пользователей.  Кроме того, если изменить группу, выбранная группа заменит текущую указанную вами группу.  Поэтому рекомендуется просто добавлять пользователей в группу SSPR.
    1. Обратите внимание на светло-синее информационное поле и скажите учащимся, что эти настройки применимы только к пользователям в вашей организации. Администраторы всегда могут самостоятельно сбрасывать свой пароль и должны использовать два метода проверки подлинности для сброса пароля.

1. На панели навигации слева от сброса пароля выберите «Способы проверки подлинности».
    1. Наведите указатель мыши на значок сведений рядом с надписью «Число способов, необходимых для сброса».  Подчеркните, что здесь задается количество альтернативных способов идентификации пользователя в этом каталоге, необходимое для сброса пароля».   Не изменяйте эти настройки.
    1. Расскажите о различных «способах, доступных пользователям», включая поддержку контрольных вопросов в рамках самостоятельного сброса пароля. Выберите «Контрольные вопросы» для отображения параметров использования контрольных вопросов. После обсуждения параметров вернитесь на предыдущий экран и выберите «Контрольные вопросы», чтобы снять флажок.

1. На панели навигации слева от сброса пароля выберите «Регистрация».
    1. Наведите указатель мыши на значок сведений рядом с надписью «Требовать регистрации пользователей при входе».   Привлеките внимание пользователей к экрану.  
    1. Наведите указатель мыши на значок сведений рядом с надписью «Количество дней до запроса у пользователя повторного подтверждения сведений для проверки подлинности».   Привлеките внимание пользователей к экрану.  

1. На панели навигации слева от сброса пароля выберите «Уведомления».  Обратите внимание на две настройки — наведите указатель мыши на значок сведений, чтобы просмотреть описание.

1. Обратите внимание, что на панели навигации для сброса пароля также содержатся возможности просмотра журналов аудита и аналитики использования.

1. Выберите «X» в правом верхнем углу страницы. Снова откроется главная страница клиента Contoso.

1. Не закрывайте эту страницу, поскольку она понадобится в следующей демонстрации.

#### Обзор

В рамках этой демонстрации вы рассмотрели различные настройки, связанные с самостоятельным сбросом пароля. 
