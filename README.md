![alt text](./active-nginx-process.png)

Nginx активен и работает — systemctl status nginx показывает active (running), мы так же видим PID master-процесса 7140

![alt text](./cd-to-nginx-catalog.png)

 Переходим в Nginx каталог который находиться по /etc/nginx/ и тут мы видим все конфигурационные файлы 

 ![alt text](./check-nginx-with-curl.png)

После выполнения cutl localhost можем видеть базовую страничку приветствия в nginx и давайте так же взглянем на нее в браузере

 ![alt text](./check-in-browser.png)
