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
# 📌 How to Create a Custom Product Layout in OpenCart

## 🇬🇧 English

1. **Create a new layout** in the OpenCart admin panel.  
   For example, name it **"Unique Product"** (you can use any name — it will be used to identify the custom template).
    ![Screenshot](maket.jpg) 

2. **Create or copy a product template**:  
   Go to the folder:  
   ``catalog/view/template/product/``  
   Create a new file called ``product_special.twig`` **or** copy the existing ``product.twig`` file and customize it as needed (e.g., add a JavaScript marquee script, modify HTML structure, CSS classes, etc.).
   ![Screenshot](code.jpg)

3. **Add template selection logic to the controller**:  
   Open the file:  
   ``catalog/controller/product/product.php``  
   Find the section where the view template is determined (usually just before the line return $this->load->view(...);), and insert the following code:

   ```php
   // === CUSTOM TEMPLATE DETECTION ===
   $template = 'product/product'; // default template

   if ($product_id) {
       // Get the layout_id assigned to this product
       $layout_id = $this->model_catalog_product->getLayoutId($product_id);

       if ($layout_id) {
           // Fetch the layout name from the 'layout' table
           $layout_query = $this->db->query("SELECT `name` FROM `" . DB_PREFIX . "layout` WHERE `layout_id` = '" . (int)$layout_id . "'");

           if ($layout_query->num_rows) {
               $layout_name = $layout_query->row['name'];

               // If the layout name contains "Unique Product", use the custom template
               if (strpos($layout_name, 'Unique Product') !== false) {
                   $template = 'product/product_special';
               }
           }
       }
   }
```

4. Assign the layout to a product:
In the OpenCart admin panel, open the desired product’s edit page → go to the "Design" tab → select the "Unique Product" layout.
![Screenshot](image.jpg) 

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
# 📌 Инструкция по созданию кастомного макета товара в OpenCart

## 🇷🇺 Русский

1. **Создайте новый макет** в админке OpenCart.  
   Например, назовите его **«Уникальный товар»** (название может быть любым — оно будет использоваться для определения шаблона).
   ![Screenshot](maket.jpg) 

2. **Создайте или скопируйте шаблон товара**:  
   Перейдите в папку:  catalog/view/template/product/
   Создайте новый файл `product_special.twig` **или** скопируйте `product.twig` и адаптируйте его под свои нужды (например, добавьте JavaScript-скрипт с бегущей строкой, измените структуру, классы и т.д.).

3. **Добавьте логику выбора шаблона в контроллер**:  
Откройте файл: catalog/controller/product/product.php
Найдите место, где определяется шаблон отображения (обычно перед `return $this->load->view(...)`), и вставьте следующий код:
![Screenshot](code.jpg)


```php
// === ОПРЕДЕЛЕНИЕ КАСТОМНОГО ШАБЛОНА ===
$template = 'product/product'; // шаблон по умолчанию

if ($product_id) {
    // Получаем layout_id, назначенный этому товару
    $layout_id = $this->model_catalog_product->getLayoutId($product_id);

    if ($layout_id) {
        // Получаем имя макета из таблицы layout
        $layout_query = $this->db->query("SELECT `name` FROM `" . DB_PREFIX . "layout` WHERE `layout_id` = '" . (int)$layout_id . "'");

        if ($layout_query->num_rows) {
            $layout_name = $layout_query->row['name'];

            // Если имя макета содержит "Уникальный товар" — используем кастомный шаблон
            if (strpos($layout_name, 'Уникальный товар') !== false) {
                $template = 'product/product_special';
            }
        }
    }
}
```
4. **Назначьте макет товару**:
В админке OpenCart откройте карточку нужного товара → вкладка «Дизайн» → выберите макет «Уникальный товар».
Теперь этот товар будет отображаться с использованием вашего кастомного шаблона product_special.twig.
В папке upload измененный файл product.php. В макет добавили бегущую строку.Теперь когда мы назначаем товару дизайн "Улучшеный товар" в его каточке появляется бегущая строка.

![Screenshot](image.jpg)
