# تحليل صفحات هبوط تطبيقات التغذية والوصفات العالمية
## بحث CRO/UX لصالح منصة تغذية عربية تستهدف السكري النوع 2 ومقاومة الأنسولين والسمنة في السعودية

**تاريخ البحث:** 10 سبتمبر 2026
**المنهجية:** جلب مباشر للصفحات (WebFetch + curl لتحليل الـ HTML الخام)، مع استخراج النصوص الحرفية من كود الصفحات (بما فيها ملفات الترجمة المضمّنة في Klinio/MyBody التي كشفت بنية الـ funnel كاملة)، ومراجعات خارجية موثقة لسدّ الفجوات.

**ملاحظات وصول (مهمة لفهم حدود البيانات):**
- **Klinio أعاد تسمية نفسه:** klinio.com يعمل الآn بتحويلة دائمة (308) إلى **mybody.health** — العلامة الجديدة "MyBody" من نفس الشركة (Kilo Health). حللنا الصفحة الحية الجديدة + بنية funnel السكري المضمّنة في الكود + الإرث التاريخي لـ Klinio من مراجعات موثقة. قسم المحتوى القديم **klinio.com/hub ما زال حياً** وحللناه.
- **Samsung Food** خلف حماية Cloudflare Turnstile؛ جُلبت الصفحة كاملة عبر وسيط قراءة (r.jina.ai) بنجاح.
- **Kitchen Stories** أوقف نسخته الإنجليزية (الرابط /en يعيد 410 Gone) وتحوّل لموقع ألماني بالكامل — وهذه بحد ذاتها نتيجة استراتيجية مهمة (انظر قسمه).
- **web.archive.org محجوب** في بيئة البحث، فاعتمدنا على الكود الحي والمصادر الثانوية للنسخ التاريخية.

---

# 1) Yazio — yazio.com

## بنية الصفحة section-by-section
| # | القسم | العنوان الحرفي | طريقة العرض |
|---|------|----------------|--------------|
| 1 | Navigation | — | روابط: Success stories / Foods / Calculator (4 حاسبات) / Help + زر "Try it now" |
| 2 | Hero | **"Build healthy habits you'll love to keep"** | شخصية كرتونية (mascot اسمه Yettie) + 5 لقطات شاشة مسطّحة للتطبيق + تسلسل بصري ثلاثي: "Start where you are → Stay consistent → See it pay off" |
| 3 | Features (أهداف) | "Reach your goals, your way" | شبكة 8 بطاقات هدف (lose weight, build muscle, track macros, keep cravings in check...) |
| 4 | Features (أدوات) | "Your all-in-one food, fitness and fasting tracker" | 4 بلوكات: AI food tracking / Intermittent fasting (16:8, 5:2, 6:1) / **3,000+ recipes** / Automatic tracking |
| 5 | Social proof | **"Trusted by 100M and counting"** | رقم ضخم بارز وحيد |
| 6 | Success stories | قصص قبل/بعد | بطاقات: Amber (أمريكا) **-40 lb**، Dennis (ألمانيا) **-111 lb** + اقتباس + "Read all stories" |
| 7 | Testimonials | 3 مراجعات مستخدمين | بأسماء وأعمار (Anna 24, Daniel 36, Maria 47) |
| 8 | Final CTA | **"Ready to see results? Start your plan today."** | زر "Try it now" + شارتَي App Store وGoogle Play |
| 9 | Footer | — | About / Success stories / Foods / Calculators / Help / Account / سوشيال |

## الـ Hero
- **Headline:** "Build healthy habits you'll love to keep"
- **Subheadline:** "Get your custom plan in minutes"
- **CTA أساسي:** "Try it now" → يفتح **web onboarding quiz** (وليس متجر التطبيقات) — أكد فحص الكود وجود مسارات `onboarding` و`onboarding-answers`
- صور تطبيق: نعم (لقطات مسطحة، بدون إطار جهاز) — **لا أرقام إثبات داخل الـ hero نفسه** (رقم 100M يأتي لاحقاً)

## مسار التحويل
`Try it now` → onboarding ويب (هدف → جنس → عمر → قياسات → عادات) → توليد خطة → عرض اشتراك → التطبيق. شارات المتاجر تظهر فقط في القسم الختامي كخيار ثانٍ.

## الإثبات الاجتماعي
100M مستخدم (منتصف الصفحة) + قصتا قبل/بعد بأرقام وزن حقيقية + 3 مراجعات بأسماء وأعمار. **لا تقييمات متاجر، لا شعارات إعلامية، لا دراسات** — مفاجئ لحجمهم.

## دور المحتوى
- **الوصفات ليست عامة**: `/en/recipes` يعيد 404 — الـ 3,000 وصفة ميزة داخل التطبيق فقط (تُذكر كـ feature، لا تُستخدم كـ SEO).
- الـ SEO play عندهم مختلف: **أدوات مجانية** (BMI / Ideal weight / Daily calorie intake / Calories burned calculators) + **قاعدة بيانات Foods** عامة. الأداة المجانية تجذب باحث Google ثم تدفعه لنفس الـ onboarding.

## 🟢 يستحق التقليد | 🔴 يستحق التجنب
- 🟢 **التسلسل السردي داخل الـ hero** ("Start where you are → Stay consistent → See it pay off") يبيع الرحلة لا الأداة، بنبرة عادات إيجابية لا نبرة حرمان — ملائم جداً لجمهور مرضى مزمنين يخاف من كلمة "دايت".
- 🔴 غياب تقييمات المتاجر والشعارات الإعلامية يجعل قسم الإثبات يقف على رقم واحد (100M) — لو كان الرقم أصغر (كحال أي منصة ناشئة) لانهار القسم؛ لا تبنِ الإثبات على متغير واحد.

