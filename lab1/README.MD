University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)  
Course: [Introduction to distributed technologies](https://github.com/itmo-ict-faculty/introduction-to-distributed-technologies)  
Year: 2024/2025  
Group: K4110c  
Author: Льдоков Роман Александрович  
Lab: Lab1  
Date of create: 02.01.2025  
Date of finished: 03.01.2025  

# Лабораторная работа №1 "Установка Docker и Minikube, мой первый манифест."

## Цель работы
Ознакомиться с инструментами Minikube и Docker, развернуть свой первый "под".

## Ход работы

### 1. На локальную машину были уставновлены Docker и Minikube

### 2. Развернут minikube cluster

```
minikube start
```

![image](./img/1.png)

### 3. Развернута "пода" HashiCorp Vault с использованием написанного манифеста

```
apiVersion: v1
kind: Pod
metadata:
  name: vault
  namespace: default
  labels:
    app: vault
spec:
  containers:
  - name: vault
    image: vault:1.13.3
    ports:
    - containerPort: 8200
```
![image](./img/2.png)

### 4. Выполнен проброс портов

```
kubectl port-forward pod/vault 8200:8200
```

![image](./img/3.png)

### 5. Открыта страница в браузе по ссылке http://localhost:8200

![image](./img/4.png)

### 6. В конце вывода команды найден токен

```
kubectl logs vault
```

![image](./img/5.png)

### 7. Успешно пройдена авторизация

![image](./img/6.png)

### Диаграмма

![image](./img/diagram.png)
