# Full Redacted Project Report

This public GitHub version keeps the complete technical report text while removing private identifiers such as student IDs and email addresses.

Original binary report files are intentionally not committed to the public repository because they may contain private front-matter metadata.

---

[DOCX Deep_Learning_OMB.docx]
Deep Learning
31245
גילוי דלקת ריאות מצילומי רנטגן באמצעות CNN
מגישים :
מוחמד יחיא             [REDACTED_ID]
בשאר מריח             [REDACTED_ID]
עובאדה שייח חליל    [REDACTED_ID]
מוגש אל :
פרופ'ח אדלר אמיר
תאריך הגשה :
20-5-2026
מבוא
דלקת ריאות היא מחלה נפוצה העלולה לגרום לסיבוכים רפואיים משמעותיים ואף לסכן חיים. אבחון מוקדם של המחלה חשוב לצורך טיפול מהיר ויעיל. בשנים האחרונות, תחום הבינה המלאכותית ובעיקר רשתות נוירונים קונבולוציוניות  (CNN)  הפך לכלי מרכזי בתחום עיבוד התמונות הרפואיות.
בפרויקט זה מומש פתרון מבוסס למידה עמוקה לצורך גילוי דלקת ריאות מתוך צילומי רנטגן של בית החזה (Chest X-Ray) .
לצורך האימון והבדיקה נעשה שימוש במאגר התמונות Chest X-Ray Pneumonia Dataset מאתר Kaggle,  הכולל אלפי תמונות מסווגות על ידי רופאים.
במסגרת הפרויקט נבנו שתי רשתות שונות:
רשת CNN רגילה ללא שימוש ב.Transfer Learning-
רשת CNN המבוססת על. Transfer Learning
בנוסף, נבדקו מספר אלגוריתמי אימון שונים, בוצע ניתוח ביצועים באמצעות
Accuracy, Precision, Recall ו-F1-Score,  וכן בוצע סיווג לשלוש קטגוריות:
Normal
Bacterial Pneumonia
Viral Pneumonia
מאגר הנתונים  :
מאגר הנתונים נלקח מהקישור:
https://www.kaggle.com/datasets/paultimothymooney/chest-xray-pneumonia
המאגר כולל תמונות רנטגן של בית החזה המחולקות לשלוש קטגוריות:
תמונות תקינות (Normal)
דלקת ריאות חיידקית (Bacterial Pneumonia)
דלקת ריאות נגיפית (Viral Pneumonia)
לצורך הפרויקט בוצעה חלוקה מחדש של הדאטה לסט אימון, סט ולידציה וסט בדיקה בהתאם לדרישות המטלה.
Combined Task 1 and Task 2
Deep CNN Design, Training and Performance Analysis
תיאור הרשת :
במסגרת משימה 1 ומשימה 2 נבנו שתי רשתות CNN לצורך גילוי דלקת ריאות מתוך תמונות Chest X-Ray . 
הרשת הראשונה נבנתה ללא שימוש ב־Transfer Learning, בעוד שהרשת השנייה התבססה על Transfer Learning באמצעות רשת שאומנה מראש על מאגר ImageNet .
לאחר תכנון הרשתות בוצע תהליך אימון והערכת ביצועים באמצעות מדדי Accuracy,     Precision, Recall  ו־F1-Score  עבור ערכי Threshold שונים, במטרה להשוות בין ביצועי המודלים ולבחור את הקונפיגורציה האופטימלית.
מבנה הרשת :
מבנה הרשתות כלל שכבות Convolution ו־MaxPooling  לצורך חילוץ מאפיינים מהתמונה, ולאחר מכן שכבות Fully Connected לצורך ביצוע הסיווג הסופי.
ברשת המבוססת Transfer Learning נעשה שימוש ברשת בסיס שאומנה מראש על מאגר ImageNet, כאשר נוספו לה שכבות מותאמות לצורך פתרון בעיית הסיווג.
השכבות המרכזיות שבהן נעשה שימוש:
Conv2D
MaxPooling2D
Flatten / GlobalAveragePooling2D
Dropout
Dense
Output Layer (Sigmoid)
CNN  ללא Transfer Learning
קטעי קוד :
קטע  Data Augmentation
קטע   מבנה הרשת
קטע  סיווג ואימון
קטע מדדי ביצועים
Dataset Used in the Project :
בכל שלבי הפרויקט נעשה שימוש במאגר נתונים שחולק לשלושה סטים עיקריים לצורך אימון, ולידציה ובדיקה של המודל.
ולאחר מכן:
Train Set: 5138 images
Validation Set: 284 images
Test Set: 434 images
אימון רשת ללא שימוש ב transfer learning :
תוצאות :
גרפים :
רשת שנייה — CNN עם Transfer Learning
תיאור הרשת :
בחלק זה נעשה שימוש ב־Transfer Learning לצורך גילוי דלקת ריאות מתוך תמונות Chest X-Ray .
הרשת מבוססת על מודל שאומן מראש על מאגר ImageNet, כאשר שכבות הבסיס משמשות לחילוץ מאפיינים מהתמונה, ונוספו שכבות סיווג חדשות המותאמות לבעיה הבינארית של זיהוי דלקת ריאות.
מבנה הרשת :
רשת הבסיס שימשה כ־Feature Extractor,  ולאחריה נוספו שכבות נוספות לצורך התאמת המודל למשימת הסיווג.
השכבות שנוספו כוללות GlobalAveragePooling2D, שכבות Dense ושכבת Output עם  Sigmoid  לצורך חיזוי הסתברות לקיום דלקת ריאות.
קטעי קוד :
ResNet50V2 Base Model
Added Classification Layers
Compilation
Architecture of the Transfer Learning Model
Training Configuration
תוצאות :
Training Configuration — Fine Tuning
בשלב זה בוצע Fine Tuning לרשת המבוססת  Transfer Learning   
במסגרת האימון הוקפאו 31 השכבות הראשונות של רשת הבסיס, ואילו השכבות האחרונות נשארו ניתנות לאימון לצורך התאמה טובה יותר לנתוני ה־Chest X-Ray.
קטע קוד :
תוצאות וגרפים :
Precision–Recall Analysis
גרף ה־Precision–Recall  מציג את ביצועי המודל עבור ערכי Threshold שונים.
ניתן לראות כי המודל מצליח לשמור על ערכי Precision גבוהים מאוד לאורך רוב ערכי ה־Threshold, תוך שמירה על ערכי Recall גבוהים יחסית.
בנוסף, ערכי ה־F1-Score שהתקבלו מצביעים על איזון טוב בין Precision לבין Recall, כאשר הביצועים הטובים ביותר התקבלו עבור ערכי Threshold בטווח הביניים.
Training and Validation Analysis
גרפי ה־Loss  ו־Accuracy  מציגים את תהליך ההתכנסות של המודל במהלך האימון.
ניתן לראות כי ערכי ה־Training Loss ו־Validation Loss  יורדים בהדרגה לאורך ה־Epochs,  דבר המעיד על תהליך למידה תקין ויציב.
בנוסף, ערכי ה־Accuracy  של סט האימון וסט ה־Validation  משתפרים לאורך תהליך האימון, כאשר מודל ה־Fine Tuning  השיג ביצועים טובים יותר בהשוואה למודל שבו שכבות הבסיס נשארו מוקפאות.
Threshold Analysis
ניתוח ערכי ה־Precision, Recall ו־F1-Score עבור ערכי Threshold שונים מראה כי ערך ה־F1-Score המקסימלי התקבל עבור:
Threshold = 0.1
עם זאת, ערך סף נמוך במיוחד עלול לגרום למודל להיות רגיש מדי ולייצר מספר גבוה יותר של False Positives, ולכן הוא נחשב לפחות יציב ואמין מבחינה מעשית ורפואית.
TASK 3
Comparison Between Training Optimizers
מבוא :
במשימה זו בוצעה השוואה בין מספר אלגוריתמי אימון שונים לצורך בדיקת השפעתם על ביצועי המודל.
במהלך הניסוי נבדקו האלגוריתמים:
SGD
SGD with Momentum
Adam
RMSProp
בנוסף, נבדקה השפעת ערכי ה־Learning Rate ומספר ה־Epochs על תהליך האימון ועל ביצועי המודל.
חלק ראשון WITHOUT TRANSFER  :
קטעי קוד :
בחירת  Optimizer:
בדיקת  Thresholds
תוצאות וגרפים :
Sgd:
Lr = 0.001, epochs=10 :
Lr = 0.001, epochs=15 :
Lr = 0.001, epochs=25 :
Lr = 0.0001, epochs=10 :
Lr = 0.0001, epochs=15 :
Lr = 0.0001, epochs=25 :
Lr = 0.01, epochs=10 :
Lr = 0.01, epochs=15 :
Lr = 0.01, epochs=25 :
Sgd momentum
:
Lr = 0.001, epochs=10 :
Lr = 0.001, epochs=15 :
Lr = 0.001, epochs=25 :
Lr = 0.0001, epochs=10 :
Lr = 0.0001, epochs=15 :
Lr = 0.0001, epochs=25 :
Lr = 0.01, epochs=10 :
\\\
Lr = 0.01, epochs=15 :
Lr = 0.01, epochs=25 :
Adam:
Lr = 0.001, epochs=10 :
Lr = 0.001, epochs=15:
Lr = 0.001, epochs=25:
Lr = 0.01, epochs=12:
Lr = 0.01, epochs=25:
Lr = 0.0001, epochs=10:
Lr = 0.0001, epochs=12:
Lr = 0.0001, epochs=25:
Rmsprop:
Lr = 0.01, epochs=12:
Lr = 0.01, epochs=25:
Lr = 0.0001, epochs=12:
Lr = 0.0001, epochs=25:
הערך הגבוה התקבל עבור:	                         תוצאות :
Threshold Analysis
חלק שני WITH TRANSFER  :
קטעי קוד :
ResNet50V2 with Fine Tuning
Added Classification Layers  :
Optimizers Comparison :
תוצאות וגרפים :
Adam:
Lr = 0.01, epochs=10:
Lr = 0.01, epochs=20:
Lr = 0.001, epochs=10:
Lr = 0.001, epochs=20:
Msprop:
Lr = 0.01, epochs=10:
Lr = 0.01, epochs=20:
Lr = 0.0 01, epochs=10:
Lr = 0.001, epochs=20
Sgd:
Lr = 0.01, epochs=10:
Lr = 0.01,  epochs=20:
Lr = 0.001, epochs=10:
Lr = 0.001, epochs=20:
Sgd momentum:
Lr = 0.01, epochs=10:
Lr = 0.01, epochs=20:
Lr = 0.001, epochs=10:
Lr = 0.001, epochs=20:
תוצאות :
Best Configuration — Transfer Learning
Results:
Threshold Analysis
Task 4
Multi-Class Classification Using CNN Without Transfer Learning
מבוא :
במשימה זו בוצע סיווג לשלוש קטגוריות שונות מתוך תמונות Chest X-Ray:
Normal
Bacterial Pneumonia
Viral Pneumonia
לצורך כך בוצע שינוי ברשת ה־CNN  ללא Transfer Learning, כך ששכבת הפלט תתאים לסיווג מרובה מחלקות באמצעות פונקציית  Softmax .
קטעי קוד :
Softmax Output Layer
Loss Function
Confusion Matrix
Training Configuration
תוצאות :
Results for the Selected Model
בחזרה ל task 3 עבור אופטימיזרים שונים :
Adam:
Lr = 0.001, epochs=15 :
Lr=0.001,epochs=25
Lr = 0.0001, epochs=15 :
Lr = 0.0001, epochs=25 :
sgd_momentum optimizer:
Lr = 0.001, epochs=15 :
Lr = 0.001, epochs=25 :
Lr = 0.0001, epochs=15 :
Lr = 0.0001, epochs=25 :
Rmsprop optimizer:
Lr = 0.001, epochs=15 :
Lr = 0.001, epochs=25:
Lr = 0.0001, epochs=15:
Lr = 0.0001, epochs=25:
sgd optimizer:
Lr = 0.001, epochs=15:
Lr = 0.001, epochs=25:
Lr = 0.0001, epochs=15:
Lr = 0.0001, epochs=25:
הערך הכי גבוה התקבל עבור:
תוצאה לאחר הפעלת Early stop :
סיכום :
בפרויקט זה מומשו מספר מודלים מבוססי Deep Learning לצורך גילוי דלקת ריאות מתוך תמונות Chest X-Ray .
במהלך הפרויקט בוצעה השוואה בין רשת CNN רגילה ללא Transfer Learning לבין רשת המבוססת על Transfer Learning באמצעות  ResNet50V2 .
בשלב הראשון נבנו ואומנו שתי רשתות שונות לצורך סיווג בינארי בין תמונות תקינות לבין תמונות המכילות דלקת ריאות.
לאחר מכן בוצע ניתוח ביצועים באמצעות המדדים Accuracy, Precision, Recall ו־F1-Score  עבור ערכי Threshold שונים.
תוצאות הניסוי הראו כי שימוש ב־Fine Tuning  שיפר משמעותית את ביצועי רשת ה־Transfer Learning, כאשר המודל השיג Accuracy  גבוה יחד עם ערכי Precision ו־F1-Score  גבוהים במיוחד.
בהמשך בוצעה השוואה בין מספר אלגוריתמי אימון שונים, ביניהם:
SGD
SGD with Momentum
Adam
RMSProp
בנוסף, נבדקה השפעת ערכי Learning Rate ומספר ה־Epochs על ביצועי המודלים.
לפי התוצאות שהתקבלו, האלגוריתמים Adam ו־RMSProp השיגו את הביצועים הטובים ביותר עבור מרבית הניסויים.
במשימה האחרונה בוצע סיווג לשלוש קטגוריות שונות:
Normal
Bacterial Pneumonia
Viral Pneumonia
לצורך כך שונתה רשת ה־CNN ללא Transfer Learning כך שתתמוך בסיווג מרובה מחלקות באמצעות פונקציית Softmax ו־Categorical Crossentropy.
בנוסף, נעשה שימוש ב־Confusion Matrix ובמדדי Precision, Recall ו־F1-Score לצורך הערכת ביצועי המודל.
המודל הצליח לבצע הבחנה טובה בין שלוש הקטגוריות, כאשר התוצאות הטובות ביותר התקבלו באמצעות האלגוריתם RMSProp.
לבסוף, נבדקה גם השפעת טכניקת Early Stopping במטרה למנוע Overfitting. למרות שהטכניקה סייעה בייצוב תהליך האימון, המודל ללא Early Stopping השיג ביצועים טובים יותר ולכן נבחר כמודל הסופי עבור משימת הסיווג מרובה המחלקות.
לסיכום, הפרויקט הדגים את היכולת של רשתות Deep Learning לבצע גילוי וסיווג של דלקת ריאות מתוך תמונות רפואיות ברמת דיוק גבוהה, תוך שימוש בטכניקות מתקדמות של CNN, Transfer Learning ו־Fine Tuning.

