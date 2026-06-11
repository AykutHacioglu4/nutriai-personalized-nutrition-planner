# NutriAI - Personalized Nutrition Planner

## English

NutriAI is a Streamlit-based personalized nutrition planning application that combines calorie calculation, machine learning prediction, rule-based diet recommendation, and genetic algorithm optimization.

The application takes user information such as age, gender, height, weight, activity level, goal, cuisine preference, and allergies. Based on these inputs, it calculates daily calorie and macronutrient targets, predicts possible weekly weight change, recommends a suitable diet type, and generates a daily meal plan that tries to match the user’s calorie, protein, carbohydrate, and fat targets.

The project was developed to understand how different Artificial Intelligence methods can be combined in a single decision-support system. It does not only train or run a model; it connects user input, prediction, optimization, filtering, visualization, and CSV output generation inside a working web application.

---

## Project Overview

NutriAI follows a complete nutrition planning workflow:

1. Collect user profile data through a Streamlit interface
2. Calculate BMR and TDEE values
3. Adjust daily calories based on the user’s goal
4. Calculate daily protein, carbohydrate, and fat targets
5. Predict weekly weight change using a machine learning model or fallback calorie-balance logic
6. Recommend a diet type based on BMI, goal, and activity level
7. Filter foods according to diet type, allergies, and cuisine preference
8. Use a genetic algorithm to generate an optimized daily meal plan
9. Visualize nutrition results with interactive charts
10. Export generated meal plans and optimization results as CSV files

---

## Main Features

* Step-by-step Streamlit user interface
* Gender, age, height, weight, activity level, and goal input
* Cuisine preference and allergy filtering
* BMR calculation
* TDEE calculation
* Goal-based target calorie calculation
* Protein, carbohydrate, and fat target calculation
* Weekly weight change prediction
* Rule-based diet recommendation
* Genetic algorithm based meal plan optimization
* Food filtering by diet suitability, allergens, and cuisine
* Target vs generated meal plan comparison
* Macro distribution visualization
* Calories per meal visualization
* CSV export for generated meal plans
* Output files for model and optimization results

---

## Dataset

The project uses two main datasets:

### Food Dataset

The food dataset contains meal options with nutrition and filtering information.

Main fields include:

* Food name
* Meal type
* Calories
* Protein
* Carbohydrates
* Fat
* Serving size
* Category
* Suitable diet types
* Not suitable diet types
* Allergens
* Cuisine

This dataset is used by the genetic algorithm to generate meal combinations.

### User Weight Dataset

The user weight dataset contains profile and health-related numerical features used for prediction experiments.

Main fields include:

* Age
* Gender
* Weight
* Height
* BMI
* Physical activity level
* Daily caloric intake
* Weekly exercise hours
* Diet adherence score
* Nutrient imbalance score
* Diet recommendation

This dataset is used for the machine learning part of the project.

---

## Machine Learning Module

The machine learning module predicts possible weekly weight change based on user information.

The model input includes:

* Age
* Gender
* Weight
* Height
* BMI
* Physical activity level
* Daily caloric intake
* Weekly exercise hours
* Diet adherence score
* Nutrient imbalance score

If a trained model file is available, the application loads it using Joblib and makes a prediction. If the model file is not available or cannot be loaded, the system uses a fallback calorie-balance calculation.

This structure makes the application more robust because the web app can still produce a result even when the trained model file is missing.

---

## Diet Recommendation Logic

The project includes a simple rule-based diet recommendation function.

The recommendation is based on:

* BMI
* User goal
* Activity level

Example logic:

* Higher BMI can lead to a low-calorie recommendation
* Weight loss goal can lead to a low-carb recommendation
* Weight gain or high activity level can lead to a high-protein recommendation
* Otherwise, the system recommends a balanced diet

This part helped connect numerical user data with a simple decision-making layer.

---

## Genetic Algorithm Module

The genetic algorithm generates a daily meal plan by selecting one item for each meal type:

* Breakfast
* Lunch
* Dinner
* Snack

Before optimization, the food list is filtered according to:

* Recommended diet type
* Allergies
* Preferred cuisine

Each individual in the population represents a possible daily meal plan. The fitness score is calculated according to how close the selected meal plan is to the target nutrition values.

The optimization compares the generated plan with these targets:

* Calories
* Protein
* Carbohydrates
* Fat

The error function gives different weights to nutrition targets. Protein, fat, calories, and carbohydrates all affect the final score. The algorithm uses selection, crossover, mutation, and elitism to improve the meal plan over generations.

---

## Streamlit Web Interface

The project includes a Streamlit interface that guides the user step by step.

The interface includes:

