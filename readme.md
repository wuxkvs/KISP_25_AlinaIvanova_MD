# Полное рукводство по Expo

**Expo** — это полноценная open-source экосистема и фреймворк для разработки нативных кроссплатформенных приложений для Android, iOS и Web. Платформа позволяет писать логику приложения один раз на JavaScript/TypeScript, запуская её везде.
## Создание проекта
- ```npx create-expo-app@latest```

- ```npx create-expo-app@latest --example```

- ```npx create-expo-app@latest --example with-widgets```

## Среды тестирования кода
* **Expo Go** — бесплатное мобильное приложение для App Store и Google Play. Позволяет мгновенно открывать локальный проект на физическом телефоне, просто отсканировав QR-код. Идеально подходит для обучения и создания прототипов.
* **Сборки разработки** (Development Builds) — это ваша персональная копия Expo Go, созданная специально под конкретный проект. Она необходима, если вы добавляете кастомный нативный код (плагины), используете сторонние сложные библиотеки или готовите приложение к релизу в магазины.
* **Expo Snack** — полностью браузерная песочница. Позволяет писать и тестировать код Expo с нулевой локальной настройкой компьютера.

# Ключевые компоненты архитектуры

### Expo Router (Файловая маршрутизация)
Позволяет управлять экранами приложения по принципу веб-разработки (аналогично Next.js).
* Каждый файл внутри директории src/app/ автоматически становится экраном (роутом).
* Поддерживает нативную анимацию переходов, создание вложенных меню и вкладок (tabs).
* Обеспечивает глубокую интеграцию со ссылками (Deep Linking) из коробки.
### Модули Expo SDK и Expo UI
Expo предоставляет огромный набор стандартизированных готовых модулей для работы с системными функциями смартфона
* **Image, Camera** — работа с графикой и камерой устройства.
* **Notifications** — отправка и обработка пуш-уведомлений.
* **Expo UI** — стабильные нативные интерфейсные примитивы на базе Jetpack Compose (для Android) и SwiftUI (для iOS), дающие высокую производительность анимаций.
### Непрерывная нативная генерация (CNG)
Концепция Continuous Native Generation избавляет разработчика от необходимости вручную править файлы конфигураций в папках android и ios. Платформа сама генерирует нативный код на основе вашего файла конфигурации app.json и аргументов команды prebuild.

# Инструменты для разработки
## Expo CLI
**Expo CLI** — это инструмент разработки, который устанавливается автоматически вместе с пакетом при создании нового проекта. Вы можете использовать его, используя (Node.js package runner).```expo npx```
Он создан для того, чтобы помочь вам быстрее двигаться на этапе разработки приложения. Например, ваше первое взаимодействие с Expo CLI — это запуск сервера разработки с помощью команды: ```npx expo start```
Ниже приведён список распространённых команд, которые вы будете использовать с Expo CLI при разработке приложения:

```npx expo start```

```npx expo prebuild```

```npx expo run:android```

```npx expo run:ios```

```npx expo install```

```package-name```

```npx expo lint```

В двух словах, Expo CLI позволяет разрабатывать, компилировать, запускать приложение и многое другое. Смотрите справочник Expo CLI для получения дополнительных доступных опций и действий, которые можно выполнить с помощью CLI.

## EAS CLI
EAS CLI используется для входа в ваш аккаунт Expo и компиляции приложения с помощью различных сервисов EAS, таких как Build, Update или Submit. Вы также можете использовать этот инструмент, чтобы:

* Опубликуйте своё приложение в магазинах приложений
* Создайте разработку, превью или продакшн для вашего приложения
* Создание обновлений по эфиру (OTA)
* Управляйте учетными данными вашего приложения
* Создайте ad hoc профиль для устройства iOS

```npm install --global eas-cli```

## Expo Doctor
**Expo Doctor** — это инструмент командной строки, используемый для диагностики проблем в вашем проекте Expo. Чтобы воспользоваться им, выполните следующую команду в корневой директории вашего проекта:

```npx expo-doctor```

## Орбита
**Orbit** — это приложение для macOS, Windows и Linux, которое позволяет:

* Устанавливайте и запускайте сборки с EAS на физических устройствах и эмуляторах.
* Устанавливайте и запускайте обновления от EAS на эмуляторах Android или симуляторах iOS.
* Запускайте проекты с закусками на эмуляторах Android или симуляторах iOS.
* Используйте локальные файлы для установки и запуска приложений. Orbit поддерживает любые Android .apk, совместимые с iOS Simulator .app или специальные подписанные приложения.
* Посмотрите список закреплённых проектов на вашей панели управления EAS.
### Установка

```brew install expo-orbit```

## Expo Tools для VS Code
**Expo Tools**— это расширение VS Code, которое улучшает опыт разработки при работе с конфигурационными файлами приложений. Он предоставляет такие функции, как автозаполнение и intellisense для файлов, таких как конфигурация приложений, конфигурация EAS, конфигурация хранилища и конфигурации модуля Expo.

# Навигация в приложениях Expo и React Native
Основная библиотека React Native не включает встроенного навигационного решения, поэтому вы можете выбрать навигационную библиотеку, которая лучше всего соответствует вашим потребностям. Для приложений Expo и React Native обычно выбирают между React Navigation и Expo Router.
## React Navigation
**React Navigation** — это навигационная библиотека на основе компонентов, широко используемая в экосистеме React Native. Он позволяет компоназировать навигаторы стека, вкладок и ящиков полностью в коде, чтобы реализовать сложные потоки, пользовательские переходы и специфичные для приложения UX-паттерны.
## Экспо-роутер
**Expo Router**— это файловая библиотека маршрутизации для проектов Expo и React Native. Следуя правилам каталога приложений, файлы превращаются в маршруты и интегрируются с Expo for Expo CLI и пакетированием без дополнительной настройки. Библиотека также добавляет такие функции, как типизированные маршруты, динамические маршруты, ленивое объединение в разработке, статическое рендеринг для веба и автоматическое глубокое ссылание.

# Обучающее: Использование React Native и Expo
## О React Native и обучающих материалах по Expo
> Данное руководство предназначено для первичного знакомства с платформой Expo и инструментами Expo SDK. Программа курса включает в себя:
* Инициализацию приложения на TypeScript с использованием стандартного шаблона.

* Проектирование двуэкранной навигации с нижними вкладками при помощи Expo Router.

* Изучение принципов макетирования интерфейса и его адаптацию через Flexbox.

* Работу с нативным API для выбора изображений из галереи пользователя.

* Разработку модального окна со стикерами через компоненты <Modal> и <FlatList> в 
React Native.
* Внедрение обработки жестов для интерактивного взаимодействия с объектами.

* Применение сторонних модулей для создания снимков экрана и их записи на диск.

* Анализ и учет межплатформенных различий (Android, iOS и Web).

* Финальное конфигурирование иконки, сплэш-скрина и строки состояния.

Описанные темы составляют базовый стек знаний, необходимый для разработки на Expo. 
Самостоятельное освоение материала займет около двух часов. 

Курс разделен на девять последовательных глав, что позволяет прерывать обучение и возвращаться к нему по мере необходимости. 