[TABLE 1]
Layer | Filters | Kernel Size | Pool Size | Output Size
Layer 1 | 32 | 4×4 | 2×2 | (80, 80, 32)
Layer 2 | 64 | 4×4 | 2×2 | (40, 40, 64)
Layer 3 | 128 | 2×2 | 2×2 | (20, 20, 128)
Layer 4 | 256 | 3×3 | 2×2 | (10, 10, 256)
Layer 5 | 512 | 3×3 | 2×2 | (5, 5, 512)
Layer 6 | — | Flatten | — | 5×5×512 = 12800
Layer 7 | — | Dense | — | 512
Layer 8 | — | Dense (Sigmoid) | — | 1

[TABLE 2]
Parameter | Value
Optimizer | Adam
Learning Rate | 0.001
Epochs | 25
Batch Size | 10

[TABLE 3]
Metric | Value
Test Accuracy | 95.62%
Precision | 0.9896
Recall | 0.9183
F1 Score | 0.9526

[TABLE 4]
Layer | Output Shape
ResNet50V2 | (None, 7, 7, 2048)
GlobalAveragePooling2D | (None, 2048)
Dense | (None, 256)
Dense | (None, 128)
Dense (Sigmoid) | (None, 1)

[TABLE 5]
Parameter | Value
Optimizer | Adam
Learning Rate | 0.00001
Epochs | 15
Batch Size | 16