* Welcome screen
* Personal information input
* Body measurement input
* Activity level selection
* Goal selection
* Cuisine and allergy selection
* Result screen with tabs
* Meal plan table
* Nutrition charts
* AI and genetic algorithm details
* CSV download button

The UI makes the system easier to use because the user does not need to interact with code or command-line inputs.

---

## Technologies Used

* Python
* Streamlit
* Pandas
* NumPy
* Scikit-learn
* Joblib
* Plotly
* Genetic Algorithm
* CSV file processing
* Machine Learning
* Data visualization

---

## How to Run

Install the required dependencies:

```bash
pip install -r requirements.txt
```

Run the Streamlit application:

```bash
streamlit run app.py
```

The application opens in the browser and starts the step-by-step nutrition planning flow.

---

## Outputs

The project can generate output files such as:

* Generated meal plan CSV
* Optimization history CSV
* Model result CSV

These outputs make it possible to review the generated plan and optimization process outside the web interface.

---

## What I Implemented and Learned

In this project, I implemented a complete AI-supported nutrition planning workflow.

I practiced how to calculate BMR, TDEE, target calories, and macronutrient goals from user profile data. This helped me understand how numerical user inputs can be transformed into meaningful targets for a recommendation system.

In the machine learning part, I worked on preparing model input data, loading a trained model with Joblib, making predictions, and creating fallback logic when the model is not available. This made the application more stable and showed me the importance of handling failure cases in AI-based systems.

In the genetic algorithm part, I implemented population creation, fitness calculation, crossover, mutation, elitism, and best-plan selection. This helped me understand how optimization algorithms can be used to search for a better solution when there are many possible combinations.

In the Streamlit part, I connected all modules into a usable web application. I practiced building a step-based interface, managing session state, displaying results, visualizing nutrition data, and allowing users to download generated outputs.

Main topics I practiced:

* Building an AI-supported web application with Streamlit
* Calculating BMR, TDEE, calorie targets, and macro targets
* Preparing user input for machine learning prediction
* Loading and using a trained model with Joblib
* Creating fallback prediction logic
* Building a rule-based recommendation layer
* Filtering food data by diet type, allergies, and cuisine
* Implementing a genetic algorithm for meal plan optimization
* Creating fitness and error functions
* Applying crossover, mutation, and elitism
* Visualizing results with Plotly
* Exporting generated results as CSV files
* Organizing a Python project with separate modules

---

## Important Note

This project is a software and AI methods implementation. The generated meal plans and predictions are not intended to replace professional medical or dietitian advice.

---

# NutriAI - Kişiselleştirilmiş Beslenme Planlayıcı

## Türkçe

NutriAI; kalori hesaplama, makine öğrenmesi tahmini, kural tabanlı diyet önerisi ve genetik algoritma optimizasyonunu bir araya getiren Streamlit tabanlı kişiselleştirilmiş bir beslenme planlama uygulamasıdır.

Uygulama kullanıcıdan yaş, cinsiyet, boy, kilo, aktivite seviyesi, hedef, mutfak tercihi ve alerji bilgilerini alır. Bu bilgilere göre günlük kalori ve makro besin hedeflerini hesaplar, olası haftalık kilo değişimini tahmin eder, uygun bir diyet tipi önerir ve kullanıcının kalori, protein, karbonhidrat ve yağ hedeflerine yakın bir günlük yemek planı oluşturur.

Bu proje, farklı Yapay Zeka yöntemlerinin tek bir karar destek sistemi içinde nasıl birlikte kullanılabileceğini anlamak için geliştirildi. Proje yalnızca bir model çalıştırmakla sınırlı değildir; kullanıcı girdisi, tahmin, optimizasyon, filtreleme, görselleştirme ve CSV çıktı üretimi aynı web uygulaması içinde birleştirilmiştir.

---

## Proje Özeti

NutriAI tam bir beslenme planlama akışı izler:

1. Streamlit arayüzü üzerinden kullanıcı profil bilgilerini alma
2. BMR ve TDEE değerlerini hesaplama
3. Kullanıcının hedefine göre günlük kalori hedefini belirleme
4. Günlük protein, karbonhidrat ve yağ hedeflerini hesaplama
5. Makine öğrenmesi modeli veya yedek kalori dengesi mantığıyla haftalık kilo değişimi tahmin etme
6. BMI, hedef ve aktivite seviyesine göre diyet tipi önerme
7. Yiyecekleri diyet tipi, alerji ve mutfak tercihine göre filtreleme
8. Genetik algoritma ile optimize edilmiş günlük yemek planı oluşturma
9. Beslenme sonuçlarını interaktif grafiklerle gösterme
10. Oluşturulan yemek planını ve optimizasyon sonuçlarını CSV olarak dışa aktarma