Каждая часть снабжена актуальными листингами кода, благодаря чему вы можете создавать проект с нуля либо использовать готовые фрагменты для интеграции.

### Как пользоваться этим уроком
``` import { StyleSheet, Text, View } from 'react-native'; 
export default function Index() {
  return (
    <View style={styles.container}>
      <Text>Hello world!</Text>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
    alignItems: 'center',
    justifyContent: 'center',
  },
});
```
# Создание первого приложения на Expo 
### Инициализировать новый проект Expo, запустить его на смартфонах и в веб-версии, а также отредактировать главный экран. В рамках туториала создается приложение StickerSmash.

**1. Требования перед стартом**
* Установленное приложение Expo Go на физическом устройстве (iOS или Android).

* Node.js (LTS-версия).

* Редактор кода (VS Code или аналог).

* Терминал (macOS, Linux, Windows PowerShell / WSL2).

* Базовые знания: Понимание TypeScript и React

**2. Инициализация проекта и загрузка ресурсов**

Для создания приложения используется инструмент командной строки create-expo-app.

>Команда для создания проекта:

``` npx create-expo-app@latest StickerSmash ```

Плюсы дефолтного шаблона:
* Автоматически предустановлен пакет expo и инструменты Expo CLI.

* Встроен навигатор вкладок (Expo Router).

* Готовность к кроссплатформенной работе (iOS, Android, Web).

* Из коробки настроен TypeScript.

Подготовка медиафайлов:

Необходимо скачать архив с ресурсами туториала, разархивировать его и заменить стандартные изображения в папке проекта ``` assets/images.  ```

**3. Сброс шаблонного кода**

> Поскольку приложение создается с нуля, дефолтный код удаляется специальным скриптом:

``` npm run reset-project ```


**4. Запуск сервера разработки**

> Запуск локального сервера выполняется командой:

``` npx expo start ```

**На смартфонах:** В терминале отобразится QR-код.Для Android его нужно отсканировать через функцию Scan QR code внутри приложения Expo Go. Для iOS — просто через стандартное приложение Камера.

**В вебе:** Чтобы открыть приложение в браузере на ПК, нужно нажать клавишу W в терминале.

**5. Редактирование главного экрана**

Импортируйте из и создайте объект для определения наших пользовательских стилей.``` StyleSheetreact-nativestyles ```

Добавьте свойство с значением. Это меняет цвет фона. ``` styles.container.backgroundColor<View>#25292e ```

Замените значение по умолчанию на «Главный экран».<Text>

Добавьте свойство с значением (белый) для изменения цвета текста.``` styles.text.color<Text>#fff```

 # Добавление навигации в Expo

> Изучить основы Expo Router, настроить стековую навигацию (Stack) и создать нижнюю панель вкладок (Tabs) с двумя экранами.

### Базовые принципы Expo Router
Expo Router использует файловую маршрутизацию (как в Next.js) для iOS, Android и Web. Основные правила:
* Папка app: Находится по пути ```src/app.``` Любой файл в ней автоматически становится экраном приложения.

* Корневой макет (Root layout): Файл ```src/app/_layout.tsx.``` Он определяет общие элементы интерфейса для всех экранов.

* Индексы: Файл ```index.tsx``` внутри папки отвечает за корневой маршрут (/).

### Создание нового экрана и Стека (Stack)
**Стековый навигатор (Stack)** — это база для переходов. При переходе новый экран накладывается поверх старого (анимация сверху на Android, справа на iOS).

Шаг 1: Создается файл ```src/app/about.tsx``` 

Шаг 2: В ```src/app/_layout.tsx``` подключается компонент <Stack> и задаются заголовки (```options={{ title: '...' }}```) для экранов ```index``` и ```about.```

### Навигация между экранами
Для переходов используется компонент <Link> из библиотеки expo-router.
* Компонент принимает проп href с указанием пути (например, ```href="/about"```).

* Стилизуется точно так же, как стандартный <Text> (можно менять ```fontSize, color``` и т.д.).

### Обработка ошибки 404 (Not Found)
Чтобы приложение не падало при переходе на несуществующий маршрут, используется специальный файл ```+not-found.tsx в папке src/app```. В нем настраивается экран-заглушка с кнопкой возврата на главную.

### Создание нижней панели вкладок (Bottom Tabs)
Для группировки экранов в табы используется папка со специальным именем в круглых скобках — (tabs). Скобки означают, что папка организует структуру, но не добавляет сегмент в URL-путь.
* Новая структура папок:

``` 
src/app/
├── _layout.tsx (Корневой стек)
├── +not-found.tsx
└── (tabs)/
    ├── _layout.tsx (Макет вкладок)
    ├── index.tsx (Главная вкладка)
    └── about.tsx (Вкладка "О нас")
```

* **Изменение src/app/_layout.tsx:** Теперь корневой стек содержит только одну группу name="(tabs)" и скрывает для неё верхний заголовок (```headerShown: false```). Это позволяет экрану 404 перекрывать табы, если произойдет ошибка.

* **В** ```src/app/(tabs)/_layout.tsx``` импортируется компонент <Tabs> и его дочерние элементы <Tabs.Screen> для настройки вкладок.

### Стилизация табов и иконки
> Для добавления иконок используется библиотека векторной графики.
* **Установка пакета**: Сверните сервер разработки (Ctrl + C) и выполните команду:

```npx expo install @expo/vector-icons```

После этого снова запустите сервер через ```npx expo start.```

* Добавление иконок и цвета:
В файле (tabs)/_layout.tsx импортируется набор иконок (например, Ionicons). Через свойство tabBarIcon настраивается отображение разных иконок в зависимости от того, активна ли вкладка в данный момент (focused).

