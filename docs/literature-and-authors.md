# Literature And Authors From Dudnyk Dissertation

Source analyzed: `Дисертація.docx` from Google Drive folder `Дудник-Дисертація-Рельєфне-Текстурування`.

Dissertation:

- Author: Олександр Олександрович Дудник / Oleksandr O. Dudnyk.
- Institution: Vinnytsia National Technical University, Ukraine.
- Year: 2018.
- Topic: methods and tools for increasing realism and productivity of texture mapping in computer graphics systems.
- Keywords from dissertation: texturing, texture mapping, texture filtering, anisotropic filtering, perspective-correct texturing, relief texturing, parallax mapping.

Note on countries: the country/context column below is inferred from publication venue, publisher, institution, or widely known affiliation when it is evident from the reference. It is not a verified nationality/origin claim. Treat entries marked `verify` as placeholders for later literature cleanup.

## Main Research Direction Of The Dissertation

The dissertation is strongly connected to texture filtering and performance, with a smaller but important part on relief texturing and parallax mapping.

Main technical themes:

- perspective-correct texture mapping;
- anisotropic texture filtering;
- pixel footprint models, especially Gaussian/elliptical models;
- acceleration through cached/precomputed texture maps;
- parallax mapping combined with anisotropic filtering;
- modified distance-map approach based on Donnelly's method;
- OpenGL/GPU shader implementation.

The most relevant overlap with this project is the part where Dudnyk studies artifacts caused by combining parallax mapping with anisotropic filtering and proposes a modified distance map that accounts for texel visibility.

## Literature Clusters

| Cluster | References | Why It Matters |
| --- | --- | --- |
| Core texture mapping | 60, 70, 74, 76-79 | Classic foundation for texture mapping, mipmapping, anisotropic filtering, and EWA filtering. |
| Relief/parallax mapping | 80-93 | Directly relevant to relief texturing, parallax mapping, POM, cone mapping, and distance mapping. |
| GPU/rendering pipeline | 3, 49, 52, 56, 58, 103, 106, 115-125, 130-133 | Background on programmable graphics pipelines, shaders, OpenGL, DirectX, Vulkan, and GPU architecture. |
| Dudnyk/Romanyuk local work | 11-44 | Dissertation author's own research line, mostly anisotropic filtering, parallax mapping, distance maps, and performance. |
| Image quality/statistics | 99-102 | Used for evaluating image quality or expert agreement. |
| Compression/data representation | 134-138 | Used for texture/data storage context. |

## Key Authors For This Project