---

# 2) Noom — noom.com

## بنية الصفحة section-by-section
| # | القسم | العنوان الحرفي | العرض |
|---|------|----------------|-------|
| 1 | Hero (مسار مزدوج) | **"Meds to lose the weight. Noom to keep it off."** | صورة شخص حقيقي + بطاقتا مسار: أدوية/نفسي-سلوكي |
| 2 | Products | "We're changing the way the world thinks about weight loss." | 3 بطاقات: Advanced GLP-1 / Microdose GLP-1 / Preventive Health — كل واحدة بزر "SEE IF YOU QUALIFY" |
| 3 | Noom Med + إحصائية | "Access to trusted, powerful weight-loss medications with Noom Med." | **"37% more weight lost with Noom + GLP-1 than with medication alone"** (حاشية: تحليل 14,203 عضو نشط على 40 أسبوعاً) |
| 4 | Noom Weight | "Proven weight loss that lasts—backed by science and personalization." | 3 بطاقات: دروس يومية قصيرة / كوتش بشري + AI / خطط مخصصة |
| 5 | Features deep-dive | — | 5 أقسام متناوبة نص/لقطة جوال (توصيل دواء، أطباء أونلاين، Muscle Defense™، عادات، مجتمع) |
| 6 | B2B | "Enterprise solutions for employers, health plans, and partners." | بطاقة منفصلة |
| 7 | Authority | **"Recommended by doctors. Backed by experts."** | صورة واقتباس من Dr. Jeffrey Egler (Chief Medical Officer) |
| 8 | Media logos | "AS SEEN IN:" | Forbes, Fortune, Healthline, Bloomberg, WebMD, Fast Company, NYT |
| 9 | Blog | "The latest from Noom's blog:" | شبكة 9 مقالات حديثة جداً (بتواريخ سبتمبر 2026) |
| 10 | FAQ | 11 سؤالاً | أكورديون؛ فيه "98% of Noomers say Noom helps change their habits" + معايير استبعاد (حامل، اضطراب أكل، BMI<18.5) |
| 11 | Instagram | "Follow us on Instagram @noom" | شبكة منشورات |
| 12 | Final CTA | "Reach your weight-loss goals and start living your healthiest life." | "Get started" → quiz |
| 13 | Footer | — | + شهادة LegitScript + حاسبات سعرات/ماكروز |

## الـ Hero
- **Headline:** "Meds to lose the weight. Noom to keep it off." — يركب موجة GLP-1 ويموضع Noom كضامن الاستدامة
- **CTAs:** "See if you qualify" (مسار طبي/أهلية) و"Start your trial" (مسار سلوكي) — **كلاهما يقود لتقييم/quiz، لا يوجد رابط متجر تطبيقات إطلاقاً في الصفحة**
- لا أرقام في الـ hero — الأرقام تأتي في القسم 3

## مسار التحويل (quiz-first funnel نموذجي)
CTA → "free evaluation" (quiz يسأل عن الهدف، الدافع "ultimate why"، الحالة الصحية، الثقة بالنجاح) → **شاشة نتائج مخصصة**: خطة مقترحة + منحنى تقدم متوقع → عرض trial → دفع. التسعير لا يظهر أبداً قبل الـ quiz (فقط في حواشي دقيقة: Microdose من $79 بداية + $199/شهر؛ Advanced من $149 + $349/شهر).

## الإثبات الاجتماعي
هرمي ومتنوع: إحصائية بحثية بعيّنة معلنة (14,203) → توصية طبيب بمنصبه → 7 شعارات إعلامية → "98%" داخل FAQ → ملايين مستخدمين (بدون رقم دقيق). **لا قصص قبل/بعد على الصفحة الرئيسية** — الإثبات "مؤسسي/علمي" لا فردي.

## دور المحتوى (جوهري هنا)
- **المدونة محرك SEO ضخم ومربوط عضوياً بالصفحة الرئيسية** (قسم كامل قبل الـ FAQ). عناوين المقالات نفسها نية بحث تجارية-معلوماتية: "Semaglutide cost: With and without insurance in 2026"، "How long does it take Wegovy to work?"، "Is xylitol bad for you?"، وحتى "Starbucks fall menu 2026: Nutrition facts".
- الصيغة: **اصطد سؤال المريض القلِق في Google → أجب بمصداقية → حوّله لنفس الـ quiz**. المحتوى ليس قسم وصفات بل قسم "أسئلة المريض".

## 🟢 | 🔴
- 🟢 **إحصائية النتيجة بصيغة "X% أفضل مع منصتنا + العلاج مقارنة بالعلاج وحده" مع حجم عيّنة معلن** — هذه أقوى جملة إقناع لجمهور طبي، وقابلة للنسخ لسياق السكري (برنامجنا + دواء الطبيب مقابل الدواء وحده).
- 🔴 ازدحام العروض (Med / Weight / Microdose / Preventive / B2B / HRT) شتّت الصفحة الرئيسية؛ زائر واحد يواجه 5 منتجات وقرارَي CTA مختلفين قبل أن يفهم أيها له. المنصة الناشئة يجب أن تقاوم إغراء عرض كل شيء.

---

# 3) Klinio → MyBody — klinio.com / mybody.health ⭐ (التحليل المعمّق)

> **الحدث الاستراتيجي أولاً:** Klinio (تطبيق حمية السكري الأشهر، من Kilo Health) أعاد التسمية إلى **MyBody** ووسّع المظلة: نفس المحرك يشغّل الآن funnels للسكري، ما قبل السكري، A1C، إدارة الوزن، كيتو، PCOS، القلب، وحتى مصاحبة GLP-1 — كل funnel له عنوان hero خاص وأسئلة خاصة. هذا درس بحد ذاته: **الصفحة ليست موقعاً، بل قالب توليد صفحات هبوط لكل حالة/إعلان**.