[TABLE 6]
Metric | Value
Test Accuracy | 84.10%
Precision | 0.9860
Recall | 0.6779
F1 Score | 0.8034

[TABLE 7]
Parameter | Value
Frozen Layers | First 31 layers
Optimizer | Adam
Learning Rate | 0.00001
Epochs | 10
Batch Size | 16

[TABLE 8]
Metric | Value
Test Accuracy | 94.01%
Precision | 0.9892
Recall | 0.8846
F1 Score | 0.9340

[TABLE 9]
Parameter | Value
Optimizer | Adam
Learning Rate | 0.001
Epochs | 15

[TABLE 10]
Metric | Value
Test Accuracy | 93.55%
Best F1-Score | 0.9347
Best Threshold | 0.55

[TABLE 11]
Threshold | Precision | Recall | F1-Score
0.10 | 0.8112 | 0.9712 | 0.8840
0.25 | 0.8950 | 0.9423 | 0.9180
0.40 | 0.9458 | 0.9231 | 0.9430
0.50 | 0.9592 | 0.9083 | 0.9307
0.55 | 0.9789 | 0.8942 | 0.9347
0.90 | 0.9853 | 0.6442 | 0.7791

[TABLE 12]
Parameter | Value
Optimizer | SGD
Learning Rate | 0.001
Epochs | 10

[TABLE 13]
Metric | Value
Test Accuracy | 93.09%
Best F1-Score | 0.9631
Best Threshold | 0.10

[TABLE 14]
Threshold | Precision | Recall | F1-Score
0.10 | 0.9849 | 0.9423 | 0.9631
0.25 | 0.9947 | 0.9083 | 0.9471
0.40 | 1.0000 | 0.8702 | 0.9306
0.55 | 1.0000 | 0.8269 | 0.9053
0.90 | 1.0000 | 0.4471 | 0.6179

[TABLE 15]
Parameter | Value
Model | CNN Without Transfer Learning
Output Layer | Softmax
Loss Function | Categorical Crossentropy
Classes | 3
Image Size | 160×160
Batch Size | 10

[TABLE 16]
Parameter | Value
Optimizer | Adam
Learning Rate | 0.001
Epochs | 25

[TABLE 17]
Parameter | Value
Optimizer | RMSProp
Learning Rate | 0.001
Epochs | 25

[TABLE 18]
Metric | Value
Test Accuracy | 82.95%
Precision | 0.8417
Recall | 0.8295
F1 Score | 0.8259

[TABLE 19]
Metric | Value
Test Accuracy | 79.26%
Precision | 0.8281
Recall | 0.7926
F1 Score | 0.7798

[FILE Task 1 + Task 2 — CNN without Transfer Learning..py]
import tensorflow as tf
from tensorflow.keras.preprocessing.image import ImageDataGenerator
from tensorflow.keras.layers import Conv2D, MaxPool2D, Flatten, Dense, Dropout, BatchNormalization
from tensorflow.keras.models import Sequential
from tensorflow.keras.callbacks import EarlyStopping, ReduceLROnPlateau
from sklearn.utils.class_weight import compute_class_weight
from sklearn.metrics import precision_score, recall_score, f1_score
import numpy as np
import matplotlib.pyplot as plt

from google.colab import drive
drive.mount('/content/drive')

# הגדרת פרמטרים
img_size = 160
batch_size = 10

base_path = "/content/drive/MyDrive/DEEP-LEARNING/chest_xray"

train_path = base_path + "/train"
val_path   = base_path + "/val"
test_path  = base_path + "/test"

# Data Augmentation עבור אימון
train_datagen = ImageDataGenerator(
    rescale=1./255,
    rotation_range=30,
    width_shift_range=0.2,
    height_shift_range=0.2,
    shear_range=0.2,
    zoom_range=0.2,
    horizontal_flip=True,
    fill_mode='nearest'
)

val_test_datagen = ImageDataGenerator(rescale=1./255)

# יצירת מחוללי תמונות (Generators)
train_generator = train_datagen.flow_from_directory(
    train_path,
    target_size=(img_size, img_size),
    batch_size=batch_size,
    color_mode='grayscale',
    class_mode='binary',
    shuffle=True
)

val_generator = val_test_datagen.flow_from_directory(
    val_path,
    target_size=(img_size, img_size),
    batch_size=batch_size,
    color_mode='grayscale',
    class_mode='binary',
    shuffle=False
)

test_generator = val_test_datagen.flow_from_directory(
    test_path,
    target_size=(img_size, img_size),
    batch_size=batch_size,
    color_mode='grayscale',
    class_mode='binary',
    shuffle=False
)

# חישוב משקולות למחלקות (Class Weights)
classes = train_generator.classes
class_labels = np.unique(classes)
class_weights = compute_class_weight('balanced', classes=class_labels, y=classes)
class_weights_dict = dict(enumerate(class_weights))

# יצירת מודל CNN עם יותר שכבות
def build_medical_cnn(input_shape=(img_size, img_size, 1)):
    model = Sequential()

    # שכבת קונבולוציה ראשונה
    model.add(Conv2D(32, (4, 4), activation='relu', padding='same', input_shape=input_shape))
    model.add(BatchNormalization())
    model.add(MaxPool2D((2, 2)))

    # שכבת קונבולוציה שניה
    model.add(Conv2D(64, (4, 4), activation='relu', padding='same'))
    model.add(BatchNormalization())
    model.add(MaxPool2D((2, 2)))
    model.add(Dropout(0.3))

    # שכבת קונבולוציה שלישית
    model.add(Conv2D(128, (3, 3), activation='relu', padding='same'))
    model.add(BatchNormalization())
    model.add(MaxPool2D((2, 2)))
    model.add(Dropout(0.4))

    # שכבת קונבולוציה רביעית
    model.add(Conv2D(256, (3, 3), activation='relu', padding='same'))
    model.add(BatchNormalization())
    model.add(MaxPool2D((2, 2)))
    model.add(Dropout(0.5))

    # שכבת קונבולוציה חמישית
    model.add(Conv2D(512, (3, 3), activation='relu', padding='same'))
    model.add(BatchNormalization())
    model.add(MaxPool2D((2, 2)))
    model.add(Dropout(0.5))

    # Flatten ו-Dense
    model.add(Flatten())
    model.add(Dense(512, activation='relu'))
    model.add(Dropout(0.5))

    model.add(Dense(1, activation='sigmoid'))

    model.compile(optimizer=tf.keras.optimizers.Adam(learning_rate=0.001),
                  loss='binary_crossentropy',
                  metrics=['accuracy'])

    return model

