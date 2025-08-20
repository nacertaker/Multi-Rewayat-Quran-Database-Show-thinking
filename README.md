# Multi-Rewayat Quran Database (قاعدة بيانات القرآن الكريم متعددة الروايات)

## 📜 Overview
This project provides a comprehensive, all-in-one SQLite database for the Holy Quran, designed to be the foundational backend for advanced Quranic applications. Data has been aggregated from various reliable open-source projects and structured to support multiple Rewayat (narrations), audio recitations, full indexes, and ayah-timing data.

This is a community effort. We ask Allah to accept it as a beneficial and ongoing charity.

## ✨ Features

* **Support for 6 Rewayat:** Full Quranic text for Hafs, Warsh, Qaloun, Shu'bah, Al-Douri, and Al-Susi.
* **Custom Fonts:** Each Rewayah is mapped to its specific font for an authentic, print-like display (included in the `/fonts` directory).
* **Tafsir & Translation:** Rewayat Hafs includes Tafsir Al-Muyassar and Saheeh International English translation.
* **Comprehensive Reciter List:** A large list of reciters for each supported Rewayah.
* **Ayah Timings:** Precise start and end timings for each ayah (currently for Hafs reciters) from the MP3Quran.net API, enabling audio-highlighting features.
* **Full Indexes:** Dedicated tables for Surahs, Juzs, and Hizbs, linked by page number for easy navigation.
* **Multiple Formats:** Data is available as a single `SQLite` file for direct use and as `JSON` files for greater flexibility.

---

## 📁 Repository Structure

* `Multi-Rewayat-Quran-Database.db`: The primary SQLite database file.
* `/json_export/`: A directory containing a JSON version of each table in the database.
* `/fonts/`: A directory containing all the necessary Quranic fonts for correct rendering.

---

## 🏛️ Database Schema

The database consists of 12 interconnected tables.

#### 📖 Quranic Text & Custom Fonts

| Table Name | Rewayah | Required Font |
| :--- | :--- | :--- |
| `quran_hafs` | Hafs A'n Assem | `HafsSmart_08.ttf` |
| `quran_warsh` | Warsh A'n Nafi' | `uthmanic_warsh_v21.ttf` |
| `quran_qaloun`| Qaloun A'n Nafi' | `uthmanic_qaloun_v21.ttf` |
| `quran_shuba` | Shu'bah A'n Assem | `uthmanic_shuba_v20.ttf` |
| `quran_douri` | Al-Douri A'n Abi 'Amr| `uthmanic_douri_v20.ttf` |
| `quran_susi` | Al-Susi A'n Abi 'Amr| `uthmanic_sousi_v20.ttf` |

*Note: `quran_hafs` contains additional columns (`translation`, `tafseer`, `aya_text_emlaey`). The Tafsir text should be rendered using its dedicated fonts: `uthman_tn1_ver20.ttf` and `uthman_tn1b_ver20.ttf`.*

#### 🎤 Audio & Recitations

* **`riwayat`**: Central table for Rewayah names and IDs.
* **`reciters`**: A comprehensive list of reciters, each linked to their Rewayah (`riwaya_id`) and containing the audio server URL. The `has_timing` column indicates support for audio highlighting.
* **`audio_timings`**: Ayah timing data for reciters where `has_timing = 1`.

#### 📚 Indexes for Navigation

* **`surahs`**: Information for all 114 Surahs (name, ayah count, type, start page).
* **`juzs`**: Information for all 30 Juzs (Juz number, start page).
* **`hizbs`**: Information for all 60 Hizbs (Hizb number, start page).

---

## 🤝 Contributing

We warmly welcome any contributions aimed at improving this database. If you find any errors, have suggestions for the schema, or wish to add new data (like other Tafsirs, translations, or timing data for new Rewayat), please feel free to open an "Issue" or submit a "Pull Request". May Allah reward you.

---

## 🙏 Sources & Credits

This database was built by aggregating data from several open and community-driven sources. All credit goes to them:

