---
Demo:
    title: 'Настройки пользователя Azure Active Directory'
    module: 'Модуль 2. Урок 1. Описание возможностей решений Майкрософт по управлению удостоверениями и доступом. Знакомство со службами и типами удостоверений Azure AD'
---

# Демонстрация. Настройки пользователя Azure Active Directory

### Сценарий демонстрации

В рамках этой демонстрации вы получите доступ к Azure Active Directory и изучите различные настройки существующего пользователя.

1. Перейдите на вкладку **Главная страница – Microsoft Azure** в вашем браузере.  Если вы ранее закрыли эту вкладку, откройте Microsoft Edge и в адресной строке введите portal.azure.com, затем выполните вход с использованием тех же учетных данных администратора, которые соответствуют вашему клиенту Microsoft 365.

1. На целевой странице портала Azure отображаются службы Azure. Выберите **Azure Active Directory**. Если соответствующий переход сразу не отображается, в поле списка рядом с надписью «Microsoft Azure», введите Azure Active Directory.  Кроме того, можно также показать, как осуществляется доступ через значок отображения меню портала (три горизонтальные линии, которые иногда называются значком гамбургера, расположенные на синей панели в верхней части страницы) слева от надписи «Microsoft Azure».

1. На панели навигации слева выберите **Пользователи**. Обратите внимание, что в вашем клиенте пользователи уже настроены.

1. В списке пользователей выберите **Adele Vance**.

1. Обратите внимание, что на панели навигации слева выбран пункт **Профиль**.  Покажите и обсудите сведения, отображаемые на странице профиля.

1. На панели навигации слева выберите **Назначенные роли**.  У этого пользователя нет назначенных административных ролей.  В верхней части страницы выберите **+ Добавить назначения**, чтобы показать типы доступных административных ролей.  Пока ничего не добавляйте, просто закройте страницу, нажав **X** в правой верхней части страницы.

1. На панели навигации слева выберите **Группы**.  Обсудите тот факт, что данный пользователь является участником нескольких групп.  Здесь можно также поговорить о типах групп.  Чтобы добавить этого пользователя в другие группы, следует просто выбрать **+ Добавить участия**.  Не добавляйте какие-либо новые группы, просто обсудите тему простоты добавления пользователя в существующие группы. Закройте окно групп, выбрав **X** в правом верхнем углу страницы.

1. На панели навигации слева выберите **Лицензии**. Обратите внимание, что этому пользователю назначены лицензии Microsoft 365 E5 и лицензия EMS.  Чтобы добавить лицензию, выберите **+ Назначения** в верхней части главного окна.  Отобразите лицензии для этого пользователя. НИЧЕГО не меняйте.  Закройте это окно, выбрав **X** в правом верхнем углу страницы.

1. На панели навигации слева выберите **Устройства**.  Ничего не отображается, однако вы можете сказать, что если этому пользователю нужно было назначить устройства, они бы появились здесь.

1. На панели навигации слева выберите **Назначение ролей Azure**.  Обратите особое внимание на следующее.
    1. Эта вкладка отличается от вкладки назначенных ролей, отображавшейся ранее: она предназначена для управления доступом на основе ролей в Azure Active Directory (подчеркните, что именно Active Directory).
    1. На этой вкладке вы сможете просмотреть назначение ролей пользователям для доступа к ресурсам Azure. Например, если вам было бы нужно создать группу ресурсов Azure и вы назначите пользователю Adele определенную роль, например роль владельца или участника для группы ресурсов, эта роль отобразилась бы здесь. Это часть управления доступом на основе ролей Azure (Azure RBAC). Данное назначение ролей управляется в рамках конкретного ресурса.

1. На панели навигации слева выберите **Способы проверки подлинности**.  Обратите внимание на описание «Здесь вы можете указать номера телефонов и адреса эл. почты, которые пользователи смогут использовать для выполнения многофакторной проверки подлинности и самостоятельного сброса пароля пользователя». Если настройки пользователя позволяют ему самостоятельно сбрасывать свой пароль (SSPR) или если он обязан применять многофакторную проверку подлинности (MFA), а вы как администратор заполнили это поле, значит данный пользователь уже зарегистрирован и не должен будет выполнять действия по регистрации для SSPR и MFA.  Обычным явлением является самостоятельная регистрация пользователя, а не регистрация его администратором.

1. На панели навигации слева выберите **Входы в систему**.  Здесь вы сможете просмотреть события входа для этого пользователя.  Вы можете ничего не увидеть для данного пользователя (Adele), поскольку она еще не выполнила вход в систему.

1. Выберите **X** в правом верхнем углу страницы. В результате вы вернетесь к списку пользователей.  Перед закрытием этого списка можно подчеркнуть, что многофакторная проверка подлинности отображается в верхней части страницы.  Выберите **Многофакторная проверка подлинности**.  Это приведет к открытию нового окна браузера.  Здесь можно установить многофакторную проверку подлинности для нескольких пользователей.  Это один из способов включения MFA для пользователей.  Мы расскажем больше о проверке MFA в контексте условного доступа, который обеспечивает более детальное управление многофакторной проверкой подлинности.  Закройте в браузере вкладку, посвященную многофакторной проверке подлинности.

1. Выберите **X** в правом верхнем углу страницы. Снова откроется главная страница клиента Contoso.

### Обзор

В рамках этой демонстрации вы просмотрели настройки существующего пользователя, включая группы, которым может быть назначен этот пользователь, рассмотрели доступность ролей и назначение пользовательских лицензий.