# UI компоненты (Button и Input) для Vue-проекта
**CompositionAPI и TypeScrypt**

Небольшая библиотека компонентов, для использования в проектах Vue3 (не тестировалась во Vue2).
В компонентах изпользуются требуемые стили. Управлять поведением можно через добавление необязательных атрибутов.

## Установка

Необходимо перенести папку UI из данного репозитория в свой проект.
После чего можно импортировать каждый компонент по отдельности.

Либо скачать архив по [ссылке](https://drive.google.com/drive/folders/1xlYcBJ4e6kFXbVgsC7t6FooS5O_yhPXe?usp=sharing).

## Компонент Button
Компонент может быть использован в двух режимах - “button” и “submit”.
Режим “submit” предназначен для использования компонета в тэге form, при нажатии срабатывает событие **onsubmit**.

При использовании по-умолчанию - компонет ведет себя, как button, при нажатии срабатывает событие **onclick**.

**У компонента имеется четыре необязательных свойства:**
| Имя | Тип | Значения | Описание | По-умолчанию |
| ------ | ------ | ------ | ------ | ------ |
| label | String | - | Надпись | "Button" |
| buttonType | String | "button", "submit" | Тип/режим | "button" |
| size | String | "lg", "md", "sm" | Размер | "md" |
| disabled | Boolean | true, false | Кликабельность | false |

## Компонент Input
Компонент копирует поведение тэга input с добавлением простых настроек и предустановленных стилей.

Описание для поля input можно установить через атрибуты label и/или placeholder.

Ширину поля ввода можно задать атрибутом width, установив значение ширины в процентах (без знака %).

**У компонента имеется семь необязательных свойств:**
| Имя | Тип | Значения | Описание | По-умолчанию |
| ------ | ------ | ------ | ------ | ------ |
| label | String | - | Значение для label | "" |
| placeholder | String | - | Плайсхолдер | "" |
| width | Number | - | Ширина поля в процентах | 100 |
| value | String | - | Значение поля | "" |
| name | String | - | атрибут "name" | "input" |
| isSecret | Boolean | true, false | Скрытие ввода | false |
| disabled | Boolean | true, false | Кликабельность | false |

## Пример использования
```html
<form @submit.prevent="eventSubTest">
  <Input placeholder="name" name="name" v-model:value="formData.name" />
  <Input placeholder="pass" name="pass" isSecret v-model:value="formData.password" />
  <Button label="My button submit" size="lg" buttonType="submit" />
</form>
```
```html
<script setup lang="ts">
  import { ref } from "vue";
  import Button from "./UI/Button.vue";
  import Input from "./UI/Input.vue";

  const formData = ref({ name: "", password: "" });

  const eventSubmit = () => {
    const { name, password } = formData.value;
    //
    formData.value = { name: "", password: "" };
  };
</script>
```
