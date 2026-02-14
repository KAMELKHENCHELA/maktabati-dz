# Implementation Plan - Algerian E-commerce Store (Maktabati DZ)

## Goal Description
Enhance the existing "Maktabati DZ" (Algerian Stationery Store) to be a fully functional, premium-looking e-commerce site. The user has mentioned adding images, which need to be integrated. The goal is to create a "Wow" factor with the design and ensure smooth functionality for browsing products, adding to cart, and checkout (simulated).

## User Review Required
> [!IMPORTANT]
> **Missing Images**: You mentioned adding images, but I could not find any image files (jpg, png, webp, svg) in the `e:\ecomerss 3` directory.
> Please confirm where these images are located or upload them to a specific folder (e.g., `src/assets/images`).
> I will proceed with placeholders or the existing links until the images are available.

## Proposed Changes

### Project Structure
#### [NEW] `src/assets/images`
- Create directory for storing local product images once provided.

### Frontend
#### [MODIFY] [index.html](file:///e:/ecomerss%203/index.html)
- Improve semantic structure and accessibility.
- Update modal structures for better UI/UX.

#### [MODIFY] [main.css](file:///e:/ecomerss%203/src/styles/main.css)
- Implement a modern, premium design with "Wow" factor.
- Use a refined color palette (likely deep blues, whites, and vibrant accents for call-to-actions).
- Add micro-animations (hover effects, smooth transitions, card lifts).
- Ensure full mobile responsiveness.

#### [MODIFY] [main.js](file:///e:/ecomerss%203/src/scripts/main.js)
- Enhance product rendering logic.
- Implement cart functionality (add, remove, update quantity, calculate total).
- Implement checkout form validation and submission handling (simulated).
- Add "toast" notifications for user actions (e.g., "Added to cart").

#### [MODIFY] [products.js](file:///e:/ecomerss%203/src/data/products.js)
- Update product data to use local images once available, or keep placeholders if not.
- Ensure prices are in Algerian Dinar (DZD).

## Verification Plan

### Manual Verification
1.  **Visual Inspection**: Open `index.html` in the browser (via `open_browser_url` or manually) to verify the "Wow" design and responsiveness.
2.  **Functional Testing**:
    - Click "Add to Cart" on various products.
    - Check Cart sidebar opening and updating correctly.
    - Verify Total Price calculation.
    - Fill out Checkout form and submit -> check for success message.
    - Test "Contact Us" links (visual only).

<!DOCTYPE html>
<html lang="ar" dir="rtl">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>مكتبتي DZ | متجر الأدوات المكتبية الجزائري</title>
    <meta name="description"
        content="مكتبتي DZ - أفضل متجر للأدوات المدرسية والمكتبية في الجزائر. توصيل سريع وأسعار تنافسية.">
    <!-- Google Fonts: Cairo and Outfit for a modern look -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link
        href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700;800&family=Outfit:wght@300;400;600;700&display=swap"
        rel="stylesheet">
    <!-- Supabase Client -->
    <script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>
    <!-- Main Styles -->
    <link rel="stylesheet" href="./src/styles/main.css">
    <!-- Font Awesome for Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
</head>

