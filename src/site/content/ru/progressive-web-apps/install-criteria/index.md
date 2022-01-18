---
layout: post
title: Что нужно для возможности установки?
authors:
  - petelepage
date: 2020-02-14
updated: 2021-05-19
description: |2-

  Критерии устанавливаемости прогрессивных веб-приложений.
tags:
  - progressive-web-apps
---

Прогрессивные веб-приложения (PWA) - это современные высококачественные приложения, созданные с использованием веб-технологий. PWA дают возможности, аналогичные приложениям iOS/Android и десктопным приложениям, они надежно работают даже в условиях нестабильной сети и могут быть установлены, что упрощает их поиск и использование.

Большинство пользователей знакомы с установкой и преимуществами работы с установленными приложениями. Установленные приложения появляются в плоскости запуска операционной системы, например, в папке «Приложения» в Mac OS X, в меню «Пуск» в Windows и на главном экране в Android и iOS. Установленные приложения также отображаются в переключателе действий, поисковых системах устройств, таких как Spotlight, и на листах обмена контентом.

Большинство браузеров указывают пользователю, что прогрессивное веб-приложение (PWA) можно установить, если оно соответствует определенным критериям. Среди индикаторов — кнопка «Установить» в адресной строке или пункт «Установить» в дополнительном меню.

<div class="w-columns">
  <figure class="w-figure" id="browser-install-promo">{% Img src="image/tcFciHGuF3MxnTr1y5ue01OGLBn2/O9KXz4aQXm3ZOzPo98uT.png", alt="Скриншот омнибокса с отображаемым индикатором установки.", width="800", height="307" %}<figcaption class="w-figcaption"> Браузер предлагает установку (настольный компьютер)</figcaption></figure>
  <figure class="w-figure">{% Img src="image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bolh05TCEeT7xni4eUTG.png", alt="Скриншот браузера, предлагающего установку.", width="800", height="307" %} <figcaption class="w-figcaption"> Браузер предлагает установку (мобильное устройство) </figcaption></figure>
</div>

Кроме того, при соблюдении критериев многие браузеры запускают событие `beforeinstallprompt`, что позволяет предоставить встроенный в приложение пользовательский интерфейс, который будет запускать процесс установки в вашем приложении.

## Критерии установки {: #criteria }

Чтобы запустить событие `beforeinstallprompt` и показать внутрибраузерное предложение установки, ваше прогрессивное веб-приложение в Chrome должно соответствовать следующим критериям:

- Веб-приложение еще не установлено
- Соответствует эвристике взаимодействия с пользователем
- Поставляется по HTTPS
- Включает [манифест веб-приложения](/add-manifest/), в который входят:
    - `short_name` или `name`
    - `icons` — должно включать значки размером 192 пикселя и 512 пикселей.
    - `start_url`
    - `display` — значение должно быть `fullscreen`, `standalone` или `minimal-ui`
    - `prefer_related_applications` не должен присутствовать или быть `false`
- Регистрирует сервис-воркер с помощью обработчика `fetch`

Другие браузеры имеют аналогичные критерии для установки, хотя могут быть незначительные отличия. Чтобы получить подробную информацию, посетите соответствующие сайты:

- [Edge](https://docs.microsoft.com/en-us/microsoft-edge/progressive-web-apps#requirements)
- [Firefox](https://developer.mozilla.org/docs/Web/Progressive_web_apps/Installable_PWAs)
- [Opera](https://dev.opera.com/articles/installable-web-apps/)
- [Samsung Internet](https://hub.samsunginter.net/docs/ambient-badging/)
- [UC Browser](https://plus.ucweb.com/docs/pwa/docs-en/zvrh56)

{% Aside %} На Android, если манифест веб-приложения включает `related_applications` и `"prefer_related_applications": true`, пользователь будет перенаправлен в магазин Google Play и вместо этого ему будет предложено [установить указанное приложение Android.](https://developers.google.com/web/fundamentals/app-install-banners/native) {% endAside %}