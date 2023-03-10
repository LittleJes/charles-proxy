## Пример подмены запроса в Charles Proxy

Перед началом я настроил Charles Proxy и добавил сертификаты на два устройства (В данном случае это iMac и iPhone) а также подключил телефон к прокси-серверу 

Для примера - проводить подмену запроса я буду в приложении популярной сети фастфуда

Цель: протестировать приложение на отображение большого количества бонусов и обмена бонусов на товар. 

![Screen1](https://github.com/LittleJes/charles-proxy/blob/main/assets/1.jpg)

В данный момент на моем аккаунте 3 бонуса. Их можно обменивать на различные позиции в кафе. 

Попробуем заменить это значение на другое число. Для этого нам в charles надо найти запрос который дергается при запуске приложения и передает количество бонусов

![Screen2](https://github.com/LittleJes/charles-proxy/blob/main/assets/2.jpg)

В данном случае, нам нужне следующая апишка: /api/v1/loyalty/user

Переходим в proxy - breakpoint settings
Нажимаем Enable Breakpoint а затем кнопку add. В открывшемся прописываем URL нашего запроса 

![Screen3](https://github.com/LittleJes/charles-proxy/blob/main/assets/3.jpg)

Теперь когда будет дергаться наша апишка, будет срабатывать Breakpoint. 

![Screen4](https://github.com/LittleJes/charles-proxy/blob/main/assets/4.jpg)

Менять ответ рано, сначала надо получить ответ от сервера, поэтому нажимаем Execute, после чего уже во владке "Edit response" - JSON меняем наше значение

![Screen5](https://github.com/LittleJes/charles-proxy/blob/main/assets/5.jpg)

Отлично! Теперь у нас бексконечное количество бонусов. 

![Screen6](https://github.com/LittleJes/charles-proxy/blob/main/assets/6.jpg)

Теперь переходим на экран где эти бонусы можно обменять и изменяем их количество  еще раз (апшика дергается повторно при переходе на этот экран)

![Screen7](https://github.com/LittleJes/charles-proxy/blob/main/assets/7.jpg)

Теперь выберам товар, на который мы хотим обемнять наши бонусы и...
Кнопка получить не доступна 

![Screen8](https://github.com/LittleJes/charles-proxy/blob/main/assets/8.jpg)

 Хоть и большое количество бонусов отображается корректно, обменять на предложонный товар мы их не можем. Следовательно тест пройдет