---

## Temel Özellikler

* Adım adım ilerleyen Streamlit kullanıcı arayüzü
* Cinsiyet, yaş, boy, kilo, aktivite seviyesi ve hedef girişi
* Mutfak tercihi ve alerji filtreleme
* BMR hesaplama
* TDEE hesaplama
* Hedefe göre günlük kalori hesaplama
* Protein, karbonhidrat ve yağ hedefi hesaplama
* Haftalık kilo değişimi tahmini
* Kural tabanlı diyet önerisi
* Genetik algoritma ile yemek planı optimizasyonu
* Diyet uygunluğu, alerjen ve mutfak tipine göre yiyecek filtreleme
* Hedef değerler ile oluşturulan yemek planını karşılaştırma
* Makro dağılım grafiği
* Öğün bazlı kalori grafiği
* Oluşturulan yemek planını CSV olarak indirme
* Model ve optimizasyon sonuçları için çıktı dosyaları

---

## Veri Seti

Projede iki ana veri seti kullanılmaktadır:

### Yiyecek Veri Seti

Yiyecek veri seti, yemek seçeneklerini besin değerleri ve filtreleme bilgileriyle birlikte içerir.

Başlıca alanlar:

* Yiyecek adı
* Öğün tipi
* Kalori
* Protein
* Karbonhidrat
* Yağ
* Porsiyon bilgisi
* Kategori
* Uygun diyet tipleri
* Uygun olmayan diyet tipleri
* Alerjenler
* Mutfak tipi

Bu veri seti, genetik algoritmanın yemek kombinasyonları üretmesi için kullanılır.

### Kullanıcı Kilo Veri Seti

Kullanıcı kilo veri seti, tahmin deneyleri için kullanılan profil ve sağlıkla ilişkili sayısal özellikleri içerir.

Başlıca alanlar:

* Yaş
* Cinsiyet
* Kilo
* Boy
* BMI
* Fiziksel aktivite seviyesi
* Günlük kalori alımı
* Haftalık egzersiz saati
* Diyet uyum skoru
* Besin dengesizliği skoru
* Diyet önerisi

Bu veri seti, projenin makine öğrenmesi kısmında kullanılmıştır.

---

## Makine Öğrenmesi Modülü

Makine öğrenmesi modülü, kullanıcı bilgilerine göre olası haftalık kilo değişimini tahmin eder.

Model girdileri şunlardan oluşur:

* Yaş
* Cinsiyet
* Kilo
* Boy
* BMI
* Fiziksel aktivite seviyesi
* Günlük kalori alımı
* Haftalık egzersiz saati
* Diyet planına uyum skoru
* Besin dengesizliği skoru

Eğitilmiş model dosyası varsa uygulama bu modeli Joblib ile yükler ve tahmin yapar. Model dosyası bulunamazsa veya yüklenemezse sistem yedek kalori dengesi hesaplamasını kullanır.

Bu yapı uygulamayı daha dayanıklı hale getirir. Model dosyası eksik olsa bile web uygulaması sonuç üretebilir.

---

## Diyet Öneri Mantığı

Projede basit bir kural tabanlı diyet öneri fonksiyonu bulunmaktadır.

Öneri şu bilgilere göre yapılır:

* BMI
* Kullanıcının hedefi
* Aktivite seviyesi

Örnek mantık:

* Yüksek BMI düşük kalorili diyet önerisine gidebilir
* Kilo verme hedefi düşük karbonhidrat önerisine gidebilir
* Kilo alma veya yüksek aktivite seviyesi yüksek protein önerisine gidebilir
* Diğer durumlarda dengeli diyet önerilir

Bu bölüm, sayısal kullanıcı verilerinin basit bir karar verme katmanına nasıl bağlanabileceğini göstermektedir.

---

## Genetik Algoritma Modülü

Genetik algoritma, her öğün tipi için bir yiyecek seçerek günlük yemek planı oluşturur:

* Kahvaltı
* Öğle yemeği
* Akşam yemeği
* Ara öğün

Optimizasyon öncesinde yiyecek listesi şu bilgilere göre filtrelenir:

* Önerilen diyet tipi
* Alerjiler
* Tercih edilen mutfak

Popülasyondaki her birey olası bir günlük yemek planını temsil eder. Fitness skoru, seçilen yemek planının hedef besin değerlerine ne kadar yakın olduğuna göre hesaplanır.

Optimizasyon şu hedeflerle karşılaştırma yapar:

* Kalori
* Protein
* Karbonhidrat
* Yağ