# יצירת המודל
model = build_medical_cnn()
model.summary()

# Callbacks
early_stop = EarlyStopping(monitor='val_loss', patience=5, restore_best_weights=True, verbose=1)
reduce_lr = ReduceLROnPlateau(monitor='val_loss', factor=0.1, patience=2, min_lr=1e-8, verbose=1)

# אימון המודל
history = model.fit(
    train_generator,
    epochs=25,
    validation_data=val_generator,
    class_weight=class_weights_dict,
    callbacks=[early_stop, reduce_lr]
)

# הערכת המודל על סט הבדיקה
test_loss, test_acc = model.evaluate(test_generator)
print(f"\nTest Accuracy: {test_acc * 100:.2f}%")

# חיזוי תוצאות על סט הבדיקה
y_probs = model.predict(test_generator)
y_pred = (y_probs > 0.5).astype(int)
y_true = test_generator.classes

# חישוב Precision, Recall ו-F1 Score
precision = precision_score(y_true, y_pred)
recall = recall_score(y_true, y_pred)
f1 = f1_score(y_true, y_pred)

print(f"Precision: {precision:.4f}")
print(f"Recall: {recall:.4f}")
print(f"F1 Score: {f1:.4f}")

# הצגת Precision-Recall curve
from sklearn.metrics import precision_recall_curve

precision, recall, thresholds = precision_recall_curve(y_true, y_probs)

plt.figure(figsize=(8, 6))
plt.plot(recall, precision, marker='*', color='b', label='Precision-Recall curve')
plt.xlabel('Recall')
plt.ylabel('Precision')
plt.title('Precision vs Recall')
plt.legend()
plt.grid(True)
plt.show()

# הצגת גרפים עבור Loss ו-Accuracy של האימון וה-Validation
plt.figure(figsize=(12, 6))

plt.subplot(1, 2, 1)
plt.plot(history.history['loss'], label='Training Loss')
plt.plot(history.history['val_loss'], label='Validation Loss')
plt.title('Loss over Epochs')
plt.xlabel('Epochs')
plt.ylabel('Loss')
plt.legend()

plt.subplot(1, 2, 2)
plt.plot(history.history['accuracy'], label='Training Accuracy')
plt.plot(history.history['val_accuracy'], label='Validation Accuracy')
plt.title('Accuracy over Epochs')
plt.xlabel('Epochs')
plt.ylabel('Accuracy')
plt.legend()

plt.tight_layout()
plt.show()

[FILE Task 1 + Task 2 — WITH Transfer Learning.py]
import tensorflow as tf
from tensorflow.keras.preprocessing.image import ImageDataGenerator
from tensorflow.keras.applications import ResNet50V2
from tensorflow.keras.layers import Dense, Dropout, BatchNormalization, GlobalAveragePooling2D
from tensorflow.keras.models import Sequential
from tensorflow.keras.optimizers import Adam
from tensorflow.keras.callbacks import EarlyStopping, ReduceLROnPlateau
from sklearn.metrics import precision_score, recall_score, f1_score
from sklearn.utils.class_weight import compute_class_weight

import numpy as np
import matplotlib.pyplot as plt

from google.colab import drive
drive.mount('/content/drive')

# הגדרת פרמטרים
img_size = 224
batch_size = 16

base_path = "/content/drive/MyDrive/DEEP-LEARNING/chest_xray"

train_path = base_path + "/train"
val_path   = base_path + "/val"
test_path  = base_path + "/test"

# Augmentation לסט האימון
train_datagen = ImageDataGenerator(
    rescale=1./255,
    rotation_range=30,
    width_shift_range=0.2,
    height_shift_range=0.2,
    shear_range=0.2,
    zoom_range=0.2,
    horizontal_flip=True,
    fill_mode='nearest'
)

val_test_datagen = ImageDataGenerator(rescale=1./255)

# יצירת מחוללי תמונות (Generators)
train_generator = train_datagen.flow_from_directory(
    train_path,
    target_size=(img_size, img_size),
    batch_size=batch_size,
    color_mode='rgb',
    class_mode='binary',
    shuffle=True
)

val_generator = val_test_datagen.flow_from_directory(
    val_path,
    target_size=(img_size, img_size),
    batch_size=batch_size,
    color_mode='rgb',
    class_mode='binary',
    shuffle=False
)

test_generator = val_test_datagen.flow_from_directory(
    test_path,
    target_size=(img_size, img_size),
    batch_size=batch_size,
    color_mode='rgb',
    class_mode='binary',
    shuffle=False
)


classes = train_generator.classes
class_labels = np.unique(classes)

# חישוב המשקלות לכל מחלקה
class_weights = compute_class_weight('balanced', classes=np.unique(classes), y=classes)

# המרה למילון לשימוש באימון המודל
class_weights_dict = dict(enumerate(class_weights))

# טעינת מודל ResNet50V2 מאומן מראש (ללא שכבת הסיווג)
base_model = ResNet50V2(weights='imagenet', include_top=False, input_shape=(img_size, img_size, 3))
base_model.trainable = False  # הקפאת כל השכבות

# בניית המודל באמצעות Sequential
model = Sequential([
    base_model,  # שכבת הבסיס של ResNet50V2
    GlobalAveragePooling2D(),
    Dense(256, activation='relu'),
    BatchNormalization(),
    Dropout(0.5),
    Dense(128, activation='relu'),
    BatchNormalization(),
    Dropout(0.3),
    Dense(1, activation='sigmoid')  # שכבת יציאה בינארית
])

# קומפילציה
model.compile(optimizer=Adam(learning_rate=0.00001),
              loss='binary_crossentropy',
              metrics=['accuracy'])

# הצגת מבנה המודל
model.summary()

# Callbacks
early_stop = EarlyStopping(monitor='val_loss', patience=5, restore_best_weights=True, verbose=1)
reduce_lr = ReduceLROnPlateau(monitor='val_loss', factor=0.1, patience=3, min_lr=1e-7, verbose=1)

# אימון המודל (שלב ראשון - הקפאת ResNet50V2)
history = model.fit(
    train_generator,
    epochs=15,
    validation_data=val_generator,
    callbacks=[early_stop, reduce_lr],
    class_weight=class_weights_dict
)

# הערכת המודל על סט הבדיקה
test_loss, test_acc = model.evaluate(test_generator)
print(f"\nTest Accuracy: {test_acc * 100:.2f}%")

# חיזוי תוצאות על סט הבדיקה
y_probs = model.predict(test_generator)
y_pred = (y_probs > 0.5).astype(int)
y_true = test_generator.classes

