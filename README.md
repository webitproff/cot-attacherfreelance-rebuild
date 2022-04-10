# cot-attacherfreelance-rebuild
Плагин-дополнение для плагина attacher
<a href="http://freelance-script.abuyfile.com/attacher-freelance-plugin/" target="_blank" rel="noopener"><strong>Документация и руководство с примерами</strong></a>
<h1 class="entry-title">«Attacher Freelance» — прикрепление файлов</h1>

<p>«<a href="https://github.com/webitproff/cot-attacherfreelance-rebuild" target="_blank" rel="noopener"><strong>AttacherFreelance</strong></a>» — Плагин для «сборка «Фриланс-Биржа»».  С помощью которого можно загружать файлы, изображения, и прикреплять к публикациям <strong>основных модулей фриланс-биржи: <em>маркет, проекты, портфолио</em></strong>, услуги<br>
«AttacherFreelance» работает на основе API плагина attacher и является мостиком для взаимодействия с модулями projects (проекты биржи фриланса), market (витрина услуг и магазин цифровых товаров), folio (портфолио фрилансеров).<br>
<span style="color: #ff0000;"><strong>Для работы плагина требуется установленный плагин «<a href="http://freelance-script.abuyfile.com/attacher-plugin-cotonti/">Attacher</a>».</strong></span><br>
<span style="color: #ff0000;"><strong>Установка рекомендуется только на чистую сборку, то есть новый сайт.</strong></span><br>
Не устанавливать наряду с плагинами «Mavatars» и «MAvatars for freelance2» <span style="color: #e40a5d;"><strong>(крайне устарели)</strong></span> или другими расширениями (плагинами), выполняющими эти функциональные задачи. Конфликты и риски не исключены — всё под свою ответственность!</p>
<blockquote>
<h6>Attacherfreelance — плагин для фриланс-биржи на Cotonti Siena<br>
Code=attacherfreelance<br>
Name=Attacherfreelance<br>
Category=files-media<br>
Description=Attaching images and files for freelance (projects,market,folio)<br>
Version=1.0.0.beta<br>
Date=2019-01-26<br>
Author=Roffun<br>
Requires_plugins=attacher</h6>
</blockquote>
<h3>Установка плагина «AttacherFreelance»</h3>
<p>— Скачать архив, распаковать. Переименовать папку с плагином в attacherfreelance. Её нужно разместить в корневой каталог plugins, где все плагины находятся.<br>
<strong>(Плагин «AttacherFreelance» уже включен в состав базовой сборки.!!!)</strong><br>
— Перейти в «Управление сайтом / Расширения / Загрузка изображений и файлов фриланс» и установить с помощью интерфейса (плагин attacher уже должен быть установлен).<br>
На этом процесс установки можно считать завершенным.<br>
<span style="color: #ff0000;"><strong>Остается подключить плагин в шаблонах, — добавить код в соответствующие шаблоны модулей фриланс-биржи скина вашего сайта</strong></span>.</p>
<h1>Модуль projects сборки «Фриланс-Биржа»</h1>
<p>Для прикрепления файлов к создаваемому проекту.</p>
<p><strong><a href="http://masterscity.abuyfile.com/projects/marketing/3-testovoe-zadanie-po-testirovaniyu" target="_blank" rel="noopener">пример прикрепления файлов к проекту (заданию)</a></strong></p>
<p><a href="http://freelance-script.abuyfile.com/wp-content/uploads/2019/11/attacher-cotonti-projects.jpg"><img class="aligncenter size-large wp-image-1202" src="http://freelance-script.abuyfile.com/wp-content/uploads/2019/11/attacher-cotonti-projects-1024x621.jpg" alt="" srcset="http://freelance-script.abuyfile.com/wp-content/uploads/2019/11/attacher-cotonti-projects-1024x621.jpg 1024w, http://freelance-script.abuyfile.com/wp-content/uploads/2019/11/attacher-cotonti-projects-300x182.jpg 300w, http://freelance-script.abuyfile.com/wp-content/uploads/2019/11/attacher-cotonti-projects-768x466.jpg 768w, http://freelance-script.abuyfile.com/wp-content/uploads/2019/11/attacher-cotonti-projects-445x270.jpg 445w, http://freelance-script.abuyfile.com/wp-content/uploads/2019/11/attacher-cotonti-projects.jpg 1526w" sizes="(max-width: 640px) 100vw, 640px" width="640" height="388"></a></p>
<p>В projects.add.tpl:</p>
<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="html">&lt;!-- IF {PHP|cot_auth('plug', 'attacher', 'W')} --&gt;
  {PHP.L.Files}:
  {PHP|att_filebox('projects', 0)}
