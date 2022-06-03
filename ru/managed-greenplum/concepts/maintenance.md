# Техническое обслуживание

Под техническим обслуживанием понимается:

* автоматическая установка обновлений и исправлений СУБД для хостов (в т. ч. для выключенных кластеров);
* изменение класса хостов и объема хранилища;
* другие сервисные работы.

Техническое обслуживание проводится в следующем порядке:

1. [Хосты-сегменты](index.md) последовательно проходят техническое обслуживание. Порядок хостов в очереди определяется случайным образом. Если во время технического обслуживания потребуется перезагрузка хоста-сегмента, он станет недоступным на это время.
1. Резервный (STANDBY) хост-мастер проходит техническое обслуживание. Если во время технического обслуживания потребуется перезагрузка резервного хоста-мастера, он станет недоступным на это время.
1. Первичный (PRIMARY) хост-мастер проходит техническое обслуживание. Если во время технического обслуживания потребуется перезагрузка первичного хоста-мастера и он станет недоступным, его роль возьмет на себя резервный хост-мастер. Если вы используете для доступа к кластеру FQDN или IP-адрес первичного хоста-мастера, такой кластер может стать недоступным. Чтобы обеспечить бесперебойную работу приложения, подключайтесь к кластеру через [особый FQDN](../operations/connect.md#fqdn-master), всегда указывающий на первичный хост-мастер.