# חישוב Precision, Recall ו-F1 Score
precision = precision_score(y_true, y_pred)
recall = recall_score(y_true, y_pred)
f1 = f1_score(y_true, y_pred)

print(f"Precision: {precision:.4f}")
print(f"Recall: {recall:.4f}")
print(f"F1 Score: {f1:.4f}")


# ערכים שונים של סף (Threshold) בטווח 0.1 עד 0.9 בקפיצות של 0.05
thresholds = np.arange(0.1, 1.0, 0.05)

# יצירת מערכים לאחסון Precision, Recall ו-F1 Score
precisions = []
recalls = []
f1_scores = []

# חישוב Precision, Recall ו-F1 עבור כל סף
for threshold in thresholds:
    y_pred = (y_probs > threshold).astype(int)
    precision = precision_score(test_generator.classes, y_pred)
    recall = recall_score(test_generator.classes, y_pred)
    f1 = f1_score(test_generator.classes, y_pred)

    precisions.append(precision)
    recalls.append(recall)
    f1_scores.append(f1)

# יצירת גרף Precision-Recall
plt.figure(figsize=(10, 6))
plt.plot(precisions, recalls, marker='o', label='Precision-Recall Curve', color='b')

# ציור נקודות F-Score
for i in range(len(thresholds)):
    plt.text(precisions[i], recalls[i], f'F1: {f1_scores[i]:.2f}', fontsize=9)

# הגדרת הגרף
plt.xlabel('Precision')
plt.ylabel('Recall')
plt.title('Precision vs Recall for Different Thresholds')
plt.grid(True)
plt.legend()
plt.show()


# שלב שני - Fine-Tuning
base_model.trainable = True
for layer in base_model.layers[:31]:  # מקפיאים את 100 השכבות הראשונות
    layer.trainable = False

# קומפילציה מחדש עם Fine-Tuning
model.compile(optimizer=Adam(learning_rate=0.00001),
              loss='binary_crossentropy',
              metrics=['accuracy'])

# אימון המודל עם Fine-Tuning
history_fine = model.fit(
    train_generator,
    epochs=10,
    validation_data=val_generator,
    callbacks=[early_stop, reduce_lr],class_weight=class_weights_dict
)

# הערכת המודל על סט הבדיקה
test_loss, test_acc = model.evaluate(test_generator)
print(f"\nTest Accuracy: {test_acc * 100:.2f}%")

# חיזוי תוצאות על סט הבדיקה
y_probs = model.predict(test_generator)
y_pred = (y_probs > 0.5).astype(int)
y_true = test_generator.classes

# חישוב Precision, Recall ו-F1 Score
precision = precision_score(y_true, y_pred)
recall = recall_score(y_true, y_pred)
f1 = f1_score(y_true, y_pred)

print(f"Precision: {precision:.4f}")
print(f"Recall: {recall:.4f}")
print(f"F1 Score: {f1:.4f}")

# ערכים שונים של סף (Threshold) בטווח 0.1 עד 0.9 בקפיצות של 0.05
thresholds = np.arange(0.1, 1.0, 0.05)

# יצירת מערכים לאחסון Precision, Recall ו-F1 Score
precisions = []
recalls = []
f1_scores = []

# חישוב Precision, Recall ו-F1 עבור כל סף
for threshold in thresholds:
    y_pred = (y_probs > threshold).astype(int)
    precision = precision_score(test_generator.classes, y_pred)
    recall = recall_score(test_generator.classes, y_pred)
    f1 = f1_score(test_generator.classes, y_pred)

    precisions.append(precision)
    recalls.append(recall)
    f1_scores.append(f1)

# יצירת גרף Precision-Recall
plt.figure(figsize=(10, 6))
plt.plot(precisions, recalls, marker='o', label='Precision-Recall Curve', color='b')

# ציור נקודות F-Score
for i in range(len(thresholds)):
    plt.text(precisions[i], recalls[i], f'F1: {f1_scores[i]:.2f}', fontsize=9)

# הגדרת הגרף
plt.xlabel('Precision')
plt.ylabel('Recall')
plt.title('Precision vs Recall for Different Thresholds')
plt.grid(True)
plt.legend()
plt.show()

# גרפים להערכת ביצועי המודל
def plot_learning_curve(history, fine_tune_history=None):
    plt.figure(figsize=(12, 5))

    # Loss
    plt.subplot(1, 2, 1)
    plt.plot(history.history['loss'], label='Train Loss', color='blue')
    plt.plot(history.history['val_loss'], label='Validation Loss', color='red')
    if fine_tune_history:
        plt.plot(fine_tune_history.history['loss'], label='Train Loss (Fine-Tune)', linestyle='dashed', color='blue')
        plt.plot(fine_tune_history.history['val_loss'], label='Validation Loss (Fine-Tune)', linestyle='dashed', color='red')
    plt.xlabel('Epochs')
    plt.ylabel('Loss')
    plt.legend()
    plt.title('Training & Validation Loss')

    # Accuracy
    plt.subplot(1, 2, 2)
    plt.plot(history.history['accuracy'], label='Train Accuracy', color='blue')
    plt.plot(history.history['val_accuracy'], label='Validation Accuracy', color='red')
    if fine_tune_history:
        plt.plot(fine_tune_history.history['accuracy'], label='Train Accuracy (Fine-Tune)', linestyle='dashed', color='blue')
        plt.plot(fine_tune_history.history['val_accuracy'], label='Validation Accuracy (Fine-Tune)', linestyle='dashed', color='red')
    plt.xlabel('Epochs')
    plt.ylabel('Accuracy')
    plt.legend()
    plt.title('Training & Validation Accuracy')

    plt.show()

# הצגת הגרפים
plot_learning_curve(history, history_fine)

[FILE Task 3 WITH Transfer Learning.py]
import tensorflow as tf
from tensorflow.keras.preprocessing.image import ImageDataGenerator
from tensorflow.keras.applications import ResNet50V2
from tensorflow.keras.layers import Dense, Dropout, BatchNormalization, GlobalAveragePooling2D
from tensorflow.keras.models import Sequential
from tensorflow.keras.optimizers import Adam
from tensorflow.keras.callbacks import EarlyStopping, ReduceLROnPlateau
from sklearn.metrics import precision_score, recall_score, f1_score
from sklearn.utils.class_weight import compute_class_weight

import numpy as np
import matplotlib.pyplot as plt

from google.colab import drive
drive.mount('/content/drive')

# הגדרת פרמטרים
img_size = 224
batch_size = 16

base_path = "/content/drive/MyDrive/DEEP-LEARNING/chest_xray"

train_path = base_path + "/train"
val_path   = base_path + "/val"
test_path  = base_path + "/test"

# Augmentation לסט האימון
train_datagen = ImageDataGenerator(
    rescale=1./255,
    rotation_range=30,
    width_shift_range=0.2,
    height_shift_range=0.2,
    shear_range=0.2,
    zoom_range=0.2,
    horizontal_flip=True,
    fill_mode='nearest'
)

val_test_datagen = ImageDataGenerator(rescale=1./255)

# יצירת מחוללי תמונות (Generators)
train_generator = train_datagen.flow_from_directory(
    train_path,
    target_size=(img_size, img_size),
    batch_size=batch_size,
    color_mode='rgb',
    class_mode='binary',
    shuffle=True
)

val_generator = val_test_datagen.flow_from_directory(
    val_path,
    target_size=(img_size, img_size),
    batch_size=batch_size,
    color_mode='rgb',
    class_mode='binary',
    shuffle=False
)