* **Quranic Texts, Fonts & Tafsir Al-Muyassar:** [King Fahd Glorious Quran Printing Complex](https://qurancomplex.gov.sa/) for their invaluable projects providing Quranic texts for various Rewayat and the high-quality fonts to render them, including the specific fonts for Tafsir.
* **Reciter and Audio Timing Data:** [MP3Quran.net API](https://mp3quran.net/api).
* **English Translation:** [QuranEnc.com](https://quranenc.com) for the Saheeh International translation.

This project is licensed under the [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0/). Please mention the sources when using this data in your projects.

<br>
<hr>
<br>

<div dir="rtl" align="right">

## 📜 نظرة عامة

هذا المشروع يوفر قاعدة بيانات SQLite متكاملة وشاملة للقرآن الكريم، مصممة لتكون حجر الأساس لبناء تطبيقات قرآنية متقدمة وحديثة. تم تجميع البيانات من مصادر موثوقة ومفتوحة المصدر، ودمجها في هيكلية منظمة تدعم روايات متعددة، تلاوات صوتية، فهارس كاملة، وبيانات تظليل الآيات.

هذا العمل هو جهد مجتمعي، نرجو من الله أن يتقبله ويكون صدقة جارية.

## ✨ المميزات الرئيسية

* **دعم 6 روايات:** نص قرآني كامل لروايات (حفص، ورش، قالون، شعبة، الدوري، السوسي).
* **خطوط مخصصة:** كل رواية مرتبطة بخطها القرآني الخاص لضمان عرض مطابق للمصحف المطبوع (مرفقة في مجلد `fonts`).
* **تفسير وترجمة:** تحتوي رواية حفص على التفسير الميسر والترجمة الإنجليزية (Saheeh International).
* **قائمة قراء شاملة:** تحتوي على قائمة كبيرة من القراء لكل رواية مدعومة.
* **توقيتات الآيات:** بيانات دقيقة لوقت بداية ونهاية كل آية (لرواية حفص حالياً) من مصدر MP3Quran.net، مما يسمح بميزة تظليل الآيات.
* **فهارس كاملة:** جداول مخصصة لفهارس السور، الأجزاء، والأحزاب مرتبطة بأرقام الصفحات لسهولة التنقل.
* **تنسيق متعدد:** البيانات متاحة بصيغة `SQLite` للاستخدام المباشر، وبصيغة `JSON` لمرونة أكبر.

---

## 📁 هيكل المشروع

* `Multi-Rewayat-Quran-Database.db`: ملف قاعدة البيانات الأساسي بنظام SQLite.
* `/json_export/`: مجلد يحتوي على نسخة JSON من كل جدول في قاعدة البيانات.
* `/fonts/`: مجلد يحتوي على كل الخطوط القرآنية اللازمة لعرض النصوص بشكل صحيح.

---

## 🏛️ هيكلية قاعدة البيانات (Schema)

تتكون قاعدة البيانات من 12 جدولاً مترابطاً.

#### 📖 جداول النص القرآني والخطوط المخصصة

| اسم الجدول | الرواية | الخط المخصص للعرض |
| :--- | :--- | :--- |
| `quran_hafs` | حفص عن عاصم | `HafsSmart_08.ttf` |
| `quran_warsh` | ورش عن نافع | `uthmanic_warsh_v21.ttf` |
| `quran_qaloun`| قالون عن نافع | `uthmanic_qaloun_v21.ttf` |
| `quran_shuba` | شعبة عن عاصم | `uthmanic_shuba_v20.ttf` |
| `quran_douri` | الدوري عن أبي عمرو| `uthmanic_douri_v20.ttf` |
| `quran_susi` | السوسي عن أبي عمرو| `uthmanic_sousi_v20.ttf` |

**ملاحظات هامة:**
* جدول `quran_hafs` يحتوي على أعمدة إضافية (`translation`, `tafseer`, `aya_text_emlaey`).
* نص التفسير (`tafseer`) يجب عرضه بخطوطه المخصصة: `uthman_tn1_ver20.ttf` و `uthman_tn1b_ver20.ttf`.

#### 🎤 جداول الصوتيات

* **`riwayat`**: جدول مركزي لأسماء الروايات وأرقامها التعريفية.
* **`reciters`**: قائمة شاملة بالقراء، كل قارئ مرتبط بروايته (`riwaya_id`) ويحتوي على رابط السيرفر الصوتي. عمود `has_timing` يحدد إذا كان القارئ يدعم التظليل الصوتي.
* **`audio_timings`**: بيانات توقيت الآيات للقراء الداعمين (`has_timing = 1`).

#### 📚 جداول الفهارس

* **`surahs`**: معلومات كل سورة (الاسم، عدد الآيات، مكية/مدنية، صفحة البداية).
* **`juzs`**: معلومات الأجزاء (رقم الجزء، صفحة البداية).
* **`hizbs`**: معلومات الأحزاب (رقم الحزب، صفحة البداية).

---

## 🤝 المساهمة (Contributing)

نرحب ترحيباً حاراً بأي مساهمة تهدف إلى تحسين هذه القاعدة وجعلها أكثر دقة وفائدة. إذا اكتشفت أي خطأ في البيانات، أو كان لديك اقتراح لتحسين الهيكلية، أو ترغب في إضافة بيانات جديدة (مثل تفاسير أو ترجمات أو توقيتات لروايات أخرى)، فلا تتردد في فتح "Issue" أو تقديم "Pull Request". وجزاكم الله خيراً.

---

## 🙏 المصادر والحقوق (Sources & Credits)

تم بناء قاعدة البيانات هذه بالاعتماد على عدة مصادر مفتوحة ومجتمعية، فلهم كل الشكر والتقدير:

* **النصوص القرآنية، الخطوط، والتفسير الميسر:** [مجمع الملك فهد لطباعة المصحف الشريف](https://qurancomplex.gov.sa/) لمشاريعهم القيمة في توفير نصوص القرآن لمختلف الروايات والخطوط عالية الجودة لعرضها، بما في ذلك الخطوط المخصصة للتفسير.
* **بيانات القراء والتوقيتات الصوتية:** [MP3Quran.net API](https://mp3quran.net/api).
* **الترجمة الإنجليزية:** [QuranEnc.com](https://quranenc.com) لترجمة (Saheeh International).

هذا المشروع متاح تحت رخصة [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/). يرجى ذكر المصادر عند استخدام هذه البيانات في مشاريعك.

</div>
