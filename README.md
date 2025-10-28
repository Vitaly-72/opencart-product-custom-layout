# OpenCart 4 — Custom Product Layout with Unique Twig Template

Easily assign a **custom Twig template** to any product in OpenCart 4.1.0.3 by simply selecting a special layout in the admin panel — **no hardcoded product IDs**, **no core hacks**.

> 🇷🇺 [Читать на русском](#описание-на-русском)

---

## ✨ Features

- Assign a unique product page design via **Admin → Product → Links → Layout**
- Uses your own `product_special.twig` template for selected products
- Works with **OpenCart 4.1.0.3**
- Fully managed from admin — no code changes per product
- Preserves all standard functionality: options, cart, reviews, etc.

## 📥 Installation

1. Backup your store!
2. Place your custom template:  
   `catalog/view/theme/YOUR_THEME/template/product/product_special.twig`
3. Replace or modify:  
   `catalog/controller/product/product.php`
4. In Admin:
   - Go to **Design → Layouts → Add New**
   - Name it: `Special Product Layout` (or any name you prefer)
   - Save
5. Edit a product → **Links** tab → select your layout → Save
6. Visit the product — it now uses your custom template!

> 💡 Tip: Change the layout name check in `product.php` if you use a different name.

---

<br><br>
<a name="описание-на-русском"></a>
<div align="center">
  <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/f3/Flag_of_Russia.svg/24px-Flag_of_Russia.svg.png" alt="RU">  
  <strong>Описание на русском языке</strong>
</div>

# OpenCart 4 — Кастомный макет товара со своим Twig-шаблоном

Назначайте **уникальный Twig-шаблон** любому товару в OpenCart 4.1.0.3, просто выбрав специальный макет в админке — **без прописывания ID товаров в коде** и **без правок ядра под каждый случай**.

---

## ✨ Возможности

- Назначайте уникальный дизайн через **Админка → Каталог → Товары → Связи → Макет**
- Используется ваш собственный шаблон `product_special.twig`
- Работает с **OpenCart 4.1.0.3**
- Полностью управляется через интерфейс
- Сохраняется вся стандартная функциональность: опции, корзина, отзывы и т.д.

## 📥 Установка

1. Сделайте резервную копию!
2. Поместите ваш шаблон:  
   `catalog/view/theme/ВАША_ТЕМА/template/product/product_special.twig`
3. Замените или измените файл:  
   `catalog/controller/product/product.php`
4. В админке:
   - Перейдите **Дизайн → Макеты → Добавить**
   - Назовите макет, например: `Уникальный товар`
   - Сохраните
5. Откройте товар → вкладка **Связи** → выберите ваш макет → Сохраните
6. Откройте страницу товара — теперь используется ваш шаблон!

> 💡 Совет: Если вы используете другое имя макета, измените проверку в файле `product.php`.

---
