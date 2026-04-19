# Лабораторная работа 3

**Тема:** CI/CD для статического сайта в SourceCraft и GitHub Actions

---

## 1. Задания

- Реализовать сценарий автоматического развертывания статического сайта, построенного на движке mkdocs с использованием платформы Sourcecraft.
- Реализовать сценарий автоматического развертывания этого же статического сайта с помощью GitHub Actions. В рамках одного локального репозитория добавить 2 удаленных репозитория.
- Продемонстрировать результаты выполнения.

## 2. Выполненные действия

### 2.1. Настройка SourceCraft

1. Выполнена авторизация на [sourcecraft.dev](https://sourcecraft.dev) через аккаунт Яндекс
2. Создана публичная организация
3. Создан публичный репозиторий `portfolio-site`
4. Создан персональный токен доступа с правами **Maintainer** сроком на 1 год
5. В локальный репозиторий добавлен второй удалённый репозиторий:
6. Выполнена проверка что оба репозитория добавлены
7. Выполнен пуш в оба репозитория

### 2.2. Настройка CI/CD на SourceCraft

- Создан файл `.sourcecraft/ci.yaml` с конфигурацией автоматической сборки
- Создан файл `.sourcecraft/sites.yaml` для публикации сайта

### 2.3. Настройка GitHub Actions

Создан файл `.github/workflows/deploy.yml`

---

## 3. Что необходимо сделать для деплоя

### Для GitHub Pages + GitHub Actions:

1. В настройках репозитория GitHub:
   **Settings → Pages → Source: Deploy from branch → Branch: main, /docs**
2. В настройках Actions:
   **Settings → Actions → General → Workflow permissions → Read and write permissions**
3. После этого любой `git push origin main` автоматически запускает сборку
   и публикацию сайта через GitHub Actions

### Для SourceCraft:

1. Репозиторий должен быть **публичным** и находиться в **публичной организации**
2. Создать файл `.sourcecraft/sites.yaml` — указывает откуда брать файлы сайта
3. Создать файл `.sourcecraft/ci.yaml` — описывает процесс сборки
4. После любого `git push sourcecraft main` CI/CD автоматически
   собирает сайт и публикует его

---

## 4. Выводы

В ходе выполнения лабораторной работы были реализованы два независимых CI/CD пайплайна для автоматического развёртывания статического сайта.

Теперь не нужно вручную запускать `mkdocs build`. Достаточно отредактировать `.md` файл,  сделать коммит и пуш — система сама соберёт и опубликует сайт.

Были изучены принципы работы CI/CD, настройка автоматизации на двух платформах — GitHub Actions и SourceCraft, а также работа с несколькими удалёнными репозиториями в рамках одного локального проекта.

**Результаты:**

| Платформа | Сайт | Репозиторий |
|-----------|------|-------------|
| GitHub Pages | [ciom14.github.io](https://ciom14.github.io) | [github.com/ciom14/ciom14.github.io](https://github.com/ciom14/ciom14.github.io) |
| SourceCraft | [styleicon.sourcecraft.site/portfolio-site](https://styleicon.sourcecraft.site/portfolio-site) | [sourcecraft.dev/styleicon/portfolio-site](https://sourcecraft.dev/styleicon/portfolio-site) |