# AS Feature Stories Production Roadmap

**Project:** Seller Exchange  
**Document:** AS Feature Stories Production Roadmap  
**Version:** 1.1  
**Status:** Planning

---

# Vision

Создать единую систему производства коротких продуктовых видеороликов (15–30 секунд), рассказывающих о возможностях Seller Exchange через реальные бизнес-сценарии.

Это не рекламные ролики.

Это не обучающие видео.

Это сериал о продукте.

Каждый новый ролик должен выглядеть как естественное продолжение предыдущего.

Главная цель — сделать производство роликов масштабируемым, повторяемым и легко поддерживаемым.

---

# Production Pipeline

Business Feature

↓

AS Feature Story

↓

Scenario Card

↓

Storyboard

↓

Screen Recording

↓

Motion Design

↓

Sound Design

↓

Export

↓

Publication

---

# Production Architecture

```
AS Feature Stories Matrix

        ↓

AS Feature Story Card

        ↓

Storyboard

        ↓

AS Feature Stories Style Guide

        ↓

AS Visual Kit

        ↓

AS Motion Kit

        ↓

Cavalry Master Template

        ↓

Story Production
```

---

# Phase 0 — AS Motion Identity

## Goal

Определить единый визуальный язык сериала до начала производства первого ролика.

Эта фаза является фундаментом всей серии.

---

## Deliverables

### AS Feature Stories Style Guide

Определяет

- философию сериала
- визуальный стиль
- Tone of Voice
- Motion Principles
- стиль монтажа
- язык титров
- язык эмодзи
- правила записи интерфейса
- звуковое оформление

---

### Motion Language

Зафиксировать

- темп роликов
- правила движения
- правила появления информации
- минимализм интерфейсной анимации

---

### Caption System

Определить

- размеры
- положение
- длину текста
- safe areas
- правила появления

---

### Emoji Language

Создать словарь эмодзи.

Каждый эмодзи имеет фиксированное значение.

---

### Audio Identity

Определить

- музыку
- UI-звуки
- громкость
- отсутствие диктора

---

### Recording Standard

Зафиксировать

- Browser
- Resolution
- FPS
- Theme
- Cursor
- Zoom
- Language
- Test Data

---

## Deliverable

✅ AS Feature Stories Style Guide v1.0

---

# Phase 1 — AS Visual Kit

## Goal

Создать небольшую дизайн-систему сериала.

Visual Kit отвечает на вопрос:

> **Из каких визуальных элементов состоит каждый ролик?**

Все элементы создаются один раз и используются повторно.

---

## 1. Typography

- Font Family
- Font Size Scale
- Font Weight
- Line Height
- Letter Spacing

Задать размеры для:

- Hook
- Caption
- Section Title
- Outro

---

## 2. Caption Components

Создать готовые компоненты

- Caption
- Secondary Caption
- Badge
- Hint
- CTA

Определить

- положение
- внутренние отступы
- максимальную длину

---

## 3. Emoji Components

Создать SVG-компоненты

🤔

🔍

📦

📄

🚀

📈

🏭

🛒

🤖

💰

👥

💬

⚠

✅

✨

🎯

Определить

- размер
- прозрачность
- отступы
- использование

---

## 4. Highlight Components

Создать библиотеку

- Focus Ring
- Glow Outline
- Selection Frame
- Highlight Background
- Click Circle
- Cursor Ripple

---

## 5. Callout Components

Создать

- Arrow
- Pointer
- Pulse Dot
- Tooltip
- Floating Label

---

## 6. Logo System

Подготовить

- Intro Logo
- Outro Logo
- Watermark
- Safe Area
- Logo Animation Placeholder

---

## 7. Layout Grid

Зафиксировать

- Safe Areas
- Margins
- Caption Grid
- Alignment Rules

---

## 8. Color System

Использовать цвета Seller Exchange.

Добавить только

Success

Warning

Danger

Info

Accent

Все остальные цвета — только из интерфейса платформы.

---

## 9. Recording Frames

Создать готовые композиции

- Browser Frame
- Background
- Device Shadow
- Dark Theme
- Light Theme

---

## Deliverable

✅ AS Visual Kit v1.0

---

# Phase 2 — AS Motion Kit

## Goal

Создать библиотеку переиспользуемых анимаций.

Motion Kit отвечает на вопрос:

> **Как двигаются элементы Visual Kit?**

