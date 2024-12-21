<template>
  <root />
</template>

<script setup lang="ts">
import './styles.scss';
import { Root } from '@tok/generation';

// Инициализация Telegram Web App
const telegram = window.Telegram.WebApp;

// Функция для закрытия приложения
function closeApp() {
  telegram.close();
}

// Обработка нажатия кнопки "Закрыть приложение"
function handleButtonClick(buttonText: string) {
  if (buttonText === 'Закрыть приложение') {
    closeApp();
  }
}

// Подписка на событие клика по кнопке
telegram.onEvent('onclick', (event) => {
  if (event.type === 'button' && event.text) {
    handleButtonClick(event.text);
  }
});
</script>