&lt;!-- ENDIF --&gt;</pre>
<p>&nbsp;</p>
<p>Для прикрепления файлов к редактируемому проекту.</p>
<p>В projects.edit.tpl:</p>
<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="html">&lt;!-- IF {PHP|cot_auth('plug', 'attacher', 'W')} --&gt;
  {PHP.L.Files}:
  {PRJEDIT_FORM_ID|att_filebox('projects', $this)}
&lt;!-- ENDIF --&gt;</pre>
<p>&nbsp;</p>
<p>Предпросмотр списка прикрепленных файлов перед публикацией проекта.</p>
<p>В projects.preview.tpl:</p>
<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="html">&lt;!-- IF {PRJ_ID|att_count('projects',$this)} &gt; 0 --&gt;
&lt;div data-att-display="all"&gt;
    &lt;h3&gt;{PHP.L.att_attachments}&lt;/h3&gt;
    {PRJ_ID|att_display('projects',$this,'','attacher.display','all')}
&lt;/div&gt;
&lt;!-- ENDIF --&gt;</pre>
<p>&nbsp;</p>
<p>Вывод прикрепленных файлов на странице проекта:</p>
<p>В projects.tpl:</p>
<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="html">&lt;!-- IF {PRJ_ID|att_count('projects',$this)} &gt; 0 --&gt;
&lt;div data-att-display="all"&gt;
    &lt;h3&gt;{PHP.L.att_attachments}&lt;/h3&gt;
    {PRJ_ID|att_display('projects',$this,'','attacher.display','all')}
&lt;/div&gt;
&lt;!-- ENDIF --&gt;</pre>
<p>&nbsp;</p>
<p>Вывод изображений в списках (категориях) проектов:</p>
<p>В projects.list.tpl:</p>
<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="html">&lt;!-- IF {PRJ_ROW_ID|att_count('projects',$this,'','images')} &gt; 0 --&gt;
&lt;div&gt;
    &lt;a href="{PRJ_ROW_URL}" title="{PRJ_ROW_SHORTTITLE}"&gt;
        &lt;img src="{PRJ_ROW_ID|att_get('projects',$this,'')|att_thumb($this,200,160,'crop',false)}" alt="{PRJ_ROW_SHORTTITLE}"&gt;
    &lt;/a&gt;
&lt;/div&gt;
&lt;!-- ENDIF --&gt;</pre>
<p>&nbsp;</p>
<p>Вывод изображений в списках проектов на главной:</p>
<p>В projects.index.tpl:</p>
<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="html">&lt;!-- IF {PRJ_ROW_ID|att_count('projects',$this,'','images')} &gt; 0 --&gt;
&lt;div&gt;
    &lt;a href="{PRJ_ROW_URL}" title="{PRJ_ROW_SHORTTITLE}"&gt;
        &lt;img src="{PRJ_ROW_ID|att_get('projects',$this,'')|att_thumb($this,200,160,'crop',false)}" alt="{PRJ_ROW_SHORTTITLE}"&gt;
    &lt;/a&gt;
&lt;/div&gt;
&lt;!-- ENDIF --&gt;</pre>
<p>&nbsp;</p>
<p>Вывод изображений в списках проектов в профиле:</p>
<p>В projects.userdetails.tpl:</p>
<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="html">&lt;!-- IF {PRJ_ROW_ID|att_count('projects',$this,'','images')} &gt; 0 --&gt;
&lt;div&gt;
    &lt;a href="{PRJ_ROW_URL}" title="{PRJ_ROW_SHORTTITLE}"&gt;
        &lt;img src="{PRJ_ROW_ID|att_get('projects',$this,'')|att_thumb($this,200,160,'crop',false)}" alt="{PRJ_ROW_SHORTTITLE}"&gt;
    &lt;/a&gt;
