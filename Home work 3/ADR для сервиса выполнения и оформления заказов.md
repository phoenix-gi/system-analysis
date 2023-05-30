## ADR-001 Изоляция выполнения и оформления заказов в сервис

### Status - proposed

### Context
MCF был разделен на разные поддомены, и соответствующие им боундед-контексты.
К каждому боундед-контексту были определены наиболее важные требования.

Вот их список:
- **Работа с заказами**
  - *Оформление заказов*
    - Agility, Deployability, Testability
    - Maintainability, Modifiability, Availability, Performance, Usability
  - *Выполнение заказов*
    - Agility, Deployability, Testability
    - Maintainability, Modifiability
  - *Расчет стоимости услуг*
    - Agility, Deployability, Testability
    - Maintainability, Modifiability, Consistency, Securability
- **Найм воркеров**
  - *Отбор кандидатов в воркеры*
    - Agility, Deployability, Testability
    - Scalability
- **Подбор воркера под заказ клиента**
  - *Матчинг*
    - Agility, Deployability, Testability
    - Availability
- **Мотивация менеджеров**
  - *Ставки на воркеров*
    - Agility, Deployability, Testability
    - Simplicity, Usability
- **Качественное выполнение услуг**
  - *Отслеживание результатов выполнения заказов*
    - Agility, Deployability, Testability
    - Simplicity, Usability
- **Увеличение скорости обслуживания**
  - Сборка расходников
    - Agility, Deployability, Testability
    - Simplicity, Usability
  - Планирование работы воркеров
    - Agility, Deployability, Testability
    - Simplicity, Usability
- **Выплаты сотрудникам**
  - *Расчета выплат*
    - Agility, Deployability, Testability
    - Consistency, Securability


### Decision - изолировать в сервис
Принято решение выделить выполнение и оформление заказов в отдельный сервис.
Причины:
- Оба контекста находятся в одном поддомне
- У них есть общие важные характеристики Agility, Deployability, Testability, Maintainability, Modifiability
- Эти контексты тесно связаны между собой

Сервис будет реализован в виде монолита, так как мы его выделили из общей системы, мы не можем разбить его на микросервисы, ведь сервисов станет слишком много.

### Consequences
Принятое решение выделит в отдельный сервис, который будет изолирован от остальных, и это не повлечет за собой большой ответственности при проблемах безопасности, так как к этому сервису, по сравнению с остальными требования безопасности не самые высокие.

### Сompliance
Проверка полученного решения осуществляется вручную
Анализ метрик cohesion, coupling
Проверка производительнотси при высокой нагрузке