test_generator = val_test_datagen.flow_from_directory(
    test_path,
    target_size=(img_size, img_size),
    batch_size=batch_size,
    color_mode='rgb',
    class_mode='binary',
    shuffle=False
)


classes = train_generator.classes
class_labels = np.unique(classes)

# חישוב המשקלות לכל מחלקה
class_weights = compute_class_weight('balanced', classes=np.unique(classes), y=classes)

# המרה למילון לשימוש באימון המודל
class_weights_dict = dict(enumerate(class_weights))


def build_model():

  # טעינת מודל ResNet50V2 מאומן מראש (ללא שכבת הסיווג)
  base_model = ResNet50V2(weights='imagenet', include_top=False, input_shape=(img_size, img_size, 3))
  base_model.trainable = False  # הקפאת כל השכבות

  # בניית המודל באמצעות Sequential
  model = Sequential([
      base_model,
      GlobalAveragePooling2D(),
      Dense(256, activation='relu'),
      BatchNormalization(),
      Dropout(0.5),
      Dense(128, activation='relu'),
      BatchNormalization(),
      Dropout(0.3),
      Dense(1, activation='sigmoid')
  ])

  # הצגת מבנה המודל
  model.summary()

  # Callbacks
  early_stop = EarlyStopping(monitor='val_loss', patience=5, restore_best_weights=True, verbose=1)
  reduce_lr = ReduceLROnPlateau(monitor='val_loss', factor=0.1, patience=3, min_lr=1e-7, verbose=1)

  # שלב שני - Fine-Tuning
  base_model.trainable = True
  for layer in base_model.layers[:31]:  # מקפיאים את 100 השכבות הראשונות
      layer.trainable = False

  # קומפילציה מחדש עם Fine-Tuning
  model.compile(
      optimizer=Adam(learning_rate=0.00001),
      loss='binary_crossentropy',
      metrics=['accuracy']
  )

  return model


def train_model_with_optimizer(optimizer, lr, epochs):
    model = build_model()

    if optimizer == 'sgd':
        opt = tf.keras.optimizers.SGD(learning_rate=lr)
    elif optimizer == 'sgd_momentum':
        opt = tf.keras.optimizers.SGD(learning_rate=lr, momentum=0.9)
    elif optimizer == 'adam':
        opt = tf.keras.optimizers.Adam(learning_rate=lr)
    elif optimizer == 'rmsprop':
        opt = tf.keras.optimizers.RMSprop(learning_rate=lr)

    model.compile(
        optimizer=opt,
        loss='binary_crossentropy',
        metrics=['accuracy']
    )

    # early_stop = EarlyStopping(monitor='val_loss', patience=5, restore_best_weights=True, verbose=1)
    reduce_lr = ReduceLROnPlateau(monitor='val_loss', factor=0.1, patience=2, min_lr=1e-8, verbose=1)

    history = model.fit(
        train_generator,
        epochs=epochs,
        validation_data=val_generator,
        class_weight=class_weights_dict,
        callbacks=[reduce_lr]  # early_stop, reduce_lr
    )

    return model, history


# הגדרת ערכים של Learning Rate ו-Epochs לבדוק
learning_rates = [0.01, 0.001]
epochs_values = [10, 20]

# מילון לשמירת התוצאות
history_results = {}

# אופטימיזרים
optimizers = ['adam', 'rmsprop', 'sgd', 'sgd_momentum']

# לולאה עבור כל אופטימיזר, Learning Rate ו-Epochs
for opt in optimizers:
    history_results[opt] = {}

    for lr in learning_rates:
        for epochs in epochs_values:

            print(f"Training with {opt} optimizer, Learning Rate: {lr}, Epochs: {epochs}")

            model, history = train_model_with_optimizer(opt, lr, epochs)
            history_results[opt][(lr, epochs)] = history

            # הערכת המודל על סט הבדיקה
            test_loss, test_acc = model.evaluate(test_generator)
            print(f"\nTest Accuracy: {test_acc * 100:.2f}%")

            # חיזוי על Test set
            y_probs = model.predict(test_generator)
            y_pred = (y_probs > 0.5).astype(int)
            y_true = test_generator.classes

            # חישוב והדפסת תוצאות לכל סף מ-0.1 עד 0.9
            thresholds = np.arange(0.1, 0.95, 0.05)
            precision_list = []
            recall_list = []

            plt.figure(figsize=(8, 6))

            for t in thresholds:
                y_pred = (y_probs > t).astype(int)
                precision = precision_score(y_true, y_pred)
                recall = recall_score(y_true, y_pred)
                f1 = f1_score(y_true, y_pred)

                precision_list.append(precision)
                recall_list.append(recall)

                print(
                    f"Threshold {t:.2f} => "
                    f"Precision: {precision:.4f}, "
                    f"Recall: {recall:.4f}, "
                    f"F1 Score: {f1:.4f}"
                )

            # ציור גרף Precision-Recall עם נקודות לכל סף
            plt.plot(
                recall_list,
                precision_list,
                marker='o',
                linestyle='-',
                color='b',
                label='Precision-Recall'
            )

            plt.xlabel('Recall')
            plt.ylabel('Precision')
            plt.title(f'Precision vs Recall for {opt} - LR: {lr}, Epochs: {epochs}')
            plt.legend()
            plt.grid(True)
            plt.show()

            # Loss
            plt.figure(figsize=(12, 6))

            plt.subplot(1, 2, 1)
            plt.plot(history.history['loss'], label='Training Loss')
            plt.plot(history.history['val_loss'], label='Validation Loss')
            plt.title(f'{opt} - LR: {lr}, Epochs: {epochs} - Loss over Epochs')
            plt.xlabel('Epochs')
            plt.ylabel('Loss')
            plt.legend()

            # Accuracy
            plt.subplot(1, 2, 2)
            plt.plot(history.history['accuracy'], label='Training Accuracy')
            plt.plot(history.history['val_accuracy'], label='Validation Accuracy')
            plt.title(f'{opt} - LR: {lr}, Epochs: {epochs} - Accuracy over Epochs')
            plt.xlabel('Epochs')
            plt.ylabel('Accuracy')
            plt.legend()

            plt.tight_layout()
            plt.show()

[FILE Task 3 — WITHOUT Transfer Learning.py]
import tensorflow as tf
from tensorflow.keras.preprocessing.image import ImageDataGenerator
from tensorflow.keras.layers import Conv2D, MaxPool2D, Flatten, Dense, Dropout, BatchNormalization
from tensorflow.keras.models import Sequential
from tensorflow.keras.callbacks import EarlyStopping, ReduceLROnPlateau
from sklearn.utils.class_weight import compute_class_weight
from sklearn.metrics import precision_score, recall_score, f1_score, accuracy_score, precision_recall_curve
import numpy as np
import matplotlib.pyplot as plt

from google.colab import drive
drive.mount('/content/drive')

# הגדרת פרמטרים
img_size = 160
batch_size = 10

base_path = "/content/drive/MyDrive/DEEP-LEARNING/chest_xray"

train_path = base_path + "/train"
val_path   = base_path + "/val"
test_path  = base_path + "/test"

# Data Augmentation עבור אימון
train_datagen = ImageDataGenerator(
    rescale=1./255,
    rotation_range=30,
    width_shift_range=0.2,
    height_shift_range=0.2,
    shear_range=0.2,
    zoom_range=0.2,
    horizontal_flip=True,
    fill_mode='nearest'
)