&lt;/div&gt;
&lt;!-- ENDIF --&gt;</pre>
<p>&nbsp;</p>
<p>Вывод формы прикрепления файлов для исполнителя и заказчика в заявках проекта.</p>
<p>В projects.offers.tpl перед:</p>
<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="html">&lt;!-- BEGIN: PROJECTFORPRO --&gt;
&lt;div class="alert alert-warning"&gt;{PHP.L.paypro_warning_onlyforpro}&lt;/div&gt;
&lt;!-- END: PROJECTFORPRO --&gt;</pre>
<p>Добавить:</p>
<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="html">&lt;!-- IF {PHP|cot_auth('plug', 'attacher', 'W')} --&gt;
{PHP.item.item_id|att_performer_attach($this,'all',2)}
&lt;!-- ENDIF --&gt;</pre>
<p>Эта конструкция выведет форму прикрепления файлов, видимую только если:</p>
<p>Назначен исполнитель, статус проекта не реализован. Видят заказчик и исполнитель.<br>
Нет исполнителя, но есть прикрепленные файлы от предыдущего исполнителя (после отказа). Видит заказчик.<br>
Выбран исполнитель, проект отмечен как реализованный. Видит заказчик при наличии файлов.</p>
<p>Так как форма предназначена для прикрепления файлов, видимых только заказчику и исполнителю, они могут оба видеть всё что прикреплено в форму (если условие 1), могут удалять свои файлы, но не могут удалить файлы друг друга. Это подстраховка для обеих сторон.</p>
<p>Админ сайта видит форму и файлы при возникновении любого из перечисленных условий, и имеет права на удаление любого из них. При добавлении конструкции в шаблон темы, второй и третий параметр — это настройка типов файлов и количества, разрешенных для прикрепления. Так как функция att_performer_attach() — это обертка для функции att_filebox(), для более детального понимания параметров 2 и 3 смотрите описание $type, $limit для att_filebox().</p>
<p>p.s. Плагин attacher и attacherfreelance работают по принципу API, и не знают, где в какой момент, какой модуль или плагин их использует. Они лишь выводят форму загрузки или уже загруженное содержимое, ничего не зная о фрилансерах, работодателях, статусах и прочем. Применяют только разрешения указанные для них.</p>
<p>При интеграции в свои расширения нужно самостоятельно позаботиться об этом. В качестве примера такой функции — att_performer_attach(), которая обрабатывает логику вывода формы, но не является частью API. Она анализирует данные на основе переданного параметра, и создает условия для вывода формы att_filebox() по конкретным условиям.</p>
<h1>Модуль market freelance</h1>
<p>Для прикрепления файлов к добавляемому товару (не самого товара!). Для продажи файлов и цифровых товаров используется <a href="http://freelance-script.abuyfile.com/category/plugins/">плагин</a> для <a href="http://freelance-script.abuyfile.com/category/builds-freelance-script/">сборки сайта «<strong>Фриланс-биржа</strong>«</a> — «<a href="http://freelance-script.abuyfile.com/plugin-marketorders/"><strong>МаркетОрдерс</strong></a>«.</p>
<p>В шаблон модуля <strong>market.add.tpl</strong> :</p>
<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="html">&lt;!-- IF {PHP|cot_auth('plug', 'attacher', 'W')} --&gt;
  {PHP.L.Files}:
  {PHP|att_filebox('market', 0)}
&lt;!-- ENDIF --&gt;</pre>
<p>&nbsp;</p>
<p>Для прикрепления файлов к редактируемому товару.</p>
<p>В <strong>market.edit.tpl</strong>:</p>
<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="html">&lt;!-- IF {PHP|cot_auth('plug', 'attacher', 'W')} --&gt;
{PHP.L.Files}:
{PRDEDIT_FORM_ID|att_filebox('market', $this)}
&lt;!-- ENDIF --&gt;</pre>
<p>&nbsp;</p>
<p>Предпросмотр списка прикрепленных файлов перед публикацией товара на витрину.</p>
<p>В <strong>market.preview.tpl</strong>:</p>
<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="html">&lt;!-- IF {PRD_ID|att_count('market',$this)} &gt; 0 --&gt;
&lt;div data-att-display="all"&gt;
    &lt;h3&gt;{PHP.L.att_attachments}&lt;/h3&gt;
    {PRD_ID|att_display('market',$this,'','attacher.display','all')}
&lt;/div&gt;
&lt;!-- ENDIF --&gt;</pre>
<p>&nbsp;</p>
<p>Вывод прикрепленных файлов на странице (карточки) товара:</p>
<p>В <strong>market.tpl</strong>:</p>
<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="html">&lt;!-- IF {PRD_ID|att_count('market',$this)} &gt; 0 --&gt;
&lt;div data-att-display="all"&gt;
    &lt;h3&gt;{PHP.L.att_attachments}&lt;/h3&gt;
    {PRD_ID|att_display('market',$this,'','attacher.display','all')}
