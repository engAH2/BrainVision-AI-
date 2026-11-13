<?php
//medical_store/public/index.php
require_once __DIR__ . '/../includes/config.php';
require_once __DIR__ . '/../includes/functions.php';

// ═══════════════════════════════════════════
// دالة تحويل Hex إلى RGB (يجب تعريفها أولاً قبل الاستخدام)
// ═══════════════════════════════════════════
function hexToRgb($hex) {
    $hex = str_replace("#", "", $hex);
    if(strlen($hex) == 3) {
        $r = hexdec(substr($hex,0,1).substr($hex,0,1));
        $g = hexdec(substr($hex,1,1).substr($hex,1,1));
        $b = hexdec(substr($hex,2,1).substr($hex,2,1));
    } else {
        $r = hexdec(substr($hex,0,2));
        $g = hexdec(substr($hex,2,2));
        $b = hexdec(substr($hex,4,2));
    }
    return "$r, $g, $b";
}

// ═══════════════════════════════════════════
// 1. جلب الإعدادات
// ═══════════════════════════════════════════
$admin_color = get_setting($pdo, 'primary_color', '#6A0DAD');
$secondary_color = get_setting($pdo, 'secondary_color', '#8E3CCB');
$admin_color_rgb = hexToRgb($admin_color);

// ═══════════════════════════════════════════
// 2. لغة العرض
// ═══════════════════════════════════════════
$lang = $_SESSION['lang'] ?? 'ar';
$dir = $lang === 'ar' ? 'rtl' : 'ltr';

include __DIR__ . '/../includes/header_user.php';
?>

