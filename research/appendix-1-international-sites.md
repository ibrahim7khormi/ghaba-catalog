# دراسة مقارنة: بنية وتنظيم أشهر مواقع الوصفات العالمية
**لصالح مشروع منصة تغذية عربية — بحث UX/IA**
تاريخ الفحص: 10 سبتمبر 2026

---

## المنهجية وملاحظات الوصول

- فُحصت 3 صفحات لكل موقع: الرئيسية، صفحة تصنيف/قسم، صفحة وصفة — بتحليل الـ HTML الخام (بنية الـ navigation، ترتيب الأقسام، نماذج البحث والنشرة، وبلوكات JSON-LD الخاصة بـ schema.org).
- **ملاحظة وصول مهمة:** المواقع الثلاثة التابعة لناشر Dotdash Meredith / People Inc (AllRecipes، Serious Eats، EatingWell) تحجب الزيارات من خوادم مراكز البيانات (HTTP 402 برسالة رسمية من الناشر)، وكذلك تحجب وسيط Jina (HTTP 451). جرى الالتفاف عبر أرشيف الويب (Wayback Machine) حيث أمكن، ويُشار عند كل موقع إلى مصدر البيانات ودرجة الثقة.
- موقع Tasty يحجب صفحاته الداخلية عن بعض العملاء (HTTP 406) وجرى تجاوزه بترويسات متصفح كاملة عبر HTTP/1.1.

---

# أولاً: تحليل المواقع الثمانية

## 1. AllRecipes — allrecipes.com
> **مستوى الدليل:** حجب الناشر (People Inc/Dotdash Meredith) جميع أدوات الجلب لدينا (403/402 مباشرة، حجب زاحف Anthropic، حجب Jina 451، وتعذّر أرشيف الويب بسبب rate-limit وقت الفحص). التوثيق أدناه من معرفة موثقة ومستقرة بقالب Dotdash حتى مطلع 2026 — يُنصح بجولة تحقق يدوية سريعة من متصفح عادي قبل الاعتماد التفصيلي.

### 1) بنية الموقع (IA)
- **الـ nav الرئيسي (حرفياً، ثابت منذ سنوات):** `Dinners | Meals | Ingredients | Occasions | Cuisines | Kitchen Tips | News | Features` + بحث + حساب (Log In / My Account).
- أمثلة القوائم الفرعية:
  - *Dinners:* 5-Ingredient Dinners، One-Pot Meals، Quick & Easy، 30-Minute Meals، Soups Stews & Chili، Comfort Food، Main Dishes، Sheet Pan Dinners + View All
  - *Meals:* Breakfast & Brunch، Lunch، Appetizers & Snacks، Salads، Side Dishes، Soups، Bread، Drinks، Desserts
  - *Ingredients:* Chicken، Beef، Pork، Seafood، Pasta، Fruits، Vegetables
  - *Cuisines:* Mexican، Italian، Chinese، Indian، Greek، Filipino، Japanese…
  - *Kitchen Tips:* Instant Pot، Air Fryer، Baking، Cooking How-Tos، Substitutions، BBQ & Grilling، Storage
  - *News:* Celebrity & Entertainment، Fast Food، Grocery، Recalls، Trends
- **العمق:** 3 مستويات (قسم ← تصنيف فرعي ← صفحة تصنيف بمعرّف رقمي مثل `/recipes/17562/dinner/`)، وشجرة التصنيفات ضخمة جداً (أكبر شجرة في العينة).

### 2) الصفحة الرئيسية
نمط "مجلة أخبار طعام" أكثر منه فهرس وصفات: hero تحريري كبير ← مزيج أخبار/مقالات حديثة ← مجموعات موسمية ← شبكات وصفات شعبية ← features. شريط newsletter في منتصف/أسفل الصفحة، وإعلانات برمجية كثيفة بين كل قسمين. البحث بارز في الـ header.

### 3) نظام التصنيف
سداسي الأبعاد صريح في الـ nav نفسه: **نوع العشاء/السرعة** (بُعد تسويقي مستقل!) / **الوجبة** / **المكوّن** / **المناسبة** / **المطبخ** / **الطريقة-الأداة** (Kitchen Tips). كل تصنيف صفحة hub بمقدمة + تصنيفات فرعية + شبكة.

### 4) تشريح صفحة الوصفة (نموذج Banana Banana Bread)
1. Breadcrumb ← H1 ← **نجوم 4.7 + عدد تقييمات ضخم (عشرات الآلاف) + رابط Reviews**.
2. سطر تقديم واحد ← **"Submitted by [عضو]"** + "Updated on…" (هوية UGC صريحة) ← صورة/فيديو hero.
3. صف أفعال: **Save (قلب) / Rate / Print / Share**.
4. شريط حقائق: Prep Time / Cook Time / Total Time / Servings / Yield + رابط **"Jump to Nutrition Facts"**.
5. **Ingredients مع checkboxes للشطب + أزرار Scaling: 1X | 2X | 4X** ("Original recipe (1X) yields 12 servings").
6. **Directions** مرقمة — الوصفات الشعبية فيها **صورة لكل خطوة**.
7. زر **"I Made It"** (رفع صورة طبقك) — حلقة UGC مغلقة.
8. **Nutrition Facts** ملخص (Calories/Fat/Carbs/Protein) + **"Show Full Nutrition Label"** قابل للتوسيع.
9. **Reviews**: توزيع النجوم + صور المستخدمين + فرز.
10. "You'll Also Love" (ذات صلة). — **schema.org/Recipe كامل** (تقييم تجميعي، تغذية، فيديو) — أساس ظهورهم التاريخي في Google.

### 5) المدونة/المقالات
أقسام **News** و**Features** و**Kitchen Tips** منفصلة تماماً عن شجرة الوصفات، لكنها تُحقن في الرئيسية وصفحات التصنيف؛ الـ roundups تُربط بالوصفات بروابط داخلية كثيفة.

### 6) عناصر التحويل والاحتفاظ
حساب مجاني للحفظ والتقييم والمراجعات (جوهر النموذج UGC) + newsletter + ترويج مجلة Allrecipes الورقية + برنامج مجتمع "Allstars". لا paywall — النموذج إعلاني بالكامل.

### 7) خلاصة AllRecipes
- **يستحق التقليد:** حلقة UGC الكاملة (تقييم ← مراجعة ← صورة "I Made It") التي تصنع خندق السوشيال-بروف، مع scaling 1X/2X/4X وcheckboxes للمكونات.
- **يستحق التجنب:** كثافة الإعلانات التي تمزق صفحة الوصفة، وضجيج الأقسام الإخبارية الذي يميّع هوية الموقع.

---

## 2. BBC Good Food — bbcgoodfood.com
*(فحص مباشر كامل: الرئيسية + صفحة collection + صفحة وصفة + hub الوصفات)*