&lt;/div&gt;
&lt;!-- ENDIF --&gt;</pre>
<p>или так</p>
<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="generic">&lt;div class="uk-inline uk-cover-container"&gt;
  &lt;!-- IF {PRD_ID|att_get('market', $this, '', '', '2')} --&gt;
    &lt;canvas width="200" height="200"&gt;&lt;/canvas&gt;
    &lt;a href="{PRD_ID|att_get('market', $this, '', '', '2')|att_thumb($this, 850, 650, auto)}" data-caption="{PRD_SHORTTITLE} - " title="{PRD_SHORTTITLE}"&gt;
    &lt;img src="{PRD_ID|att_get('market', $this, '', '', '2')|att_thumb($this, 250, 250, crop)}" alt="" uk-cover&gt;&lt;/a
  &lt;!-- ENDIF --&gt;
&lt;/div&gt;
</pre>
<p>или так, <span style="color: #ff0000;">в шаблоне модуля, через шаблон плагина</span> <strong>attacher.display.market.tpl</strong></p>
<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="generic">&lt;div class="uk-container" uk-slider="center: true"&gt;
  &lt;div class="uk-position-relative uk-visible-toggle uk-light" tabindex="-1"&gt;
  &lt;div class="uk-slider-items" uk-lightbox&gt;
  &lt;!-- BEGIN: ATTACHER_ROW --&gt;
    &lt;div class="uk-width-1-1"&gt;
    &lt;!-- IF {ATTACHER_ROW_IMG} AND {ATTACHER_ROW_NUM} == 1 --&gt;
    &lt;a href="{ATTACHER_ROW_URL}"  data-caption="{PRD_ROW_SHORTTITLE}{ATTACHER_ROW_TITLE} - {ATTACHER_ROW_FILENAME}" alt="{ATTACHER_ROW_TITLE}"&gt;
      &lt;img width="640" height="320" src="{ATTACHER_ROW_ID|att_thumb($this,640,420,'crop')}" alt="{ATTACHER_ROW_TITLE} - {ATTACHER_ROW_FILENAME}" title="{ATTACHER_ROW_TITLE} - {ATTACHER_ROW_FILENAME}" /&gt;  
    &lt;/a&gt;
    &lt;!-- ENDIF --&gt;
    &lt;!-- IF {ATTACHER_ROW_IMG} AND {ATTACHER_ROW_NUM} == 2 --&gt;
    &lt;a href="{ATTACHER_ROW_URL}"  data-caption="{PRD_ROW_SHORTTITLE}{ATTACHER_ROW_TITLE} - {ATTACHER_ROW_FILENAME}" alt="{ATTACHER_ROW_TITLE}"&gt;
      &lt;img width="640" height="320" src="{ATTACHER_ROW_ID|att_thumb($this,640,420,'crop')}" alt="{ATTACHER_ROW_TITLE} - {ATTACHER_ROW_FILENAME}" title="{ATTACHER_ROW_TITLE} - {ATTACHER_ROW_FILENAME}" /&gt;  
    &lt;/a&gt;
    &lt;!-- ENDIF --&gt;
    &lt;!-- IF {ATTACHER_ROW_IMG} AND {ATTACHER_ROW_NUM} == 3 --&gt;
    &lt;a href="{ATTACHER_ROW_URL}"  data-caption="{PRD_ROW_SHORTTITLE}{ATTACHER_ROW_TITLE} - {ATTACHER_ROW_FILENAME}" alt="{ATTACHER_ROW_TITLE}"&gt;
      &lt;img width="640" height="320" src="{ATTACHER_ROW_ID|att_thumb($this,640,420,'crop')}" alt="{ATTACHER_ROW_TITLE} - {ATTACHER_ROW_FILENAME}" title="{ATTACHER_ROW_TITLE} - {ATTACHER_ROW_FILENAME}" /&gt;  
    &lt;/a&gt;
    &lt;!-- ENDIF --&gt;
    &lt;/div&gt;
  &lt;!-- END: ATTACHER_ROW --&gt;
  &lt;/div&gt;
  &lt;a class="uk-position-center-left uk-position-small uk-hidden-hover" href="#" uk-slidenav-previous uk-slider-item="previous"&gt;&lt;/a&gt;
  &lt;a class="uk-position-center-right uk-position-small uk-hidden-hover" href="#" uk-slidenav-next uk-slider-item="next"&gt;&lt;/a&gt;
  &lt;/div&gt;
  &lt;ul class="uk-slider-nav uk-dotnav uk-flex-center uk-margin"&gt;&lt;/ul&gt;
