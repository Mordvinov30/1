![image](https://github.com/user-attachments/assets/c04e333d-d7cf-47dd-b5c8-1c774e8843d1)

Для начала устанавливаем гостевые дополнения
потом переходим к установке утилит 
`sudo yum install wget`

![image](https://github.com/user-attachments/assets/579dd3fb-ebb6-414d-8dd2-10fc7b86ad26)

`sudo yum install curl`

![image](https://github.com/user-attachments/assets/abc125b0-8ecb-4a7c-9d29-33368f0aa18e)

скачиваем репозиторий `sudo wget -P /etc/yum.repos.d/ https://download.docker.com/linux/centos/docker-ce.repo`

![image](https://github.com/user-attachments/assets/984f30ad-a6d1-41b0-8f55-ccaf88cdc5a3)

устанавливаем докер `sudo yum install docker-ce docker-ce-cli containerd.io`

![image](https://github.com/user-attachments/assets/b964c509-ef7c-4c53-8334-90b7952eef24)

разрешаем автозапукс `sudo systemctl enable docker --now`

![image](https://github.com/user-attachments/assets/bd53e912-2856-4a62-99fa-5d707b30baad)

проверяем версию докера и сохраняем ее в переменную `COMVER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep 'tag_name' | cut -d\" -f4)`

![image](https://github.com/user-attachments/assets/37f4a24c-37df-4232-8bfa-a02a0d7758ac)

![image](https://github.com/user-attachments/assets/e146644a-633e-408f-8c1d-ed7b211e6618)

проверяем версию докера `docker-compose --version`

![image](https://github.com/user-attachments/assets/eaec1279-7ac0-4306-a1f3-e9f86240e8f4)

копируем репозиторий `git clone https://github.com/skl256/grafana_stack_for_docker.git`

![image](https://github.com/user-attachments/assets/874355b4-790c-4810-87d6-096c7d621195)

переходим в другую папку `cd grafana_stack_for_docker`

![image](https://github.com/user-attachments/assets/e8079c6a-ea6d-4d56-a24a-6e499ff9ef4b)

создаем новый репозиторий `sudo mkdir -p /mnt/common_volume/swarm/grafana/config`

![image](https://github.com/user-attachments/assets/f630094c-c78b-439a-87b2-56015df1b028)

создаем места для хранения графаны и пометеуса `sudo mkdir -p /mnt/common_volume/grafana/{grafana-config,grafana-data,prometheus-data}`

![image](https://github.com/user-attachments/assets/52f855fa-fe89-4683-8c2f-b53e14bf5152)

создаем пустой файл `touch /mnt/common_volume/grafana/grafana-config/grafana.ini`

![image](https://github.com/user-attachments/assets/176d5d96-aa1b-48ec-b04f-bb302dbe9e67)

копируем все файлы с одного каталога в другой `cp config/* /mnt/common_volume/swarm/grafana/config/`

![image](https://github.com/user-attachments/assets/d3261f74-4611-4615-a942-c640cd3cceb1)

переименовываем файл grafana.yaml в docker-compose.yaml
`mv grafana.yaml docker-compose.yaml`

![image](https://github.com/user-attachments/assets/fd7a1c11-87cb-4a56-aae7-6f8650a150c6)

поднимаем докер `sudo docker compose up -d` 

![image](https://github.com/user-attachments/assets/27f24588-b8e8-4535-9442-ec93da7a8dfb)

вводим команду `sudo vi docker-compose.yaml` и переходим в файл
вносим в него изменения и тоже самое елаем с другим файлом `sudo vi prometheus.yaml`

переходим на сайт `localhost:3000`
Пользователь и пароль: admin. - Код графаны 1816. - Код прометеуса: http://prometheus:9090.

![image](https://github.com/user-attachments/assets/051d8127-fbcb-4e7c-9b01-28c4ded4c58a)

Создаем новый Dashboard

![image](https://github.com/user-attachments/assets/3ea83ca8-5099-4ca3-8214-99145c8eb593)
![image](https://github.com/user-attachments/assets/eeae326b-98ab-40f0-b098-7bc63f33d653)

далее выбираем визуализацию

![image](https://github.com/user-attachments/assets/fbf28b6b-9482-45e9-a136-5e8c3656ecd2)

нажимаем синию кнопку 

![image](https://github.com/user-attachments/assets/119eea07-ec91-46f4-870b-c6c35ff3365e)

выбираем прометеус

![image](https://github.com/user-attachments/assets/734f9ee4-33d8-4616-ba0c-5dc781c92cce)

заполняем как на фото

![image](https://github.com/user-attachments/assets/80bb0aa5-9dfa-466b-9529-e8c8ee5e2f3b)
![image](https://github.com/user-attachments/assets/ec9313da-30e0-40d0-8243-270b8805fb60)

возвращаемся на пару шагов назад и вместо визуализации выбираем импортирование

![image](https://github.com/user-attachments/assets/4084c58c-6fc0-42c3-b26c-8758a82c4352)

вводим код 

![image](https://github.com/user-attachments/assets/4ed243e0-a0d1-4740-8946-b7d924ff4c3b)

заполняем все и нажимаем ипорт

![image](https://github.com/user-attachments/assets/dc5da381-31c0-4245-b1d5-d8c5fc6c5f7b)
![image](https://github.com/user-attachments/assets/eaf9e709-a797-4087-aa90-242259c0fb30)

далее переходим на сайт localhost:8428 и на сайт localhost:9090

создаем викторию метрикс по той же инструкции что и прометеус только меняем код прометеуса и ставим No autentification

![image](https://github.com/user-attachments/assets/a8b52d66-d3a4-46a3-a3a6-c65bd83b39e4)

возвращаемся назад и открываем то что создали

![image](https://github.com/user-attachments/assets/18fa0746-13d4-40b3-a9b3-b75a44e4bd91)

в терминале вводим `echo -e "# TYPE light_metric1 gauge\nlight_metric1 0" | curl --data-binary @- http://localhost:8428/api/v1/import/prometheus `

Потом переходим на Victoria metrics и выбираем `vmui`
в строке вводим `light_metric1`

![image](https://github.com/user-attachments/assets/5cafd310-b36e-4ce8-81b4-1053cfe773c4)

переходим в графану и тоже самое пишем в строке 

![image](https://github.com/user-attachments/assets/d9cb1a9d-abd1-4b0a-8dc6-fbde0c489f8f)




