Error function, besin hedeflerine farklı ağırlıklar verir. Protein, yağ, kalori ve karbonhidrat değerleri final skoru etkiler. Algoritma nesiller boyunca daha iyi yemek planı üretmek için selection, crossover, mutation ve elitism mantığını kullanır.

---

## Streamlit Web Arayüzü

Projede kullanıcıyı adım adım yönlendiren bir Streamlit arayüzü bulunmaktadır.

Arayüz şunları içerir:

* Karşılama ekranı
* Kişisel bilgi girişi
* Vücut ölçüsü girişi
* Aktivite seviyesi seçimi
* Hedef seçimi
* Mutfak tercihi ve alerji seçimi
* Sekmeli sonuç ekranı
* Yemek planı tablosu
* Beslenme grafikleri
* AI ve genetik algoritma detayları
* CSV indirme butonu

Bu arayüz sayesinde kullanıcı, kod veya komut satırıyla uğraşmadan sistemi kullanabilir.

---

## Kullanılan Teknolojiler

* Python
* Streamlit
* Pandas
* NumPy
* Scikit-learn
* Joblib
* Plotly
* Genetic Algorithm
* CSV dosya işleme
* Machine Learning
* Veri görselleştirme

---

## Çalıştırma

Gerekli bağımlılıkları kurmak için:

```bash
pip install -r requirements.txt
```

Streamlit uygulamasını çalıştırmak için:

```bash
streamlit run app.py
```

Uygulama tarayıcıda açılır ve adım adım beslenme planlama akışı başlar.

---

## Çıktılar

Proje şu çıktı dosyalarını üretebilir:

* Oluşturulan yemek planı CSV dosyası
* Optimizasyon geçmişi CSV dosyası
* Model sonucu CSV dosyası

Bu çıktılar, oluşturulan planın ve optimizasyon sürecinin web arayüzü dışında da incelenebilmesini sağlar.

---

## Bu Projede Ne Uyguladım ve Ne Öğrendim?

Bu projede, AI destekli tam bir beslenme planlama akışı geliştirdim.

Kullanıcı profil verilerinden BMR, TDEE, hedef kalori ve makro besin hedefleri hesaplamayı uyguladım. Bu kısım, sayısal kullanıcı girdilerinin bir öneri sistemi için anlamlı hedeflere nasıl dönüştürülebileceğini anlamamı sağladı.

Makine öğrenmesi kısmında model girdisi hazırlama, Joblib ile eğitilmiş model yükleme, tahmin yapma ve model mevcut olmadığında yedek tahmin mantığı kullanma konularını uyguladım. Bu yapı, AI tabanlı sistemlerde hata durumlarının yönetilmesinin ne kadar önemli olduğunu gösterdi.

Genetik algoritma kısmında popülasyon oluşturma, fitness hesaplama, crossover, mutation, elitism ve en iyi plan seçimi işlemlerini implemente ettim. Bu sayede çok sayıda olası kombinasyon arasından daha iyi bir çözüm aramak için optimizasyon algoritmalarının nasıl kullanılabileceğini gördüm.

Streamlit kısmında tüm modülleri kullanılabilir bir web uygulaması içinde birleştirdim. Step-based arayüz oluşturma, session state yönetme, sonuçları gösterme, beslenme verilerini görselleştirme ve kullanıcıya CSV çıktısı indirme imkanı sağlama konularında pratik yaptım.

Bu projede pratik yaptığım ana konular:

* Streamlit ile AI destekli web uygulaması geliştirme
* BMR, TDEE, hedef kalori ve makro besin hesaplama
* Kullanıcı girdilerini machine learning tahmini için hazırlama
* Joblib ile eğitilmiş model yükleme ve kullanma
* Fallback tahmin mantığı oluşturma
* Kural tabanlı öneri katmanı geliştirme
* Yiyecek verilerini diyet tipi, alerji ve mutfak tercihine göre filtreleme
* Yemek planı optimizasyonu için genetik algoritma implementasyonu
* Fitness ve error function oluşturma
* Crossover, mutation ve elitism uygulama
* Plotly ile sonuçları görselleştirme
* Oluşturulan sonuçları CSV olarak dışa aktarma
* Python projesini ayrı modüller halinde organize etme

---

## Önemli Not

Bu proje bir yazılım ve Yapay Zeka yöntemleri uygulamasıdır. Oluşturulan yemek planları ve tahminler profesyonel tıbbi veya diyetisyen tavsiyesinin yerine geçmez.
Bu proje bir yazılım ve Yapay Zeka yöntemleri uygulamasıdır. Oluşturulan yemek planları ve tahminler profesyonel tıbbi veya diyetisyen tavsiyesinin yerine geçmez.