| Author(s) | Country/context | Dissertation refs | Topic |
| --- | --- | --- | --- |
| Paul S. Heckbert | USA, classic computer graphics research | 60, 76 | Texture mapping survey, EWA filtering. |
| Lance Williams | USA, SIGGRAPH | 70 | Mipmapping / pyramidal parametrics. |
| Ned Greene, Paul Heckbert | USA | 76 | Elliptical weighted average filtering. |
| J. McCormack, R. Perry, K. I. Farkas, N. P. Jouppi | USA, Compaq/HP research context | 74 | FELINE anisotropic texture filtering. |
| Natalya Tatarchuk | USA/AMD graphics context, Ukrainian-born background should be verified before use | 3, 85, 91 | Parallax Occlusion Mapping, dynamic POM, soft shadows. |
| William Donnelly | USA/NVIDIA GPU Gems context | 93 | Per-pixel displacement mapping with distance functions. |
| Jonathan Dummer | verify; original paper hosted via lonesock.net/Scribd mirrors | added-1 | Cone Step Mapping. |
| Fabio Policarpo, Manuel M. Oliveira | Brazil, UFRGS computer graphics context | added-2 | Relaxed Cone Stepping, relief mapping. |
| Terry Welsh | USA/Infiscape context, verify | 88 | Parallax mapping with offset limiting. |
| Morgan McGuire | USA/Canada academic and game graphics context, verify | 89 | Steep parallax mapping. |
| Yu-Jen Chen, Yung-Yu Chuang | Taiwan, National Taiwan University context, verify | 92 | Anisotropic cone mapping. |
| K. Kosin | Thailand context from case-study location, verify author affiliation | 84 | POM in architectural heritage / augmented reality case study. |
| K. Dmitriev, E. Makarov | Russia or Eastern Europe context, verify | 86 | Generating displacement from normal maps. |
| M. Lundgren, E. Hrkalovic | Sweden, Blekinge Tekniska Hogskola context | 80 | Review of displacement mapping techniques. |
| P. Mavridis, G. Papaioannou | Greece, Athens University context, verify | 77 | High quality elliptical texture filtering on GPU. |
| Markus Zwicker et al. | Switzerland/USA mixed context, verify per author | 78 | EWA splatting. |
| L. Ren et al. | USA/China mixed context, verify per author | 79 | Object-space EWA surface splatting. |
| Michael Bailey, Steve Cunningham | USA academic context | 58 | Shader theory and practice. |
| Mark Pharr, Randima Fernando | USA/NVIDIA graphics context | 106 | GPU Gems 2. |
| Eric Lengyel | USA/game engine math context | 113 | Mathematics for 3D game programming. |
| Oleksandr O. Dudnyk | Ukraine, VNTU | 11, 13-25, 28-44 | Dissertation author; anisotropic filtering, parallax mapping, distance maps. |
| Oleksandr N. Romanyuk | Ukraine, VNTU | many local refs | Dissertation supervisor/coauthor; computer graphics, rendering, texture filtering. |
| Serhiy I. Vyatkin | Ukraine/Russia context, verify | 27, 31, 33, 39 | GPU architecture, scalar perturbation functions, anisotropic filtering. |

## Most Relevant Sources For Relief Texturing And Parallax Mapping

These should be read first for this project's topic.

| Ref | Source | Relevance |
| --- | --- | --- |
| 80 | M. Lundgren, E. Hrkalovic, `Review of Displacement Mapping Techniques and Optimization`, 2012 | Survey-style entry point into displacement and relief techniques. |
| 84 | K. Kosin, `Parallax Occlusion Mapping in Augmented Reality Case Study...`, 2015 | Applied POM case study. Less central for Unity Desktop, but useful for seeing POM in a practical scene. |
| 85 | N. Tatarchuk, `Dynamic Parallax Occlusion Mapping with Approximate Soft Shadows`, 2006 | Core POM reference. Highly relevant. |
| 86 | K. Dmitriev, E. Makarov, `Generating Displacement from Normal Map for Use in 3D Games`, 2011 | Relevant to converting normal information into displacement/height-like data. |
| 88 | T. Welsh, `Parallax mapping with offset limiting`, 2004 | Important basic parallax mapping variant. |
| 89 | M. McGuire, `Steep parallax mapping`, 2005 | Important bridge between basic parallax and POM/ray marching. |
| 91 | N. Tatarchuk, `Practical Dynamic Parallax Occlusion Mapping`, 2005 | Practical POM implementation reference. Highly relevant. |
| 92 | Yu-Jen Chen, Yung-Yu Chuang, `Anisotropic cone mapping`, 2009 | Relevant to cone-step style acceleration and directional approximations. |
| 93 | W. Donnelly, `Per-pixel displacement mapping with distance functions`, GPU Gems 2, 2005 | Directly relevant to distance-map acceleration and this project's RGBA/directional-distance idea. |
| added-1 | Jonathan Dummer, `Cone Step Mapping: An Iterative Ray-Heightfield Intersection Algorithm`, 2006 | Original cone step mapping paper. Important for understanding conservative cone maps and safe step computation. |
| added-2 | Fabio Policarpo, Manuel M. Oliveira, `Relaxed Cone Stepping for Relief Mapping`, GPU Gems 3, Chapter 18, 2007 | Core reference for relaxed cone maps: wider cones plus binary search refinement for relief mapping. |
| 23 | Romanyuk, Dudnyk, `Особливості анізотропної фільтрації текстур при використанні технології parallax mapping`, 2017 | Local work on parallax mapping plus anisotropic filtering artifacts. |
| 24 | Romanyuk, Dudnyk, Romanyuk, `Модифікований метод parallax mapping з використанням карти відстаней до поверхні`, 2017 | Very relevant to distance-map modification. |
| 25 | Romanyuk, Dudnyk, `Використання модифікованої мір-піраміди для підвищення продуктивності parallax mapping`, 2018 | Relevant to mip/pyramid acceleration for parallax mapping. |
| 40 | Dudnyk, `Аналіз методів рельєфного текстурування`, 2017 | Likely useful local overview of relief texturing methods. |
| 44 | Dudnyk, copyright registration for distance-map generation from height maps with visibility | Indicates tooling/precomputation direction similar to this project's baked-data idea. |

