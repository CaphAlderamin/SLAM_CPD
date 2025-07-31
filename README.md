# SLAM_CPD
#### SLAM (Simultaneous Localization and Mapping) using the CPD (Cooperative Point Drift) Method.

Метод CPD (Coherent Point Drift) (Когерентный дрейф точек) - это алгоритм машинного обучения, предназначенный для кластеризации данных. Он основан на идее, что каждая точка данных принадлежит определенному кластеру, и кластеры имеют свои центры. Метод CPD позволяет обрабатывать данные с различными распределениями и шума, так как он учитывает расстояния между точками и центрами кластеров.

Код проекта в Colab: https://colab.research.google.com/drive/1UhOAbh55-v8iiZLBuziz1ZeiCRnEZj2k?usp=sharing

Класс "Map" является реализацией метода Occupancy Grid Mapping представленного в главе 9 "Вероятностной робототехники" Себастьяна Труна (Sebastian Thrun) и др.

Книга: https://github.com/literator1996/veroyatnostnaya_robototehnica/blob/master/src/9/1-9-ready2final-inedit.pdf

Код: https://gist.github.com/superjax/33151f018407244cb61402e094099c1d

## Демонстрация работы алгоритма в условиях различной геометрии комнат.

#### Демонстрация с "H"-образной комнатой:

https://github.com/user-attachments/assets/af181bc7-5b44-4ea4-ba18-c066af2d9c09

#### Демонстрация с "\"-образной комнатой:

https://github.com/user-attachments/assets/9877ff84-82e0-4bfa-9d15-6bb9d283d267

#### Демонстрация с "∷"-образной комнатой (сканирование с низкой частотой):

https://github.com/user-attachments/assets/14492627-364f-44c6-97c4-25bdf5da61c8

#### Демонстрация с "∷"-образной комнатой (сканирование с высокой частотой):

https://github.com/user-attachments/assets/fd4d49b7-a85a-4236-9215-d7a7c4e03aae

#### Демонстрация с "house"-образной комнатой:

https://github.com/user-attachments/assets/4129f326-476e-416f-b01d-ddcdf8b7e04c
