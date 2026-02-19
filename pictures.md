## pictures

<img width="720" alt="treefingers sequence from v2_0_4-preview-5" title="testing version: 2-0-4-preview-5" src="https://github.com/user-attachments/assets/1116a753-455c-4a8e-a016-5a2bd5c71a2c" />
<img width="720" title="treefingers  2_0_5 locator test" src="https://github.com/user-attachments/assets/6a2854bc-78d2-4187-830d-5049c3ae7e06" />

<img width="300" title="treefingers  2_0_4 preview-9 a: a sketch for style editor" src="https://github.com/user-attachments/assets/ded6e98d-b842-45b4-85b4-c1c51b70afba" /> <img width="300" title="treefingers  2_0_4 preview-9 b: scaling test, animation test. (last frame)" src="https://github.com/user-attachments/assets/400253ba-849b-416d-9c4d-a632856c3951" />


---

#### pictures: old font vs new font

old demo script had multiple issues with the font because i was trying to tie glyphs' strokes to some "magic numbers" to make the font looking "cohesive" | now i have moved away from that layout, even though certain combinations of glyphs were looking really chill; here is my new improved font
:-: | :-:
<img width="450" title="old demo script's font" src="https://user-images.githubusercontent.com/98284211/167231096-d6b4b19e-d460-42dd-946e-767da28a84f3.svg" alt="treefingers high contrast A4" /> | <img width="450" alt="treefingers  2_0_3 A4" title="my new improved font" src="https://github.com/user-attachments/assets/6c386da2-fae5-48f0-bec3-773606b9f629" />

## ISSUES
  - [ ] the animation blinks (on repeated elements, because they are erased between two consecutive frames) <img alt="updated script`s output B4" title="treefingers (v2_0_3, B4)" src="https://github.com/user-attachments/assets/7fcef47a-6244-4efb-8059-a58dfb6e0523" width="400" />
  - [x] the global scaling is supposed to be no less than `5`, but it results in the image size of `2665x3769 pixels`, which is not suitable for small screens (or may cause performance hits on embedded platforms); but setting the scaling to the least value which is still sane, the value of `3`, results in ugly inconsistent scaling of glyphs (yet the image size is `1599x2261 pixels`). so i need to turn off the rounding: either completely or for small scaling values specifically, or alternatively (bad idea) to accept the scaling factor inconsistency. [SOLVED] by reverting to using floats; also improved functionality for the scaling (adding a dialogue; syncing `iPenMark` to the new global scaling paradigm). tested for the tiny screens: `1@{533x754 pixels}`; `.5@{267x377 pixels}`; `.25@{133x188 pixels}`. <ins>the legend for the images: first value is `cryptic {minor member bloom, major member bloom, major member, minor member, letter}`, second one is actual `$zoomValue`</ins>

<img width="600" title="treefingers  2_0_5 small screen scaling issues a" src="https://github.com/user-attachments/assets/f5a2fd17-a3b4-4d28-b4e1-8b4ea694191c" />
<img width="600" title="treefingers  2_0_5 small screen scaling issues b" src="https://github.com/user-attachments/assets/f515f8ca-4ab4-4591-9b28-af89096fcb82" />
<img width="600" title="treefingers  2_0_5 small screen scaling  floats c" src="https://github.com/user-attachments/assets/79e17f92-c9bb-4d75-abce-caef9cf20b97" />
<img width="600" title="treefingers  2_0_5 small screen scaling  floats d" src="https://github.com/user-attachments/assets/0cb5f39f-31bd-4fc2-8a1e-18988838a6f6" />
<img width="600" title="treefingers  2_0_5 small screen scaling  floats2 e" src="https://github.com/user-attachments/assets/6de2823b-5e76-4874-8405-21507e29bce2" />
<img width="600" title="treefingers  2_0_5 small screen scaling  floats2 f" src="https://github.com/user-attachments/assets/9011e2a8-32bf-4304-9ca5-897e9c503224" />
<img width="600" title="treefingers  2_0_5 small screen scaling  floats1 g" src="https://github.com/user-attachments/assets/91fafb4b-c9c4-45f1-bc8d-e641a3fabf5b" />
<img width="600" title="treefingers  2_0_5 small screen scaling  floats1 h" src="https://github.com/user-attachments/assets/a262c1da-9709-44ac-812c-8a75cb50adb3" />
<img width="600" title="treefingers  2_0_5 small screen scaling  floats.5 i" src="https://github.com/user-attachments/assets/c7003f37-d211-4b4e-b4af-aa31aa72799c" />
<img width="600" title="treefingers  2_0_5 small screen scaling  floats.5 k" src="https://github.com/user-attachments/assets/7dc4bf06-5493-45dd-acb4-a501410b2a20" />
<img width="600" title="treefingers  2_0_5 small screen scaling  floats.25 l" src="https://github.com/user-attachments/assets/e4f62cfa-d6de-4b32-a71f-785b1425772f" />
<img width="600" title="treefingers  2_0_5 small screen scaling  floats.25 m" src="https://github.com/user-attachments/assets/a952b603-cb8b-4eb9-aa4a-fccdb5b6c240" />

and here are small sheets again, now at their actual size

<img width="533" height="754" title="treefingers  2_0_5 small screen scaling  floats1 g; {533x754 pixels}" src="https://github.com/user-attachments/assets/91fafb4b-c9c4-45f1-bc8d-e641a3fabf5b" />
<img width="533" height="754" title="treefingers  2_0_5 small screen scaling  floats1 h; {533x754 pixels}" src="https://github.com/user-attachments/assets/a262c1da-9709-44ac-812c-8a75cb50adb3" />

..

<img width="267" height="377" title="treefingers  2_0_5 small screen scaling  floats.5 i; {267x377 pixels}" src="https://github.com/user-attachments/assets/c7003f37-d211-4b4e-b4af-aa31aa72799c" />
<img width="267" height="377" title="treefingers  2_0_5 small screen scaling  floats.5 k; {267x377 pixels}" src="https://github.com/user-attachments/assets/7dc4bf06-5493-45dd-acb4-a501410b2a20" />

..

<img width="133" height="188" title="treefingers  2_0_5 small screen scaling  floats.25 l; {133x188 pixels})" src="https://github.com/user-attachments/assets/e4f62cfa-d6de-4b32-a71f-785b1425772f" />
<img width="133" height="188" title="treefingers  2_0_5 small screen scaling  floats.25 m; {133x188 pixels})" src="https://github.com/user-attachments/assets/a952b603-cb8b-4eb9-aa4a-fccdb5b6c240" />
