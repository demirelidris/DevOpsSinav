# DevOpsSinav

Bu repository staj kapsamında istenilen haftalık çalışmaları kapsamaktadır.



1- Alpine üzerine htop ve curl komutlarının kurulu olduğu bir image oluşturun

Dockerfile: İmage oluşturma işlemlerini otomatize etmek için kullanılan bir dosyadır.Bu dosyanın ismi "Dockerfile" olmalıdır.

<img width="457" alt="Screenshot 2021-08-09 at 15 51 57" src="https://user-images.githubusercontent.com/82338626/128709021-6569878d-e4a7-4393-91e3-37de728b66fb.png">

FROM alpine:latest
-> Burada alpine image'ının latest versiyonunu eğer localimizde böyle bir image yoksa DockerHub'dan Docker Engine vasıtasıyla çekiyoruz.


-> sonrasında indirilen image içerisinde aşağıdaki komutların çalıştırılmasını sağlıyoruz.
RUN apk update 

RUN apk add curl

RUN apk add htop

<img width="795" alt="Screenshot 2021-08-09 at 14 27 59" src="https://user-images.githubusercontent.com/82338626/128709447-f1e41d86-6c78-4b07-9f67-9b5f49bbb3ea.png">
<img width="798" alt="Screenshot 2021-08-09 at 14 27 44" src="https://user-images.githubusercontent.com/82338626/128709454-6e0db2a0-fdf5-46eb-a3da-d984c8ba2658.png">

Dockerfile dosyası çalıştırıldığında alpine ve bizim içinde özle olarak yüklenmesini istediğimiz 2 image oluşturuyor. Özelleştridiğimiz image aslında alpine image üzerine kurulan paketlerin olduğu image'dır.



2- Wordpress docker image'ını ve mysql image'ını docker-compose ile ayaga kaldırın

Docker-compose: Infrastructure as Code formatında tek bir dosyada bütün containerları oluşturmamızı ve ayağa kaldırmamızı sağlıyor.

<img width="420" alt="Screenshot 2021-08-09 at 16 18 20" src="https://user-images.githubusercontent.com/82338626/128712589-c8137df7-83d8-41ab-b90e-08d981940edb.png">


Bu şekilde wordpress ve mysql imagelarını indirip çalışacakları portları image'ları ve verilerini kaydedecekleri volumeleri belirtmiş oluyoruz.

docker-compose up -d komutuyla docker-compose.yaml dosyamızı çalıştırıyoruz.

<img width="1060" alt="Screenshot 2021-08-09 at 14 46 38" src="https://user-images.githubusercontent.com/82338626/128710731-2ddd5547-e03b-49ee-81fe-9cf617ef88ec.png">

Containerlarımızın ayağa kalktığını görebiliyoruz.

Web browser üzerinde localhostumuzun verdiğimiz poruna bağlandığımızda ise 

<img width="1171" alt="Screenshot 2021-08-09 at 14 45 08" src="https://user-images.githubusercontent.com/82338626/128710885-fe7bee0d-298f-48f3-9d44-389f6d99830d.png">

<img width="1166" alt="Screenshot 2021-08-09 at 14 55 40" src="https://user-images.githubusercontent.com/82338626/128710919-fc5ce6a7-d723-458f-b941-9bc5f00ef901.png">

Wordpress'e bağlanmış oluyoruz.



3- Ansible ile Ubuntu üzerinde docker kurulumu yapacak playbook.

Ansible, manuel yapılan işlemleri otomatize etmek için sıkça kullanılır. Elimizde tuttuğumuz inventory dosyamızdaki sunuculara SSH ile bağlanıp kendisine verilen görevi yerine getirir.

host.ini dosyasının içeriği

<img width="425" alt="Screenshot 2021-08-09 at 16 09 26" src="https://user-images.githubusercontent.com/82338626/128711345-b190e848-4a5d-42e5-a4aa-664ee362a3ca.png">

roles.yaml dosyasının içeriği

<img width="304" alt="Screenshot 2021-08-09 at 16 09 47" src="https://user-images.githubusercontent.com/82338626/128711381-bf5f4b05-fa83-4b4f-b489-551a8254d73b.png">

roles/docker/tasks altında bulunan main.yaml dosyasının içeriği

<img width="631" alt="Screenshot 2021-08-09 at 16 10 43" src="https://user-images.githubusercontent.com/82338626/128711500-7b6d51ef-2ba2-4f32-b08d-5103ecd80891.png">

Playbook'u çalıştırmadan önce client makinemin durumu

<img width="925" alt="Screenshot 2021-08-09 at 16 41 52" src="https://user-images.githubusercontent.com/82338626/128715995-633b36bd-9c9c-434c-9793-2825abb6f966.png">


Playbook'umu çalıştırdığım da ise:

<img width="1054" alt="Screenshot 2021-08-09 at 15 36 10" src="https://user-images.githubusercontent.com/82338626/128712173-1a6e6b66-05ef-4a1d-8d19-296cee50bb83.png">

<img width="769" alt="Screenshot 2021-08-09 at 16 42 03" src="https://user-images.githubusercontent.com/82338626/128716053-1bc55436-60f4-4455-b970-c3c9cf3764bb.png">