<style>
/* ═══════════════════════════════════════════
   CSS Variables
═══════════════════════════════════════════ */
:root {
    --main-color: <?= e($admin_color) ?>;
    --main-color-rgb: <?= $admin_color_rgb ?>;
    --secondary-color: <?= e($secondary_color) ?>;
    --hero-bg: linear-gradient(160deg, #fdfbfd 0%, #f4f7ff 100%);
    --text-dark: #1a1a2e;
    --text-muted: #6b7280;
    --card-bg: #ffffff;
}

html.dark {
    --hero-bg: linear-gradient(160deg, #1a1a2e 0%, #0f0f1a 100%);
    --text-dark: #f1f1f1;
    --text-muted: #a0a0b0;
    --card-bg: #1a1a2e;
}

/* ═══════════════════════════════════════════
   Hero Section
═══════════════════════════════════════════ */
.hero-landing {
    background: var(--hero-bg);
    padding: 80px 0 100px;
    min-height: 80vh;
    display: flex;
    align-items: center;
    position: relative;
    overflow: hidden;
}

.hero-landing::before {
    content: '';
    position: absolute;
    top: -50%;
    <?= $dir === 'rtl' ? 'left' : 'right' ?>: -20%;
    width: 600px;
    height: 600px;
    background: radial-gradient(circle, rgba(var(--main-color-rgb), 0.08) 0%, transparent 70%);
    border-radius: 50%;
    pointer-events: none;
}

.hero-landing::after {
    content: '';
    position: absolute;
    bottom: -30%;
    <?= $dir === 'rtl' ? 'right' : 'left' ?>: -10%;
    width: 400px;
    height: 400px;
    background: radial-gradient(circle, rgba(var(--main-color-rgb), 0.05) 0%, transparent 70%);
    border-radius: 50%;
    pointer-events: none;
}

.hero-content {
    position: relative;
    z-index: 2;
}

.hero-title {
    color: var(--main-color) !important;
    font-size: clamp(1.8rem, 5vw, 3rem);
    font-weight: 800;
    line-height: 1.3;
    margin-bottom: 1.5rem;
}

.hero-subtitle {
    color: var(--text-muted);
    font-size: clamp(1rem, 2.5vw, 1.25rem);
    line-height: 1.8;
    margin-bottom: 2rem;
    max-width: 500px;
}

.hero-btn {
    display: inline-flex;
    align-items: center;
    gap: 10px;
    background: linear-gradient(135deg, var(--main-color), var(--secondary-color)) !important;
    border: none !important;
    color: #ffffff !important;
    padding: 16px 40px;
    border-radius: 50px;
    font-weight: 700;
    font-size: 1rem;
    text-decoration: none;
    transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
    box-shadow: 0 10px 30px rgba(var(--main-color-rgb), 0.3);
    position: relative;
    overflow: hidden;
}

.hero-btn::before {
    content: '';
    position: absolute;
    top: 0;
    left: -100%;
    width: 100%;
    height: 100%;
    background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
    transition: left 0.5s;
}

.hero-btn:hover::before {
    left: 100%;
}

.hero-btn:hover {
    transform: translateY(-4px);
    box-shadow: 0 20px 40px rgba(var(--main-color-rgb), 0.4);
    color: #fff !important;
}

.hero-btn i {
    font-size: 1.1rem;
}

/* Hero Image */
.hero-img-wrapper {
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
}

.hero-img {
    max-width: 100%;
    height: auto;
    animation: float 5s ease-in-out infinite;
    filter: drop-shadow(0 30px 50px rgba(var(--main-color-rgb), 0.2));
    position: relative;
    z-index: 2;
}

@keyframes float {
    0%, 100% { transform: translateY(0) rotate(0deg); }
    25% { transform: translateY(-15px) rotate(1deg); }
    75% { transform: translateY(-10px) rotate(-1deg); }
}

.hero-img-bg {
    position: absolute;
    width: 80%;
    height: 80%;
    background: radial-gradient(circle, rgba(var(--main-color-rgb), 0.1) 0%, transparent 70%);
    border-radius: 50%;
    z-index: 1;
}

/* ═══════════════════════════════════════════
   Features Section
═══════════════════════════════════════════ */
.features-section {
    padding: 80px 0;
    background: var(--card-bg);
    position: relative;
}

.section-title {
    text-align: center;
    margin-bottom: 50px;
}

.section-title h2 {
    color: var(--text-dark);
    font-size: clamp(1.5rem, 4vw, 2rem);
    font-weight: 800;
    margin-bottom: 15px;
}

.section-title p {
    color: var(--text-muted);
    max-width: 600px;
    margin: 0 auto;
}

.feature-card {
    background: var(--hero-bg);
    border-radius: 20px;
    padding: 40px 30px;
    text-align: center;
    transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
    height: 100%;
    border: 1px solid rgba(var(--main-color-rgb), 0.1);
    position: relative;
    overflow: hidden;
}

.feature-card::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    height: 4px;
    background: linear-gradient(90deg, var(--main-color), var(--secondary-color));
    transform: scaleX(0);
    transition: transform 0.4s;
}

.feature-card:hover::before {
    transform: scaleX(1);
}

.feature-card:hover {
    transform: translateY(-10px);
    box-shadow: 0 20px 50px rgba(var(--main-color-rgb), 0.15);
}

.feature-icon {
    width: 90px;
    height: 90px;
    background: linear-gradient(135deg, rgba(var(--main-color-rgb), 0.1), rgba(var(--main-color-rgb), 0.05));
    border-radius: 50%;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 25px;
    color: var(--main-color);
    font-size: 2rem;
    transition: all 0.4s;
    position: relative;
}

.feature-icon::after {
    content: '';
    position: absolute;
    inset: -5px;
    border-radius: 50%;
    border: 2px dashed rgba(var(--main-color-rgb), 0.2);
    animation: spin 20s linear infinite;
}

@keyframes spin {
    100% { transform: rotate(360deg); }
}

.feature-card:hover .feature-icon {
    background: linear-gradient(135deg, var(--main-color), var(--secondary-color));
    color: #fff;
    transform: scale(1.1);
}

.feature-card h5 {
    color: var(--text-dark);
    font-weight: 700;
    font-size: 1.15rem;
    margin-bottom: 12px;
}

.feature-card p {
    color: var(--text-muted);
    font-size: 0.95rem;
    line-height: 1.7;
    margin: 0;
}

/* ═══════════════════════════════════════════
   Stats Section (إضافة جديدة)
═══════════════════════════════════════════ */
.stats-section {
    background: linear-gradient(135deg, var(--main-color), var(--secondary-color));
    padding: 60px 0;
    margin-top: -1px;
}

.stat-item {
    text-align: center;
    padding: 20px;
}

.stat-number {
    font-size: clamp(2rem, 5vw, 3rem);
    font-weight: 800;
    color: #fff;
    display: block;
    line-height: 1;
    margin-bottom: 10px;
}

.stat-label {
    color: rgba(255,255,255,0.85);
    font-size: 0.95rem;
    font-weight: 500;
}

/* ═══════════════════════════════════════════
   Responsive Design
═══════════════════════════════════════════ */
@media (max-width: 991px) {
    .hero-landing {
        padding: 60px 0 80px;
        min-height: auto;
    }

    .hero-img-wrapper {
        margin-bottom: 40px;
    }

    .hero-img {
        max-width: 70%;
    }

    .hero-content {
        text-align: center;
    }

    .hero-subtitle {
        margin-left: auto;
        margin-right: auto;
    }

    .hero-btn {
        padding: 14px 35px;
    }
}

@media (max-width: 767px) {
    .hero-landing {
        padding: 40px 0 60px;
    }

    .hero-img {
        max-width: 80%;
    }

    .hero-btn {
        padding: 12px 28px;
        font-size: 0.95rem;
        width: 100%;
        justify-content: center;
    }

    .features-section {
        padding: 50px 0;
    }

    .feature-card {
        padding: 30px 20px;
    }

    .feature-icon {
        width: 70px;
        height: 70px;
        font-size: 1.5rem;
    }

    .stat-item {
        padding: 15px 10px;
        border-bottom: 1px solid rgba(255,255,255,0.1);
    }

    .stat-item:last-child {
        border-bottom: none;
    }
}

@media (max-width: 480px) {
    .hero-title {
        font-size: 1.6rem;
    }

    .hero-subtitle {
        font-size: 0.95rem;
    }
}
</style>

<!-- ═══════════════════════════════════════════
     Hero Section
═══════════════════════════════════════════ -->
<section class="hero-landing">
    <div class="container">
        <div class="row align-items-center">
            <!-- Image (يظهر أولاً في الجوال) -->
            <div class="col-lg-6 order-1 order-lg-2">
                <div class="hero-img-wrapper">
                    <div class="hero-img-bg"></div>
                    <img src="assets/images/h.png" class="hero-img" alt="<?= $lang === 'ar' ? 'المتجر الطبي' : 'Medical Store' ?>">
                </div>
            </div>

            <!-- Content -->
            <div class="col-lg-6 order-2 order-lg-1">
                <div class="hero-content">
                    <h1 class="hero-title">
                        <?= $lang === 'ar'
                            ? 'كل ما تحتاجه من الأجهزة والمستلزمات الطبية'
                            : 'All Your Medical Equipment & Supplies Needs' ?>
                    </h1>
                    <p class="hero-subtitle">
                        <?= $lang === 'ar'
                            ? 'تسوق أحدث الأجهزة الطبية المعتمدة والمضمونة بخيارات دفع سهلة وشحن سريع لكافة المناطق.'
                            : 'Shop the latest certified and guaranteed medical devices with easy payment options and fast shipping to all regions.' ?>
                    </p>
                    <div class="d-flex flex-wrap gap-3 <?= $lang === 'ar' ? '' : '' ?> justify-content-center justify-content-lg-start">
                        <a href="<?= BASE_URL ?>/app/user/product.php" class="btn hero-btn">
                            <i class="fa-solid fa-cart-shopping"></i>
                            <?= $lang === 'ar' ? 'ابدأ التسوق الآن' : 'Start Shopping Now' ?>
                        </a>
                    </div>
                </div>
            </div>
        </div>
    </div>
</section>

<!-- ═══════════════════════════════════════════
     Stats Section
═══════════════════════════════════════════ -->
<section class="stats-section">
    <div class="container">
        <div class="row">
            <div class="col-6 col-md-3">
                <div class="stat-item">
                    <span class="stat-number" data-count="500">500+</span>
                    <span class="stat-label"><?= $lang === 'ar' ? 'منتج متوفر' : 'Products Available' ?></span>
                </div>
            </div>
            <div class="col-6 col-md-3">
                <div class="stat-item">
                    <span class="stat-number" data-count="10000">10K+</span>
                    <span class="stat-label"><?= $lang === 'ar' ? 'عميل سعيد' : 'Happy Customers' ?></span>
                </div>
            </div>
            <div class="col-6 col-md-3">
                <div class="stat-item">
                    <span class="stat-number" data-count="50">50+</span>
                    <span class="stat-label"><?= $lang === 'ar' ? 'علامة تجارية' : 'Trusted Brands' ?></span>
                </div>
            </div>
            <div class="col-6 col-md-3">
                <div class="stat-item">
                    <span class="stat-number" data-count="24">24/7</span>
                    <span class="stat-label"><?= $lang === 'ar' ? 'دعم متواصل' : 'Customer Support' ?></span>
                </div>
            </div>
        </div>
    </div>
</section>

<!-- ═══════════════════════════════════════════
     Features Section
═══════════════════════════════════════════ -->
<section class="features-section">
    <div class="container">
        <div class="section-title">
            <h2><?= $lang === 'ar' ? 'لماذا تختارنا؟' : 'Why Choose Us?' ?></h2>
            <p><?= $lang === 'ar' ? 'نقدم لكم أفضل الخدمات والمنتجات بجودة عالية وأسعار منافسة' : 'We offer you the best services and products with high quality and competitive prices' ?></p>
        </div>

        <div class="row g-4">
            <div class="col-md-6 col-lg-4">
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fa-solid fa-truck-fast"></i>
                    </div>
                    <h5><?= $lang === 'ar' ? 'توصيل سريع وآمن' : 'Fast & Safe Delivery' ?></h5>
                    <p><?= $lang === 'ar' ? 'توصيل آمن ومضمون لجميع مدن المملكة خلال 24-48 ساعة' : 'Safe and guaranteed delivery to all cities within 24-48 hours' ?></p>
                </div>
            </div>

            <div class="col-md-6 col-lg-4">
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fa-solid fa-shield-halved"></i>
                    </div>
                    <h5><?= $lang === 'ar' ? 'ضمان معتمد' : 'Certified Warranty' ?></h5>
                    <p><?= $lang === 'ar' ? 'ضمان لمدة سنتين على كافة الأجهزة الطبية من الشركة المصنعة' : '2-year warranty on all medical devices from the manufacturer' ?></p>
                </div>
            </div>

            <div class="col-md-6 col-lg-4">
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fa-solid fa-headset"></i>
                    </div>
                    <h5><?= $lang === 'ar' ? 'دعم فني متواصل' : '24/7 Technical Support' ?></h5>
                    <p><?= $lang === 'ar' ? 'فريق متخصص لخدمتكم على مدار الساعة عبر الهاتف والواتساب' : 'Specialized team to serve you around the clock via phone and WhatsApp' ?></p>
                </div>
            </div>

            <div class="col-md-6 col-lg-4">
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fa-solid fa-credit-card"></i>
                    </div>
                    <h5><?= $lang === 'ar' ? 'طرق دفع متعددة' : 'Multiple Payment Methods' ?></h5>
                    <p><?= $lang === 'ar' ? 'ادفع بالطريقة التي تناسبك: بطاقات، تحويل بنكي، أو عند الاستلام' : 'Pay your way: cards, bank transfer, or cash on delivery' ?></p>
                </div>
            </div>

            <div class="col-md-6 col-lg-4">
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fa-solid fa-rotate-left"></i>
                    </div>
                    <h5><?= $lang === 'ar' ? 'استرجاع سهل' : 'Easy Returns' ?></h5>
                    <p><?= $lang === 'ar' ? 'سياسة استرجاع مرنة خلال 14 يوم من تاريخ الاستلام' : 'Flexible return policy within 14 days of receipt' ?></p>
                </div>
            </div>

            <div class="col-md-6 col-lg-4">
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fa-solid fa-award"></i>
                    </div>
                    <h5><?= $lang === 'ar' ? 'منتجات أصلية' : 'Original Products' ?></h5>
                    <p><?= $lang === 'ar' ? 'جميع منتجاتنا أصلية 100% ومعتمدة من هيئة الغذاء والدواء' : 'All our products are 100% original and FDA approved' ?></p>
                </div>
            </div>
        </div>
    </div>
</section>

<?php include __DIR__ . '/../includes/footer.php'; ?>