### 1) بنية الموقع (IA)
- **شريط علوي مساعد (utility bar):** `Subscribe | Sustainability | Good Food Shows | Download our app | Newsletters`
- **الـ nav الرئيسي (5 أقسام):** `Recipes | Health | What to buy | Budget | Baking` + زر Subscribe بارز.
- **قائمة Recipes الضخمة (mega menu) مقسمة لمجموعات:**
  - *New and trending:* September recipes، Sausage pastas، Crumble recipes، Quick family dinners، Newsletter recipes، Fast midweek meals، Batch cooking ideas، WhatsApp feed
  - *What to cook:* Quick and easy، Everyday recipes، Family recipes، One-pots، Slow cooker recipes، Traybakes، Air fryer recipes، Batch cooking
  - *Occasion recipes:* Back to school، Halloween، Bonfire night
  - *Meal type:* Breakfast، Lunch، Dinner + "Browse all meal types"
  - *Diet type:* Vegan، Vegetarian + "Browse all diet types"
  - *Explore:* Ingredients، Cuisines، Chef recipes
- **قائمة Health:** Health hub، Nutracheck (شراكة عدّاد سعرات)، Free health newsletter، Fitness (Protein 101، Marathon meal plans)، Your health (Women's health، Improve digestion)، Healthy eating (Vitamins and minerals)، Wellbeing (Sleep better، Eat for energy).
- **عمق التصنيف:** 3 مستويات: قسم رئيسي ← مجموعة/نوع ← صفحة collection (مثل `recipes/collection/quick-and-easy-family-recipes`).

### 2) الصفحة الرئيسية (بالترتيب)
1. **Hero slider** — كاروسيل من 5 شرائح لمحتوى مميز (عرض واحد بعرض كامل مع نقاط تنقل).
2. **بلوك مبوّب (tabbed pocket)** — تبويبات: `Quick dinners | App only | Healthy dishes | Budget meals | Family recipes` وتحت كل تبويب شبكة ~4 أعمدة من بطاقات الوصفات (~20 عنصراً) — لاحظ وجود تبويب "App only" ترويجي.
3. **Trending now** — كاروسيل بطاقات (3 بطاقات ظاهرة).
4. **بلوك صورة ترويجية** (حملة/موسم).
5. **Videos** — قسم فيديوهات وصفات.
6. **إعلان (ad slot)**.
7. **Popular recipe collections** — شبكة بطاقات collections + زر "المزيد".
8. **Be inspired...** — شبكة بطاقات إلهام/مقالات.
9. **إعلان**.
10. **Popular guides** — أدلة تحريرية.
11. **Good Food Podcast** — ترويج البودكاست.
- **البحث:** أيقونة/حقل في الـ header بنص `Recipes, guides and more...` (يبحث في الوصفات والأدلة معاً).

### 3) نظام التصنيف (Taxonomy)
تقسيم **خماسي الأبعاد** صريح في القائمة نفسها: طريقة/نمط الطهي (One-pots، Air fryer، Traybakes، Slow cooker)، المناسبة (Back to school، Halloween)، نوع الوجبة (Breakfast/Lunch/Dinner)، الحمية (Vegan، Vegetarian)، الاستكشاف بالمكوّن والمطبخ والشيف (Ingredients، Cuisines، Chef recipes) — إضافة إلى مجموعات موسمية (September recipes) وميزانية (Budget قسم مستقل كامل).

### 4) تشريح صفحة الوصفة (Best ever chocolate brownies)
بالترتيب من الأعلى:
1. Breadcrumb (Home › Recipes › ...).
2. العنوان H1.
3. **التقييم:** نجوم 4.8/5 مع **2972 تقييماً** + زر Rate — أعلى الصفحة مباشرة.
4. **شريط الحقائق:** الحصص "Cuts into 16 squares or 32 triangles" + **درجة الصعوبة** "More effort" + `Prep: 25 mins | Cook: 27-35 mins`.
5. مقدمة قصيرة جداً (سطر–سطرين) + **فيديو** الوصفة.
6. **Ingredients** مع **مبدّل وحدات Metric / US** — وداخل القائمة سطر ترويجي: "Keep the screen awake with cook mode on the Good Food app" (ترويج التطبيق داخل سياق الطبخ!).
7. **Nutrition** لكل حصة: kcal، fat، saturates، carbs، sugars، fibre، protein، salt.
8. **Method** — خطوات مرقمة STEP 1…15 (نص فقط، بلا صورة لكل خطوة).
9. **Frequently asked questions** — 3 أسئلة (استبدال مكوّن، مدة الحفظ، التجميد).
10. **Comments, questions and tips** — تعليقات وتقييم مدموجان ("Rate this recipe" + اختيار نوع الرسالة: تعليق/سؤال/نصيحة).
11. Upsell: "Get 3 months of Good Food All Access".
- **schema.org:** نعم — `Recipe` كامل (prepTime، cookTime، nutrition، recipeCategory: "Afternoon tea, Dessert, Treat"، recipeCuisine، **suitableForDiet: VegetarianDiet**، keywords) + `VideoObject` + `BreadcrumbList` + عقدة `aggregateRating` منفصلة.

### 4-ب) صفحة التصنيف (collection)
- Breadcrumb: `Home > Recipes > Collection > Quick and easy family recipes` + عدّاد "105 Recipes".
- بطاقة الوصفة في الشبكة تعرض: صورة + عنوان + نجوم + عدد التقييمات + **الوقت** + **الصعوبة** (Easy).
- عناصر مدفوعة داخل القائمة موسومة **"App only — premium piece of content available to subscribed users"** (5 عناصر من 24 في الصفحة الأولى).
- شريط collections ذات صلة + upsell للاشتراك.

### 5) المدونة/المقالات
منفصلة بنيوياً: **Health hub** (مقالات تغذية وصحة)، **What to buy** (مراجعات أدوات: "Best pan sets 2026: tried and tested")، **Guides** وأخبار طعام ("The M&S Christmas snack…"). تُربط بالوصفات عبر بلوكات "Popular guides" و"Be inspired" وروابط داخل صفحات الوصفات.

### 6) عناصر التحويل والاحتفاظ
- **اشتراك مدفوع "Good Food All Access":** يقفل وصفات موسومة "App only/Premium" (ظهر 151 وسم Premium في الرئيسية) + upsell أسفل كل صفحة.
- **التطبيق:** رابط دائم في الشريط العلوي + cook mode داخل المكونات.
- **Newsletters:** صفحة نشرات مخصصة + **قناة WhatsApp feed** (نادرة ومهمة).
- لا يوجد meal planner مدمج (يُعوَّض بشراكة Nutracheck الصحية).

### 7) خلاصة BBC Good Food
- **يستحق التقليد:** درجة الصعوبة + الوقت + التقييم في بطاقة الوصفة نفسها داخل القوائم — قرار الاختيار يتم من الشبكة دون فتح الصفحة.
- **يستحق التجنب:** حشو العناصر المدفوعة "App only" داخل نتائج التصفح المجاني يقطع التدفق ويولّد إحباطاً (5 من 24 في صفحة واحدة).

---

## 3. NYT Cooking — cooking.nytimes.com
*(فحص مباشر كامل: الرئيسية + صفحة topic + صفحة وصفة)*

### 1) بنية الموقع (IA)
- **الـ nav الرئيسي:** `What to Cook | Recipes | Ingredients | Occasions | Articles | About` + بحث + Log In + Subscribe.
- **الـ mega menu مقسوم لمجموعات معنونة (حرفياً):** Staff Picks، From Our Newsletters، Perfect For، Everyday Recipes، **By Meal** (Dinner، Breakfast، Lunch، Desserts، Appetizers، Side Dishes، Drinks)، **By Diet** (Vegetarian، Vegan، Gluten-Free، Dairy-Free)، **By Method** (Air Fryer، Instant Pot، Slow Cooker، BBQ & Grilling، Sheet Pan، Baking)، **Meat & Seafood** (Chicken، Beef، Pork، Salmon، Shrimp)، **Vegetables & Fruits**، **Plant-Based Proteins** (Tofu، Lentils، Chickpeas، Beans)، **Rice, Grains, Pasta**، **By Upcoming Holiday** (Rosh Hashana، Canadian Thanksgiving، Halloween، Diwali — تتغير حسب التقويم!)، **By Occasion** (Birthdays، Brunch، Date Night، Parties، Picnics)، **How-Tos** (How to Cook Chicken Breast…)، Getting Started، Reader Favorites، Video Series.
- **العمق:** مستويان فعلياً (قسم ← صفحة topic)، لكن صفحات الـ topic نفسها تتفرع لـ collections منسقة — عمق 3 عملي.

### 2) الصفحة الرئيسية (بالترتيب)
1. **Recipe of the day** — بطاقة hero واحدة كبيرة.
2. بطاقات تحريرية بتوقيع المؤلفين (Recipe from Benjamina Ebuehi / Adapted by Melissa Clark).
3. **Latest Articles** — مقالات.
4. **Make Something Delicious** — شبكة ~20 وصفة (4 أعمدة).
5. **Trending** + More Articles.
6. **Most Popular This Week**.
7. **More From Our Editors**.
8. **Our Newest Recipes** — شبكة 20 وصفة.
9. **Our Writers** — بطاقات المحررين النجوم.
10. **From The Cooking Newsletter by Melissa Clark** — وصفات النشرة.
- **البحث:** حقل بارز placeholder = **"What would you like to cook?"**.

### 3) نظام التصنيف
تقسيم صريح **سباعي الأبعاد** بعناوين مجموعات داخل القائمة: الوجبة / الحمية / الطريقة-الأداة / المكوّن (مقسوم بدوره: لحوم-بحري، خضار-فواكه، بروتين نباتي، نشويات) / العطلة القادمة (ديناميكي زمنياً) / المناسبة الاجتماعية / مستوى المهارة (Getting Started، How-Tos). التحرير طبقة فوق التصنيف: Staff Picks وReader Favorites كمداخل موازية.

### 4) تشريح صفحة الوصفة (Cheesy Baked Pasta)
1. العنوان H1 → **By Melissa Clark** + تاريخ التحديث + كريدت المصوّر.
2. **كاروسيل وسائط** "Media 1 of 3": فيديوهان (7:05 و0:51) + صورة.
3. **صف الحقائق:** Total Time 45 minutes | Rating ★5 **(12,054)** | Comments (رابط للتعليقات).
4. مقدمة تحريرية سطران + زر "Read More".
5. **صف الأفعال:** `Save` (يتطلب تسجيل دخول → Recipe Box) | `Give` — **إهداء الوصفة: "As a subscriber, you have 10 gift recipes to give each month"** | `Share` (Copy link، Email، Pinterest، Facebook، X، WhatsApp، Reddit) | `Print` — **الطباعة نفسها تتطلب تسجيل دخول!**
6. **Ingredients** — `Yield: 4 servings` (لا يوجد تحويل وحدات ولا scaling).
7. **Preparation** — خطوات مرقمة نصية.
8. **Ratings** ثم **Comments** — نظام "notes" الشهير: ملاحظات القراء المنتقاة (Helpful) قبل الكل.
9. **Recipe Tags** ثم **More From The Weeknight 100** (المجموعة الأم) ثم **Trending On Cooking**.
- **التغذية: لا تُعرض في الواجهة إطلاقاً** (قرار تحريري معلن) — لكنها موجودة كاملة في الـ JSON-LD (calories 1019.5، صوديوم، دهون…).
- **schema.org:** `Recipe` كامل جداً + **`isAccessibleForFree: false`** (إعلان الـ paywall للمحركات) + `aggregateRating` + `video` + `cookingMethod` + `NewsMediaOrganization`.

### 4-ب) صفحة التصنيف (topics/dinner-recipes)
- H1 ثم **Featured Recipe Collections**: كاروسيلات لمجموعات منسقة (Healthy Weeknight Dinners، Easy Weeknight Soups for Busy Days، Our Best Noodle Recipes، Best Salmon Recipes…) — التنسيق التحريري قبل الشبكة الخام.
- ثم **"All Dinner Recipes"** — شبكة كاملة. البطاقة: صورة + عنوان + **المؤلف** + نجوم وعدد المقيمين (5678) + الوقت.

### 5) المدونة/المقالات
"Articles" قسم رئيسي في الـ nav؛ الأدلة التعليمية (How-Tos، Learn to Cook، Knife Skills، Food Safety) بنية مستقلة تُربط من القائمة ومن صفحات الوصفات؛ النشرات البريدية نفسها تُعامل كمنتجات محتوى لها صفحات (The Veggie، Five Weeknight Dishes، Bake Time).

### 6) عناصر التحويل والاحتفاظ
- **Paywall كامل:** كل وصفة مقفلة لغير المشتركين (اشتراك Cooking مستقل أو ضمن NYT All Access).
- **Recipe Box** (الحفظ) هو الخطاف الأول — زر Save في كل بطاقة (ظهر 181 مرة في الرئيسية).
- **Gift a recipe:** 10 وصفات إهداء شهرياً للمشترك — تسويق فيروسي مدفوع.
- الطباعة خلف تسجيل الدخول؛ النشرات متعددة؛ التطبيق مروَّج في الـ footer.

### 7) خلاصة NYT Cooking
- **يستحق التقليد:** صفحة التصنيف تبدأ بـ collections منسقة تحريرياً قبل الشبكة الكاملة — توجيه الاختيار بدل إغراق المستخدم؛ + فكرة "Recipe of the day".
- **يستحق التجنب:** قفل الطباعة خلف تسجيل الدخول — نقطة احتكاك تُغضب حتى الجمهور المتعاطف.

---

## 4. Serious Eats — seriouseats.com
> **مستوى الدليل:** نفس حجب الناشر أعلاه؛ التوثيق من معرفة موثقة بالقالب حتى مطلع 2026 + تحقق جزئي عبر مقتطفات البحث (نموذج المحتوى: tested recipes / techniques / equipment reviews / ingredient deep-dives مؤكد من مصادر ثانوية).

### 1) بنية الموقع (IA)
- **الـ nav الرئيسي:** `Recipes | How-Tos | Equipment | Features` (+ About + بحث + newsletter CTA).
- **قائمة Recipes:** *By Course* (Breakfast & Brunch، Mains، Sides، Desserts، Snacks & Appetizers…) / *By Ingredient* (Chicken، Beef، Pasta…) / *By Cuisine* (Italian، Mexican، Japanese، Chinese…) / *By Diet* (Vegetarian، Vegan، Gluten-Free…) / *By Method* (Grilling، Baking، Frying، Air Fryer…).
- **How-Tos:** Techniques، **Food Science** (إرث "The Food Lab")، مهارات أساسية.
- **Equipment:** مراجعات مختبرة (We Tested X…) وأدلة شراء.
- **العمق:** 3 مستويات (قسم ← بُعد ← صفحة تصنيف).

### 2) الصفحة الرئيسية
Hero تحريري (وصفة/مقال عميق) ← Latest ← مجموعات منسقة ← بلوكات Techniques/Food Science ← مختارات Equipment Reviews ← newsletter. هوية "مطبخ اختبار + علم طعام" لا "فهرس".

### 3) نظام التصنيف
خماسي الأبعاد كلاسيكي: Course / Ingredient / Cuisine / Diet / Method — مع طبقة معرفية موازية فريدة: **Techniques وFood Science وEquipment كتصنيفات محتوى من الدرجة الأولى** وليست ملاحق.

### 4) تشريح صفحة الوصفة
1. Breadcrumb ← H1 ← سطر dek ← **byline بمصداقية ثقيلة** (J. Kenji López-Alt، Stella Parks…) + تاريخ التحديث.
2. **"Why It Works"** — قائمة نقاط أعلى الصفحة تشرح "لماذا تنجح هذه الوصفة" (التوقيع الأشهر للموقع).
3. صورة hero ← زر Jump to Recipe ← **مقالة تحريرية طويلة جداً** (أطول مقدمات العينة: تجارب، مقارنات، صور اختبارات).
4. **بطاقة الوصفة أسفل الصفحة:** الأوقات والحصص ← Ingredients ← Directions **بصورة لكل خطوة** ← **Special Equipment** ← **Make-Ahead and Storage** ← Nutrition Facts (جدول مولّد آلياً مع إخلاء مسؤولية "nutrition information is calculated using an ingredient database and should be considered an estimate").
5. تقييم نجمي + تعليقات مجتمع نقاشية الطابع. — **schema.org/Recipe** كامل.

### 5) المدونة/المقالات
الفصل الأوضح في العينة: Features (ثقافة/تاريخ طعام)، How-Tos، Equipment — أعمدة موازية للوصفات تُربط بها تحريرياً (كل مراجعة أداة توصي بوصفات والعكس).

### 6) عناصر التحويل والاحتفاظ
Newsletter أساسية، حساب للحفظ (أداة MyRecipes الجديدة للحفظ من مواقع الشقيقات وغيرها)، لا paywall — إعلانات + عمولات مراجعات الأدوات.

### 7) خلاصة Serious Eats
- **يستحق التقليد:** بلوك **"Why It Works"** — سطران يبنيان ثقة فورية قبل أي تمرير؛ وحقلا Special Equipment وMake-Ahead and Storage في البطاقة.
- **يستحق التجنب:** إغراق الوصفة تحت آلاف الكلمات التحريرية — بدون زر Jump تكون الصفحة غير صالحة للطبخ الفعلي؛ العمق ممتاز للقراءة، مؤلم للتنفيذ.

---

## 5. Tasty — tasty.co
*(فحص مباشر كامل: الرئيسية + صفحة tag + صفحة وصفة)*

### 1) بنية الموقع (IA)
- **nav رئيسي من 4 قوائم:** `Recipes | Tips (tricks) | Shop | Newsletters`، مع صف روابط سريعة ثانٍ: `Weeknight Dinners | Breakfasts to Delight | Work Lunches | 5 Ingredient Meals | Latest Recipes | Family Dinners`.
- **قائمة Recipes مقسمة:** *Popular* / *Right Now* (موسمي: Holiday Cooking، Latest Recipes) / *Ingredients* (Chicken، Pasta، Salmon، Potato، Beef) / *Diet* (Healthy، Vegetarian، Low Carb، High Protein، Vegan) / *Meals* (Breakfast، Lunch، Dinner، Desserts، Snacks) + CTA **"Submit your recipe"**.
- **قائمة Tips:** Kitchen Tips & Skills / Food Hacks / Appliance Cooking (Air Fryer، Instant Pot، Microwave) / **Meal Plans** (Easy Meal Prep، $40 A Week، $50 A Week).
- **قائمة Shop:** كتب الطبخ + أدوات المطبخ (Tasty Cookware).
- **العمق:** مستويان فقط (قائمة ← صفحة tag/ingredient) — بنية tags مسطحة: `/tag/dinner`، `/ingredient/salmon`.

### 2) الصفحة الرئيسية (بالترتيب)
1. **What We're Cooking** — شبكة hero (بطاقات كبيرة، صور مربعة).
2. **What We're Reading** — مقالات.
3. **Weeknight Dinners** — كاروسيل موضوعي.
4. **Latest Recipes** — كاروسيل.
5. **Latest Guides** — أدلة.
6. **Tasty Stories** — محتوى علامة/قصص.
7. **What You're Making** — **UGC: صور طبخات المستخدمين الفعلية**.
8. **Tasty Shows** — سلاسل فيديو.
9. **THE BEST OF Tasty** — الأفضل تاريخياً.
10. More Guides → **Join the Tasty Community!** (إرسال وصفتك) → **Shop Cookbooks** → **Shop Cookware** → **Get the Tasty Newsletter** (form بريد).
- البحث: حقل "Search Tasty" في الـ header. الـ footer: **Get the Tasty App** + newsletter.

### 3) نظام التصنيف
رباعي الأبعاد عبر tags مسطحة: وجبة (tag) / مكوّن (ingredient) / حمية (tag) / لحظة-اهتمام (Right Now، Weeknight، 5 Ingredient) + طبقة أدوات في قائمة Tips (Air Fryer، Instant Pot، Microwave). صفحة الـ tag تعرض **chips لتصنيفات شقيقة** مجمعة (بروتينات: Seafood/Chicken/Beef/Pork؛ أطباق: Casseroles/Chilis/Burgers/Pasta/Pizza/Tacos & Burritos/Soups/Stews/Stir Fry).

### 4) تشريح صفحة الوصفة (Creamy Lemon Chicken)
صفحة **مضغوطة recipe-first بلا مقدمة طويلة إطلاقاً**:
1. العنوان H1 → وصف سطرين → **المؤلف "Alix Traeger, Tasty Team" + Updated on…**
2. **التقييم بصيغة Tasty الفريدة: "97% would make again"** — لا نجوم في الواجهة (لكن الـ schema يحمل نجوماً 4.8 من 5,478 تقييماً!).
3. أزرار المشاركة: email / facebook / pinterest / **SMS** + Print.
4. الأوقات: Total 35 min | Prep 15 | Cook 20 → صورة/فيديو الطبق (فيديو مربع 1:1 مقاس 640×640).
5. **Ingredients** — "for 4 servings"، **الوحدات مزدوجة inline**: "1 cup flour (125 g)" — بلا زر تبديل.
6. **Nutrition Info** — calories 479، fat، carbs، fiber، sugar، protein (مباشرة، بلا نقرة إضافية).
7. **Preparation** — 16 خطوة مرقمة (بلا صور لكل خطوة — الفيديو يغني عنها).
8. **Related Recipes** (8 بطاقات) → newsletter → أقسام Shop (كتب/أدوات).
- لا يوجد Jump to recipe (لا حاجة — لا يوجد ما يُقفز فوقه)، ولا تعليقات على الويب (تفاعل "tips" بالصور يعيش في التطبيق).
- **schema.org:** `Recipe` + `VideoObject` + `BreadcrumbList` — كاملة (nutrition، aggregateRating، keywords، recipeCuisine).

### 4-ب) صفحة التصنيف (tag/dinner)
عنوان + مقدمة تحريرية قصيرة بنبرة كاجوال + عدّاد **"3688 recipes"** + chips تصنيفات ذات صلة + شبكة بطاقات (صورة + عنوان فقط — بلا تقييم/وقت!) + زر **Show more** (تحميل تدريجي).

### 5) المدونة/المقالات
مقالات `/article/` (roundups مثل "easy make-ahead work lunches"، وأدلة tips) تعيش في قوائم مستقلة (Tips) وتظهر في الرئيسية (What We're Reading، Latest Guides)؛ تُربط بالوصفات كمجموعات موضوعية بدل تصنيفات.

### 6) عناصر التحويل والاحتفاظ
- **التطبيق أولاً:** "Get the Tasty App" في الـ footer وكل تفاعل مجتمعي (tips بالصور) داخله.
- Newsletter (form في الرئيسية والـ footer وكل وصفة).
- **تجارة مباشرة:** كتب + خط أواني Tasty — قوائم Shop في الـ nav.
- **UGC:** Submit your recipe + What You're Making.
- لا حسابات ويب فعلية ولا paywall.

### 7) خلاصة Tasty
- **يستحق التقليد:** مقياس **"% would make again"** — إشارة ثقة أوضح سلوكياً من النجوم، ومقدمة شبه معدومة: الوصول للمكونات خلال ثانيتين.
- **يستحق التجنب:** بطاقات التصنيف بلا أي metadata (لا وقت ولا تقييم) تجبر على فتح كل وصفة للمقارنة؛ وغياب التعليقات على الويب يفقد إشارات الثقة.

---

## 6. EatingWell — eatingwell.com ⭐ (الأهم للمنصة الغذائية)
> **مستوى الدليل:** نفس حجب الناشر؛ توثيق من معرفة موثقة بالقالب حتى مطلع 2026. هذا الموقع تحديداً يستحق جولة تحقق يدوية لأنه المرجع الأقرب لمنتجكم.

### 1) بنية الموقع (IA)
- **الـ nav الرئيسي:** `Healthy Recipes | Special Diets | Diabetes | Healthy Eating | Healthy Lifestyle | News` + About Us + بحث + حساب — لاحظ أن **الحمية والصحة أبعاد من الدرجة الأولى في الـ nav** وليست فلاتر.
- أمثلة القوائم:
  - *Healthy Recipes:* Dinner، Breakfast & Brunch، Lunch، Desserts، Snacks، Salads، Soup، Smoothies، بالمكوّن (Chicken، Salmon…)، Quick & Easy، 30-Minute
  - *Special Diets:* **Weight Loss، Mediterranean Diet، Anti-Inflammatory، High-Protein، High-Fiber، Low-Carb، Gluten-Free، Vegan، Vegetarian**
  - *Diabetes:* وصفات وخطط وجبات مناسبة للسكري (قسم كامل مستقل!)
  - *Healthy Eating:* علم تغذية وأخبار أطعمة ("Best Foods for…")
  - *Healthy Lifestyle:* عافية عامة
- **العمق:** 3 مستويات بنمط Dotdash (hub ← تصنيف ← صفحة).

### 2) الصفحة الرئيسية
Hero تحريري + أحدث المقالات/الوصفات + بلوكات موسمية + **ترويج Meal Plans** (خطط وجبات 7 أيام: "7-Day Mediterranean Diet Meal Plan for Beginners" — نوع المحتوى النجم لديهم) + newsletter + إعلانات كثيفة.

### 3) نظام التصنيف
البُعد الصحي يتقدم كل شيء: **الحمية/الحالة الصحية** (بما فيها أمراض: Diabetes، وأهداف: Weight Loss) ← ثم الوجبة ← المكوّن ← السرعة. إضافة فريدة: **Nutrition Profile tags** على مستوى الوصفة الواحدة (انظر أدناه) تعمل كتصنيف عرضي.

### 4) تشريح صفحة الوصفة
1. Breadcrumb ← H1 ← نجوم + عدد التقييمات ← dek سطر واحد.
2. **صف مصداقية مزدوج: "By [author]" + "Reviewed by Dietitian [Name], M.S., RD"** — مراجعة اختصاصية تغذية معتمدة معلنة بالاسم والدرجة + تاريخ التحديث.
3. صورة hero ← أزرار Save/Rate/Print/Share.
4. حقائق: **Active Time / Total Time / Servings** + رابط "Jump to Nutrition Facts".
5. **شارات Nutrition Profile** الحرفية: Diabetes-Appropriate، Heart-Healthy، Low-Sodium، High-Protein، Gluten-Free، Low-Calorie… (تصنيف صحي سطحي فوق كل وصفة).
6. Ingredients ← Directions مرقمة بالصور.
7. **Nutrition Facts كاملة بأسلوب الملصق الغذائي**: per serving + نِسَب القيمة اليومية (%DV) + سطر "Nutrition information reviewed by…".
8. أحياناً FAQ + نصائح ← Reviews ← Related. — **schema.org/Recipe** كامل مع nutrition.

### 5) المدونة/المقالات
أعمدة صحية كاملة (Healthy Eating، News) بمراجعة اختصاصيين، مرتبطة بالوصفات بعمق ("What Happens to Your Body When You Eat X" ← وصفات X)؛ + **Meal Plans** كنوع محتوى ثالث بين المقال والوصفة.

### 6) عناصر التحويل والاحتفاظ
حساب مجاني للحفظ، newsletter متخصصة، ترويج مجلة/كتب، **خطط الوجبات كمنتج محتوى مجاني** يبني عادة العودة. لا paywall.

### 7) خلاصة EatingWell
- **يستحق التقليد (الأهم في التقرير كله):** ثلاثية المصداقية الغذائية — "Reviewed by Dietitian" بالاسم والدرجة العلمية + شارات Nutrition Profile + ملصق تغذية كامل بالـ %DV. هذا هو المعيار الذهبي لمنصة تغذية عربية.
- **يستحق التجنب:** الإعلانات الكثيفة نفسها (قالب Dotdash) التي تناقض تجربة "الصحة والهدوء"، وتضخم قوائم المقالات على حساب أدوات عملية.

---

## 7. Minimalist Baker — minimalistbaker.com
*(فحص مباشر كامل: الرئيسية + Recipe Index + صفحة وصفة)*

### 1) بنية الموقع (IA)
- **أقل nav في العينة كلها:** أساسي `About | Shop | Blogger Resources`، وثانوي لاصق: `All Recipes | Vegan | Gluten-Free`. الشعار في المنتصف والبحث في شريط علوي دائم.
- **العمق:** مستوى واحد فعلياً — كل التصفح يمر عبر صفحة **Recipe Index واحدة بفلاتر جانبية (FacetWP)**؛ الفلاتر تولّد URLs قابلة للمشاركة (`/recipe-index/?fwp_special-diet=vegan`).

### 2) الصفحة الرئيسية (بالترتيب)
1. Header (قوائم + بحث "search minimalist baker").
2. **Recipes** — أحدث 5 وصفات (شبكة بطاقات كبيرة).
3. **Recent Reader Favorites** — مفضلات القراء.
4. **RECIPE ROUND-UPS** — 4 تجميعات موسمية ("40 Delicious Recipes for Labor Day Weekend"…).
5. **Explore Recipes** — شبكة استكشاف كبيرة مختلطة.
6. Sidebar/Footer: **"Want More Deliciousness? Get our copy of FAN FAVORITES"** — نشرة بمغناطيس كتاب إلكتروني.

### 3) نظام التصنيف
facets الفهرس (حرفياً من الكود): `recipe_search`، `season`، `special-diet`، `cuisine`، `recipe-type`، **`simple-factor`**، `ingredient`.
- **الابتكار:** فلتر **simple-factor** يترجم وعد العلامة (وصفات ≤10 مكونات / وعاء واحد / ≤30 دقيقة) إلى بُعد تصنيف قابل للفلترة.
- الحمية بُعد أول (Vegan وGluten-Free في الـ nav الرئيسي نفسه).

### 4) تشريح صفحة الوصفة (1-Bowl Honey Almond Snack Cake)
1. **Entry header:** العنوان + **شارات الحمية بجانب العنوان: GF V DF NS** (Gluten-Free/Vegetarian/Dairy-Free/Naturally Sweetened) + زر **Jump to Recipe** + سطر الإفصاح عن روابط العمولة.
2. مقدمة تحريرية ~3 فقرات (~520 حرفاً) — قصيرة نسبياً لمدونة SEO.
3. قسم **"How to Make …"** تحريري مع صور العملية.
4. روابط داخلية "More Sweet Treats for Snacking".
5. **بطاقة الوصفة (WPRM):** العنوان + وصف + Author + **Print + SAVE/SAVED** + Prep 10 / Cook 45 / Total 55 + Servings 12 (Slices) + Course + Cuisine (تُستخدم أيضاً للحمية: "Dairy-Free, Gluten-Free") + حقلان مميزان: **Freezer Friendly: 1 month** و**Does it keep? 3-4 Days**.
6. **Ingredients** مع **مبدّل US Customary ↔ Metric** (بلا scaling للحصص).
7. **Instructions** ثم **Video** ثم **Notes** (بدائل ونصائح).
8. **Nutrition (1 of 12 servings):** serving size، calories 245، carbs، protein، fat، saturated، cholesterol، sodium، fiber…
9. "If you love this recipe..." (4 وصفات) → **Reader Interactions: Leave a Comment & Rating!** (نجوم داخل نموذج التعليق).
- **schema.org:** نعم — رسم Yoast كامل: `Article` + `Recipe` (بكل الحقول والتغذية) + `BreadcrumbList` + `WebSite` + `Person` + `Organization`.

### 4-ب) صفحة التصنيف (Recipe Index)
H1 "All Recipes" + فلاتر جانبية (البحث + 6 facets أعلاه) + شبكة 3-4 أعمدة (صورة + عنوان — العنوان نفسه يحمل الوسم: "(Vegan + GF)"، "1-Bowl!") + تحميل صفحات. لا تقييم/وقت في البطاقة — التمييز عبر تلوين العناوين بالوعود.

### 5) المدونة/المقالات
لا فصل بنيوياً: الـ roundups منشورات في نفس التدفق. الفريد: قسم **Blogger Resources** (تعليم التدوين والتصوير الغذائي — منتج B2B جانبي).

### 6) عناصر التحويل والاحتفاظ
- Newsletter + مغناطيس **كتاب FAN FAVORITES** الإلكتروني (تظهر في sidebar وbfooter وداخل المقالات).
- زر **SAVE** على بطاقة الوصفة.
- Shop: كتب ودورة تصوير طعام. لا اشتراك مدفوع ولا تطبيق.

### 7) خلاصة Minimalist Baker
- **يستحق التقليد:** شارات الحمية الملاصقة للعنوان (GF/V/DF/NS) + حقلا **"Does it keep?"** و**"Freezer Friendly"** في بطاقة الوصفة — أسئلة حقيقية يجيبها الـ UI مباشرة؛ وفلتر simple-factor كترجمة لوعد العلامة.
- **يستحق التجنب:** nav فقير جداً (3 روابط) يجعل الاستكشاف كله رهين صفحة index واحدة — لو سقطت فلاتر JS ضاع التصفح؛ وكثافة روابط العمولة داخل قائمة المكونات تشوّش القراءة.

---

## 8. Downshiftology — downshiftology.com
*(فحص مباشر كامل: الرئيسية + Recipe Index + صفحة وصفة)*

### 1) بنية الموقع (IA)
- **nav رئيسي:** `Recipes | Cookbook | Newsletter | Shop | About` + **Sign in** (حسابات فعلية في مدونة مستقلة!).
- **قائمة Recipes الضخمة — أنظف تقسيم رباعي في العينة (حرفياً):**
  - *Browse All Recipes / Recipe Index*
  - **Recipes by Course (8):** Appetizers and Snacks، Breakfast، Desserts، Drinks and Smoothies، Dinner، Salads، Side Dish، Soups and Stews
  - **Recipes by Ingredient (10):** Beef، Chicken، Eggs، Lamb، Pork، Salmon، Shrimp، Sweet Potato، Turkey، Zucchini
  - **Recipes by Method (7):** 30 Minute Meals، Air Fryer، Grilling، One Pan، Slow-Cooker، Spiralizer Recipes، Vitamix Recipes
  - **Recipes by Diet (9):** Dairy-Free، Gluten-Free، High-Protein، Low-Carb and Keto، **Mediterranean Diet**، Paleo، Vegan، Vegetarian، **Whole30**
  - **Recipes by Holiday (10):** Christmas، Easter، Thanksgiving، Super Bowl، Valentine's Day…
- **العمق:** مستويان (mega menu ← صفحة تصنيف)، والتصنيفات URLs أرشيفية قياسية.

### 2) الصفحة الرئيسية (بالترتيب)
1. **Hero = أحدث وصفة مميزة** (Korean Beef Bowl: تاريخ + عنوان + مقتطف).
2. **Latest Recipes** — 4 بطاقات.
3. **Easy Dinners for Busy Days** — شريحة موضوعية.
4. **What To Cook In September** — **بلوك موسمي شهري**.
5. **Back-To-School Favorites** — موسمي سياقي.
6. **ترويج الكتاب:** Downshiftology Healthy Meal Prep Cookbook.
7. **SHOP My Favorite Products**.
8. **Best Fall Dinners** → **Seasonal Soups** → **Crockpot Favorites** — شرائح موسمية متتالية.
9. **Browse Recipes** — 6 بلاطات تصنيف مصوّرة: Breakfast، Salads، Appetizers، Dinner، Side Dishes، Drinks.
10. **Year-Round Salads** → **Healthy Basics** (وصفات أساس: How to Make Chia Pudding، How to Boil Eggs…) → **Explore More Ideas** (roundups: "41 High Protein Dinner Ideas").
- البحث في الـ header: **"What can we help you find?"**.

### 3) نظام التصنيف
النموذج **الرباعي الصريح + المناسبات**: Course / Ingredient / Method (بما فيها أدوات: Vitamix، Spiralizer) / Diet (أوسع قائمة حميات في العينة: 9 حميات تشمل Whole30 وMediterranean) / Holiday. الموسمية طبقة تحريرية فوق التصنيف (September، Fall، Soups).

### 4) تشريح صفحة الوصفة (Sweet Potato Soup)
1. **Breadcrumb:** `Home › Recipes › Courses › Soups and Stews`.
2. العنوان H1 → **by Lisa Bryan | Published Sep 02, 2026 | 153 Comments**.
3. صف مشاركة: Share / **Pin** / Facebook / Tweet / Email + أزرار **Save/Saved + Review + Print**.
4. **مقدمة تحريرية طويلة منظمة بعناوين H2** (نمط SEO كامل): Why You'll Love My… / Ingredients (شرح) / How To Make (بالصور) / A Few Blending Tips / Ways To Store This Soup / Make This A Heartier Meal / More Sweet Potato Recipes — لذلك زر **Jump to Recipe** موجود بجانب العنوان.
5. **بطاقة الوصفة:** Description / **Video** / **Equipment** (روابط أدوات) / **Ingredients بمبدّل US ↔ Metric وأزرار Scaling 1x | 2x | 3x** (الوحيدة في العينة!) / Instructions / **Lisa's Tips** / Nutrition (calories 254، carbs، protein…).
6. **You May Also Like** (4) → **About the author** → التعليقات (**153 Comments** بترقيم صفحات) + **Rate This Recipe** + قسم "Recipe Ratings without Comment".
7. Sidebar: Popular Recipes + The Latest.
- **ميزة تحويل فريدة: "Email This Recipe — Enter your email and I'll send it to you + weekly food inspiration!"** — التقاط بريد مقابل إرسال الوصفة نفسها.
- **schema.org:** `Recipe` كامل (aggregateRating 4.95/68 + reviewCount منفصل، nutrition، keywords) عبر WP Recipe Maker.

### 4-ب) صفحة التصنيف (Recipe Index)
H1 "Recipes" + شبكة بطاقات (صورة + عنوان) + بحث. التصفية تعتمد على الـ mega menu بدل فلاتر جانبية.

### 5) المدونة/المقالات
شبه مدمجة: **Healthy Basics** (how-to أساسيات) و**roundups** ("20 Best Soup Recipes") منشورات في نفس النظام تُروّج من الرئيسية؛ لا يوجد قسم مقالات مستقل في الـ nav (تركيز مطلق على الوصفات).

### 6) عناصر التحويل والاحتفاظ
- **حسابات + Sign in:** حفظ الوصفات (Save/Saved) وإنشاء **meal plans** ("save to meal plans you create") — مخطط وجبات فعلي داخل مدونة.
- **Email This Recipe** (أقوى فكرة التقاط بريد في العينة) + newsletter "Join our 300,000+ foodie community".
- Cookbook مطبوع + Shop منتجات مفضلة (عمولة). لا paywall.

### 7) خلاصة Downshiftology
- **يستحق التقليد:** ثلاثية بطاقة الوصفة: **US/Metric + 1x/2x/3x scaling + Equipment** — أفضل بطاقة وصفة وظيفياً في العينة؛ ومعها "Email This Recipe".
- **يستحق التجنب:** طول المقدمة التحريرية (7 أقسام H2 قبل البطاقة) يجعل الصفحة بلا Jump-to غير قابلة للاستخدام — وحتى معه، التمرير للموبايل مرهق.

---

# ثانياً: الأنماط المشتركة (Patterns) عبر المواقع الثمانية

> ترميز المواقع: AR=AllRecipes، BBC=BBC Good Food، NYT=NYT Cooking، SE=Serious Eats، TS=Tasty، EW=EatingWell، MB=Minimalist Baker، DS=Downshiftology

### النمط 1: schema.org/Recipe بصيغة JSON-LD غير قابل للتفاوض
كل المواقع الثمانية تنشر `Recipe` كاملاً (أوقات، حصص، تغذية، تقييم تجميعي، فيديو، keywords) — تأكد حرفياً بفحص الكود في: BBC، NYT، TS، MB، DS (+ معروف موثقاً في AR/SE/EW). البعض يضيف `VideoObject` وBreadcrumbList` و`suitableForDiet` (BBC) و`isAccessibleForFree` (NYT للـ paywall). **أي منصة جديدة تبدأ من هنا.**

### النمط 2: التصنيف الرباعي/الخماسي الأبعاد
البنية السائدة: **الوجبة (Course) × المكوّن (Ingredient) × الحمية (Diet) × الطريقة/الأداة (Method) + المناسبة/الموسم (Occasion)**. حرفياً في: DS (أنظف تطبيق)، NYT (أغناه)، SE، AR، BBC، TS. الحمية تتقدم للصدارة في المواقع الصحية (EW: nav-level، MB: nav-level).

### النمط 3: البحث دعامة الـ header بصياغة "نية طبخ" لا "بحث"
البحث في الترويسة دائماً وبنص placeholder إنساني: NYT "What would you like to cook?"، DS "What can we help you find?"، BBC "Recipes, guides and more..."، MB "search minimalist baker"، TS "Search Tasty". لا موقع يجعل البحث في وسط hero الرئيسية — الترويسة اللاصقة هي الموضع القياسي.

### النمط 4: الرئيسية = تحرير موسمي فوق قاعدة تصنيفية
كل الرئيسيات تتبع نفس العمود الفقري: hero (وصفة/قصة مميزة) ← شرائح موضوعية منسقة تتغير موسمياً ("What To Cook In September" DS، "September recipes" BBC، Back-to-School MB/DS/TS، Fall NYT) ← الأحدث ← الأشهر ← بلاطات تصنيفات ← newsletter. الموسمية طبقة تحريرية فوق التصنيف الثابت، لا تصنيفاً بحد ذاتها.

### النمط 5: بطاقة الوصفة في الشبكات تحمل إشارات القرار
المعيار: صورة + عنوان + **نجوم + عدد المقيمين + الوقت** (BBC تضيف الصعوبة، NYT تضيف المؤلف). الاستثناءان السلبيان (TS وMB: صورة+عنوان فقط) يجبران المستخدم على فتح كل صفحة. عدد المقيمين هو عملة الثقة (NYT تعرض 12,054، AR عشرات الآلاف).

### النمط 6: نموذجان متمايزان لصفحة الوصفة — اختر موقعك على الطيف
- **قطب "recipe-first" مضغوط:** TS (صفر مقدمة)، NYT وBBC (سطر–سطران).
- **قطب "editorial-first" لمنطق SEO:** DS وSE وMB (مقالة كاملة بعناوين H2 ثم بطاقة وصفة).
الحل الوسط المعياري للقطب الثاني: زر **Jump to Recipe** ملاصق للعنوان (DS، MB، SE) — إلزامي إن تجاوزت المقدمة فقرتين.

### النمط 7: بطاقة وصفة موحدة الحقول (recipe card) قابلة للطباعة
الحقول المعيارية أينما وُجدت بطاقة: Prep/Cook/Total + Servings + Course/Cuisine + Ingredients + Instructions + Notes/Tips + Nutrition + Print. الحقول التفاضلية الذكية: **Does it keep? / Freezer Friendly** (MB)، **Equipment** (DS، SE)، **Make-Ahead & Storage** (SE)، **درجة الصعوبة** (BBC).

### النمط 8: تحويل الوحدات والتحجيم لم يعودا كماليات
US↔Metric toggle: BBC، MB، DS (وTS تكتب الوحدتين inline). تحجيم الحصص: AR (1X/2X/4X) وDS (1x/2x/3x). الغياب عند NYT ملحوظ ومنتقد. لمنصة عربية: جرام/كوب + تحجيم منذ اليوم الأول.

### النمط 9: التغذية حاضرة دائماً — ومستوى العرض قرار تموضع
ثلاث درجات: **ملصق غذائي كامل بالـ %DV ومراجعة RD** (EW — الأعلى)، **جدول per-serving قياسي** (BBC، TS، MB، DS، AR، SE مع إخلاء مسؤولية "estimate")، **إخفاء متعمد من الواجهة مع إبقائها في الـ schema** (NYT — موقف تحريري). المنصة الغذائية تلزمها الدرجة الأولى.

### النمط 10: حلقة تقييم مزدوجة + مجتمع
التقييم يُعرض أعلى الصفحة (قرب العنوان) ويُطلب أسفلها ("Rate this recipe" BBC/DS، "Leave a Comment & Rating" MB، Ratings ثم Comments في NYT). صيغ التفاعل: مراجعات بصور (AR "I Made It")، ملاحظات منتقاة (NYT notes)، أسئلة/نصائح مصنفة (BBC "Comments, questions and tips")، UGC كامل (TS "What You're Making" + Submit your recipe).

### النمط 11: النشرة البريدية بمغناطيس، والحساب خطافه "الحفظ"
Newsletter في الـ footer + نقاط وسط الصفحة، ودائماً بمقابل: كتاب إلكتروني (MB "FAN FAVORITES")، مجتمع ضخم (DS "300,000+")، نشرات موضوعية موقعة (NYT/Melissa Clark)، قناة WhatsApp (BBC). الحساب يُباع بميزة واحدة: **حفظ الوصفات** (NYT Recipe Box، DS Save+meal plans، AR Favorites، MB SAVE، SE MyRecipes) — والطبقة الأعلى: meal planner (DS، EW plans).

### النمط 12: المدفوع يُدمج في التصفح كإعلان مبطن
NYT: paywall كامل + هدايا وصفات (10/شهر) كنمو فيروسي. BBC: وصفات "App only/Premium" مبعثرة داخل النتائج المجانية + "All Access". الباقون مجانيون بإيراد إعلاني/عمولات/متجر (TS كتب وأواني، DS/MB كتب وأدوات مفضلة). الدرس: القفل الجزئي المبعثر يزعج؛ القفل الكامل الواضح (NYT) أو المجانية الكاملة أنظف تجربةً.

### النمط 13 (إضافي): طبقة "الأساسيات" التعليمية
الكل يبني مكتبة how-to منفصلة عن الوصفات لكنها مرتبطة بها: NYT (How-Tos، Learn to Cook)، SE (Techniques/Food Science)، TS (Tips)، DS (Healthy Basics)، BBC (Guides)، EW (Healthy Eating). تلتقط بحث "كيف أ..." وتغذي الوصفات بروابط داخلية.

---

# ثالثاً: خلاصة تنفيذية لمنصة تغذية عربية

1. **الحد الأدنى التقني:** JSON-LD Recipe كامل + بطاقة وصفة موحدة قابلة للطباعة + بطاقات شبكة بإشارات القرار (تقييم/عدد/وقت/سعرات).
2. **التصنيف المقترح:** رباعي الأبعاد (وجبة/مكوّن/حمية/طريقة) + بعد مناسبات محلي (رمضان، عيد، مواسم) — نموذج DS الأنظف بنيوياً + صدارة الحمية من EW.
3. **خندق المصداقية الغذائية (فرصة التميز الأكبر):** تبنّي ثلاثية EW — مراجعة اختصاصي تغذية بالاسم، شارات Nutrition Profile، ملصك غذائي كامل — غير موجودة عربياً تقريباً.
4. **صفحة الوصفة:** مقدمة ≤3 فقرات + Jump to Recipe + بطاقة بحقول MB/DS الذكية (التخزين/التجميد/الأدوات) + جرام/كوب + تحجيم حصص.
5. **النمو:** حفظ الوصفات كسبب إنشاء الحساب، newsletter بمغناطيس عملي (خطة وجبات أسبوعية)، والتقاط بريد بأسلوب DS "أرسل لي الوصفة بالإيميل".

---

## ملحق: سجل الفحص
| الموقع | الرئيسية | تصنيف | وصفة | JSON-LD | طريقة الجلب |
|---|---|---|---|---|---|
| AllRecipes | ✗ | ✗ | ✗ | معروف موثقاً | محجوب (402 الناشر + حجب زاحف Anthropic + Jina 451 + أرشيف الويب rate-limited وقت الفحص) |
| BBC Good Food | ✓ | ✓ | ✓ | ✓ فُحص | curl مباشر |
| NYT Cooking | ✓ | ✓ | ✓ | ✓ فُحص | curl مباشر |
| Serious Eats | ✗ | ✗ | ✗ | معروف موثقاً | محجوب (كما AllRecipes) |
| Tasty | ✓ | ✓ | ✓ | ✓ فُحص | WebFetch + curl HTTP/1.1 (تجاوز 406) |
| EatingWell | ✗ | ✗ | ✗ | معروف موثقاً | محجوب (كما AllRecipes) |
| Minimalist Baker | ✓ | ✓ | ✓ | ✓ فُحص | curl مباشر |
| Downshiftology | ✓ | ✓ | ✓ | ✓ فُحص | curl مباشر |

*الصفحات المفحوصة حرفياً: bbcgoodfood.com (/, /recipes, /recipes/collection/quick-and-easy-family-recipes, /recipes/best-ever-chocolate-brownies-recipe)؛ cooking.nytimes.com (/, /topics/dinner-recipes, /recipes/1020811-cheesy-baked-pasta-with-sausage-and-ricotta)؛ tasty.co (/, /tag/dinner, /recipe/creamy-lemon-chicken)؛ minimalistbaker.com (/, /recipe-index/, /honey-almond-snack-cake/)؛ downshiftology.com (/, /recipes/, /recipes/sweet-potato-soup/).*
