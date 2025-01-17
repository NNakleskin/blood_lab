[[Разметка]]
**Bounding Boxes** (ограничивающие прямоугольники) — это прямоугольные рамки, которые используются для выделения и локализации объектов на изображении. Этот метод широко используется в задачах **обнаружения объектов (Object Detection)**, где задача состоит не только в классификации объекта, но и в нахождении его местоположения на изображении.

### Как работают Bounding Boxes?

Bounding Box представляет собой прямоугольник, который обворачивает объект на изображении. Обычно он задается с помощью **координат двух углов**:

- **Левый верхний угол (x₁, y₁)**
- **Правый нижний угол (x₂, y₂)**

Эти координаты определяют прямоугольник, в который "вписан" объект. Таким образом, каждая рамка указывает на точное расположение объекта, что помогает нейросети не только распознавать объекты, но и точно их локализовать.

### Формат разметки Bounding Boxes

Для разметки изображений с bounding boxes используется несколько форматов:

1. **COCO формат** (один из самых популярных):
    - Каждый объект на изображении имеет соответствующую метку и координаты bounding box.
    - Пример: для объекта "собака" с координатами bounding box `(x₁, y₁, x₂, y₂)` будет добавлена метка "собака" и прямоугольник, ограничивающий её.
2. **Pascal VOC формат**:
    - Каждое изображение и объект имеют свои XML файлы, где указаны метки и координаты прямоугольников.
    - Пример:
        
        xml
        
        Copy code
        
        `<object>   <name>dog</name>   <bndbox>     <xmin>30</xmin>     <ymin>50</ymin>     <xmax>200</xmax>     <ymax>300</ymax>   </bndbox> </object>`
        
3. **YOLO (You Only Look Once) формат**:
    - В отличие от других форматов, YOLO представляет координаты bounding box в нормализованном виде относительно размера изображения.
    - Пример:
        - Каждому объекту присваиваются: метка, координаты центра прямоугольника (cx, cy) и размеры прямоугольника (width, height), нормализованные по ширине и высоте изображения.

### Как размечаются данные с помощью Bounding Boxes?

Для создания bounding boxes используется разметка изображений вручную с помощью специализированных инструментов. Процесс обычно включает в себя:

1. **Выбор инструмента разметки**:
    - Программы, такие как **LabelImg**, **RectLabel**, **VGG Image Annotator (VIA)**, позволяют вручную рисовать bounding boxes вокруг объектов.
2. **Рисование bounding box**:
    - После загрузки изображения пользователь рисует прямоугольники вокруг объектов, указывая их положение.
    - Каждому прямоугольнику присваивается метка объекта (например, "собака", "автомобиль").
3. **Сохранение данных**:
    - После того как все объекты на изображении размечены, программа генерирует файл, содержащий информацию о координатах прямоугольников и соответствующих метках для каждого объекта.

### Преимущества и недостатки Bounding Boxes:

**Преимущества**:

- **Простота**: Относительно простая и понятная техника разметки для локализации объектов.
- **Быстрота**: Процесс разметки с использованием bounding boxes быстрее, чем, например, полная сегментация объектов.
- **Широкая применимость**: Используется в широком спектре задач, таких как распознавание лиц, автомобилей, животных и т.д.

**Недостатки**:

- **Не точная форма**: Bounding box может не точно соответствовать форме объекта, особенно если объект имеет сложные контуры, как, например, в случае с людьми, животными или неоднородными предметами.
- **Множество объектов**: Если на изображении несколько объектов одного типа (например, несколько собак), bounding box может быть сложным для точного выделения каждого объекта отдельно.

### Применение Bounding Boxes:

Bounding boxes активно используются в таких задачах, как:

- **Обнаружение объектов**: например, для распознавания автомобилей на дорогах, лиц на фотографиях, или животных в природе.
- **Автономные транспортные средства**: распознавание других автомобилей, пешеходов и препятствий.
- **Медицина**: например, для обнаружения опухолей или других аномалий на медицинских снимках.

### Пример задачи:

Предположим, вам нужно обучить нейросеть для обнаружения автомобилей на изображении. Вам нужно:

1. Собрать данные с изображениями, на которых есть автомобили.
2. Разметить каждое изображение, нарисовав прямоугольные рамки вокруг каждого автомобиля.
3. Обучить модель на этих данных, чтобы она могла распознавать автомобили и точно локализовывать их на новых изображениях.

В результате, нейросеть будет предсказывать для новых изображений не только метку (автомобиль), но и точные координаты прямоугольника, в котором этот автомобиль находится.х