## Authors To Investigate Further

For parallax/relief texturing:

- Natalya Tatarchuk: POM, dynamic POM, approximate soft shadows.
- William Donnelly: distance functions for per-pixel displacement.
- Jonathan Dummer: cone step mapping.
- Fabio Policarpo and Manuel M. Oliveira: relief mapping and relaxed cone stepping.
- Terry Welsh: offset-limited parallax mapping.
- Morgan McGuire: steep parallax mapping.
- Yu-Jen Chen and Yung-Yu Chuang: anisotropic cone mapping.
- Oleksandr Dudnyk and Oleksandr Romanyuk: parallax mapping with distance maps and anisotropic filtering.

For filtering and sampling:

- Paul Heckbert: texture mapping survey and EWA foundations.
- Lance Williams: mipmapping.
- Ned Greene and Paul Heckbert: EWA filtering.
- J. McCormack, R. Perry, K. I. Farkas, N. P. Jouppi: FELINE anisotropic filtering.
- P. Mavridis and G. Papaioannou: GPU elliptical texture filtering.

## Complete Extracted Bibliography

1. Е. Петровичев, `Компьютерная графика`. Litres, 2017.
2. Д. В. Щегрикович, `Компьютерная графика`. № УД-1709/уч. 2016.
3. N. Tatarchuk, `Evolution of Programmable Models for Graphics Engines`, High Performance Graphics, 2017.
4. C. Pang, A. Hindle, B. Adams, and A. E. Hassan, `What Do Programmers Know about Software Energy Consumption?`, IEEE Software, vol. 33, no. 3, pp. 83-89, 2016.
5. І. В. Ільїна, О. В. Біжко, `Аналіз особливостей візуалізації тривимірних об'єктів`, Системи управління, навігації та зв'язку, вип. 2, c. 88-92, 2016.
6. E. Agu, `Lecture 2: Advanced Computer Graphics Part 2: Texturing`, Computer Graphics (CS 563), 2016.
7. Д. Вольф, `OpenGL 4. Язык шейдеров. Книга рецептов`. ДМК Пресс, 368 с., 2015.
8. J. Mcdonald and B. Burley, `Per-face texture mapping for real-time rendering`, ACM SIGGRAPH 2011 Studio Talks, 2011.
9. S. Gustavson, `Procedural Textures in GLSL`, OpenGL Insights, pp. 105-120, 2012.
10. И. М. Лебедева, `О некоторых проблемах текстурирования зображений`, Вестник МГСУ, с. 4-5, 2010.
11. О. Н. Романюк, І. В. Абрамчук, О. О. Дудник, `Анізотропна фільтрація з використанням вагової функції на основі Гаусівської моделі`, Вимірювальна та обчислювальна техніка в технологічних процесах, № 2, с. 117-121, 2016.
12. О. Н. Романюк, І. В. Абрамчук, О. О. Дудник, О. В. Мельник, `Модифікація гаусівської моделі пікселя для задач антиаліайзингу`, Наукові праці ДонНТУ, № 1(20), с. 84-88, 2015.
13. О. Н. Романюк, О. О. Дудник, `Розробка методів текстурування для задач фотореалістичного рендерингу`, Матеріали сьомої міжнародної науково-технічної конференції `Моделювання і комп'ютерна графіка`, с. 26-33, 2017.
14. О. Н. Романюк, О. О. Дудник, `Підвищення реалістичності зафарбовування тривимірних графічних об'єктів`, Вісник ХНТУ, № 3(58), с. 269-272, 2016.
15. О. Н. Романюк, О. О. Дудник, `Анізотропна фільтрація з використанням текстурних карт вагових коефіцієнтів`, Реєстрація, зберігання і обробка даних, № 3, c. 34-41, 2017.
16. С. О. Романюк, О. О. Дудник, Л. А. Савицька, О. В. Романюк, `Анізотропна фільтрація з використанням вагових функцій`, Вісник Херсонського національного технічного університету, № 3, c. 459-462, 2015.
17. О. Н. Романюк, О. О. Дудник, `Метод підвищення продуктивності перспективно-коректного текстурування`, Наукові праці ДонНТУ, № 1(22), c. 43-46, 2016.
18. A. N. Romanyuk and O. O. Dudnyk, `Ways to improve performance of anisotropic texture filtering`, SIBCON, IEEE, 2017.
19. О. Н. Романюк, О. О. Дудник, `Підвищення продуктивності перспективно-коректного текстурування з використанням анізотропної фільтрації`, Вимірювальна та обчислювальна техніка в технологічних процесах, № 3, с. 192-195, 2016.
20. О. Н. Романюк, О. О. Дудник, `Анізотропна фільтрація текстур з використанням методів кешування`, Вісник Вінницького політехнічного інституту, № 6, с. 59-64, 2016.
21. О. Н. Романюк, О. О. Дудник, `Підвищення продуктивності текстурування з виконанням процедурних операцій в об'єктному просторі`, Наукові праці ДонНТУ, № 2(23), c. 45-51, 2016.
22. О. Н. Романюк, О. О. Дудник, Н. С. Костюкова, `Реалізація альтернативного конвеєра рендерингу на GPU з використанням обчислювальних шейдерів`, Наукові праці ДонНТУ, 2017.
23. О. Н. Романюк, О. О. Дудник, `Особливості анізотропної фільтрації текстур при використанні технології parallax mapping`, Вісник Хмельницького національного університету, № 1(245), c. 236-245, 2017.
24. О. Н. Романюк, О. О. Дудник, О. В. Романюк, `Модифікований метод parallax mapping з використанням карти відстаней до поверхні`, Інформаційні технології та комп'ютерна інженерія, № 1, c. 78-82, 2017.
25. О. Н. Романюк, О. О. Дудник, `Використання модифікованої мір-піраміди для підвищення продуктивності parallax mapping`, Вісник Вінницького політехнічного інституту, № 1, с. 112-116, 2018.
26. О. Н. Романюк, О. О. Дудник, `Еволюція конвеєра рендерингу в відеокартах`, Електронні інформаційні ресурси: створення, використання, доступ, с. 440-448, 2016.
27. S. I. Vyatkin, S. A. Romanyuk, S. V. Pavlov and O. O. Dudnyk, `Function-based GPU architecture`, Measuring and Computing Equipment in Technological Processes, № 1, pp. 139-144, 2015.
28. О. О. Дудник, О. Н. Романюк, `Аналіз методів фільтрації текстур`, МТН-2015, Вінниця, 2015.
29. О. Н. Романюк, О. О. Дудник, `Модифікація білінійного текстурування з використнням кругової моделі пікселя`, Вимірювальна та обчислювальна техніка в технологічних процесах, № 1, c. 243-245, 2016.
30. О. Н. Романюк, О. О. Дудник, `Математичні моделі Пікселя`, Електронні інформаційні ресурси в освіті і науці, Вінниця, c. 3-8, 2014.
31. С. И. Вяткин, А. Н. Романюк, А. А. Дудник, `Анизотропная фильтрация текстуры в реальном времени`, Измерительная и вычислительная техника в технологических процесах, № 4, c. 217-221, 2015.
32. О. Н. Романюк, О. О. Дудник, `Аналіз методів анізотропної фільтрації текстур`, Електронні інформаційні ресурси в освіті і науці, Вінниця, c. 3-8, 2014.
33. О. Н. Романюк, О. О. Дудник, С. В. Вяткін, `Шляхи підвищення продуктивності анізотропної фільтрації`, МТН-2016, Вінниця, 2016.
34. О. Н. Романюк, О. О. Дудник, комп'ютерна програма `Визначення кольору пікселя з використанням кругової моделі`, свідоцтво №66660, Україна, 15.07.16.
35. О. Н. Романюк, О. О. Дудник, комп'ютерна програма `Обчислення об'єму перетину пікселя`, свідоцтво №61823, Україна, 25.09.15.
36. О. Н. Романюк, О. О. Дудник, комп'ютерна програма `Система експертного оцінювання сформованого зображення по відношенню до еталону`, свідоцтво №66659, Україна, 15.07.16.
37. О. Н. Романюк, О. О. Дудник, Б. Л. Войт, комп'ютерна програма `Рендеринг тривимірних зображень із використанням процедурних операцій в об'єктному просторі`, свідоцтво №71796, Україна, 05.05.17.
38. О. Н. Романюк, О. О. Дудник, О. В. Мельник, `Неортогональна растеризація при перспективнокоректному текстуруванні`, Моделирование и компьютерная графика, c. 174-178, 2015.
39. S. I. Vyatkin, S. A. Romanyuk, O. O. Dudnyk, `Geometric modeling with scalar perturbation functions`, Measuring and Computing Equipment in Technological Processes, № 4, pp. 45-50, 2014.
40. О. О. Дудник, `Аналіз методів рельєфного текстурування`, Електронні інформаційні ресурси: створення, використання, доступ, Вінниця, 2017.
41. О. О. Дудник, комп'ютерна програма `Генерація вагових текстурних карт`, свідоцтво №78246, Україна, 12.04.18.
42. О. О. Дудник, комп'ютерна програма `Анізотропна фільтрація текстур з використанням вагової функції на основі гаусівської моделі пікселя`, свідоцтво №78247, Україна, 12.04.18.
43. О. О. Дудник, комп'ютерна програма `Анізотропна фільтрація текстур з використанням вагових текстурних карт`, свідоцтво №78249, Україна, 12.04.18.
44. О. О. Дудник, комп'ютерна програма `Генерація текстурних карт відстаней до поверхні на основі карт висот з урахуванням видимості точок поверхні`, свідоцтво №78248, Україна, 12.04.18.
45. B. G. Blundell, `An Introduction to Computer Graphics and Creative 3-D Environments`, Springer, 2008.
46. Дж. Фоли, А. Вэн Дэм, `Основы интерактивной машинной графики`, М.: Мир, 1995.
47. А. Игнатенко, `Методы представления дискретных трехмерных даннях`, Компьютерная графика и мультимедиа, №1(1), 2003.
48. Ágnecz-Roland, Norbert Zsolt Zentai-Gergely, Takács-Sándor Kaczur, `Hardware accelerated 3D/2D rendering`, Journal of Applied Multimedia, 2013.
49. H. Bao and W. Hua, `Architecture of Real-Time Rendering Engine`, Advanced Topics in Science and Technology in China, 2011.
50. Д. И. Мазовка, `Формальный подход к решению задачи визуализации`, Международный конгресс по информатике, Минск, 2011.
51. C. Doppioslash, `The Graphics Pipeline`, Physically Based Shader Development for Unity 2017, pp. 33-42, 2017.
52. S. Laine and T. Karras, `High-performance software rasterization on GPUs`, HPG 2011.
53. А. В. Боресков, А. А. Харламов, `Архитектура и программирование массивно-параллельных вычислительных систем`.
54. К. В. Снопов, О. Н. Романюк, `Використання графічних конвеєрів для візуалізації тривирмірних моделей`, МТН-2015.
55. О. Н. Романюк, М. Д. Обідник, О. В. Романюк, Н. С. Костюкова, `Особливості архітектурної побудови систем формування тривимірних зображень`, Наукові праці ДонНТУ, 2010.
56. C. Mcclanahan, `History and evolution of GPU architecture`, 2010.
57. А. В. Орещенко, `Апаратне забезпечення для тривимірної графіки: причини становлення і занепаду фірм-виробників`, Часопис картографії, 2013.
58. M. Bailey and S. Cunningham, `Graphics Shaders: Theory and Practice`, CRC Press, 2016.
59. Ф. Хилл, `OpenGL. Программирование компьютерной графики. Для профессионалов`, СПб.: Питер, 2002.
60. P. S. Heckbert, `Survey of Texture Mapping`, IEEE Computer Graphics and Applications, vol. 6, no. 11, pp. 56-67, 1986.
61. А. Ю. Поляков, В. А. Брусенцов, `Методы и алгоритмы компьютерной графики`, СПб.: БХВ-Петербург, 2003.
62. T. P. Kersten and D. Stallmann, `Automatic Texture Mapping Of Architectural And Archaeological 3D Models`, ISPRS Archives, 2012.
63. С. И. Вяткин, С. А. Романюк, С. О. Крищук, `Метод вычисления текстурных координат для отображения текстуры на плоские полигоны`, 2012.
64. Д. Роджерс, `Алгоритмические основы машинной графики`, Мир, Москва, 1989.
65. Д. Роджерс, `Математические основы машинной графики`, Мир, Москва, 2001.
66. А. М. Данилов, И. А. Гарькина, `Интерполяция, аппроксимация, оптимизация: анализ и синтез сложных систем`, 2014.
67. Е. Янке, Ф. Эмде, Ф. Леш, `Специальные функции: Формулы, графики, таблицы`, Directmedia, 2016.
68. Д. С. Яковлев, М. Н. Фаворская, `Технологии фильтрации текстур`, 2011.
69. А. В. Белоконь, А. В. Проскурин, М. Н. Фаворская, `Классификация методов синтеза текстур`, 2011.
70. L. Williams, `Pyramidal Parametrics`, SIGGRAPH 1983.
71. Р. Гонсалес, Р. Вудс, `Цифровая обработка зображений`, М.: Техносфера, 2005.
72. X. U. Ying, `An Improved Texture Rendering Technique Based on MipMap Algorithm`, Journal of Mianyang Normal University, 2013.
73. W. Matusik, `Sampling, Aliasing, & Mipmaps`, MIT OpenCourseWare 6.837, 2012.
74. J. McCormack, R. Perry, K. I. Farkas, N. P. Jouppi, `Feline: fast elliptical lines for anisotropic texture mapping`, SIGGRAPH 1999.
75. В. М. Гусятин, Я. В. Чаговец, Д. Г. Кожушко, `Метод анизотропной фильтрации текстур при синтезе изображений обратным трассированием`, ДонНТУ, 2009.
76. N. Greene and P. Heckbert, `Creating Raster Omnimax Images from Multiple Perspective Views Using the Elliptical Weighted Average Filter`, IEEE CG&A, 1986.
77. P. Mavridis and G. Papaioannou, `High Quality Elliptical Texture Filtering on GPU`, I3D 2011.
78. M. Zwicker et al., `EWA Splatting`, IEEE TVCG, vol. 8, no. 3, 2002.
79. L. Ren et al., `Object Space EWA Surface Splatting: A Hardware Accelerated Approach to High Quality Point Rendering`, Computer Graphics Forum, 2002.
80. M. Lundgren, E. Hrkalovic, `Review of Displacement Mapping Techniques and Optimization`, Blekinge Tekniska Hogskola, 2012.
81. S. Marschner, `Detail mapping`, CS562, 2016.
82. A. Tujula et al., `Lighting and normal mapping in computer graphics: implementing normal mapping in HactEngine`, 2016.
83. J. Hanyoung and J. Han, `Feature-Preserving Displacement Mapping With GPU Tessellation`, Computer Graphics Forum, 2012.
84. K. Kosin, `Parallax Occlusion Mapping in Augmented Reality Case Study on Facade of Sino Portuguese Architecture Phuket, Thailand`, Digital Heritage, 2015.
85. N. Tatarchuk, `Dynamic Parallax Occlusion Mapping with Approximate Soft Shadows`, SI3D, 2006.
86. K. Dmitriev and E. Makarov, `Generating Displacement from Normal Map for Use in 3D Games`, SIGGRAPH Talks, 2011.
87. C. González, M. Pérez, J. M. Orduña, `A hybrid GPU technique for real-time terrain visualization`, CMMSE, 2016.
88. T. Welsh et al., `Parallax mapping with offset limiting: A per-pixel approximation of uneven surfaces`, Infiscape Corporation, 2004.
89. M. McGuire, `Steep parallax mapping`, I3D 2005 Poster, 2005.
90. С. Дасгупта, Х. Пападимитриу, У. Вазирани, `Алгоритмы`, М.: МЦНМО, 2014.
91. N. Tatarchuk, `Practical Dynamic Parallax Occlusion Mapping`, SIGGRAPH 2005 Sketches.
92. Yu-Jen Chen, Yung-Yu Chuang, `Anisotropic cone mapping`, APSIPA ASC, 2009.
93. W. Donnelly, `Per-pixel displacement mapping with distance functions`, GPU Gems 2, 2005.
94. К. С. Солнушкин, `О значении терминов "производительность" и "быстродействие" в применении к ЭВМ`, 2008.
95. I. V. Kerlow, `The Art of 3D: Computer Animation and Effects`, John Wiley & Sons, 2004.
96. P. Demorest, `GPU benchmarking`, 2010.
97. `Монітори`, Hotline.ua.
98. A. Watt and F. Policarpo, `3D Games: Real-Time Rendering and Software Technology`, Addison Wesley, 2000.
99. М. Д. Обідник, А. О. Стахов, `Аналіз методів оцінки якості графічних зображень`, 2011.
100. Ю. И. Монич, В. В. Старовойтов, `Оценки качества для анализа цифровых зображений`, ОИПИ НАН Беларуси, Минск, 2008.
101. `Коэффициент конкордации или согласия Кендалла`, Mathmetod.
102. В. І. Жлуктенко, С. І. Наконечний, `Теорія ймовірностей і математична статистика`, К.: ІЗМН, 1997.
103. R. F. Lyon, `Phong Shading Reformulation for Hardware Renderer Simplification`, Apple Technical Report #43, 1993.
104. Д. А. Кулагин, `Модели затенения. Плоская модель. Затенение по Гуро и Фонгу`.
105. Д. Херн, М. П. Бейкер, `Компьютерная графика и стандарт OpenGL`, 3-е изд., Вильямс, 2005.
106. M. Pharr and R. Fernando, `GPU Gems 2`, Addison-Wesley Professional, 2005.
107. О. Н. Романюк, `Комп'ютерна графіка: навч. посіб.`, Вінниця: ВДТУ, 2001.
108. О. В. Романюк, В. В. Войтко, `Використання барицентричних координат для розрахунку векторів у довільній точці трикутника`, 2009.
109. C. Lomont, `Fast inverse square root`, Technical Report, 2003.
110. О. Н. Романюк, А. В. Чорний, `Високопродуктивні методи та засоби зафарбовування тривимірних графічних об'єктів`, Вінниця, 2006.
111. Ю. Н. Косников, `Геометрические преобразования в компьютерной графике`, Пенза, 2011.
112. Д. А. Кулагин, `Аффинные преобразования пространства`.
113. E. Lengyel, `Mathematics for 3D Game Programming and Computer Graphics`, Cengage Learning, 2012.
114. Д. А. Кулагин, `Векторы в пространстве. Однородные координаты. Матрицы преобразований`.
115. J. Kessenich, D. Baldwin, R. Rost, `The OpenGL Shading Language Version 4.30`, Khronos Group, 2013.
116. K. Gray, `Microsoft DirectX 9. Programmable Graphics Pipeline`, Microsoft Press, 2003.
117. W. Engel, `GPU Pro 5: Advanced Rendering Techniques`, CRC Press, 2014.
118. R. Marroquim and A. Maximo, `Introduction to GPU Programming with GLSL`, SIBGRAPI Tutorials, 2009.
119. R. Madsen and S. Madsen, `OpenGL Game Development By Example`, Packt, 2016.
120. M. Bailey, `OpenGL Compute Shaders`, Oregon State University, 2016.
121. J. Darby, `Beginning OpenGL Game Programming`, Cengage Learning, 2014.
122. P. Eimandar, `DirectX 11.1 Game Programming`, Packt, 2013.
123. F. Luna, `Introduction to 3D Game Programming with DirectX 11`, Mercury Learning & Information, 2012.
124. `Direct3D 11 Graphics`, Microsoft documentation.
125. The Khronos Vulkan Working Group, `Vulkan 1.0.66 - A Specification`, Khronos Group, 2017.
126. B. Stroustrup, `The C++ Programming Language`, 4th ed., Addison-Wesley, 2013.
127. Б. Страуструп, `Программирование. Принципы и практика с использованием C++`, 2-е изд., Вильямс, 2016.
128. С. Мейерс, `Эфективный и современный C++`, Вильямс, 2016.
129. R. Smith, `Working Draft, Standard for Programming Language C++ N4659`, Google Inc., 2017.
130. J. Kessenich, D. Baldwin, R. Rost, `The OpenGL Shading Language Version 4.50`, Khronos Group, 2017.
131. J. Kessenich, G. Sellers, D. Shreiner, `OpenGL Programming Guide`, 9th ed., Addison-Wesley, 2017.
132. G. Sellers, R. S. Wright Jr., N. Haemel, `OpenGL SuperBible`, 7th ed., Addison-Wesley, 2015.
133. J. Clevenger and V. Scott Gordon, `Computer Graphics Programming in OpenGL with Java`, Mercury Learning and Information, 2017.
134. В. П. Майданюк, `Кодування та захист інформації`, ВНТУ, Вінниця, 2009.
135. А. М. Пєтух, В. П. Майданюк, О. О. Ліщук, `Аналіз алгоритмів стиснення даних і їх програмних реалізацій`, Інформаційні технології та комп'ютерна інженерія, № 2, c. 4-9, 2016.
136. Y. Jiang et al., `Texture Compression with Variable Data Formats`, IEEE CIT, 2012.
137. Philipp Klaus Krause, `Ftc - Floating Precision Texture Compression`, Computers & Graphics, vol. 34, no. 5, pp. 594-601, 2010.
138. `754-2008 - IEEE Standard for Floating-Point Arithmetic`, IEEE Xplore.

