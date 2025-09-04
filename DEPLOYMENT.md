# Развертывание N8N с постоянным URL

## Шаги для перезапуска N8N без потери данных:

### 1. Остановка старого контейнера
```bash
cd /Users/volkovvladislav/AiProjects/n8n
docker-compose down
```

### 2. Перезапуск с новой конфигурацией
```bash
docker-compose up -d
```

### 3. Перезапуск основного сайта для применения nginx конфигурации
```bash
cd /Users/volkovvladislav/AiProjects/AiAutomatizationSite
docker-compose restart truescale-site
```

## Результат:

После выполнения этих команд:
- N8N будет доступен по адресу: https://true-scale.ru/n8n/
- Все ваши workflow и данные сохранятся в volume `n8n_data`
- Webhook URL будет постоянным: https://true-scale.ru/n8n
- SSL сертификат от Let's Encrypt будет работать автоматически

## Важные изменения:

1. **Volume persistence**: Все данные N8N сохраняются в Docker volume
2. **Постоянный URL**: Вместо временного cloudflare туннеля используется ваш домен
3. **SSL через nginx**: Proxy настроен для работы через существующий SSL сертификат
4. **WebSocket support**: Добавлена поддержка WebSocket для real-time функций N8N

## Проверка:

После перезапуска откройте https://true-scale.ru/n8n/ - вы должны увидеть ваши существующие workflow.