val_test_datagen = ImageDataGenerator(rescale=1./255)

# יצירת מחוללי תמונות (Generators)
train_generator = train_datagen.flow_from_directory(
    train_path,
    target_size=(img_size, img_size),
    batch_size=batch_size,
    color_mode='grayscale',
    class_mode='binary',
    shuffle=True
)

val_generator = val_test_datagen.flow_from_directory(
    val_path,
    target_size=(img_size, img_size),
    batch_size=batch_size,
    color_mode='grayscale',
    class_mode='binary',
    shuffle=False
)

test_generator = val_test_datagen.flow_from_directory(
    test_path,
    target_size=(img_size, img_size),
    batch_size=batch_size,
    color_mode='grayscale',
    class_mode='binary',
    shuffle=False
)

# חישוב משקולות למחלקות (Class Weights)
classes = train_generator.classes
class_labels = np.unique(classes)
class_weights = compute_class_weight('balanced', classes=class_labels, y=classes)
class_weights_dict = dict(enumerate(class_weights))

# יצירת מודל CNN עם יותר שכבות
def build_medical_cnn(input_shape=(img_size, img_size, 1)):
    model = Sequential()

    model.add(Conv2D(32, (4, 4), activation='relu', padding='same', input_shape=input_shape))
    model.add(BatchNormalization())
    model.add(MaxPool2D((2, 2)))

    model.add(Conv2D(64, (4, 4), activation='relu', padding='same'))
    model.add(BatchNormalization())
    model.add(MaxPool2D((2, 2)))
    model.add(Dropout(0.3))

    model.add(Conv2D(128, (3, 3), activation='relu', padding='same'))
    model.add(BatchNormalization())
    model.add(MaxPool2D((2, 2)))
    model.add(Dropout(0.4))

    model.add(Conv2D(256, (3, 3), activation='relu', padding='same'))
    model.add(BatchNormalization())
    model.add(MaxPool2D((2, 2)))
    model.add(Dropout(0.5))

    model.add(Conv2D(512, (3, 3), activation='relu', padding='same'))
    model.add(BatchNormalization())
    model.add(MaxPool2D((2, 2)))
    model.add(Dropout(0.5))

    model.add(Flatten())
    model.add(Dense(512, activation='relu'))
    model.add(Dropout(0.5))

    model.add(Dense(1, activation='sigmoid'))

    model.compile(
        optimizer=tf.keras.optimizers.Adam(learning_rate=0.001),
        loss='binary_crossentropy',
        metrics=['accuracy']
    )

    return model

# פונקציה לאימון המודל עם אופטימיזר ופרמטרים שונים
def train_model_with_optimizer(optimizer, lr, epochs):
    model = build_medical_cnn()

    if optimizer == 'sgd':
        opt = tf.keras.optimizers.SGD(learning_rate=lr)
    elif optimizer == 'sgd_momentum':
        opt = tf.keras.optimizers.SGD(learning_rate=lr, momentum=0.9)
    elif optimizer == 'adam':
        opt = tf.keras.optimizers.Adam(learning_rate=lr)
    elif optimizer == 'rmsprop':
        opt = tf.keras.optimizers.RMSprop(learning_rate=lr)

    model.compile(
        optimizer=opt,
        loss='binary_crossentropy',
        metrics=['accuracy']
    )

    reduce_lr = ReduceLROnPlateau(
        monitor='val_loss',
        factor=0.1,
        patience=2,
        min_lr=1e-8,
        verbose=1
    )

    history = model.fit(
        train_generator,
        epochs=epochs,
        validation_data=val_generator,
        class_weight=class_weights_dict,
        callbacks=[reduce_lr]
    )

    return model, history

# הגדרת ערכים של Learning Rate ו-Epochs לבדוק
learning_rates = [0.01, 0.0001]
epochs_values = [12, 25]

# מילון לשמירת התוצאות
history_results = {}

# אופטימיזרים
optimizers = ['adam', 'rmsprop']  # אפשר להוסיף: 'sgd', 'sgd_momentum'

# לולאה עבור כל אופטימיזר, Learning Rate ו-Epochs
for opt in optimizers:
    history_results[opt] = {}

    for lr in learning_rates:
        for epochs in epochs_values:

            print(f"Training with {opt} optimizer, Learning Rate: {lr}, Epochs: {epochs}")

            model, history = train_model_with_optimizer(opt, lr, epochs)
            history_results[opt][(lr, epochs)] = history

            # הערכת המודל על סט הבדיקה
            test_loss, test_acc = model.evaluate(test_generator)
            print(f"\nTest Accuracy: {test_acc * 100:.2f}%")

            # חיזוי על Test set
            y_probs = model.predict(test_generator)
            y_pred = (y_probs > 0.5).astype(int)
            y_true = test_generator.classes

            # חישוב והדפסת תוצאות לכל סף מ-0.1 עד 0.9
            thresholds = np.arange(0.1, 0.95, 0.05)
            precision_list = []
            recall_list = []

            plt.figure(figsize=(8, 6))

            for t in thresholds:
                y_pred = (y_probs > t).astype(int)

                precision = precision_score(y_true, y_pred)
                recall = recall_score(y_true, y_pred)
                f1 = f1_score(y_true, y_pred)

                precision_list.append(precision)
                recall_list.append(recall)

                print(
                    f"Threshold {t:.2f} => "
                    f"Precision: {precision:.4f}, "
                    f"Recall: {recall:.4f}, "
                    f"F1 Score: {f1:.4f}"
                )

            # ציור גרף Precision-Recall עם נקודות לכל סף
            plt.plot(
                recall_list,
                precision_list,
                marker='o',
                linestyle='-',
                color='b',
                label='Precision-Recall'
            )

            plt.xlabel('Recall')
            plt.ylabel('Precision')
            plt.title(f'Precision vs Recall for {opt} - LR: {lr}, Epochs: {epochs}')
            plt.legend()
            plt.grid(True)
            plt.show()

            # Loss + Accuracy
            plt.figure(figsize=(12, 6))

            plt.subplot(1, 2, 1)
            plt.plot(history.history['loss'], label='Training Loss')
            plt.plot(history.history['val_loss'], label='Validation Loss')
            plt.title(f'{opt} - LR: {lr}, Epochs: {epochs} - Loss over Epochs')
            plt.xlabel('Epochs')
            plt.ylabel('Loss')
            plt.legend()

            plt.subplot(1, 2, 2)
            plt.plot(history.history['accuracy'], label='Training Accuracy')
            plt.plot(history.history['val_accuracy'], label='Validation Accuracy')
            plt.title(f'{opt} - LR: {lr}, Epochs: {epochs} - Accuracy over Epochs')
            plt.xlabel('Epochs')
            plt.ylabel('Accuracy')
            plt.legend()

            plt.tight_layout()
            plt.show()

[FILE TASK4.py]
import tensorflow as tf
from tensorflow.keras.preprocessing.image import ImageDataGenerator
from tensorflow.keras.layers import Conv2D, MaxPool2D, Flatten, Dense, Dropout, BatchNormalization
from tensorflow.keras.models import Sequential
from tensorflow.keras.callbacks import ReduceLROnPlateau
from sklearn.utils.class_weight import compute_class_weight
from sklearn.metrics import precision_score, recall_score, f1_score
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.metrics import confusion_matrix