## 3.1 بنية الصفحة الحية (mybody.health)
الصفحة **بوابة quiz فائقة الاختزال** — أقصر صفحة هبوط في العيّنة كلها:
1. **شريط شعارات إعلامية** (أعلى الصفحة): Forbes Health, The Guardian, Validation Institute (رمادية)
2. **Hero = الصفحة كلها تقريباً:**
   - العنوان الحرفي الافتراضي: **"Easy-to-follow weight-management diet"**
   - لا subheadline. صورة طبق أكل صحي.
   - الـ CTA ليس زراً عاماً بل **أول سؤال في الـ quiz مدمجاً في الـ hero**: "Select your gender:" مع زرّين **"Diet for women" / "Diet for men"**
3. **Footer:** Manage Subscription / Help Center / سياسات + **إخلاء مسؤولية طبي كامل** (نصه أدناه)

لا features، لا testimonials، لا pricing، لا FAQ على الصفحة الرئيسية — كل شيء داخل الـ funnel بعد الدخول.

## 3.2 العناوين الديناميكية (من ملفات الترجمة المضمّنة في الكود — نصوص حرفية)
الـ hero يتبدل حسب مصدر الزيارة/الإعلان:
- `landing_main_heading` = **"Easy-to-follow diabetes management plan"**
- `landing_main_heading_dynamic` = **"Easy-to-follow diabetes management diet for {{gender}} over {{age}}"** ← تخصيص بالجنس والعمر من بيانات الإعلان نفسه
- `landing_main_heading_prediabetes` = "Easy-to-follow prediabetes management diet"
- "Easy-to-follow A1C management plan" / "Easy-to-follow blood sugar management plan" / "Blood sugar management plan for prediabetics"
- "Mediterranean diet for blood sugar management" / "DASH diet for A1C level management" / "A1C diet for beginners"
- للعائد: "Glad to see you back" — وللمواسم: "Start losing weight in the New Year"، "Say goodbye to the winter weight"...
- meta للسكري: **"Diabetes Management and Weight Loss Assistant"** / "Get personalized diabetes management and meal plan in one app. Control your diabetes, lose weight, and stick to a healthy diet."

## 3.3 كيف يخاطب مريض السكري؟ (اللغة)
**مطمئنة تمكينية، ليست طبية-أكاديمية ولا تخويفية في الواجهة** — الكلمات المفتاحية: easy-to-follow, control, manage:
- "**Eat what you love** and improve blood sugar levels" — أشهر جملة في الـ funnel: تنفي الحرمان أولاً ثم تعد بالنتيجة
- "Get a **fully customized diabetes-friendly meal plan**"
- قسم القصة داخل الـ funnel (3 خطوات): "Plan your meals stress-free" → "Easily track your progress" (تتبع sugar, carbs, cholesterol) → **"Achieve your desired weight and control diabetes... Diabetes complications or symptoms will be way behind you. Feel more confident, energetic, and healthier than ever before."**
- التخويف يُستخدم بجرعة محسوبة داخل الـ quiz فقط (نتيجة BMI): "You're overweight, which increases the risk of heart disease, stroke, high blood pressure, and diabetes. **It's time to take back control.**"
- ولغير المشخّصين modal أمانة: "Without your medical information, we can't adapt your plan to your health needs. **Please consult with your doctor** before starting the program."