---

## Motion Tokens

- Duration
- Delay
- Easing
- Opacity
- Scale
- Slide
- Rotation
- Blur

---

## Motion Components

Создать

- Cursor
- Hover
- Click
- Typing
- Loader
- Progress
- Counter
- Toast
- Notification
- Highlight
- Emoji Pop
- Caption In
- Caption Out
- Logo Intro
- Logo Outro
- Scene Transition

---

## Motion Presets

Fast

Normal

Slow

---

## Deliverable

✅ AS Motion Kit v1.0

---

# Phase 3 — Cavalry Master Template

## Goal

Создать единый шаблон проекта Cavalry.

Каждый новый ролик создается из этого шаблона.

---

## Structure

Intro

↓

Story

↓

Outro

---

В шаблон входят

- Intro
- Story Scene
- Outro
- Cursor
- Caption
- Emoji
- Motion Components
- Audio
- Logo
- Transition Library

---

## Deliverable

✅ AS Feature Story Template.cavalry

---

# Phase 4 — Screen Recording Standard

## Goal

Стандартизировать запись интерфейса.

---

Определить

- Browser
- Resolution
- FPS
- Cursor
- Zoom
- Theme
- Language
- Clean Data

---

Создать

Recording Checklist

---

## Deliverable

✅ Recording Guide

---

# Phase 5 — Story Production

Для каждой новой истории используется одинаковый Production Pipeline.

Business Story

↓

Scenario Card

↓

Storyboard

↓

Recording

↓

Motion

↓

Review

↓

Export

---

## Deliverables

- Scenario Card
- Storyboard
- Cavalry Project
- Preview
- Final Export

---

# Phase 6 — Asset Library

Создать библиотеку ресурсов.

## Visual Assets

- Logos
- Icons
- Emojis
- Captions
- Backgrounds
- Browser Frames

---

## Audio

- Music
- UI Sounds
- Notifications

---

## Motion

- Cursor
- Hover
- Click
- Loader
- Zoom
- Toast

---

## Export Presets

- Telegram
- LinkedIn
- Website
- YouTube Shorts

---

## Deliverable

✅ Shared Asset Library

---

# Phase 7 — Publishing

Подготовка публикаций.

Telegram

↓

LinkedIn

↓

Website

↓

Patch Notes

↓

YouTube Shorts

---

## Deliverables

- Thumbnail
- Caption
- Description
- Preview GIF
- Cover

---

# Folder Structure

```text
feature-stories/

    roadmap/

    style-guide/

    visual-kit/

    motion-kit/

    templates/

    stories/

        GS/
        INV/
        PC/
        AI/
        NCX/
        SP/

    recordings/

    cavalry/

    assets/

        logos/
        icons/
        emojis/
        captions/
        browser/
        sounds/

    exports/

        telegram/
        linkedin/
        youtube/
        website/
```

---

# Production Documents

1. AS Feature Stories Matrix

↓

2. AS Feature Story Card

↓

3. Storyboard

↓

4. AS Feature Stories Style Guide

↓

5. AS Visual Kit

↓

6. AS Motion Kit Specification

↓

7. Cavalry Master Template

↓

8. Recording Guide

↓

9. Production Checklist

↓

10. Publishing Checklist

---

# Milestones

## M0

AS Motion Identity

---

## M1

AS Feature Stories Style Guide

---

## M2

AS Visual Kit

---

## M3

AS Motion Kit

---

## M4

Cavalry Master Template

---

## M5

First Feature Story

---

## M6

Getting Started Series

---

## M7

Feature Stories Library

---

# First Production Sprint

## Getting Started Series

GS-001

📥 Import Your Inventory

↓

GS-002

🔍 Find a Problem Product

↓

GS-003

📄 Open Product Card

↓

GS-004

📈 Compare Two Niches

↓

GS-005

🚀 Launch Your First Product

↓

GS-006

🏭 Find a Supplier

---

# Success Criteria

Через несколько месяцев команда должна выпускать новую Feature Story за несколько часов, а не за несколько дней.

Это достигается благодаря:

- единому Style Guide;
- единому Visual Kit;
- готовому Motion Kit;
- шаблону Cavalry;
- библиотеке компонентов;
- стандартизированному процессу производства.

---

# Core Principle

> **Новая история — это не новая анимация.**

> **Новая история — это новая комбинация существующих визуальных и motion-компонентов.**