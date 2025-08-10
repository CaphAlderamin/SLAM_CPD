# SLAM\_CPD

**SLAM (Simultaneous Localization and Mapping) с использованием метода CPD (Coherent Point Drift)**

В этом репозитории представлена реализация алгоритма SLAM на основе метода Coherent Point Drift (CPD) для построения карты окружающей среды и одновременной локализации робота.

---

## 📚 Оглавление

- [Описание проекта](#project)
- [Основные возможности](#opportunities)
- [Требования](#requirements)
- [Установка](#installation)
- [Использование](#using)
- [Структура репозитория](#structure)
- [Демонстрация](#demonstration)
- [Полезные ссылки](#links)
---

## 📖 Описание проекта <a name="project"></a>

Данный проект реализует алгоритм одновременной локализации и построения карты (SLAM) с применением метода Coherent Point Drift (CPD). Метод CPD позволяет эффективно выравнивать облака точек, что используется для сопоставления сканов лидара/датчиков с уже построенной картой.

Метод Coherent Point Drift (CPD) основан на идее моделирования одного облака точек как центров гауссовой смеси, а другого — как сэмплы из этой смеси. Основная цель — найти трансформацию (жёсткую, аффинную или нелинейную), которая максимизирует правдоподобие гауссовской смеси при переводе точек-образцов во второе облако:
1. Модель Гауссовой смеси (GMM): каждую точку исходного облака рассматривают как центр гауссовой компоненты GMM.
2. Вероятностная регистрация: точки второго облака «плывут» в сторону комплекта центров GMM, минимизируя энергию распределения.
3. EM-алгоритм: на каждом шаге оценивается апостериорное распределение (E‑шаг), затем обновляются параметры трансформации (M‑шаг).
4. Гладкость и когерентность: термин «Coherent» подчёркивает регуляризацию, обеспечивающую непрерывную и гладкую деформацию всего множества точек без разрывов.

Преимущества CPD:
- Стабильная регистрация даже при значительном зашуме и выбросах.
- Поддержка разных типов трансформаций (жёстких, нелинейных).
- Прямая интеграция в SLAM для оценки смещения между последовательными сканами.

Алгоритм состоит из двух ключевых компонентов:

1. **Occupancy Grid Mapping** — построение решетчатой карты оккупации на основе сенсорных данных (реализация класса `Map` по главе 9 «Probabilistic Robotics» Sebastian Thrun).
2. **CPD Data Association** — согласование текущего облака точек с картой для оценки положения робота.

Демонстрации алгоритма в Colab: [Открыть в Colab](https://colab.research.google.com/drive/1UhOAbh55-v8iiZLBuziz1ZeiCRnEZj2k?usp=sharing)

---

## 🚀 Основные возможности <a name="opportunities"></a>

- Построение и обновление карты занятости среды (Occupancy Grid).
- Согласование 2D-сканов лидара с картой с помощью алгоритма CPD.
- Визуализация результатов работы в Jupyter Notebook.
- Демонстрация работы на различных конфигурациях комнат.

---

## 🎯 Требования <a name="requirements"></a>

- Python 3.10+
- Библиотеки (устанавливаются из `requirements.txt`):
  - `scipy`
  - `numpy`
  - `pandas`
  - `matplotlib`
  - `pycpd`

---

## 📥 Установка <a name="installation"></a>

```bash
# Клонируем репозиторий
git clone https://github.com/CaphAlderamin/SLAM_CPD.git
cd SLAM_CPD

# Создаем виртуальное окружение conda (рекомендуется)
conda create -n slam_cpdenv python=3.10 -y
conda activate slam_cpdenv

# Устанавливаем ffmpeg для записи видео
conda install -c conda-forge ffmpeg
# Устанавливаем дополнительные зависимости из файла requirements.txt
pip install -r requirements.txt
```

---

## 💻 Использование <a name="using"></a>

1. Запустите Jupyter Notebook или любой другой интерпретатор Python поддерживающий формат Notebook.
2. Откройте файл `SLAM_CPD.ipynb` и выполните все ячейки по порядку.

---

## 📂 Структура репозитория <a name="structure"></a>

```
SLAM_CPD/
├─ videos/                  # Примеры анимаций работы алгоритма
│  ├─ animation_room1.H.mp4
│  ├─ animation_room2.-.mp4
│  ├─ animation_room3._notaccurate.mp4
│  ├─ animation_room3._accurate.mp4
│  └─ animation_room4.house.mp4
├─ SLAM_CPD.ipynb           # Основной ноутбук с примерами и визуализацией
├─ requirements.txt         # Зависимости проекта
└─ README.md                # Описание проекта
```

---

## 🎥 Демонстрация <a name="demonstration"></a>

- **"H"-образная комната**: `videos/animation_room1.H.mp4`

  <video controls src="videos/animation_room1(H).mp4" title="Title" width=50%></video>

- **"-"-образная комната**: `videos/animation_room2.-.mp4`

  <video controls src="videos/animation_room2(-).mp4" title="Title" width=50%></video>

- **"∷"-образная (низкая частота сканирования)**: `videos/animation_room3._notaccurate.mp4`

  <video controls src="videos/animation_room3(∷)_notaccurate.mp4" title="Title" width=50%></video>

- **"∷"-образная (высокая частота сканирования)**: `videos/animation_room3._accurate.mp4`

  <video controls src="videos/animation_room3(∷)_accurate.mp4" title="Title" width=50%></video>

- **"House"-образная комната**: `videos/animation_room4.house.mp4`

  <video controls src="videos/animation_room4(house).mp4" title="Title" width=50%></video>
  
---

## 🔗 Полезные ссылки <a name="links"></a>

- Книга «Probabilistic Robotics» (Sebastian Thrun et al.): [PDF](https://github.com/literator1996/veroyatnostnaya_robototehnica/blob/master/src/9/1-9-ready2final-inedit.pdf)
- Gist с примером использования: [superjax/33151f018407244cb61402e094099c1d](https://gist.github.com/superjax/33151f018407244cb61402e094099c1d)