from google.colab import drive
drive.mount('/content/drive')

# הגדרת פרמטרים
img_size = 160
batch_size = 10

base_path = "/content/drive/MyDrive/DEEP-LEARNING/chest_xray"

train_path = base_path + "/train"
val_path   = base_path + "/val"
test_path  = base_path + "/test"

# Data Augmentation עבור אימון
train_datagen = ImageDataGenerator(
    rescale=1./255,
    rotation_range=30,
    width_shift_range=0.2,
    height_shift_range=0.2,
    shear_range=0.2,
    zoom_range=0.2,
    horizontal_flip=True,
    fill_mode='nearest'
)

val_test_datagen = ImageDataGenerator(rescale=1./255)

# יצירת מחוללי תמונות (Generators) עם class_mode='categorical'
train_generator = train_datagen.flow_from_directory(
    train_path,
    target_size=(img_size, img_size),
    batch_size=batch_size,
    color_mode='grayscale',
    class_mode='categorical',
    shuffle=True
)

val_generator = val_test_datagen.flow_from_directory(
    val_path,
    target_size=(img_size, img_size),
    batch_size=batch_size,
    color_mode='grayscale',
    class_mode='categorical',
    shuffle=False
)

test_generator = val_test_datagen.flow_from_directory(
    test_path,
    target_size=(img_size, img_size),
    batch_size=batch_size,
    color_mode='grayscale',
    class_mode='categorical',
    shuffle=False
)

# חישוב משקולות למחלקות (Class Weights)
classes = train_generator.classes
class_labels = np.unique(classes)
class_weights = compute_class_weight('balanced', classes=class_labels, y=classes)
class_weights_dict = dict(enumerate(class_weights))

# יצירת מודל CNN עם 3 קטגוריות ו-Softmax
def build_medical_cnn(input_shape=(img_size, img_size, 1), num_classes=3):
    model = Sequential()

    # שכבת קונבולוציה ראשונה
    model.add(Conv2D(32, (4, 4), activation='relu', padding='same', input_shape=input_shape))
    model.add(BatchNormalization())
    model.add(MaxPool2D((2, 2)))

    # שכבת קונבולוציה שניה
    model.add(Conv2D(64, (4, 4), activation='relu', padding='same'))
    model.add(BatchNormalization())
    model.add(MaxPool2D((2, 2)))
    model.add(Dropout(0.3))

    # שכבת קונבולוציה שלישית
    model.add(Conv2D(128, (3, 3), activation='relu', padding='same'))
    model.add(BatchNormalization())
    model.add(MaxPool2D((2, 2)))
    model.add(Dropout(0.4))

    # שכבת קונבולוציה רביעית
    model.add(Conv2D(256, (3, 3), activation='relu', padding='same'))
    model.add(BatchNormalization())
    model.add(MaxPool2D((2, 2)))
    model.add(Dropout(0.5))

    # שכבת קונבולוציה חמישית
    model.add(Conv2D(512, (3, 3), activation='relu', padding='same'))
    model.add(BatchNormalization())
    model.add(MaxPool2D((2, 2)))
    model.add(Dropout(0.5))

    # Flatten ו-Dense
    model.add(Flatten())
    model.add(Dense(512, activation='relu'))
    model.add(Dropout(0.5))

    # שכבת הפלט עם Softmax ל-3 קטגוריות
    model.add(Dense(num_classes, activation='softmax'))

    model.compile(optimizer=tf.keras.optimizers.Adam(learning_rate=0.001),
                  loss='categorical_crossentropy',
                  metrics=['accuracy'])

    return model

# פונקציה לאימון המודל עם פרמטרים שונים
def train_model_with_optimizer(optimizer, lr, epochs, num_classes=3):
    model = build_medical_cnn(num_classes=num_classes)

    if optimizer == 'sgd':
        opt = tf.keras.optimizers.SGD(learning_rate=lr)
    elif optimizer == 'sgd_momentum':
        opt = tf.keras.optimizers.SGD(learning_rate=lr, momentum=0.9)
    elif optimizer == 'adam':
        opt = tf.keras.optimizers.Adam(learning_rate=lr)
    elif optimizer == 'rmsprop':
        opt = tf.keras.optimizers.RMSprop(learning_rate=lr)

    model.compile(optimizer=opt,
                  loss='categorical_crossentropy',
                  metrics=['accuracy'])

    reduce_lr = ReduceLROnPlateau(monitor='val_loss', factor=0.1, patience=2, min_lr=1e-8, verbose=1)

    history = model.fit(
        train_generator,
        epochs=epochs,
        validation_data=val_generator,
        class_weight=class_weights_dict,
        callbacks=[reduce_lr]
    )
    return model, history

# הגדרת ערכים של Learning Rate ו-Epochs לבדוק
learning_rates = [0.001, 0.0001]
epochs_values = [15 , 25]

# מילון לשמירת התוצאות
history_results = {}

# אופטימיזרים
optimizers = ['adam','sgd_momentum','rmsprop','sgd']

# לולאה עבור כל אופטימיזר, Learning Rate ו-Epochs
for opt in optimizers:
    history_results[opt] = {}
    for lr in learning_rates:
        for epochs in epochs_values:
            print(f"Training with {opt} optimizer, Learning Rate: {lr}, Epochs: {epochs}")
            model, history = train_model_with_optimizer(opt, lr, epochs)

            # הערכת המודל על סט הבדיקה
            test_loss, test_acc = model.evaluate(test_generator)
            print(f"\nTest Accuracy: {test_acc * 100:.2f}%")

            # חיזוי על ה-Validation set
            y_probs = model.predict(test_generator)
            y_pred = np.argmax(y_probs, axis=1)
            y_true = test_generator.classes

            # חישוב Precision, Recall, F1 לכל קטגוריה
            precision = precision_score(y_true, y_pred, average='weighted')
            recall = recall_score(y_true, y_pred, average='weighted')
            f1 = f1_score(y_true, y_pred, average='weighted')

            print(f"Precision: {precision:.4f}, Recall: {recall:.4f}, F1 Score: {f1:.4f}")

            cm = confusion_matrix(y_true, y_pred)

            # הצגת ה-Confusion Matrix בצורה גרפית
            plt.figure(figsize=(8, 6))
            sns.heatmap(
                cm,
                annot=True,
                fmt='d',
                cmap='Blues',
                xticklabels=test_generator.class_indices.keys(),
                yticklabels=test_generator.class_indices.keys()
            )
            plt.xlabel('Predicted Label')
            plt.ylabel('True Label')
            plt.title('Confusion Matrix')
            plt.show()

            # ציור גרפים של Train Loss, Validation Loss, Train Accuracy, Validation Accuracy
            plt.figure(figsize=(12, 6))

            # גרף Loss
            plt.subplot(1, 2, 1)
            plt.plot(history.history['loss'], label='Training Loss')
            plt.plot(history.history['val_loss'], label='Validation Loss')
            plt.title('Loss over Epochs')
            plt.xlabel('Epochs')
            plt.ylabel('Loss')
            plt.legend()

            # גרף Accuracy
            plt.subplot(1, 2, 2)
            plt.plot(history.history['accuracy'], label='Training Accuracy')
            plt.plot(history.history['val_accuracy'], label='Validation Accuracy')
            plt.title('Accuracy over Epochs')
            plt.xlabel('Epochs')
            plt.ylabel('Accuracy')
            plt.legend()

            plt.tight_layout()
            plt.show()