* Кастомизация цветов (screenOptions): 
    * ```tabBarActiveTintColor: '#ffd33d'``` — задает желтый цвет активной вкладке.

    * ```headerStyle и tabBarStyle``` — окрашивают верхнюю панель и нижний бар в темный цвет приложения (#25292e).
    * ```headerShadowVisible: false``` — скрывает разделительную линию-тень под заголовком.

# Сборка экрана приложения 

 Создать главный экран приложения StickerSmash, научиться выводить изображения с помощью ```expo-image``` и разрабатывать кастомные интерактивные кнопки на базе компонента ```Pressable.```

 ### Анатомия главного экрана
 > Интерфейс разбивается на два основных визуальных блока:

* **Центральная часть:** Крупная область для отображения фоновой фотографии.

*  **Нижняя часть (футер):** Две кнопки управления. Первая кнопка («Choose a photo») имеет сложную структуру: желтую рамку, иконку и текст в одну строку. Вторая кнопка («Use this photo») оформлена в виде простого текста.

### Отображение картинок через expo-image
Для кроссплатформенного рендеринга графики используется библиотека expo-image (уже встроена в стандартный шаблон). Компонент <Image> принимает статические файлы через ```require()``` или ссылки из сети через свойство ```uri```.
* Для чистоты архитектуры все кастомные элементы выносятся за пределы папки ```src/app ```(где живут только маршруты и макеты) в отдельную директорию ```src/components/.```

* Создается вспомогательный компонент ```src/components/image-viewer.tsx```, принимающий проп imgSource.

Импорт через @: Символ @ в путях (например, ```@/components/...```) — это настроенный в ```tsconfig.json ```алиас, который позволяет избегать громоздких относительных путей вида ```../../components``` 

### Создание кнопок с помощью Pressable
Вместо устаревших способов обработки тапов в React Native рекомендуется универсальный компонент <Pressable>. Он гибко распознает одиночные касания, долгие нажатия и моменты нажатия/отпускания кнопки.
Разработчики создают универсальный компонент ```src/components/button.tsx```. На данном этапе при клике на <Pressable> срабатывает стандартный нативный алерт через встроенную функцию ```onPress={() => alert('...')}```

### Улучшите компонент многоразовой кнопки

```import { StyleSheet, View, Pressable, Text } from 'react-native';
import FontAwesome from '@expo/vector-icons/FontAwesome';

type Props = {
  label: string;
  theme?: 'primary';
};

export default function Button({ label, theme }: Props) {
  if (theme === 'primary') {
    return (
      <View
        style={[
          styles.buttonContainer,
          { borderWidth: 4, borderColor: '#ffd33d', borderRadius: 18 },
        ]}>
        <Pressable
          style={[styles.button, { backgroundColor: '#fff' }]}
          onPress={() => alert('You pressed a button.')}>
          <FontAwesome name="picture-o" size={18} color="#25292e" style={styles.buttonIcon} />
          <Text style={[styles.buttonLabel, { color: '#25292e' }]}>{label}</Text>
        </Pressable>
      </View>
    );
  }

  return (
    <View style={styles.buttonContainer}>
      <Pressable style={styles.button} onPress={() => alert('You pressed a button.')}>
        <Text style={styles.buttonLabel}>{label}</Text>
      </Pressable>
    </View>
  );
}

const styles = StyleSheet.create({
  buttonContainer: {
    width: 320,
    height: 68,
    marginHorizontal: 20,
    alignItems: 'center',
    justifyContent: 'center',
    padding: 3,
  },
  button: {
    borderRadius: 10,
    width: '100%',
    height: '100%',
    alignItems: 'center',
    justifyContent: 'center',
    flexDirection: 'row',
  },
  buttonIcon: {
    paddingRight: 8,
  },
  buttonLabel: {
    color: '#fff',
    fontSize: 16,
  },
});
```

# Используйте набор изображений

React Native предоставляет встроенные компоненты в качестве стандартных строительных блоков, такие как , , и . Мы создаём функцию для выбора изображения из медиагалереи устройства. Это невозможно с основными компонентами, и нам понадобится библиотека, чтобы добавить эту функцию в наше приложение.<View><Text><Pressable>

Мы используем ```expo-image-picker```, библиотека от Expo SDK.

### Установка expo-image-picker

Чтобы установить библиотеку, остановите сервер разработки, нажав + в терминале, затем выполните следующую команду:```expo-image-picker CtrlC```

```npx expo install expo-image-picker```

### Выберите изображение из медиабиблиотеки устройства

```expo-image-picker``` предоставляет способ отображения системного интерфейса путём выбора изображения или видео из медиатеки устройства. Мы используем основную тематическую кнопку, созданную в предыдущей главе, чтобы выбрать изображение из медиабиблиотеки устройства и создать функцию запуска библиотеки изображений устройства для реализации этой функции.```launchImageLibraryAsync()```

В ```src/app/(tabs)/index.tsx``` импортируйте библиотеку и создайте функцию внутри компонента:```expo-image-pickerpickImageAsync()Index```


```// ...rest of the import statements remain unchanged
 import * as ImagePicker from 'expo-image-picker';

export default function Index() {
  const pickImageAsync = async () => {
    let result = await ImagePicker.launchImageLibraryAsync({
      mediaTypes: ['images'],
      allowsEditing: true,
      quality: 1,
    });

    if (!result.canceled) {
      console.log(result);
    } else {
      alert('You did not select any image.');
    }
  };

  // ...rest of the code remains same
}
```

* Он получает объект для указания различных опций. Этот объект — это ```launchImageLibraryAsync()``` ```ImagePickerOptions``` Объект, который мы проходим при вызове метода.
* При установке на , пользователь может обрезать изображение во время выбора на Android и iOS.```allowsEditingtrue```

### Обновить компонент кнопок

```import { StyleSheet, View, Pressable, Text } from 'react-native';
import FontAwesome from '@expo/vector-icons/FontAwesome';

type Props = {
  label: string;
  theme?: 'primary';
  onPress?: () => void;
};

export default function Button({ label, theme, onPress }: Props) {
  if (theme === 'primary') {
    return (
      <View
        style={[
          styles.buttonContainer,
          { borderWidth: 4, borderColor: '#ffd33d', borderRadius: 18 },
        ]}>
        <Pressable style={[styles.button, { backgroundColor: '#fff' }]} onPress={onPress}>
``          <FontAwesome name="picture-o" size={18} color="#25292e" style={styles.buttonIcon} />
          <Text style={[styles.buttonLabel, { color: '#25292e' }]}>{label}</Text>
        </Pressable>
      </View>
    );
  }

  return (
    <View style={styles.buttonContainer}>
      <Pressable style={styles.button} onPress={() => alert('You pressed a button.')}>
        <Text style={styles.buttonLabel}>{label}</Text>
      </Pressable>
    </View>
  );
}

const styles = StyleSheet.create({
  buttonContainer: {
    width: 320,
    height: 68,
    marginHorizontal: 20,
    alignItems: 'center',
    justifyContent: 'center',
    padding: 3,
  },
  button: {
    borderRadius: 10,
    width: '100%',
    height: '100%',
    alignItems: 'center',
    justifyContent: 'center',
    flexDirection: 'row',
  },
  buttonIcon: {
    paddingRight: 8,
  },
  buttonLabel: {
    color: '#fff',
    fontSize: 16,
  },
});
```

### Используйте выбранное изображение

Объект предоставляет массив выбранного изображения. Давайте возьмём это значение из picker изображений и используем его, чтобы показать выбранное изображение в приложении.<resultassetsuri>

Измените файл ```src/app/(tabs)/index.tsx:```

* Объявим переменную состояния, вызванную с помощью ```selectedImageuseState``` крючок от React. Мы используем эту переменную состояния, чтобы сохранить URI выбранного изображения. 

* Обновите функцию, чтобы сохранить URI изображения в переменной состояния.```pickImageAsync()selectedImage```

* Передайте его как реквизит компоненту.```selectedImageImageViewer```

Передайте реквизит компоненту, чтобы отобразить выбранное изображение вместо временного изображения.```selectedImageImageViewer```

* Модифицируйте файл ```src/components/image-viewer.tsx```, чтобы он принял проп.```selectedImage```

* Источник изображения становится длинным, поэтому давайте также переместим его в отдельную переменную под названием .```imageSource```

* Передайте как значение пропеллера на компоненте.imageSourcesourceImage

# Создайте модаль

React Native предоставляет <Modal> Компонент Это представляет контент выше остального вашего приложения. В целом, модальные методы используются для привлечения внимания пользователя к критически важной информации или для того, чтобы помочь ему принять меры. Например, в третьей главе, после нажатия кнопки, мы показывали какой-то временный текст. Так модальный компонент отображает наложение.```alert()```

В этой главе мы создадим модаль, который показывает список выборщиков эмодзи.

### Объявить переменную состояния для отображения кнопок

Перед внедрением модала мы добавим три новые кнопки. Эти кнопки видны после того, как пользователь выбирает изображение из медиабиблиотеки или использует заполняющее изображение. Одна из этих кнопок запускает модаль отбора эмодзи.

В ```src/app/(tabs)/index.tsx```:

1. Объявите переменную булевого состояния, чтобы показать или скрыть кнопки, открывающие модаль, а также несколько других опций. Когда экран приложения загружается, мы устанавливаем так, чтобы опции не отображались перед выбором изображения. Когда пользователь выбирает изображение или использует заполнительное изображение, мы устанавливаем его на .showAppOptionsfalsetrue

2. Обновите функцию, чтобы установить значение в после выбора изображения.pickImageAsync()showAppOptionstrue

3. Обновите кнопку без темы, добавив реквизит со следующим значением.onPress

```import { View, StyleSheet } from 'react-native';
import * as ImagePicker from 'expo-image-picker';
import { useState } from 'react';

import Button from '@/components/button';
import ImageViewer from '@/components/image-viewer';

const PlaceholderImage = require('@/assets/images/background-image.png');

export default function Index() {
  const [selectedImage, setSelectedImage] = useState<string | undefined>(undefined);
  const [showAppOptions, setShowAppOptions] = useState<boolean>(false);

  const pickImageAsync = async () => {
    let result = await ImagePicker.launchImageLibraryAsync({
      mediaTypes: ['images'],
      allowsEditing: true,
      quality: 1,
    });

    if (!result.canceled) {
      setSelectedImage(result.assets[0].uri);
      setShowAppOptions(true);
    } else {
      alert('You did not select any image.');
    }
  };

  return (
    <View style={styles.container}>
      <View style={styles.imageContainer}>
        <ImageViewer imgSource={PlaceholderImage} selectedImage={selectedImage} />
      </View>
      {showAppOptions ? (
        <View />
      ) : (
        <View style={styles.footerContainer}>
          <Button theme="primary" label="Choose a photo" onPress={pickImageAsync} />
          <Button label="Use this photo" onPress={() => setShowAppOptions(true)} />
        </View>
      )}
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#25292e',
    alignItems: 'center',
  },
  imageContainer: {
    flex: 1,
  },
  footerContainer: {
    flex: 1 / 3,
    alignItems: 'center',
  },
});
```

В приведённом выше фрагменте мы рендерим компонент на основе значения и перемещаем кнопки в блоке тернарного оператора. Когда значение равен , отобразите пустую компоненту. Мы рассмотрим это состояние на следующем этапе.```Button``` ```showAppOptions``` ``` ``` ```true``` ```<View>```

Теперь мы можем удалить на компоненте и обновить проп при рендеринге второй кнопки в ```src/components/button.tsx```: ```alert``` ``` Button onPress```

### Добавить кнопки

```
import { View, Pressable, StyleSheet } from 'react-native';
import MaterialIcons from '@expo/vector-icons/MaterialIcons';

type Props = {
  onPress: () => void;
};

export default function CircleButton({ onPress }: Props) {
  return (
    <View style={styles.circleButtonContainer}>
      <Pressable style={styles.circleButton} onPress={onPress}>
        <MaterialIcons name="add" size={38} color="#25292e" />
      </Pressable>
    </View>
  );
}

const styles = StyleSheet.create({
  circleButtonContainer: {
    width: 84,
    height: 84,
    marginHorizontal: 60,
    borderWidth: 4,
    borderColor: '#ffd33d',
    borderRadius: 42,
    padding: 3,
  },
  circleButton: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    borderRadius: 42,
    backgroundColor: '#fff',
  },
});
```

Для отображения значка плюса эта кнопка использует иконки, установленные из библиотеки.<MaterialIcons>```@expo/vector-icons```

Две другие кнопки также используются для отображения вертикально выровненных текстовых меток и иконок. Создайте файл с именем ```icon-button.tsx``` внутри каталога ```src/components```. Этот компонент принимает три реквизита:```<MaterialIcons>```

* ```icon```: название, соответствующее иконке библиотеки.MaterialIcons
* ```label```: текстовая метка, отображаемая на кнопке.
* ```onPress```: эта функция вызывается, когда пользователь нажимает кнопку.

Внутри ```src/app/(tabs)/index.tsx```:

1. Импортируйте компоненты и для их отображения.```CircleButton Icon Button```
2. Добавьте три временных функции для этих кнопок. Функция срабатывает при нажатии кнопки сброса, вызывая повторное появление кнопки выбора изображения. Функционал для остальных двух функций мы добавим позже.```onReset()```

### Создать модаль с отбором эмодзи

Модаль позволяет пользователю выбрать эмодзи из списка доступных эмодзи. Создайте файл ```emoji-picker.tsx``` внутри каталога ```src/components```. Этот компонент принимает три реквизита:

* ```isVisible```: булев показатель для определения состояния видимости модаля.
* ```onClose```: функция для закрытия модаля.
* ```children```: позже использовался для отображения списка эмодзи.

```
import { Modal, View, Text, Pressable, StyleSheet } from 'react-native';
import { PropsWithChildren } from 'react';
import MaterialIcons from '@expo/vector-icons/MaterialIcons';

type Props = PropsWithChildren<{
  isVisible: boolean;
  onClose: () => void;
}>;

export default function EmojiPicker({ isVisible, children, onClose }: Props) {
  return (
    <View>
      <Modal animationType="slide" transparent={true} visible={isVisible}>
        <View style={styles.modalContent}>
          <View style={styles.titleContainer}>
            <Text style={styles.title}>Choose a sticker</Text>
            <Pressable onPress={onClose}>
              <MaterialIcons name="close" color="#fff" size={22} />
            </Pressable>
          </View>
          {children}
        </View>
      </Modal>
    </View>
  );
}

const styles = StyleSheet.create({
  modalContent: {
    height: '25%',
    width: '100%',
    backgroundColor: '#25292e',
    borderTopRightRadius: 18,
    borderTopLeftRadius: 18,
    position: 'absolute',
    bottom: 0,
  },
  titleContainer: {
    height: '16%',
    backgroundColor: '#464C55',
    borderTopRightRadius: 10,
    borderTopLeftRadius: 10,
    paddingHorizontal: 20,
    flexDirection: 'row',
    alignItems: 'center',
    justifyContent: 'space-between',
  },
  title: {
    color: '#fff',
    fontSize: 16,
  },
});
```

Давайте узнаем, что делает вышеуказанный код:

* Компонент отображает заголовок и кнопку закрытия.```<Modal>```
* Его пропеллер принимает значение и определяет, открыт ли модаль или закрыт.```visibleis Visible```
* Его проп — булево значение, которое определяет, заполняет ли модаль весь обзор.```transparent```
* Его реквизит определяет, как он входит и выходит из экрана. В данном случае он скользит снизу экрана.```animation Type```
* Наконец, при нажатии кнопки закрытия пользователь вызывает проп.```<EmojiPicker> onClose <Pressable>```

Теперь давайте изменим s```rc/app/(tabs)/index.tsx```:

1. Импортируйте компонент.```<EmojiPicker>```
2. Создайте переменную состояния с помощью этого хука. Его стандартное значение — , которое скрывает модаль до тех пор, пока пользователь не нажмёт кнопку для его открытия.```isModalVisible useState false```
3. Замените комментарий в функции, чтобы обновить переменную до момента, когда пользователь нажимает кнопку. Это откроет отбор эмодзи.```onAddSticker() isModalVisibletrue```
4. Создайте функцию для обновления переменной состояния.```onModalClose() isModalVisible```
5. Разместите компонент внизу компонента.```<EmojiPicker> Index```

### Показать список эмодзи

Давайте добавим горизонтальный список эмодзи в содержимое модаля. Мы используем ```<FlatList>``` компонент от **React Native** для этого.

Создайте файл ```emoji-list.tsx``` внутри каталога ```src/components``` и добавьте следующий код:

```
import { useState } from 'react';
import { ImageSourcePropType, StyleSheet, FlatList, Platform, Pressable } from 'react-native';
import { Image } from 'expo-image';

type Props = {
  onSelect: (image: ImageSourcePropType) => void;
  onCloseModal: () => void;
};

export default function EmojiList({ onSelect, onCloseModal }: Props) {
  const [emoji] = useState<ImageSourcePropType[]>([
    require("@/assets/images/emoji1.png"),
    require("@/assets/images/emoji2.png"),
    require("@/assets/images/emoji3.png"),
    require("@/assets/images/emoji4.png"),
    require("@/assets/images/emoji5.png"),
    require("@/assets/images/emoji6.png"),
  ]);

  return (
    <FlatList
      horizontal
      showsHorizontalScrollIndicator={Platform.OS === 'web'}
      data={emoji}
      contentContainerStyle={styles.listContainer}
      renderItem={({ item, index }) => (
        <Pressable
          onPress={() => {
            onSelect(item);
            onCloseModal();
          }}>
          <Image source={item} key={index} style={styles.image} />
        </Pressable>
      )}
    />
  );
}

const styles = StyleSheet.create({
  listContainer: {
    borderTopRightRadius: 10,
    borderTopLeftRadius: 10,
    paddingHorizontal: 20,
    flexDirection: 'row',
    alignItems: 'center',
    justifyContent: 'space-between',
  },
  image: {
    width: 100,
    height: 100,
    marginRight: 20,
  },
});
```

Давайте узнаем, что делает вышеуказанный код:

* Компонент выше отображает все изображения эмодзи с помощью компонента, обёрнутого . Позже мы улучшим её, чтобы пользователь мог нажать на эмодзи на экране, чтобы он выглядел как стикер на изображении.```<FlatList> Image <Pressable>```
* Он также принимает массив элементов, предоставленных переменной массива, в качестве значения пропа. Реквизит забирает предмет из и возвращает его из списка. Наконец, мы добавили компоненты для отображения этого предмета.```emoji data renderItem data Image <Pressable>```
* Реквизит отображает список горизонтально, а не вертикально. Он использует модуль React Native для проверки значения и отображения горизонтальной полоски прокрутки на вебе.```horizontals howsHorizontalScrollIndicator Platform```

Теперь обновите ```src/app/(tabs)/index.tsx```, чтобы импортировать компонент, и заменить комментарии внутри компонента следующим фрагментом кода:```<EmojiList> <EmojiPicker>```

В компоненте проп выбирает эмодзи, а после его выбора закрывает модаль.```EmojiList onSelecton CloseModal```

### Показать выбранные эмодзи

Теперь наклеим наклейку с эмодзи на изображение. Создайте новый файл в каталоге ```src/components``` и назовите его ```emoji-sticker.tsx```. Затем добавьте следующий код:

```
import { ImageSourcePropType, View } from 'react-native';
import { Image } from 'expo-image';

type Props = {
  imageSize: number;
  stickerSource: ImageSourcePropType;
};

export default function EmojiSticker({ imageSize, stickerSource }: Props) {
  return (
    <View style={{ top: -350 }}>
      <Image source={stickerSource} style={{ width: imageSize, height: imageSize }} />
    </View>
  );
}
```

Этот компонент получает две характеристики:

* imageSize: значение, определённое внутри компонента. Мы используем это значение в следующей главе, чтобы масштабировать размер изображения при нажатии.Index
* stickerSource: источник выбранного эмодзи.

Импортируйте этот компонент в файл ```src/app/(tabs)/index.tsx``` и обновите компонент, чтобы на изображении отображалась наклейка эмодзи. Мы проверим, если состояние не является: ```Index pickedEmoji undefined```

# Добавить жесты

Жесты — отличный способ обеспечить интуитивно понятный пользовательский опыт в приложении. Библиотека React Native Gesture Handler предоставляет встроенные компоненты, способные обрабатывать жесты. Он распознаёт панорамирование, нажатие, вращение и другие жесты с помощью встроенной системы сенсорного управления платформой. В этой главе мы добавим два разных жеста с помощью этой библиотеки:

* Дважды нажимайте, чтобы масштабировать размер наклейки эмодзи, и уменьшайте масштаб при повторном нажатии.
* Панорамируйте, чтобы переместить наклейку по экрану, чтобы пользователь мог разместить наклейку в любом месте на изображении.

> Мы также будем использовать библиотеку Reanimated для анимации между состояниями жестов.

### Add GestureHandlerRootView

Чтобы взаимодействие жестов работало в приложении, мы рендерим сверху компонента. Замените компонент корневого уровня в ```src/app/(tabs)/index.tsx``` на .```<GestureHandlerRootView> react-native-gesture-handler Index <View> <GestureHandlerRootView>```

### Используйте анимированные компоненты

Компонент смотрит на проп компонента и определяет, какие значения анимировать, а также применять обновления для создания анимации. Reanimated экспортирует анимированные компоненты, такие как , , или . Мы применим анимации к компоненту, чтобы двойной нажатие работало.```Animated style <Animated.View> <Animated.Text> <Animated.ScrollView> <Animated.Image>```

1. Откройте файл emoji-sticker.tsx в каталоге src/components. Внутри него импортируйте из библиотеки для использования анимированных компонентов.Animatedreact-native-reanimated
2. Замените компонент на .```Image <Animated.Image>```

### Добавьте жест нажатия

React Native Gesture Handler позволяет добавлять поведение при обнаружении касания, например, при двойном нажатии.

В файле ```src/components/emoji-sticker.tsx```:

1. Импорт и от .```GestureGestureDetectorreact-native-gesture-handler```
2. Чтобы распознать нажатие наклейки, импортировать , , и от — анимировать стиль .```useAnimatedStyleuseSharedValuewithSpringreact-native-reanimated<Animated.Image>```
3. Внутри компонента создайте ссылку, вызванную с помощью крючка. Он возьмёт значение в качестве начального значения.```EmojiStickerscaleImageuseSharedValue()imageSize```

Создание общей ценности с помощью крючка имеет множество преимуществ. Это помогает изменять данные и запускать анимации на основе текущего значения. Мы можем получить доступ и изменить общую ценность с помощью этого свойства. Мы создадим объект для масштабирования начального значения и анимации перехода при масштабировании изображения стикера. Чтобы определить количество требуемых отжиманий, добавим .```useSharedValue() .value doubleTap Gesture.Tap() numberOfTaps()```

> Создайте следующий объект в компоненте: ```EmojiSticker```

```
const doubleTap = Gesture.Tap()
  .numberOfTaps(2)
  .onStart(() => {
    if (scaleImage.value !== imageSize * 2) {
      scaleImage.value = scaleImage.value * 2;
    } else {
      scaleImage.value = Math.round(scaleImage.value / 2);
    }
  });
```

Чтобы анимировать переход, давайте используем пружинную анимацию. Это сделает игру живой, потому что она основана на реальной физике пружины. Мы будем использовать функцию, предоставляемую .```withSpring()react-native-reanimated```

На изображение наклейки мы используем крючок для создания объекта стиля. Это поможет нам обновлять стили, используя общие значения во время анимации. Мы также масштабируем размер изображения, изменяя свойства и. Начальные значения этих свойств устанавливаются как .```useAnimatedStyle()widthheightimageSize```

### Добавьте жест панорамы
Чтобы распознать жест перетаскивания на наклейке и отслеживать его движение, мы используем жест панорамы. В ```src/components/emoji-sticker.tsx```:

* Создайте две новые общие ценности: и .```translateX translateY```
* Замените их на компонент.```<View> <Animated.View>```

```
export default function EmojiSticker({ imageSize, stickerSource }: Props) {
  const scaleImage = useSharedValue(imageSize);
  const translateX = useSharedValue(0);
  const translateY = useSharedValue(0);
  // ...rest of the code remains same

  return (
    <Animated.View style={{ top: -350 }}>
      <GestureDetector gesture={doubleTap}>
        {/* ...rest of the code remains same */}
      </GestureDetector>
    </Animated.View>
  );
}
```

> Давайте узнаем, что делает вышеуказанный код:

* Определённые значения перевода будут перемещать стикер по экрану. Поскольку наклейка движется по обеим осям, нужно отслеживать значения X и Y.
* В крючках мы установили обе переменные трансляции так, чтобы они имели начальное положение . Это начальное положение наклейки и отправная точка. Это значение задаёт начальное положение стикера при начале жеста.```useSharedValue() 0```

На предыдущем этапе мы активировали обратный вызов для жеста tap, привязанного к методу. Для жеста панорамирования укажите обратный вызов, который выполняется, когда жест активен и движется.```onStart() Gesture.Tap() onChange()```

1. Создайте объект, который будет обрабатывать жест панорамирования. Обратный вызов принимается как параметр. и свойства сохраняют изменение положения с момента последнего события и обновляют значения, хранящиеся в и .```dragonChange() event changeX changeY translateX translateY```
2. Определите объект с помощью крючка. Он вернёт массив преобразований. Для компонента нужно установить свойство значения и . Это меняет положение наклейки, когда жест активен.```containerStyle useAnimatedStyle() <Animated.View> transformtranslateX translateY```

# Сделайте скриншот
> В этом уроке узнайте, как сделать скриншот с помощью сторонней библиотеки и Expo Media Library.

В этой главе мы узнаем, как сделать скриншот с помощью сторонней библиотеки и сохранить его в медиатеке устройства. Мы используем ```react-native-view-shot``` сделать скриншот и ```expo-media-library``` чтобы сохранить изображение в медиабиблиотеке устройства.

### Библиотеки установки
Для установки и запустите следующие команды:react-native-view-shotexpo-media-library

```npx expo install react-native-view-shot expo-media-library```

### Запрос на разрешения
Приложение, требующее конфиденциальной информации, например, доступ к медиатеке устройства, должно запросить разрешение на разрешение или отказ в доступе. Используя hook from , мы можем использовать разрешение и метод для запроса доступа. Этот крючок запрашивает как разрешения на чтение, так и на запись, что включает выбор изображений из библиотеки и сохранение скриншотов в неё.```useMediaLibraryPermissions() expo-image-pickerpermissionRespon serequestPermission()```

Когда приложение загружается впервые, и статус разрешения не предоставлен и не отклонён, значение этого приложения равно . При запросе разрешения пользователь может либо предоставить разрешение, либо отказать в нём. Мы можем добавить условие, чтобы проверить, если оно не исполняется. Если не разрешено, активируйте метод. После получения доступа значение изменяется на .```permissionResponse null requestPermission() ermissionResponse granted```

### Создайте ссылку для сохранения текущего вида

Мы используем его, чтобы пользователь мог сделать скриншот внутри приложения. Эта библиотека запечатлевает скриншот изображения с помощью этого метода. Он возвращает URI файла с изображением скриншота.```react-native-view-shot <View> captureRef()```

* Импорт из React и обратно.```captureRef react-native-view-shot useRef```
* Создайте эталонную переменную для хранения ссылки на запечатлено изображение скриншота.```imageRef```
* Оберните компоненты и внутри a и затем передайте ей опорную переменную.```<ImageViewer> <EmojiSticker> View>```


### Сделайте скриншот и сохраните его
Мы можем сделать скриншот представления, вызвав метод изнутри функции. Он принимает опциональный аргумент, при котором мы можем передать и области для захвата скриншотов. Подробнее о доступных вариантах можно прочитать в документации библиотеки.```captureRef() react-native-view-sho onSaveImageAsync() width height```

Метод также возвращает обещание, которое выполняет URI скриншота. Мы передадим этот URI в качестве параметра ```captureRef() MediaLibrary.saveToLibraryAsync()``` и сохранить скриншот в медиабиблиотеке устройства.

Внутри ```src/app/(tabs)/index.tsx``` обновите функцию следующим кодом:```onSaveImageAsync()```

```
import * as ImagePicker from 'expo-image-picker';
import * as MediaLibrary from 'expo-media-library';
import { useEffect, useRef, useState } from 'react';
import { ImageSourcePropType, StyleSheet, View } from 'react-native';
import { GestureHandlerRootView } from 'react-native-gesture-handler';
import { captureRef } from 'react-native-view-shot';

import Button from '@/components/button';
import CircleButton from '@/components/circle-button';
import EmojiList from '@/components/emoji-list';
import EmojiPicker from '@/components/emoji-picker';
import IconButton from '@/components/icon-button';
import ImageViewer from '@/components/image-viewer';

import EmojiSticker from '@/components/emoji-sticker';

const PlaceholderImage = require('@/assets/images/background-image.png');

export default function Index() {
  const [selectedImage, setSelectedImage] = useState<string | undefined>(
    undefined
  );
  const [showAppOptions, setShowAppOptions] = useState<boolean>(false);
  const [isModalVisible, setIsModalVisible] = useState<boolean>(false);
  const [pickedEmoji, setPickedEmoji] = useState<
    ImageSourcePropType | undefined
  >(undefined);
  const [permissionResponse, requestPermission] = ImagePicker.useMediaLibraryPermissions();
  const imageRef = useRef<View>(null);

  useEffect(() => {
    if (!permissionResponse?.granted) {
      requestPermission();
    }
  }, []);

  const pickImageAsync = async () => {
    let result = await ImagePicker.launchImageLibraryAsync({
      mediaTypes: ['images'],
      allowsEditing: true,
      quality: 1,
    });

    if (!result.canceled) {
      setSelectedImage(result.assets[0].uri);
      setShowAppOptions(true);
    } else {
      alert('You did not select any image.');
    }
  };

  const onReset = () => {
    setShowAppOptions(false);
  };

  const onAddSticker = () => {
    setIsModalVisible(true);
  };

  const onModalClose = () => {
    setIsModalVisible(false);
  };

  const onSaveImageAsync = async () => {
    try {
      const localUri = await captureRef(imageRef, {
        height: 440,
        quality: 1,
      });

      await MediaLibrary.saveToLibraryAsync(localUri);
      if (localUri) {
        alert('Saved!');
      }
    } catch (e) {
      console.log(e);
    }
  };

  return (
    <GestureHandlerRootView style={styles.container}>
      <View style={styles.imageContainer}>
        <View ref={imageRef} collapsable={false}>
          <ImageViewer imgSource={PlaceholderImage} selectedImage={selectedImage} />
          {pickedEmoji && <EmojiSticker imageSize={40} stickerSource={pickedEmoji} />}
        </View>
      </View>
      {showAppOptions ? (
        <View style={styles.optionsContainer}>
          <View style={styles.optionsRow}>
            <IconButton icon="refresh" label="Reset" onPress={onReset} />
            <CircleButton onPress={onAddSticker} />
            <IconButton icon="save-alt" label="Save" onPress={onSaveImageAsync} />
          </View>
        </View>
      ) : (
        <View style={styles.footerContainer}>
          <Button theme="primary" label="Choose a photo" onPress={pickImageAsync} />
          <Button label="Use this photo" onPress={() => setShowAppOptions(true)} />
        </View>
      )}
      <EmojiPicker isVisible={isModalVisible} onClose={onModalClose}>
        <EmojiList onSelect={setPickedEmoji} onCloseModal={onModalClose} />
      </EmojiPicker>
    </GestureHandlerRootView>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#25292e',
    alignItems: 'center',
  },
  imageContainer: {
    flex: 1,
  },
  footerContainer: {
    flex: 1 / 3,
    alignItems: 'center',
  },
  optionsContainer: {
    position: 'absolute',
    bottom: 80,
  },
  optionsRow: {
    alignItems: 'center',
    flexDirection: 'row',
  },
});
```

# Различия по платформам управления
> В этом учебнике узнайте, как работать с различиями между нативным и веб-интерфейсом при создании универсального приложения.

Android, iOS и веб имеют разные возможности. В нашем случае и Android, и iOS могут сделать скриншот с помощью библиотеки. Однако веб-браузеры не могут.```react-native-view-shot```

В этой главе мы узнаем, как справляться с получением скриншотов для веб-браузеров, чтобы наше приложение имело одинаковую функциональность на всех платформах.

### Установка и импорт dom-to-image
Чтобы сделать скриншот в интернете и сохранить его как изображение, мы используем стороннюю библиотеку под названием ```dom-to-image```. Он делает скриншот любого узла DOM и превращает его в векторное (SVG) или растровое (PNG или JPEG) изображение.

Остановите сервер разработки и выполните следующую команду для установки библиотеки:

```npm install dom-to-image```

### Добавить код, специфичный для платформы
Используя модуль из React Native, мы можем реализовать поведение, специфичное для платформы. Внутри ```src/app/(tabs)/index.tsx:Platform```

1. Импортируйте модуль из .```Platformreact-native```
2. Импортируйте библиотеку из .```domtoimagedom-to-image```
3. Обновите функцию, чтобы проверить, связана ли текущая платформа с этим свойством. Если это так, мы используем метод для преобразования и захвата тока в формате JPEG-изображения. В противном случае мы продолжим использовать ту же логику, что и для нативных платформ.```onSaveImageAsync() 'web' Platform.OS 'web' domtoimage.toJpeg() <View>```

```
import * as ImagePicker from 'expo-image-picker';
import * as MediaLibrary from 'expo-media-library';
import { useEffect, useRef, useState } from 'react';
import { ImageSourcePropType, View, StyleSheet, Platform } from 'react-native';
import { GestureHandlerRootView } from 'react-native-gesture-handler';
import { captureRef } from 'react-native-view-shot';
import domtoimage from 'dom-to-image';

import Button from '@/components/button';
import ImageViewer from '@/components/image-viewer';
import IconButton from '@/components/icon-button';
import CircleButton from '@/components/circle-button';
import EmojiPicker from '@/components/emoji-picker';
import EmojiList from '@/components/emoji-list';
import EmojiSticker from '@/components/emoji-sticker';

const PlaceholderImage = require('@/assets/images/background-image.png');

export default function Index() {
  const [selectedImage, setSelectedImage] = useState<string | undefined>(undefined);
  const [showAppOptions, setShowAppOptions] = useState<boolean>(false);
  const [isModalVisible, setIsModalVisible] = useState<boolean>(false);
  const [pickedEmoji, setPickedEmoji] = useState<ImageSourcePropType | undefined>(undefined);
  const [permissionResponse, requestPermission] = ImagePicker.useMediaLibraryPermissions();
  const imageRef = useRef<View>(null);

  useEffect(() => {
    if (!permissionResponse?.granted) {
      requestPermission();
    }
  }, []);

  const pickImageAsync = async () => {
    let result = await ImagePicker.launchImageLibraryAsync({
      mediaTypes: ['images'],
      allowsEditing: true,
      quality: 1,
    });

    if (!result.canceled) {
      setSelectedImage(result.assets[0].uri);
      setShowAppOptions(true);
    } else {
      alert('You did not select any image.');
    }
  };

  const onReset = () => {
    setShowAppOptions(false);
  };

  const onAddSticker = () => {
    setIsModalVisible(true);
  };

  const onModalClose = () => {
    setIsModalVisible(false);
  };

  const onSaveImageAsync = async () => {
    if (Platform.OS !== 'web') {
      try {
        const localUri = await captureRef(imageRef, {
          height: 440,
          quality: 1,
        });

        await MediaLibrary.saveToLibraryAsync(localUri);
        if (localUri) {
          alert('Saved!');
        }
      } catch (e) {
        console.log(e);
      }
    } else {
      try {
        const dataUrl = await domtoimage.toJpeg(imageRef.current, {
          quality: 0.95,
          width: 320,
          height: 440,
        });

        let link = document.createElement('a');
        link.download = 'sticker-smash.jpeg';
        link.href = dataUrl;
        link.click();
      } catch (e) {
        console.log(e);
      }
    }
  };

  return (
    <GestureHandlerRootView style={styles.container}>
      <View style={styles.imageContainer}>
        <View ref={imageRef} collapsable={false}>
          <ImageViewer imgSource={PlaceholderImage} selectedImage={selectedImage} />
          {pickedEmoji && <EmojiSticker imageSize={40} stickerSource={pickedEmoji} />}
        </View>
      </View>
      {showAppOptions ? (
        <View style={styles.optionsContainer}>
          <View style={styles.optionsRow}>
            <IconButton icon="refresh" label="Reset" onPress={onReset} />
            <CircleButton onPress={onAddSticker} />
            <IconButton icon="save-alt" label="Save" onPress={onSaveImageAsync} />
          </View>
        </View>
      ) : (
        <View style={styles.footerContainer}>
          <Button theme="primary" label="Choose a photo" onPress={pickImageAsync} />
          <Button label="Use this photo" onPress={() => setShowAppOptions(true)} />
        </View>
      )}
      <EmojiPicker isVisible={isModalVisible} onClose={onModalClose}>
        <EmojiList onSelect={setPickedEmoji} onCloseModal={onModalClose} />
      </EmojiPicker>
    </GestureHandlerRootView>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#25292e',
    alignItems: 'center',
  },
  imageContainer: {
    flex: 1,
  },
  footerContainer: {
    flex: 1 / 3,
    alignItems: 'center',
  },
  optionsContainer: {
    position: 'absolute',
    bottom: 80,
  },
  optionsRow: {
    alignItems: 'center',
    flexDirection: 'row',
  },
});
```

# Настройте строку статуса, заставку и иконку приложения
> В этом уроке вы узнаете основы настройки строки статуса, иконки приложения и заставки.

### Настройте строку статуса
```expo-status-bar``` Библиотека предустановленна в каждом проекте, созданном с использованием . Эта библиотека предоставляет компонент для настройки стиля строки статуса приложения.```create-expo-appStatusBar```

Внутри ```src/app/_layout.tsx```:

1. Импортировать из .StatusBarexpo-status-bar
2. Сгруппируйте существующие компоненты с компонентом Fragment от React.```StatusBarStack```

```
import { Stack } from 'expo-router';

import { StatusBar } from 'expo-status-bar';


export default function RootLayout() {
  return (
    <>
      <Stack>
        <Stack.Screen name="(tabs)" options={{ headerShown: false }} />
      </Stack>
      <StatusBar style="light" />
    </>
  );
}
```

### Иконка приложения

Внутри проекта есть icon.png файл в папке ассетов и изображений. Это иконка нашего приложения. Это изображение размером 1024 пикселей на 1024 пикселей

Как и изображение заставки, свойство в файле app.json настраивает путь иконки приложения. По умолчанию новый проект Expo определяет правильный путь к . Нам не нужно ничего менять.```"icon"" ./assets/images/icon.png"```

Иконку можно увидеть в разных местах Expo Go. Вот пример иконки приложения, отображаемой в меню разработчиков Expo Go

### Заставка
Перед загрузкой контента приложения отображается заставка. Он использует меньшее изображение, например иконку приложения, которая расположена по центру. Он скрывается, когда содержимое приложения готово к отображению.

The ```expo-splash-screen``` Плагин уже предустановлен в каждом проекте, созданном с использованием . Эта библиотека предоставляет конфигурационный плагин для настройки заставочного экрана.```create-expo-app```

В ```app.json``` году плагин уже настроен так, чтобы использовать иконку приложения в качестве изображения заставки ( предоставленного в загружаемых ассетах) с следующим фрагментом, так что нам не нужно ничего менять:```expo-splash-screen```

```
{
  "plugins": [
    [
      "expo-splash-screen",
      {
        "image": "./assets/images/splash-icon.png"
      }
    ]
  ]
}
```

Однако для тестирования заставки мы не можем использовать Expo Go или билд для разработки. Чтобы проверить, нам нужно создать превью или производственную версию нашего приложения. Рекомендуем ознакомиться с следующими ресурсами, чтобы узнать больше о конфигурации заставки и способах её протестировать:

* Создайте руководство по иконкам splash screen, чтобы узнать, как настраивается иконка splash screen.
* Чтобы узнать, как создать предварительную сборку, ознакомьтесь с руководством по внутреннему распространению в EAS Tutorial, а чтобы создавать производственные сборки — в руководствах для Android и iOS.

# Учебные материалы
> Ознакомьтесь с подобранным списком ресурсов, чтобы узнать больше о Expo и React Native.

Теперь, когда примерное приложение готово, давайте узнаем больше о технологиях, которые мы использовали для его создания.

### Введите свой проект в приложение

Чтобы начать создавать новое приложение на вашем компьютере, вы можете последовательно использовать и настраивать среду разработки.```npx create-expo-app@latest```

#### Рекомендуемые ресурсы
После создания нового проекта вы сможете узнать больше о различных инструментах и концепциях, которые помогут вам на пути разработки приложений:

* **Инструменты разработки**: Справочник по инструментам Expo, которые помогут вам на различных этапах процесса создания приложений.
* **Сборки для разработки**: использование сборки позволяет получить полный контроль над процессом создания приложения и тестировать его на устройстве или симуляторе.
* **Обзор разработки**: Это общий обзор, который содержит подробную информацию о ключевых концепциях разработки приложения с Expo и процессе основного цикла разработки.
* **Expo Router**: Мы изучили основы Expo Router и реализовали навигатор по вкладкам. Ознакомьтесь с документацией, чтобы узнать больше о библиотеке.
* **Иконка приложения и заставочный экран**: вы можете узнать больше о том, как настраивать иконку приложения и инструкции по заставке. Также посмотрите ссылку на конфигурацию приложения на свойства, которые можно настроить в app.json файле.
* **Распространение и отправка приложений в магазины приложений:** Прочитайте эти ресурсы, чтобы узнать больше о том, как выпустить и отправить приложение в магазины приложений, когда оно будет готово к отправке.
* **Отладка**: Иногда что-то идёт не так, и когда это происходит, можно использовать инструменты отладки, чтобы найти и исправить ошибки.

### Обучение
#### React
Мы использовали компоненты и API React. Глубокое понимание React крайне важно для использования Expo для создания вашего приложения. Рекомендуем ознакомиться с разделом Quick Start документации React и разделом Hooks.

#### React Native
При разработке обучающего приложения мы активно использовали React Native. Вы можете начать с руководства по основам React Native, чтобы узнать больше. Также посмотрите следующие документы:

* ***Просмотр ссылки API***
* ***Ссылка на текстовый API***
* ***Код, специфичный для платформы***
* ***Представление данных в списке***

Мы использовали Flexbox для раскладки компонентов. Ознакомьтесь со следующими рекомендациями, чтобы узнать об этом больше:

* ***Высота и ширина***
* ***Компоновка с Flexbox***

### Жесты и анимации
Чтобы узнать больше о реализации различных типов жестов и анимации, мы рекомендуем следующую документацию:

* ***Обработчик жестов React Native***
* ***React Native Reanimated***