## Added Papers For This Project

These were added after the initial extraction from Dudnyk's dissertation bibliography.

| ID | Paper | Authors | Country/context | Year | Method/topic | Why useful | Link |
| --- | --- | --- | --- | ---: | --- | --- | --- |
| added-1 | `Cone Step Mapping: An Iterative Ray-Heightfield Intersection Algorithm` | Jonathan Dummer | verify | 2006 | Cone Step Mapping | Original CSM method. Explains precomputed cone maps and iterative ray-heightfield stepping using cone ratios. | https://www.scribd.com/document/57896129/Cone-Step-Mapping?v=0.021 |
| added-2 | `Relaxed Cone Stepping for Relief Mapping` | Fabio Policarpo, Manuel M. Oliveira | Brazil, UFRGS context | 2007 | Relaxed Cone Stepping, Relief Mapping | Combines cone-map space leaping with binary refinement. Important comparison point against conservative CSM and Donnelly distance maps. | https://developer.nvidia.com/gpugems/gpugems3/part-iii-rendering/chapter-18-relaxed-cone-stepping-relief-mapping |

## Template For Adding New Papers

Use this table format when adding new computer graphics / parallax mapping papers later.

| Status | Paper | Authors | Country/context | Year | Method/topic | Why useful | Notes |
| --- | --- | --- | --- | ---: | --- | --- | --- |
| to-read |  |  |  |  |  |  |  |