## 3.4 الـ Quiz (60-Second Quiz) — الأسئلة الفعلية من الكود
التأطير الرسمي: **"a 60-second quiz approved by our experts"**. السؤال الأول (الجنس) مدمج في الـ hero نفسه = صفر احتكاك للنقرة الأولى. تسلسل أسئلة funnel السكري:
1. الجنس (على الصفحة) → 2. **"What's your main goal?"** (خيارات حرفية: **Balance my blood sugar** / Lose weight / Boost energy and feel better / Improve health / Avoid weight regain...) → 3. **"What kind of diabetes do you have?"** (Type 1 / Type 2 / Prediabetes / **I don't know**) → 4. **"Select your A1C levels"** → 5. "Do you monitor your blood glucose?" → 6. "How long ago were you diagnosed (or self-diagnosed) with any type of diabetes?" → 7. "Any relatives with diabetes?" (+"Has a doctor ever mentioned diabetes, blood sugar, or pre-diabetes to you?" لمسار غير المشخصين) → 8. العمر ("Your age helps us with metabolic calculations") → الطول/الوزن/الوزن المستهدف → 9. تفضيلات الأكل والحساسيات والأطعمة المستبعدة → 10. عدد الوجبات ("How many meals do you prefer per day?" 2–5) → 11. مستوى النشاط → 12. **التقاط الإيميل** → صفحة الخطة/الدفع.
- **حِيَل احتكاك ذكية:** كل سؤال معه subtitle يشرح "لماذا نسأل" — و**تغذية راجعة معيارية** بعد الإجابات: "💪 **41% of users** started just like you!" / "🏃 You're more active than **58% of users**!"
- **إعادة تأطير الهدف بلغة طبية مبسطة:** عند اختيار وزن مستهدف يظهر: "✅ **DOABLE GOAL: 5% weight loss** — Just a 5% drop can improve blood pressure, cholesterol, **insulin sensitivity**..." أو "💪 **BIG GOAL: 20% weight loss** — can seriously improve **blood sugar control, insulin resistance**, and metabolic health".

## 3.5 عرض الـ Outcomes
- الوعد الأساسي مزدوج دائماً: **وزن + تحكم بسكر الدم** ("Control your diabetes, lose weight"). لا وعد رقمي بخفض HbA1c في الواجهة الحية (حماية قانونية) — الأرقام تأتي عبر **شهادات المستخدمين**: "My **fasting blood sugar dropped by 15 points** in the first month" / "Dropped 8 lbs in just a few weeks **without feeling like I was even dieting**" / (نسخة القلب: "My BP is now 118/64").
- تاريخياً كان الـ quiz ينتهي بـ **"diabetes management score"** (مثال موثق: 59.7% مع رسالة "take immediate action") + تاريخ متوقع للوصول للوزن المستهدف.
- التحوط القانوني مزدوج: "**DISCLAIMER: RESULTS MAY VARY FROM PERSON TO PERSON**" + في الـ footer: "...products are meant to support general health. Our products and services are **not intended to diagnose, treat, cure, or prevent any disease**. They should not be substituted for medical advice or medical intervention. Please consult a qualified healthcare provider."

## 3.6 الأسعار وطريقة عرضها
- **لا سعر قبل نهاية الـ quiz إطلاقاً.** صفحة الدفع تُبنى على الإلحاح والحِزم:
  - سطر فوق الخطط: **"Last week 5,347 started – it's YOUR turn now!"**
  - خطط 1 / 3 / 6 (وحتى 12) شهراً بأوصاف تموضع: "Ideal solution for trying out the plan" (شهر) / "Great for building new healthy habits" (3 أشهر) / "For achieving the best health results" (6 أشهر)
  - خصومات وكوبونات: "**up to 33% off all plans!**"، عروض VIP بعدّاد: "VIP offer expires in..."، هدايا: "Get {{discount}} off, plus a **Klinio Desserts recipe eBook** when purchasing a 6-month plan!"، ولعبة "Unwrap your discount — Tap one of the gifts"
  - **"30 days money-back guarantee"**: "We are confident in our program, and you should start seeing results within a month! If you don't notice any changes, we'll give you a full refund."
  - رابط تبرير السعر: "Discover the reasoning behind our pricing — **see why** it's worth your while."
  - FAQ مصغّر على صفحة الدفع نفسها: "People often ask us"
  - نسخة GLP-1: "Your GLP-1 plan is customized and waiting!"
- **مرجع تاريخي موثق (مراجعة Abby Langer, RD):** اشترت الخطة بـ **$60 / 3 أشهر**، ثم upsells فورية: مكمل ألياف "Weight Loss Fuel" + كتاب طبخ + برنامج تمارين، مع عدّاد "Buy in the next 15 minutes or it's all gone!" وإيميلات متابعة مستمرة من شخصية اسمها "Christine".

## 3.7 دور المحتوى: Klinio Knowledge HUB (ما زال حياً على klinio.com/hub)
- مكتبة SEO ضخمة بصيغة موحّدة تصطاد long-tail سؤال مريض السكري عن كل طعام: **"Avocado and Diabetes"، "Beer and Diabetes: Can I Still Drink Beer?"، "Orange Juice and Diabetes: Good Enough for My Condition?"، "Lasagna and Diabetes"، "Pistachios and Diabetes"...** (بأربع لغات: en/de/es/fr)
- بنية المقال نفسها أداة تحويل: إجابة علمية بمراجع (روابط دراسات) → **وصفة كاملة مدمجة داخل المقال** → CTA سياقي ختامي: "For people looking for support for managing diabetes, it can be helpful to **download the Klinio diabetes app**. The app offers... personalized diabetes meal plans and at-home workouts, so you can make the lifestyle changes necessary for keeping blood sugar levels in check."
- وأسفل صفحة الفهرس: **"Start managing your diabetes today!"**
- الخلاصة: **funnel-first في الواجهة، content-first في Google** — المحتوى لا يظهر على صفحة الهبوط أبداً لكنه يملأ أعلى القمع من البحث.

## 3.8 نقاط موثقة ضد Klinio (من مراجعات مختصين — لتتجنبها المنصة العربية)
- الـ quiz **لا يسأل عن الأدوية ولا الأنسولين** رغم سؤاله عن نوع السكري (انتقاد حرفي: "IT KNOWS I HAVE TYPE 1 DIABETES AND IT DIDN'T ASK ME IF I TAKE INSULIN")
- قَبِل وزناً مستهدفاً خطيراً (85 lb) بدون تحذير، ولا خيار "اضطراب أكل" في القائمة الصحية
- ضغط بيع عدواني (عدادات، خصومات وهمية الطابع، إيميلات مكثفة) يولّد مراجعات غاضبة تلاحق العلامة

## 🟢 | 🔴 (Klinio/MyBody)
- 🟢 **دمج أول سؤال quiz في الـ hero نفسه + عناوين ديناميكية لكل حالة وشريحة إعلانية** — أعلى صيغة CVR في القطاع لأن النقرة الأولى التزام مجهري ("أنا امرأة") لا قرار شراء، والعنوان يطابق نية الإعلان حرفياً.
- 🔴 **الإفراط في ميكانيكية البيع (عدادات + هدايا + "5,347 بدأوا") مع ثغرات أمان سريري (لا سؤال أدوية/أنسولين)** — في سوق سعودي يثق بالطبيب والجهات الصحية، هذا المزيج يقتل المصداقية الطبية التي هي رأس مال المنصة؛ خذ بنية الـ funnel واترك أسلوب الضغط.

---

# 4) Samsung Food — samsungfood.com

## بنية الصفحة section-by-section
| # | القسم | العنوان الحرفي | العرض |
|---|------|----------------|-------|
| 1 | Hero | **"Food Your Way"** | صورة hero + **"4.8 rating in the AppStore and Google Play"** تحت الـ subheadline مباشرة |
| 2 | Feature | "Save all your recipes in one place" | **فيديو منتج قصير** + نص (حفظ من أي موقع لـ recipe box) |
| 3 | Feature | "Discover new dishes you'll love" | مجتمعات وصفات حسب التفضيلات والقيود |
| 4 | Feature | "Make meal plans you'll actually want to follow" | فيديو drag & drop للـ meal planner |
| 5 | Feature | "Cut grocery shopping time in half" | فيديو تحويل الوصفة لقائمة تسوق بنقرة |
| 6 | Feature (صحة) | "Meet your health goals" | فيديو Health Score + معلومات تغذية لأي وصفة |
| 7 | Awards | "Home cooks around the world love Samsung Food" | 4 جوائز: Apple **Featured App of the Week**، Google Play **Best Everyday Essentials**، Webby Nominee 2021، Users' Choice Nominee |
| 8 | Testimonials | — | **جدار مراجعات طويل مصنّف حسب الفائدة**: "on organizing recipes" / "on better meal planning" / "on saving time shopping" / "on discovering recipes" / "on achieving health goals" (منها: "I have expanded my food horizons and **lost 14lbs** at the same time") |
| 9 | Final CTA | **"Get the award-winning app"** | شارات متاجر |

## الـ Hero
- **Headline:** "Food Your Way" | **Subheadline:** "Meet the all-in-one app for recipe saving, meal planning, grocery shopping, and recipe sharing."
- **CTA:** تنزيل التطبيق (شارات متاجر + رابط get.samsungfood.com/app) — **تحويل مباشر للمتجر، لا quiz**
- إثبات في الـ hero: نعم — تقييم 4.8 في المتجرين

## مسار التحويل
الأقصر في العيّنة: hero → متجر التطبيقات. لا onboarding ويب ولا التقاط إيميل. بديل موازٍ: **web app كامل** (app.samsungfood.com) يتيح الاستخدام من المتصفح فوراً.

## الإثبات الاجتماعي
تقييم 4.8 (hero) → جوائز منصات (منتصف) → جدار مراجعات مصنّف (أسفل). لا أرقام مستخدمين ولا شعارات إعلامية.

## دور المحتوى (قوي جداً)
- **samsungfood.com/recipes/** صفحة SEO عامة (عنوانها H1: "Food Your Way" + "★★★★★ 4.8 rating") تعرض فئات الوصفات الشائعة وتصبّ كل رابط في **الـ web app** (app.samsungfood.com/recipes، /categories، /communities، /creators) — أي أن المحتوى المجاني لا يقود للمتجر بل **لتجربة منتج فورية بلا تنزيل**، والتسجيل يأتي لاحقاً من داخل التجربة. + مدونة (samsungfood.com/blog).
- ملاحظة تشغيلية: الموقع خلف حماية بوتات صارمة (Cloudflare Turnstile) — يعيق أدوات الجلب لكنه لا يمس المستخدم.

## 🟢 | 🔴
- 🟢 **تصنيف الشهادات حسب الفائدة المزعومة** ("on better meal planning"، "on achieving health goals") — يحوّل جدار المديح العشوائي إلى إثبات موجّه: كل زائر يقرأ الإثبات الخاص بدافعه هو.
- 🔴 hero من عبارة تجريدية ("Food Your Way") بلا فائدة ملموسة ولا جمهور محدد — يعتمد كلياً على وضوح الـ subheadline؛ ولصفحة رئيسية بلا مسار تحويل ويب (متجر فقط) يخسر كل من لا يريد التنزيل الآن.

---

# 5) SideChef — sidechef.com

## بنية الصفحة section-by-section (content-first صِرف)
| # | القسم | العنوان الحرفي | العرض |
|---|------|----------------|-------|
| 1 | Nav | — | تصنيف وصفات كامل (Popular/Meal/Diet/Ingredient/Cuisine) + Meal Plans + Sign Up |
| 2 | "Hero" | **"Kick Off September with Delicious Fall Finds!"** | كاروسيل حملات موسمية، CTA: **"VIEW RECIPES"** → /recipes/fall/ (وليس تنزيل تطبيق!) |
| 3 | Trending | "Trending" | شبكة 12 وصفة، على كل بطاقة زر **"Add [X] Ingredients"** (تسوّق) |
| 4 | Viral | "Viral Recipes You'll Want to Try ASAP" | كاروسيل 10 وصفات |
| 5 | تصفح | "Pick Your Meal" | 6 أزرار حسب الوجبة |
| 6 | Collections | "Featured Content" | 4 بطاقات قوائم منسقة |
| 7 | Seasonal grid | "Warmth in a Bowl" | 12 وصفة شوربة |
| 8 | Facets | "Explore All Recipes By" | 7 محاور تصفية (SEO داخلي) |
| 9 | Creators | "Meet Our Creators" | 12 بروفايل صنّاع محتوى |
| 10 | Value props | "Why Try SideChef?" | 4 نقاط كلها عن **البقالة**: Home Delivery or Store Pickup / No Price Markups / Real-time Store Inventory / Fresh & Affordable |
| 11 | Topics | "Recommended For You" | 15+ وسم |
| 12 | Testimonials | "What Home Cooks Are Saying" | 3 اقتباسات بأسماء ومدن أمريكية |
| 13 | FAQ | "Have questions?" | 8 أسئلة معظمها عن طلبات البقالة (Walmart) |
| 14 | Promo | "Use the code SIDECHEF for $10 off your first $50 shoppable recipe order." | بانر |
| 15 | Footer | — | شارات المتاجر **هنا فقط** + روابط B2B (Cooking Experience Platform, Shoppable Tech, SideChef AI) |

## الـ Hero + مسار التحويل + الإثبات
- الـ "hero" حملة محتوى موسمية؛ التحويل الأساسي ليس التطبيق بل **الوصفة القابلة للتسوق**: اكتشف وصفة → "Add Ingredients" → سلة Walmart → توصيل/استلام. التطبيق تحويل ثانوي (footer). الإثبات خفيف: 3 شهادات + بروفايلات صنّاع؛ لا أرقام ولا جوائز على الرئيسية.

## دور المحتوى
المحتوى **هو** المنتج والقمع معاً: كل وصفة صفحة SEO وكل صفحة نقطة بيع بقالة. الربح من العمولة/الشراكات (وB2B licensing)، لا من اشتراك مستخدم. نموذج ملهم جزئياً لكنه يفترض تكامل بقالة عميق (عندنا: نون/كارفور/نعناع مستقبلاً).

## 🟢 | 🔴
- 🟢 **CTA بصيغة فعل قيمة فوري على بطاقة الوصفة نفسها** ("Add 7 Ingredients") — يحوّل الإلهام لفعل في نفس النقرة؛ الترجمة لسياقنا: "أضف لخطة أسبوعك" على كل وصفة.
- 🔴 هوية مشتتة: الرئيسية تبيع بقالة أمريكية بينما العلامة "تطبيق طبخ تفاعلي" — زائر التطبيق لا يجد قصة التطبيق إلا في الـ footer؛ لا تدع نموذج الإيراد يبتلع قصة المنتج.

---

# 6) Kitchen Stories — kitchenstories.com

## الوضع الحالي (نتيجة استراتيجية بذاتها)
- **النسخة الإنجليزية أُوقفت** (/en يعيد **410 Gone**) — المنصة التي كانت "تطبيق وصفات عالمي ثنائي اللغة بتمويل BSH/Bosch" أصبحت **مجلة طبخ ألمانية** تديرها AJNS New Media، تعيش من الشراكات والمحتوى المدعوم.

## بنية الصفحة (الألمانية الحية)
| # | القسم | العنوان (مترجماً عند الحاجة) | العرض |
|---|------|------------------------------|-------|
| 1 | Nav | Rezepte / Artikel / **App** / **Plus** / Unsere Partner | المحتوى أولاً؛ التطبيق مجرد رابط |
| 2 | Hero | "Rezept des Tages" (وصفة اليوم) | بطاقة وصفة كبيرة |
| 3 | Latest | "Unsere neuesten Rezepte" (أحدث وصفاتنا) | شبكة وصفات |
| 4 | **Partners** | "Unsere Partner" | أقسام كاملة لعلامات غذائية (HITCHCOCK, enerBiO, Riso Gallo, Rügenwalder Mühle, KLUTH) = محتوى مدعوم |
| 5 | Creators | "Entdecke die besten Rezepte von..." | وصفات حسب الصانع |
| 6 | Utility | "Was du heute Abend kochen kannst" (ماذا تطبخ الليلة) | تقسيم بنية استخدام |
| 7 | Seasonal | مجموعات موسمية (فواكه الصيف المتأخر...) | شبكات مقالات/وصفات |
| 8 | Footer | Folge uns / Wissenswertes / Finden / Für Marken ("للعلامات التجارية") | Newsletter + سوشيال |

## صفحة التطبيق المنفصلة (pages.kitchenstories.com/de/app)
هي صفحة الهبوط الفعلية للتطبيق، خارج الرئيسية: "Die Kitchen Stories-App" → نظرة عامة (Innovative Technologie / Prämiertes Design) → **Kitchen Stories Plus** (الاشتراك) → "أكثر من 10,000 وصفة" → كتب طبخ رقمية → "خطوة بخطوة لأفضل نتيجة" → "وصفات مضمونة النجاح من محترفين" → جوائز (Auszeichnungen) → 6 شهادات مستخدمين بأسماء → **"حمّل التطبيق مجاناً!"** + شارات المتاجر.

## مسار التحويل + الإثبات + المحتوى
التحويل الأول على الرئيسية هو **قراءة وصفة + Newsletter**؛ التطبيق تحويل من الدرجة الثانية عبر صفحة فرعية. الإثبات (جوائز التصميم + شهادات) معزول في صفحة التطبيق. المحتوى هو المنتج، والإيراد من "Für Marken" (بوابة إعلانات للعلامات).

## 🟢 | 🔴
- 🟢 **"وصفة اليوم" + "ماذا تطبخ الليلة"** — نمطا عادة يوميان يصنعان سبب عودة يومي (retention للمحتوى قبل التطبيق)، ورخيصان تحريرياً.
- 🔴 **العبرة الكبرى في العيّنة: المحتوى الصِرف بلا funnel اشتراكي قوي انتهى بتقليص العلامة نفسها** (إغلاق الإنجليزية، تحول التطبيق لهامش، الاعتماد على الرعايات). المحتوى وحده وسيلة اكتساب، ليس نموذج عمل لمنصة صحية.

---

# 7) MyFitnessPal — myfitnesspal.com

## بنية الصفحة section-by-section
| # | القسم | العنوان الحرفي | العرض |
|---|------|----------------|-------|
| 1 | Hero | **"The world's #1 nutrition tracking app"** | خلفية طبق علوي + نص مركزي |
| 2 | Social proof | **"5.5 Million 5-Star Reviews"** | 5 مراجعات قصيرة بأسماء + **شارات المتاجر مبكراً هنا** |
| 3 | Features | "Nutrition tracking made effortless" | 5 بطاقات بلقطات تطبيق: AI Nutrition Coach / **Meal Scan** (صوّر طبقك) / **Voice Log** / **GLP-1 Progress** / Barcode Scan |
| 4 | Integrations | "Compatible with 40+ apps and devices" | شبكة شعارات (Apple Health, Garmin, Samsung Health, Strava...) |
| 5 | Database scale | "Restaurant menus, home recipes, and everything in between" | أرقام: **20.5M Foods / 2K+ In-App Recipes / 30+ Cuisines** |
| 6 | Success stories | **"Nutrition tracking works."** | 5 قصص أطول ("I was **307 lbs**, and today I am **199 lbs**... I still use it everyday") |
| 7 | Media | "As seen in…" | Women's Health, USA Today, CNN, CNET, Daily Mail, Good Housekeeping, BBC Radio |
| 8 | FAQ | 5 أسئلة بصياغة SEO | ("Is MyFitnessPal a free calorie tracker app?"...) + ادعاء علمي: معادلة Mifflin-St Jeor "within 10% of actual energy needs on average" |
| 9 | Footer | "Nutrition tracking for real life." | CTA "Start Today" + شارات + رابط Blog |

## الـ Hero
- **Headline:** "The world's #1 nutrition tracking app" (ادعاء ريادة فئة مباشر)
- **Subheadline:** "Join over 280 million people on their journey to eat better, building lasting habits, and reach their goals." ← **رقم الإثبات داخل الـ subheadline نفسه**
- **CTA:** "Start for free" → **تسجيل ويب** (/account/create/welcome — onboarding ويب ثم التطبيق) + CTA ثانوي فريد: "HSA/FSA eligible if you qualify" (دفع عبر حسابات التوفير الصحي الأمريكية — أي: "قد يدفعها تأمينك")
- لا mockup جهاز في الـ hero — صورة طعام

## مسار التحويل
"Start for free" → إنشاء حساب ويب مع onboarding أهداف → التطبيق (أو الاستمرار ويب) → عرض Premium بتجربة 7 أيام. مسار مزدوج: ويب أولاً، والمتاجر معروضة مبكراً (قسم 2) لمن يفضل التنزيل مباشرة.

## الإثبات الاجتماعي (الأكثف في العيّنة)
280M مستخدم (hero) → 5.5M مراجعة 5 نجوم (فوراً بعده) → أرقام قاعدة البيانات (20.5M طعاماً) → قصص تحول بأرقام → 7 شعارات إعلامية → ادعاء علمي بمعادلة مسماة. تدرّج مثالي: حجم → رضا → قدرة → نتائج → غطاء إعلامي → علم.

## دور المحتوى
- مدونة ضخمة على subdomain (blog.myfitnesspal.com) لكنها **غير معروضة في بنية الصفحة الرئيسية** (رابط footer فقط) — عكس Noom. الحاسبات (BMR) مربوطة من إجابات الـ FAQ. الـ FAQ نفسه مكتوب كصفحة استحواذ بحثي (أسئلة بصيغة كلمات مفتاحية).

## 🟢 | 🔴
- 🟢 **الافتتاحية "ريادة الفئة + رقم مجتمع داخل جملتين"** ثم مراجعات المتاجر فوراً — أسرع بناء ثقة في العيّنة؛ وميزة "GLP-1 Progress" مثال على مواكبة موجة طبية داخل features الصفحة.
- 🔴 الصفحة عامة لدرجة أنها لا تخاطب أي حالة صحية محددة (السكري غائب تماماً رغم ملاءمة المنتج له) — تفوز بالحجم لا بالتموضع؛ المنصة المتخصصة يجب أن تفعل العكس تماماً.

---

# صيغة صفحة الهبوط الفائزة (Winning Formula)

## أولاً: النموذجان المتنافسان في العيّنة

| | **نموذج الـ Funnel أولاً** (Noom, Klinio/MyBody, Yazio جزئياً) | **نموذج المحتوى أولاً** (SideChef, Kitchen Stories, Samsung Food جزئياً) |
|---|---|---|
| الـ hero | وعد نتيجة/حالة + مدخل quiz | وصفة/حملة موسمية + تصفح |
| الـ CTA الأول | سؤال تشخيصي (التزام مجهري) | "شاهد الوصفات" / حفظ / تسوق |
| السعر | مخفي حتى نهاية الـ quiz | لا اشتراك أصلاً أو مخفي في صفحة فرعية |
| المحتوى | خارج الصفحة (blog/hub) يصب في الـ quiz | هو الصفحة نفسها |
| نقطة القوة | CVR عالٍ جداً + تخصيص + بيانات | Traffic ضخم رخيص + ثقة + عادة يومية |
| نقطة الانهيار | مصداقية طبية هشة إذا زاد الضغط البيعي (مراجعات Klinio الغاضبة) | بلا اشتراك يتآكل النموذج (مصير Kitchen Stories الإنجليزي) |
| المؤشر الحاسم | Quiz completion + trial CVR | Organic sessions + email capture |

**الخلاصة البنيوية:** الرابحون الحقيقيون يشغّلون **الاثنين كطبقتين منفصلتين متصلتين**: واجهة funnel نظيفة (لا يظهر فيها المحتوى إلا كإثبات) + محرك محتوى SEO منفصل كل مخارجه تصب في الـ funnel (نموذج Noom blog وKlinio hub وحاسبات Yazio). الخطأ القاتل هو خلط الطبقتين في صفحة واحدة (SideChef) أو الاكتفاء بطبقة واحدة (Kitchen Stories).

## ثانياً: الترتيب الأمثل للأقسام (مستخلص من السبعة، لمنصة سكري/سمنة عربية)

1. **Hero بمعادلة Klinio+MFP:** عنوان حالة محددة سهل النبرة («خطة سهلة الالتزام للتحكم بسكر الدم — مصممة لأكلنا») + رقم إثبات واحد في الـ subheadline + **أول سؤال quiz مدمجاً في الـ hero** (زرّان: رجل/امرأة أو سكري نوع 2/مقاومة أنسولين/سمنة) بدل زر "حمّل التطبيق". صورة أكل محلي حقيقي، لا mockup بارد.
2. **شريط ثقة فوري** (نمط MFP/Noom): تقييم المتاجر + عدد مستخدمين/وجبات محسوبة + شعارات جهات (إعلام صحي، جمعيات، ترخيص) — سطر واحد رمادي.
3. **"كيف تعمل" في 3 خطوات سردية** (نمط Yazio/Klinio storytelling): quiz 60 ثانية ← خطة وجبات عربية مخصصة ← تتبع السكر والوزن وتحسّن ملموس.
4. **Features بأسلوب فيديو/لقطات متناوبة** (نمط Samsung Food): خطة وجبات + بدائل أطباق محلية، تتبع مبسط (صوّر طبقك)، قائمة تسوق، متابعة مؤشرات (وزن، سكر صائم، محيط خصر).
5. **Outcomes + قصص قبل/بعد بأرقام** (نمط Yazio/MFP): «-12 كجم»، «سكر صائم انخفض 15 نقطة» بصيغة شهادة مستخدم لا وعد شركة (التحوط القانوني بأسلوب Klinio: "النتائج تختلف من شخص لآخر").
6. **إثبات علمي/طبي واحد قوي** (نمط Noom): إحصائية بعيّنة معلنة أو توصية اختصاصيين بأسمائهم ومناصبهم + جملة «لا يغني عن استشارة طبيبك» — في السوق السعودي هذه تبني أكثر مما تحد.
7. **شهادات مصنفة حسب الدافع** (ابتكار Samsung Food): «عن ضبط السكر» / «عن خسارة الوزن» / «عن سهولة الوصفات».
8. **جسر المحتوى المجاني** (نمط Noom blog): 6–9 بطاقات من محرك الـ SEO («التمر والسكري؟»، «الكبسة بطريقة تناسب السكري»، حاسبة BMI/سعرات عربية) — كل مقال ينتهي بـ CTA سياقي نحو الـ quiz (صيغة Klinio hub حرفياً).
9. **FAQ بصياغة أسئلة بحث حقيقية** (نمط MFP/Noom): «هل التطبيق يغني عن الدواء؟ (لا)»، «هل يناسب النوع الأول؟»، «كم السعر؟» — صدق الاستبعاد يبني ثقة (نمط معايير Noom).
10. **CTA ختامي + شارات المتاجر** (الجميع): تكرار وعد الـ hero + الـ quiz أولاً والمتاجر ثانياً.
11. **Footer بإخلاء المسؤولية الطبي الكامل** (صيغة MyBody) + إدارة الاشتراك وسياسة الاسترجاع بشكل ظاهر (ضمان 30 يوماً يُعرض كميزة لا كبند قانوني).

## ثالثاً: خمس قواعد ذهبية مستخلصة
1. **السؤال قبل السعر دائماً** في الحالات الطبية: كل الناجحين يخفون السعر خلف الـ quiz لأن التخصيص يبرر الاشتراك — لكن بلا عدادات ضغط عدوانية (خط Klinio الأحمر).
2. **رقم واحد في الـ hero يساوي عشرة أسفل الصفحة** (280M عند MFP، 4.8 عند Samsung Food) — ولو كنت ناشئاً استخدم رقماً صادقاً صغيراً محدداً («+3,200 وجبة سعودية محسوبة الكارب») بدل ادعاء ضخم.
3. **العنوان يطمئن والـ quiz يشخّص:** لغة الواجهة "سهل، تحكم، كل ما تحب" — والجدية الطبية (A1C، الأدوية، القياسات) داخل الـ quiz، مع سؤال الأدوية/الأنسولين الذي أهمله Klinio (فرصة تفوّق سريري وتنظيمي واضحة).
4. **المحتوى طبقة اكتساب منفصلة، صيغته «[أكلة محلية] والسكري»:** فراغ SEO العربي هنا شبه كامل، وklinio/hub يعطي القالب الجاهز: إجابة موثقة + وصفة داخل المقال + CTA سياقي.
5. **قدّم تجربة ويب قبل التنزيل** (درس Samsung Food/MFP/Yazio): onboarding ويب يلتقط الإيميل ويبني الخطة قبل حاجز المتجر — التنزيل يأتي بعد الالتزام النفسي، لا قبله.

---

## ملحق: مصادر خارجية مكملة استُخدمت لسد الفجوات
- Health Reporter — Klinio Review (تجربة اختصاصية تغذية): healthreporter.com/klinio-review/
- Abby Langer Nutrition — "Klinio Review: Can Klinio Manage Diabetes?" (تفاصيل الـ quiz والتسعير $60/3 أشهر والـ upsells): abbylangernutrition.com/klinio-review-can-klinio-manage-diabetes/
- Trustpilot — Klinio reviews: trustpilot.com/review/klinio.com
- Noom Support — Plan Pricing and What to Expect + مراجعات funnel مستقلة (prettysweet.com/is-noom-free)
- الصفحات الحية المؤرشفة محلياً في: `scratchpad/html/` (mybody, mybody_quiz, klinio_hub, yazio, ks_root, ks_app, samsungfood_jina, sf_recipes)