&lt;/div&gt;
</pre>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>Вывод изображений в списках (категориях) товаров:</p>
<p>В <strong>market.list.tpl</strong>:</p>
<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="html">&lt;!-- IF {PRD_ROW_ID|att_count('market',$this,'','images')} &gt; 0 --&gt;
&lt;div&gt;
    &lt;a href="{PRD_ROW_URL}" title="{PRD_ROW_SHORTTITLE}"&gt;
        &lt;img src="{PRD_ROW_ID|att_get('market',$this,'')|att_thumb($this,200,160,'crop',false)}" alt="{PRD_ROW_SHORTTITLE}"&gt;
    &lt;/a&gt;
&lt;/div&gt;
&lt;!-- ENDIF --&gt;</pre>
<p>Вывод изображений в списках товаров на главной:</p>
<p>В <strong>market.index.tpl</strong>:</p>
<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="html">&lt;!-- IF {PRD_ROW_ID|att_count('market',$this,'','images')} &gt; 0 --&gt;
&lt;div&gt;
    &lt;a href="{PRD_ROW_URL}" title="{PRD_ROW_SHORTTITLE}"&gt;
        &lt;img src="{PRD_ROW_ID|att_get('market',$this,'')|att_thumb($this,200,160,'crop',false)}" alt="{PRD_ROW_SHORTTITLE}"&gt;
    &lt;/a&gt;
&lt;/div&gt;
&lt;!-- ENDIF --&gt;</pre>
<p>Вывод изображений в списках товаров в профиле:</p>
<p>В <strong>market.userdetails.tpl</strong>:</p>
<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="html">&lt;!-- IF {PRD_ROW_ID|att_count('market',$this,'','images')} &gt; 0 --&gt;
&lt;div&gt;
    &lt;a href="{PRD_ROW_URL}" title="{PRD_ROW_SHORTTITLE}"&gt;
        &lt;img src="{PRD_ROW_ID|att_get('market',$this,'')|att_thumb($this,200,160,'crop',false)}" alt="{PRD_ROW_SHORTTITLE}"&gt;
    &lt;/a&gt;
&lt;/div&gt;
&lt;!-- ENDIF --&gt;</pre>
<h1>Модуль folio freelance</h1>
<h4>Для прикрепления файлов при добавлении работы в портфолио:</h4>
<p>В folio.add.tpl:</p>
<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="html">&lt;!-- IF {PHP|cot_auth('plug', 'attacher', 'W')} --&gt;
&lt;tr&gt;
    &lt;td&gt;{PHP.L.Files}:&lt;/td&gt;
    &lt;td&gt;
        {PHP|att_filebox('folio', 0)}
    &lt;/td&gt;
&lt;/tr&gt;
&lt;!-- ENDIF --&gt;</pre>
<p>&nbsp;</p>
<p>Для прикрепления файлов к редактируемой работе в портфолио.</p>
<p>В folio.edit.tpl:</p>
<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="html">&lt;!-- IF {PHP|cot_auth('plug', 'attacher', 'W')} --&gt;
&lt;tr&gt;
    &lt;td&gt;{PHP.L.Files}:&lt;/td&gt;
    &lt;td&gt;
        {PRDEDIT_FORM_ID|att_filebox('folio', $this)}
    &lt;/td&gt;
&lt;/tr&gt;
&lt;!-- ENDIF --&gt;</pre>
<p>Предпросмотр списка прикрепленных файлов перед публикацией работы в портфолио.</p>
<p>В folio.preview.tpl:</p>
<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="html">&lt;!-- IF {PRD_ID|att_count('folio',$this)} &gt; 0 --&gt;
&lt;div data-att-display="all"&gt;
    &lt;h3&gt;{PHP.L.att_attachments}&lt;/h3&gt;
    {PRD_ID|att_display('folio',$this,'','attacher.display','all')}