<body>
    <div id="app">
        <header class="main-header">
            <div class="container">
                <div class="header-top">
                    <div class="logo">
                        <h1>مكتبتي <span class="accent">DZ</span></h1>
                    </div>
                    <div class="search-bar">
                        <input type="text" placeholder="ابحث عن منتج...">
                        <button><i class="fas fa-search"></i></button>
                    </div>
                    <div class="header-actions">
                        <button class="icon-btn user-btn" aria-label="الحساب"><i
                                class="fas fa-user-circle"></i></button>
                        <button class="icon-btn cart-btn" aria-label="سلة المشتريات">
                            <i class="fas fa-shopping-cart"></i>
                            <span class="badge" id="cart-count">0</span>
                        </button>
                    </div>
                </div>
                <nav class="main-nav">
                    <ul>
                        <li><a href="#" class="active">الرئيسية</a></li>
                        <li><a href="#office">أثاث مكتبي</a></li>
                        <li><a href="#school">أدوات مدرسية</a></li>
                        <li><a href="#art">أدوات فنية</a></li>
                        <li><a href="#electronics">إلكترونيات</a></li>
                        <li><a href="#offers">العروض</a></li>
                    </ul>
                </nav>
            </div>
        </header>

        <main>
            <section class="hero" id="hero">
                <div class="hero-content">
                    <h2>تجهيزات مكتبية ومدرسية بجودة عالية</h2>
                    <p>كل ما تحتاجه لمكتبك أو مدرستك في مكان واحد. توصيل لجميع ولايات الجزائر.</p>
                    <a href="#products" class="btn primary-btn">تسوق الآن</a>
                </div>
            </section>

            <section class="products-section" id="products">
                <div class="container">
                    <div class="section-header">
                        <h3>أحدث المنتجات</h3>
                        <a href="#" class="view-all">عرض الكل</a>
                    </div>
                    <div class="products-grid" id="products-grid">
                        <!-- Products will be loaded here via JS -->
                    </div>
                </div>
            </section>
        </main>

        <footer class="main-footer">
            <div class="container">
                <div class="footer-grid">
                    <div class="footer-col about">
                        <h4>عن المتجر</h4>
                        <p>متجر جزائري متخصص في بيع الأدوات المدرسية والمكتبية بأفضل الأسعار.</p>
                        <div class="social-links">
                            <a href="https://www.facebook.com/0656813384k?locale=ar_AR" target="_blank"
                                title="Facebook"><i class="fab fa-facebook-f"></i></a>
                            <a href="https://wa.me/213656813384" target="_blank" title="WhatsApp"><i
                                    class="fab fa-whatsapp"></i></a>
                            <a href="https://web.telegram.org/a/" target="_blank" title="Telegram"><i
                                    class="fab fa-telegram-plane"></i></a>
                        </div>
                    </div>
                    <div class="footer-col links">
                        <h4>روابط سريعة</h4>
                        <ul>
                            <li><a href="#">من نحن</a></li>
                            <li><a href="#">سياسة الخصوصية</a></li>
                            <li><a href="#">الشروط والأحكام</a></li>
                        </ul>
                    </div>
                    <div class="footer-col contact">
                        <h4>تواصل معنا</h4>
                        <div class="contact-item">
                            <i class="fas fa-phone"></i>
                            <span>0656 81 33 84</span>
                        </div>
                        <div class="contact-item">
                            <i class="fas fa-envelope"></i>
                            <span>kamelkhenchela@gmail.com</span>
                        </div>
                        <div class="contact-item">
                            <i class="fas fa-map-marker-alt"></i>
                            <span>خنشلة، الجزائر</span>
                        </div>
                    </div>
                </div>
                <div class="footer-bottom">
                    <p>&copy; 2024 مكتبتي DZ. جميع الحقوق محفوظة.</p>
                </div>
            </div>
        </footer>

        <!-- Cart Modal/Sidebar -->
        <div class="cart-sidebar" id="cart-sidebar">
            <div class="cart-header">
                <h3>سلة المشتريات</h3>
                <button class="close-cart" id="close-cart"><i class="fas fa-times"></i></button>
            </div>
            <div class="cart-items" id="cart-items">
                <!-- Cart items will be injected here -->
                <p class="empty-cart-msg">السلة فارغة حالياً</p>
            </div>
            <div class="cart-footer">
                <div class="total-row">
                    <span>المجموع الفرعي:</span>
                    <span id="cart-subtotal">0 د.ج</span>
                </div>
                <div class="total-row">
                    <span>مصاريف الشحن:</span>
                    <span id="cart-shipping">0 د.ج</span>
                </div>
                <div class="total-row final-total">
                    <span>الإجمالي:</span>
                    <span id="cart-total">0 د.ج</span>
                </div>
                <button class="btn primary-btn checkout-btn">إتمام الطلب</button>
            </div>
        </div>
        <!-- Checkout Modal -->
        <div class="modal" id="checkout-modal">
            <div class="modal-content">
                <div class="modal-header">
                    <h3>إتمام الطلب</h3>
                    <button class="close-modal" id="close-checkout"><i class="fas fa-times"></i></button>
                </div>
                <div class="modal-body">
                    <form id="checkout-form">
                        <div class="form-group">
                            <label for="fullname">الاسم الكامل</label>
                            <input type="text" id="fullname" name="fullname" required placeholder="محمد بن عبد الله">
                        </div>
                        <div class="form-group">
                            <label for="phone">رقم الهاتف</label>
                            <input type="tel" id="phone" name="phone" required placeholder="0550 12 34 56">
                        </div>
                        <div class="form-group">
                            <label for="wilaya">الولاية</label>
                            <select id="wilaya" name="wilaya" required>
                                <option value="">اختر الولاية</option>
                                <option value="1">01 - أدرار</option>
                                <option value="2">02 - الشلف</option>
                                <option value="3">03 - الأغواط</option>
                                <option value="4">04 - أم البواقي</option>
                                <option value="5">05 - باتنة</option>
                                <option value="6">06 - بجاية</option>
                                <option value="7">07 - بسكرة</option>
                                <option value="8">08 - بشار</option>
                                <option value="9">09 - البليدة</option>
                                <option value="10">10 - البويرة</option>
                                <option value="11">11 - تمنراست</option>
                                <option value="12">12 - تبسة</option>
                                <option value="13">13 - تلمسان</option>
                                <option value="14">14 - تيارت</option>
                                <option value="15">15 - تيزي وزو</option>
                                <option value="16">16 - الجزائر</option>
                                <option value="17">17 - الجلفة</option>
                                <option value="18">18 - جيجل</option>
                                <option value="19">19 - سطيف</option>
                                <option value="20">20 - سعيدة</option>
                                <option value="21">21 - سكيكدة</option>
                                <option value="22">22 - سيدي بلعباس</option>
                                <option value="23">23 - عنابة</option>
                                <option value="24">24 - قالمة</option>
                                <option value="25">25 - قسنطينة</option>
                                <option value="26">26 - المدية</option>
                                <option value="27">27 - مستغانم</option>
                                <option value="28">28 - المسيلة</option>
                                <option value="29">29 - معسكر</option>
                                <option value="30">30 - ورقلة</option>
                                <option value="31">31 - وهران</option>
                                <option value="32">32 - البيض</option>
                                <option value="33">33 - إليزي</option>
                                <option value="34">34 - برج بوعريريج</option>
                                <option value="35">35 - بومرداس</option>
                                <option value="36">36 - الطارف</option>
                                <option value="37">37 - تندوف</option>
                                <option value="38">38 - تيسمسيلت</option>
                                <option value="39">39 - الوادي</option>
                                <option value="40">40 - خنشلة</option>
                                <option value="41">41 - سوق أهراس</option>
                                <option value="42">42 - تيبازة</option>
                                <option value="43">43 - ميلة</option>
                                <option value="44">44 - عين الدفلى</option>
                                <option value="45">45 - النعامة</option>
                                <option value="46">46 - عين تموشنت</option>
                                <option value="47">47 - غرداية</option>
                                <option value="48">48 - غليزان</option>
                                <option value="49">49 - تيميمون</option>
                                <option value="50">50 - برج باجي مختار</option>
                                <option value="51">51 - أولاد جلال</option>
                                <option value="52">52 - بني عباس</option>
                                <option value="53">53 - عين صالح</option>
                                <option value="54">54 - عين قزام</option>
                                <option value="55">55 - تقرت</option>
                                <option value="56">56 - جانت</option>
                                <option value="57">57 - المغير</option>
                                <option value="58">58 - المنيعة</option>
                                <option value="59">59 - آفلو</option>
                                <option value="60">60 - بريكة</option>
                                <option value="61">61 - قصر الشلالة</option>
                                <option value="62">62 - مسعد</option>
                                <option value="63">63 - عين وسارة</option>
                                <option value="64">64 - بوسعادة</option>
                                <option value="65">65 - الأبيض سيدي الشيخ</option>
                                <option value="66">66 - القنطرة</option>
                                <option value="67">67 - بئر العاتر</option>
                                <option value="68">68 - قصر البخاري</option>
                                <option value="69">69 - العريشة</option>
                            </select>
                        </div>
                        <div class="form-group">
                            <label for="commune">البلدية</label>
                            <select id="commune" name="commune" required disabled>
                                <option value="">اختر البلدية</option>
                            </select>
                        </div>
                        <div class="form-group">
                            <label for="address">العنوان</label>
                            <textarea id="address" name="address" required placeholder="الحي، الدائرة..."></textarea>
                        </div>
                        <div class="order-summary">
                            <h4>ملخص الطلب</h4>
                            <div class="summary-line">
                                <span>المنتجات:</span>
                                <span id="checkout-subtotal">0 د.ج</span>
                            </div>
                            <div class="summary-line">
                                <span>الشحن:</span>
                                <span id="checkout-shipping">0 د.ج</span>
                            </div>
                            <hr>
                            <div class="summary-line total-price">
                                <span>الإجمالي الكلي:</span>
                                <span id="checkout-total">0 د.ج</span>
                            </div>
                        </div>
                        <button type="submit" class="btn primary-btn submit-order-btn">تأكيد الطلب</button>
                    </form>
                </div>
            </div>
        </div>
        <!-- Product Details Modal -->
        <div class="modal" id="product-modal">
            <div class="modal-content product-modal-content">
                <button class="close-modal" id="close-product-modal"><i class="fas fa-times"></i></button>
                <div class="product-details-grid">
                    <div class="product-modal-image">
                        <img id="modal-img" src="" alt="">
                    </div>
                    <div class="product-modal-info">
                        <span class="product-category" id="modal-category"></span>
                        <h2 id="modal-title"></h2>
                        <p class="price" id="modal-price"></p>
                        <p class="description" id="modal-description"></p>
                        <div class="modal-actions">
                            <button class="btn primary-btn add-btn" id="modal-add-btn">
                                <i class="fas fa-cart-plus"></i> أضف للسلة
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Auth Modal (Login/Register) -->
        <div class="modal" id="auth-modal">
            <div class="modal-content auth-modal-content">
                <div class="modal-header">
                    <div class="auth-tabs">
                        <button class="auth-tab-btn active" data-tab="login">تسجيل الدخول</button>
                        <button class="auth-tab-btn" data-tab="register">إنشاء حساب</button>
                    </div>
                    <button class="close-modal" id="close-auth"><i class="fas fa-times"></i></button>
                </div>
                <div class="modal-body">
                    <!-- Login Form -->
                    <form id="login-form" class="auth-form active">
                        <div class="form-group">
                            <label for="login-email">البريد الإلكتروني</label>
                            <input type="email" id="login-email" required placeholder="example@mail.com">
                        </div>
                        <div class="form-group">
                            <label for="login-password">كلمة المرور</label>
                            <input type="password" id="login-password" required placeholder="********">
                        </div>
                        <button type="submit" class="btn primary-btn full-width">دخول</button>
                        <p class="auth-switch">ليس لديك حساب؟ <a href="#" data-switch="register">سجل الآن</a></p>
                    </form>

                    <!-- Register Form -->
                    <form id="register-form" class="auth-form">
                        <div class="form-group">
                            <label for="reg-lastname">اللقب *</label>
                            <input type="text" id="reg-lastname" name="lastname" required placeholder="اللقب">
                        </div>
                        <div class="form-group">
                            <label for="reg-firstname">الاسم *</label>
                            <input type="text" id="reg-firstname" name="firstname" required placeholder="الاسم">
                        </div>
                        <div class="form-group">
                            <label for="reg-email">البريد الإلكتروني *</label>
                            <input type="email" id="reg-email" name="email" required placeholder="example@mail.com">
                        </div>
                        <div class="form-group">
                            <label for="reg-phone">رقم الهاتف</label>
                            <input type="tel" id="reg-phone" name="phone" placeholder="0550 12 34 56" minlength="10">
                        </div>
                        <div class="form-group">
                            <label for="reg-company">الشركة (اختياري)</label>
                            <input type="text" id="reg-company" name="company" placeholder="اسم الشركة">
                        </div>
                        <button type="submit" class="btn primary-btn full-width">ابدأ الآن</button>
                        <p class="auth-switch">لديك حساب بالفعل؟ <a href="#" data-switch="login">سجل دخولك</a></p>
                    </form>
                </div>
            </div>
        </div>

        <div class="overlay" id="modal-overlay"></div>
    </div>

    <script type="module" src="./src/scripts/main.js"></script>
</body>

</html>
# Algerian E-commerce Store Plan

- [x] Project Setup
    - [x] Create folder structure
    - [x] Create assets directory structure
- [/] Develop Storefront
    - [/] Assets Generation
        - [/] Generate premium product images using AI
        - [ ] Update product data with local image paths
    - [/] UI/UX Refinement (Premium Look)
        - [ ] Enhance CSS with glassmorphism and smooth animations
        - [ ] Improve typography and color palette
        - [ ] Ensure full mobile responsiveness
    - [/] Functional Completion
        - [ ] Finalize Cart logic (persistence, quantity management)
        - [ ] Finalize Simulated Checkout flow
        - [ ] Add toast notifications for user feedback
- [ ] Final Verification
    - [ ] Test all interactions in browser
    - [ ] Verify responsive layout

