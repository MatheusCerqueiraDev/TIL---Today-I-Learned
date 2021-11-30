PT-BR 
Swiper

Swiper é uma biblioteca volta a criar carrousels para aplicações front end.

----------------------------------------------------------------------
PR-BR
Swiper com React

Como toda biblioteca, instalamos a biblioteca dentro do projeto com:

yarn add swiper -> Innstalando localmente o swiper

Para o uso do Swiper no React utilizamos o core da biblioteca:

import SwiperCore from 'swiper'
import { Swiper, SwiperSlide } from 'swiper/react';

Para podermos usar sua estilização nativa importamos as dependencias desejadas:

Exemplo:
import { Navigation, Pagination, Scrollbar, A11y, Autoplay } from 'swiper';

Virtual - Virtual Slides module
Keyboard - Keyboard Control module
Mousewheel - Mousewheel Control module
Navigation - Navigation module
Pagination - Pagination module
Scrollbar - Scrollbar module
Parallax - Parallax module
FreeMode - Free Mode module
Grid - Grid module
Manipulation - Slides manipulation module (only for Core version)
Zoom - Zoom module
Lazy - Lazy module
Controller - Controller module
A11y - Accessibility module
History - History Navigation module
HashNavigation - Hash Navigation module
Autoplay - Autoplay module
EffectFade - Fade Effect module
EffectCube - Cube Effect module
EffectFlip - Flip Effect module
EffectCoverflow - Coverflow Effect module
EffectCards - Cards Effect module
EffectCreative - Creative Effect module
Thumbs - Thumbs module

Para usarmos esse modulos utilizamos o SwipeCore:

SwiperCore.use([Navigation, Pagination, Scrollbar, A11y, Autoplay]);