&lt;/div&gt;
&lt;!-- ENDIF --&gt;</pre>
<p>&nbsp;</p>
<p>Вывод прикрепленных файлов на странице работы в портфолио:</p>
<p>В folio.tpl:</p>
<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="html">&lt;!-- IF {PRD_ID|att_count('folio',$this)} &gt; 0 --&gt;
&lt;div data-att-display="all"&gt;
    &lt;h3&gt;{PHP.L.att_attachments}&lt;/h3&gt;
    {PRD_ID|att_display('folio',$this,'','attacher.display','all')}
&lt;/div&gt;
&lt;!-- ENDIF --&gt;</pre>
<p>Вывод изображений в списках (категориях) работ портфолио:</p>
<p>В folio.list.tpl:</p>
<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="html">&lt;!-- IF {PRD_ROW_ID|att_count('folio',$this,'','images')} &gt; 0 --&gt;
&lt;div&gt;
    &lt;a href="{PRD_ROW_URL}" title="{PRD_ROW_SHORTTITLE}"&gt;
        &lt;img src="{PRD_ROW_ID|att_get('folio',$this,'')|att_thumb($this,200,160,'crop',false)}" alt="{PRD_ROW_SHORTTITLE}"&gt;
    &lt;/a&gt;
&lt;/div&gt;
&lt;!-- ENDIF --&gt;</pre>
<p>Вывод изображений в списках работ портфолио на главной:</p>
<p>В folio.index.tpl:</p>
<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="html">&lt;!-- IF {PRD_ROW_ID|att_count('folio',$this,'','images')} &gt; 0 --&gt;
&lt;div&gt;
    &lt;a href="{PRD_ROW_URL}" title="{PRD_ROW_SHORTTITLE}"&gt;
        &lt;img src="{PRD_ROW_ID|att_get('folio',$this,'')|att_thumb($this,200,160,'crop',false)}" alt="{PRD_ROW_SHORTTITLE}"&gt;
    &lt;/a&gt;
&lt;/div&gt;
&lt;!-- ENDIF --&gt;</pre>
<p>Вывод изображений в списках работ портфолио в профиле:</p>
<p>В folio.userdetails.tpl:</p>
<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="html">&lt;!-- IF {PRD_ROW_ID|att_count('folio',$this,'','images')} &gt; 0 --&gt;
&lt;div&gt;
    &lt;a href="{PRD_ROW_URL}" title="{PRD_ROW_SHORTTITLE}"&gt;
        &lt;img src="{PRD_ROW_ID|att_get('folio',$this,'')|att_thumb($this,200,160,'crop',false)}" alt="{PRD_ROW_SHORTTITLE}"&gt;
    &lt;/a&gt;
&lt;/div&gt;
&lt;!-- ENDIF --&gt;</pre>
<blockquote><p>Представленный в данной статье код для интеграции функционала в шаблоны модулей сборки фриланс-биржи является рабочим примером.</p></blockquote>
<p>Варианты интеграции кода этим не исчерпываются и дополнительно могут зависить от используемых <strong>CSS</strong>, <strong>JS</strong>, <strong>HTML</strong> библиотек и компонетов.&nbsp; <strong>Плагин attacherfreelance</strong> служит лишь мостиком между расширениями сборки модулей и плагинов сайта биржи фриланса и <a href="http://freelance-script.abuyfile.com/attacher-freelance-plugin/"><strong>API плагина attacher</strong></a>, с помощью которого и работают вышеприведенные примеры. Поэтому смотрите документацию и примеры по <a href="http://freelance-script.abuyfile.com/attacher-freelance-plugin/">функциям плагина</a>.<br>
Файлы и медиа: «Attacherfreelance — плагин Cotonti»<br>
Если вам была полезна эта информация, будьте добры, поделитесь ею в социальных сетях. Это послужит дополнительным мотиватором, стимулом к дальнейшим публикациям на сайте автора — <strong>cmscot.net</strong> статей на интересующие вас темы.</p>
<h4><a href="https://github.com/webitproff/cot-attacherfreelance-rebuild" target="_blank" rel="noopener noreferrer"><strong>скачать плагин</strong></a></h4>

<p>Помощь, поддержка, консультации, доработки сборки биржи услуг на Cotonti заказать можно по контактам:</p>
<p>— Email: webitproff@gmail.com<br>
— Telegram: <a href="https://t.me/webitproff" target="_blank" rel="noopener"> https://t.me/webitproff</a></p>
<p>&nbsp;</p>
