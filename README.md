# Что это и зачем?

Этот репозиторий содержит список IP-адресов, используемых голосовыми серверами Discord. 
Эти списки могут быть полезны для пользователей, которые хотят настроить 'корректную' маршрутизацию для обеспечения 'стабильной' работы голосовых каналов Discord.
Бонусом добавлен список всех основных доменов и голосовых каналов.

## Структура Репозитория

- `discord-domains-list` - список доменных имен, принадлежащих Discord.
- `discord-voice-domains-list` - список из доменов голосовых каналов Discord регионов: Россия, Нидерланды, Швеция, Италия, Германия, Испания, Польша, Румыния
- `discord-ips-list` - список из IP голосовых каналов Discord регионов: Россия, Нидерланды, Швеция, Италия, Германия, Испания, Польша, Румыния
- `discord-ips-ipset-list` - список в формате IPset с командой `add unblock 'IP-адрес'`, где `'IP-адрес'` — это адреса из списка `discord-ips-list`. Для использования этого файла с командой `restore`, необходимо предварительно создать соответствующий ipset список `unblock`.
- `ips-by-region` - фолдер со списками IP голосовых каналов разбитым по регионам

## Использование IPset

Несколько шагов:

1. **Создайте новый список `unblock`**:
   
```bash
~# ipset create unblock hash:net
```

2. **Склонируйте этот репозиторий**:
   
```bash
~# git clone https://github.com/GhostRooter0953/discord-voice-ips.git
```

3. **Перейдите в директорию с клонированным репозиторием**:
   
```bash
~# cd discord-voice-ips
```

4. **Добавьте адреса из файла `discord-ips-ipset-list` в ваш ipset**:
   
```bash
~# ipset restore < discord-ips-ipset-list
```

5. **Добавьте соответствующее правило в ваш фаерволл, чтобы настроить маршрутизацию**

## Примечания

- Убедитесь, что у вас установлены необходимые права для выполнения команд ipset.
- Перед использованием рекомендуется проверить актуальность IP-адресов и доменных имен, так как они могут изменяться.
