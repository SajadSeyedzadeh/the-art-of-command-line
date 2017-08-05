🌍
*[Čeština](README-cs.md) ∙ [Deutsch](README-de.md) ∙ [Ελληνικά](README-el.md) ∙ [English](README.md) ∙ [Español](README-es.md) ∙ [Français](README-fr.md) ∙ [Indonesia](README-id.md) ∙ [Italiano](README-it.md) ∙ [日本語](README-ja.md) ∙ [한국어](README-ko.md) ∙ [Português](README-pt.md) ∙ [Română](README-ro.md) ∙ [Русский](README-ru.md) ∙ [Slovenščina](README-sl.md) ∙ [Українська](README-uk.md) ∙ [简体中文](README-zh.md) ∙ [繁體中文](README-zh-Hant.md)* . [فارسی](README-fa.md)

<h1 dir="rtl" align="right"> 
هنر استفاده از ترمینال
</h1>
<p dir="rtl" align="right">
ترمینال اینجا به عنوان معادل فارسی عبارت Command Line به کار رفته است. 
</p>

[![Ask a Question](https://img.shields.io/badge/%3f-Ask%20a%20Question-ff69b4.svg)](https://airtable.com/shrzMhx00YiIVAWJg)

[![Join the chat at https://gitter.im/jlevy/the-art-of-command-line](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/jlevy/the-art-of-command-line?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

- [مقدمه](#meta)
- [اصول](#basics)
- [استفاده روزمره](#everyday-use)
- [پردازش فایل و داده](#processing-files-and-data)
- [رفع باگ سیستم](#system-debugging)
- [دستورات یک خطی](#one-liners)
- [گمنام اما مفید](#obscure-but-useful)
- [مخصوص سیستم عامل OXS](#os-x-only)
- [مخصوص ویندوز](#windows-only)
- [منابع بیشتر](#more-resources)
- [سلب مسئولیت](#disclaimer)

![curl -s 'https://raw.githubusercontent.com/jlevy/the-art-of-command-line/master/README.md' | egrep -o '`\w+`' | tr -d '`' | cowsay -W50](cowsay.png)

<p dir="rtl" align="right">
توانایی در کار با ترمینال اغلب نادیده گرفته می‌شود، اما در انعطاف و بازدهی مهندسین نرم‌تافزار تاثیرگذار است. این تاثیرات گاه آشکار و گاه غیرمحسوس هستند. این مجموعه گزیده‌ایست از یادداشت‌ها و نکته‌هایی که در استفاده از ترمینال سیستم عامل لینوکس یه شما کمک خواهند کرد. بعضی از این نکات مبتدی و بعضی جزیی و پیچیده و ناشناخته هستند. این مستند طولانی نیست اما اگر تمام مطالب این صفحه را به خاطر داشته باشید، در کار با ترمینال خیلی توانمندتر خواهید بود. 
</p>

<p dir="rtl" align="right">
این کار حاصل زحمات 
<a href="	AUTHORS.md">بسیاری از مترجمان و نویسندگان</a>
 است. برخی از مواردی که در این مستند می‌بینید در سایت پرسش و پاسخ
<a href="https://www.quora.com">کورا</a>
 نگاشته شده و پس از آن به گیت هاب منتقل گردیده است. اگر سوالی در مورد استفاده از ترمینال دارید لطفا سوال خود را 
<a href="https://airtable.com/shrzMhx00YiIVAWJg">اینجا</a>
 مطرح کنید. همچنین، اگر اشتباهی در این مستند می‌بینید یا هر قسمتی که می‌توان آن را بهبود داد، می‌توانید با 
<a href="CONTRIBUTING.md">کمک کردن</a>
 به این ریپازیتوری به گسترش آن کمک کنید. 
</p>


<h2 id="meta" dir="rtl" align="right">
مقدمه
</h2>

<p dir="rtl" align="right">
مخاطب این مستند کیست؟
<ul dir="rtl" align="right">
<li>
- این مستند مناسب برای همه افراد، چه مبتدی و چه باتجربه است. اهداف این مستند پوشش دادن سطح وسیعی از موضوعات، پرداختن به جزییات موضوع (با مثال‌هایی از مهم‌ترین موارد استفاده هر دستور) و اختصار (پرهیز از مواردی که الزاما مورد استفاده قرار نخواهند گرفت) است. تمامی موارد درج شده در این مستند در برخی شرایط بسیار مهم و مورد استفاده است و منجر به کاهش زمان انجام کار می‌شود. 
</li>
<li>

این مستند، به جز قسمت های مخصوص ویندوز و مخصوص OSX برای کاربران لینوکس نوشته شده است. بسیاری از موارد مطرح شده در سایر بخش‌ها قابل نصب روی سایر سیستم‌عامل ها هستند. 

</li>
<li>

تمرکز این مستند روی Bash است، هر چند برخی از نکات گفته شده ممکن است در سایر Shell ها قابل استفاده باشند. 

</li>
<li>

این مستند هم شامل دستوراتی است که به صورت پیش فرض در ترمینال لینوکس قابل دسترسی هستند و هم دستوراتی که نیاز به نصب پکیج‌های مخصوص خود را دارند.

</li>
</ul>
</p>

<p dir="rtl" align="right">
توجه:
<ul dir="rtl" align="right">
<li>

برای اینکه حجم مطالب را به یک صفحه محدود کنیم، برخی مطالب همراه با منابعی درج شده‌اند. می‌توانید برای اطلاعات بیشتر حول یک موضوع به لینک‌هایی که برای مطالعه بیشتر معرفی شده مراجعه کنید یا با سرچ در اینترنت قسمت‌هایی که جایی در این مستند نداشته‌اند را یاد بگیرید. برای نصب پکیج‌های جدید از `apt-get`, `yum`, `dnf`, `pacman`, `pip` یا `brew` (با توجه به نسخه سیستم‌عامل خود) استفاده کنید.

</li>
<li>

برای یادگرفتن نقش و مفهوم دستورات، گزینه‌های ضمن دستور و پایپ‌ها به <a href="https://explainshell.com/">Explainshell</a> استفاده کنید.

</li>
</ul>
</p>

<h2 id="basics" dir="rtl" align="right">
اصول
</h2>

<p dir="rtl" align="right">
<ul dir="rtl" align="right">
<li>

Bash مقدماتی یاد بگیرید. می‌توانید با تایپ کردن `man bash` و خواندن اجمالی متن اطلاعات خوبی بگیرید. این متن آسان و کوتاه است. Shell های دیگر در عین حال که می‌توانند خوب و مفید باشند، Bash از سایر گزینه ها بهتر است و تقریبا همواره در دسترس شماست، چه روی لپتاپ، چه روی سرور و غیره.

</li>
<li>

حداقل یکی از نرم‌افزارهای ویرایش متن مبتنی بر ‌Bash را یاد بگیرید (مثلا vim). 

</li>
<li>

خواندن متن مستندات تکنولوژی‌های مختلف از طریق `man` را یاد بگیرید. برای اطلاعات بیشتر در مورد `man` از `man man` استفاده کنید که شامل شماره بخش‌های مختلف می‌باشد (مثلا شماره ۱ بخش دستورات "معمولی" است، ۵  بخش قرارداد‌ها و فایل‌هاست و ۸ بخش مدیریتی است). صفحات `man` را از طریق `apropos` پیدا کنید. بدانید که برخی دستورات فایل‌های اجرایی نیست، بلکه دستورات نوشته شده در Bash هستند و با دستور `help` و `help -d` می‌توان در مورد آنها اطلاعات بیشتری به دست آورد. با تایپ کردن `type command`می‌توانید بفهمید که یک دستور یک فایل اجرایی‌است، یک دستور نوشته شده در Bash است یا یک نام جایگزین برای دستور دیگر (alias).

</li>
<li>

می توان با کاراکتر‌های `>` و `<` و پایپ‌ (`|`) ورودی و خروجی برنامه را از فایل خواند یا به فایل نوشت. توجه داشته باشید که `<<` خروجی را به محتویات فایل ضمیمه می‌کند در حالی که `<` فایل را بازنویسی می‌کند. تفاوت و مفهوم `stdout` و `stderr` را بدانید.

</li>
<li>

می‌توان اسم فایل‌ها را به صورت گسترده به عنوان ورودی به برنامه‌های Bash داد. می‌توان با کاراکتر‌های `*` (و `?` و `[...]`) اسم فایل های ورودی را گسترش داد. در مورد تفاوت " و ' در Bash مطالعه کنید. 


</li>
<li>

با مدیریت جاب در Bash آشنا باشید: `&`, **ctrl-z**, **ctrl-c**, `jobs`, `fg`, `bg`, `kill` و غیره. 

</li>
<li>

`ssh` بلد باشید. همچنین در مورد تصدیق هویت بدون رمز عبور اطلاعات داشته باشید (از طریق دستوراتی مثل `ssh-agent` و `ssh-add` و غیره)

</li>
<li>

مدیریت مقدماتی فایل‌ها: `ls` و `ls -l` (به خصوص اینکه هر ستون در خروجی `ls -l` چه معنی‌ای دارد)، `less`, `head`, `tail` و `tail -f` (یا حتی `less +F`). در مورد `ln` و `ln -s` (تفاوت بین لینک‌های نرم - soft - و سخت - hard - را بدانید). دستوراتی مثل `chown` و `chmod` و `du` را بلد باشید. برای مدیریت فایل سیستم این دستورات را بلد باشید: `df` `mount` `fdisk` `mkfs` `lsblk`. یاد بگیرید که معنی inode چیست (`ls -i` یا `df -i`).

</li>
<li>

برای مدیریت مقدماتی شبکه این دستورات را یاد بگیرید: 
`ip` یا `ifconfig`, `dig`, `traceroute`, `route`.

</li>
<li>

در مورد مدیریت نسخه نرم‌افزار از طریق نرم‌افزاهایی مثل `git` مطالعه کنید.

</li>
<li>

در مورد عبارات با قاعده (Regular Expression) مطالعه کنید. در مورد گزینه‌های `-i`, `-o`, `-v`, `-A`, `-B` و `-C` مربوط به دستور `grep`/`egrep` مطالعه کنید. 

</li>
<li>

برای پیدا کردن پکیج‌های مختلف از دستورات `apt-get`, `yum`, `dnf` یا `pacman` (بسته به توزیع لینوکس خود) استفاده کنید. همچنین برای نصب ابزارهای مبتنی بر پایتون حتما از `pip` استفاده کنید.

</li>
</ul>
</p>


<h2 id="everyday-use" dir="rtl" align="right">
استفاده روزمره
</h2>

<p dir="rtl" align="right">
<ul dir="rtl" align="right">
<li>

در Bash با استفاده از **Tab** می‌توانید ورودی‌های برنامه را کامل کنید یا لیستی از همه‌ی دستورات ممکن را ببینید. با استفاده **ctrl-r** می‌توانید در سابقه دستوراتی که اجرا کرده‌اید بگردید‌ (بعد از فشار دادن **ctrl-r** تایپ کنید تا در دستورات گذشته بگردید و هر وقت دستور مورد نظر شما پیدا شد با **enter** آن را اجرا کنید یا با فشار دادن کلید فلش چپ به انتهای دستور پیدا شده رفته و آن را قبل از اجرا ویرایش کنید).

</li>
<li>

در Bash با **ctrl-w** می‌توانید آخرین کلمه تایپ شده در ترمینال را پاک کنید. با **ctrl-u** کلمات تایپ شده قبل از اشاره‌گر تایپ را پاک کنید. با **alt-b**  و **alt-f** می‌توانید اشاره‌گر را یک کلمه به عقب و جلو ببرید. با **ctrl-a** اشاره‌گر را به ابتدای خط برده و با **ctrl-e** آن را به انتهای خط ببرید. با **ctrl-k** می‌توانید آنچه بعد از اشاره‌گر آمده را cut کنید (گاهی از این تکنیک برای پاک کرده ادامه دستور استفاده می‌شود). با استفاده **ctrl-l** صفحه ترمینال را پاک کنید. برای دیدن همه ترکیب کلید‌های ممکن از `man readline` استفاده کنید. بسیاری از این ترکیب‌های مفید وجود دارد. به عنوان مثال **alt-.** می‌توانید ورودی‌های قبلی برنامه را ببینید و با **alt-*** متغیر یا نام‌ها را گسترش دهید. 

</li>
<li>

همچنین اگر به ترکیب کلیدها در vim عادت دارید، می‌توانید با دستور `set -o vi` ترکیب کلید‌های vim را در ترمینال داشته باشید (برای برگرداندن به حالت اولیه از `set -o emacs` استفاده کنید).

</li>
<li>

برای ویرایش کردن دستورات طولانی می‌توانید از ترکیب کلید **ctrl-x** و سپس **ctrl-e** استفاده کنید تا متن دستور در یک ویرایشگر متن ظاهر شود. آنجا می‌توانید متن دستور را ویرایش کنید و سپس آن را اجرا کنید. برای انجام اینکار با ترکیبات کلید‌ها در vim از **escape-v** استفاده کنید.

</li>
<li>

برای دیدن دستوراتی که اخیرا اجرا شده‌اند از دستور `history` استفاده کنید. در ادامه این دستور از از دستور `!n` (که n شماره دستور است) استفاده کنید تا این دستور دوباره اجرا شود (بخش HISTORY EXPANSION در صفحات `man`مطالعه کنید. البته، این دستورات را می‌توان به راحتی با **ctrl-r** و **alt-.** جایگزین کرد.

</li>
<li>

با دستور `cd` دایرکتوری فعلی را تغییر دهید. برای دسترسی به فایل‌ها و فولدرها در دایرکتوری خانه از مسیر `~` استفاده کنید (مثلا `~/.bashrc`). در اسکریپ‌های `sh` برای دسترسی به دایرکتوری خانه از `$HOME` استفاده کنید.

</li>
</li>

برای رفتن به دایرکتوری قبلی از دستور `cd -` استفاده کنید.

</li>
<li>

اگر در حین تایپ یک دستور از اجرای آن پشیمان شدید از ترکیب کلید **alt-#** استفاده کنید تا آن دستور به عنوان کامنت ثبت شود (و اجرا نشود). برای اینکار همچنین می‌توانید از **ctrl-a**، **#** و **enter** استفاده کنید. برای برگشتن به این دستور می‌توانید از تاریخچه دستورات استفاده کنید.

</li>
<li>

از `xargs` و `parallel` استفاده کنید. این دو ابزارهای قدرتمندی هستند. توجه کنید می‌توانید تعداد دفعات اجرا به ازای هر خط (از طریق `-L`) و همچنین تعداد پردازه‌های موازی را (از طریق `-P`) کنترل کنید. اگر در مورد نحووه کار آن مطمئن نیستید ابتدا از `xargs echo` استفاده کنید تا نحوه کار آن را یاد بگیرید. همچنین `-I{}` خیلی کارامد است. مثال:


```bash
      find . -name '*.py' | xargs grep some_function
      cat hosts | xargs -I{} ssh root@{} hostname
```

</li>
<li>

از `pstree -p` برای نمایش پردازه‌ها استفاده کنید. 

</li>
<li>

از `pkill` و  `pgrep` برای سیگنال دادن و پیدا کردن پردازه‌های مختلف استفاده کنید (گزینه `-f` را یاد بگیرید).

</li>
<li>

سیگنال‌های مختلفی که می‌توان به پردازه‌ها ارسال کرد را بدانید. به عنوان مثال برای متوقف کردن یک پردازه از `kill -STOP [pid]` استفاده کنید. برای دیدن لیست کامل از `man 7 signal` استفاده کنید.

</li>
<li>

برای اجرای دستورات تا ابد در پس زمینه از `nohup` و `disown`استفاده کنید.

</li>
<li>

برای دیدن پردازه‌هایی که در حال گوش کردن به شبکه روی پورت‌های مختلف هستند از `netstat -lntp` یا `ss -plat` (برای TCP، برای UDP یک `-u` اضافه کنید) یا `lsof -iTCP -sTCP:LISTEN -P -n` (که روی سیستم عامل OSX هم کار می‌کند) استفاده کنید.

</li>
<li>

در مورد دستورات `lsof` و `fuser` برای کار با Socket‌ها و فایل‌های باز شده مطالعه کنید.

</li>
<li>

از دستور `uptime` یا `w` برای دیدن اینکه سیستم چقدر در حال اجرا بوده است استفاده کنید. 

</li>
<li>

برای ایجاد کردن نام‌های جایگزین برای دستورات (alias) از دستور `alias` استفاده کنید. مثلا `alias ll='ls -latr'` یک نام جایگزین برای دستور `ls -latr` ایجاد می‌کند.

</li>
<li>

نام‌های جایگزین دستورات، تنظیمات و تابع‌هایی که مرتبا از آنها استفاده می‌کنید را در فایل `~/.bashrc` ذخیره کنید. کاری کنید که سایر Shell ها از همین تنظیمات استفاده کنند. با اینکار تنظیمات در همه  نشست‌های Shell در دسترس خواهند بود. 

</li>
<li>

با استفاده از Git تنظیمات خود را در همه کامپیوترهای خود هماهنگ و یکسان نگه دارید.

</li>
<li>

نام فایل‌ها و فولدرها ممکن است شامل کاراکترهای سفید باشند (منظور اسپیس، تب، خط جدید و امثال آنهاست). متغیرهای Bash خود را با نقل قول دوتایی بنویسید، مثلا `"$FOO"`. از گزینه‌های `-0` یا `-print0` استفاده کنید تا در انتهای نام فایل‌ها کاراکتر null قرار بگیرد (\0) مثلا `locate -0 pattern | xargs -0 ls -al` یا `find / -print0 -type d | xargs -0 ls -al`. با دستور `IFS=$'\n'` می‌توانید IFS را فقط به کاراکتر خط جدید تغییر دهید. 

</li>
<li>

در اسکریپت‌های Bash می‌توانید با استفاده از `set -x` (یا `set -v` که ورودی خام را در لاگ می‌نویسد، از جمله کامنت ها و متغیرها) خروجی برنامه را دیباگ کنید. از مدهای strict استفاده کنید مگر اینکه دلیل خوبی برای استفاده نکردن از مد Strict داشته باشید. از `set -e` برای متوقف کردن خطاها استفاده کنید. از `set -u` برای شناسایی موارد استفاده از متغیرهایی بدون مقدار استفاده کنید. برای یافتن خطاها در پایپ‌ها از `set -o pipefail` استفاده کنید (قبل از استفاده در مورد آن مطالعه کنید، استفاده از آن می‌تواند پیچیده باشد). برای اجرای اسکریپت‌ها می توانید از `trap` هنگام EXIT یا ERR استفاده کنید. یک عادت خوب این است که اسکریپت را به این روش شروع کنید که باعث می‌شود خطاهای رایج را تشخیص دهد و پیامی چاپ کند.

```bash
      set -euo pipefail
      trap "echo 'error: Script failed: see failed command above'" ERR
```

</li>
<li>

در اسکریپت‌های بش، Shell‌های زیر مجموعه که داخل پرانتز نوشته می‌شوند روش خوبی برای قرار دادن چند دستور در یک گروه است. یک مثال ساده جا به جا کردن دایرکتوری کار است:

```bash
      # do something in current dir
      (cd /some/other/dir && other-command)
      # continue in original dir
```

</li>
<li>

توجه کنید که در Bash روش‌های بسیاری برای گسترش اسم متغیرها وجود دارد. مثلا برای چک کردن اینکه یک متغیر وجود دارد: `${name:?error message}`. به عنوان مثال اگر یک Script نیاز فقط به یک آرگمان ورودی دارد، کافیست بنویسید `input_file=${1:?usage: $0 input_file}`. اگر می‌خواهید متغیرهای بیشتر (اختیاری) به مثال قبلی اضافه شود از چیزی شبیه این استفاده کنید: `output_file=${2:-logfile}`. اگر `$2` پاک شود و در نتیجه خالی باشد، مقدار متغیر `output_file` به `logfile` تغییر خواهد کرد. عبارات جبری: `i=$(( (i + 1) % 5 ))`. کوتاه کردین تنظیمات: `${var%suffix}` و `${var#prefix}`. به عنوان مثال `var=foo.pdf` و سپس `echo ${var%.pdf}.txt` این خروجی را خواهد داد: `foo.txt`.

</li>
<li>

گسترش نام متغیرها از طریق آکولاد `{`...`}` می‌تواند از تایپ کردن نام متغیرهایی که شبیه هم هستند جلوگیری کند. این کار در مثال‌هایی مانند `mv foo.{txt,pdf} some-dir` (که هر دو فایل را جا به جا می‌کند)، `cp somefile{,.bak}` (که هر دو فایل را کپی می‌کند. فرم گسترش یافته آن به صورت `cp somefile somefile.bak` است.) و  `mkdir -p test-{a,b,c}/subtest-{1,2,3}` که گسترش یافته آن همه ترکیبات ممکن (۹ حالت متفاوت) را می‌سازد. مفید است. 

</li>
<li>

از طریق `<(some command)` می‌توانید با خروجی یک دستور مثل یک فایل رفتار کنید. مثلا می‌توانیم فایل /etc/hosts روی کامپیوتر خودمان را با همین فایل روی یک کامپیوتر دیگر مقایسه کنیم:

```bash
      diff /etc/hosts <(ssh somehost cat /etc/hosts)
```

</li>
<li>

هنگام نوشتن اسکریپت، تمام قسمت‌های کد خود را در آکولاد قرار دهید. اگر یکی از آکولادها را فراموش کنید، اسکریپت شما به علت Syntax Error اجرا نخواهد شد. این کار برای زمانی که اسکریپت شما قرار است دانلود شود بسیار مفید است چرا که از اجرا شدن نصفه اسکریپت جلوگیری می‌کند. 

```bash
{
      # Your code here
}
```

</li>
<li>

در مورد "here document" ها در Bash مطالعه کنید. مثلا `cat <<EOF ...`. 

</li>
<li>

در Bash، می‌تواند خروجی Stdout و Stderr را به جای دیگری (به جز صفحه خروجی، مثلا فایل) ارسال کنید: `some-command >logfile 2>&1` یا `some-command &>logfile`. مطمئن شوید که هیچ دستوری اشاره‌گر فایل را باز نمی‌گذارد. جهت اطمینان خوب است که در انتها این را اضافه کنید: `</dev/null`. 

</li>
<li>

برای دیدن جدول کاراکترهای اسکی (ASCII) از `man ascii` استفاده کنید. برای اطلاعات بیشتر در مورد encoding کاراکترها از `man unicode`، `man utf-8` `man latin1` استفاده کنید. 

</li>
<li>

از `screen` برای چند پنجره‌ای کردن ترمینال استفاده کنید. این دستور به خصوص در ssh و اتصال به کامپیوتر های روی شبکه مفید است. `byobu` می‌تواند با اطلاعات بیشتر و مدیریت آسان‌تر screen راه بهبود دهد. یک جایگزین کوچک و ساده هم 
<a href="https://github.com/bogner/dtach">dtach</a>
 است.

</li>
<li>

در ssh، دانستن اینکه می توان Tunnel را با `-L` یا `-D`پورت کرد مفید اس، مثلا برای دسترسی به یک وبسایت از یک کامپیوتر ریموت. 

</li>
<li>

می‌توانید با اعمال تنظیمات زیر در فایل `~/.ssh/config` اتصالات ssh خود را مقداری بهبود دهید:

```bash
      TCPKeepAlive=yes
      ServerAliveInterval=15
      ServerAliveCountMax=6
      Compression=yes
      ControlMaster auto
      ControlPath /tmp/%r@%h:%p
      ControlPersist yes
```

</li>
<li>

چند گزینه دیگر مربوط به ssh مربوط به امنیت شبکه هستند و باید با آنها با احتیاط رفتار کنید: `StrictHostKeyChecking=no`, `ForwardAgent=yes`.

</li>
<li>

یک جایگزین خوب برای ssh، 
<a href="https://mosh.mit.edu/">mosh</a>
است که به جای TCP از UDP استفاده می‌کند که از قطع شدن دائمی ارتباط با سرور جلوگیری می‌کند (توجه کنید استفاده از mosh نیاز به نصب کردن آن در سمت سرور هم دارد). 

</li>
<li>

برای دیدن اجازه‌های مربوط به یک فایل در مبنای ۸ (که برای تنظیم کردن سیستم مفید‌تر است) از چیزی مثل 
```sh
      stat -c '%A %a %n' /etc/timezone
```
استفاده کنید. 

</li>
<li>

برای انتخاب کردن مقادیر مورد نظر خود به صورت interactive از خروجی یک دستور، از 
<a href="https://github.com/mooz/percol">percol</a>
 یا 
<a href="https://github.com/junegunn/fzf">fzf</a>
 استفاده کنید. 

</li>
<li>


برای تعامل کردن با فایل‌ها بر اساس خروجی یک دستور دیگر (مثلا گیت) از 
<a href="https://github.com/facebook/PathPicker">fpp</a>
 استفاده کنید.

</li>
<li>

برای درست کردن یک وب سرور ساده برای همه فایل‌ها در دایرکتوری فعلی، که قابل دسترس توسط همه افراد در شبکه شماست از `python -m http.server 7777` استفاده کنید. 

</li>
<li>

برای اجرا کردن یک دستور از طرف یک کاربر دیگر از `sudo` استفاده کنید. این دستور بنابر پیش فرض کاربر را root در نظر می‌گیرد. از `-u` برای مشخص کردن یک کاربر دیگر استفاده کنید. از `-i` برای لاگین کردن به جای یک کاربر دیگر استفاده کنید (در اینصورت باید رمز عبور کاربری که می‌خواهید از طرف او لاگین کنید را وارد کنید). 

</li>
<li>

در مورد محدودیت 
<a href="https://wiki.debian.org/CommonErrorMessages/ArgumentListTooLong">128K</a>
 مطالعه کنید. زمانی که تعداد ورودی‌های یک برنامه از طریق نام‌های گسترش‌پذیر متغیر خیلی طولانی شود با این محدودیت مواجه می‌شوید (زمانی که این اتفاق می‌افتد از جایگزین‌هایی مثل `find` و `xargs` استفاده کنید.

</li>
</li>

از `python` می‌توانید به عنوان یک ماشین حساب ساده استفاده کنید:


```
>>> 2+3
5
```

</li>
</ul>
</p>



<h2 id="everyday-use" dir="rtl" align="right">
پردازش فایل و داده
</h2>

<p>
<ul dir="rtl" align="right">
<li>

برای پیدا کردن فایل‌ها در دایرکتوری فعلی از دستور `find . -iname '*something*'` استفاده کنید. برای پیدا کردن فایل در همه دایرکتوری ها از `locate something` استفاده کنید (اما توجه کنید که `updatedb` ممکن است فایل‌هایی که اخیرا ساخته شدن اند را فهرست نکرده باشد). 

</li>
<li>

برای جستجو به صورت کلی در فایل‌ها و داده‌ها از 
<a href="https://github.com/ggreer/the_silver_searcher">ag</a>
 استفاده کنید. این دستور قابلیت‌های بیشتری از `grep -r` در اختیار شما می‌گذارد. 

</li>
<li>

برای تبدیل کردن HTML به متن معمولی از `lynx -dump -stdin` استفاده کنید. 

</li>
<li>

برای تبدیل مارک‌داون، HTML و ... از 
<a href="https://github.com/ggreer/the_silver_searcher">pandoc</a>
 استفاده کنید.

</li>
<li>

برای کار کردن با XML از `xmlstarlet` استفاده کنید. 

</li>
<li>

برای کار کردن با JSON از 
<a href="http://stedolan.github.io/jq/">jq</a>
 استفاده کنید.

</li>
<li>

برای کار کردن با YAML از 
<a href="https://github.com/0k/shyaml">shyaml</a>
 استفاده کنید.

</li>
<li>

برای کار کردن با فایل‌های اکسل یا CSV از 
<a href=؛https://github.com/onyxfish/csvkit">csvkit</a>
 استفاده کنید. دستورات `in2csv`, `csvcut`, `csvjoin`, `csvgrep` را در اختیار شما قرار می‌دهد.

</li>
<li>

برای استفاده از سرویس S3 آمازون، 
<a href="https://github.com/s3tools/s3cmd">s3cmd</a>
 ابزار مفیدی است. 
<a href="https://github.com/bloomreach/s4cmd">s4cmd</a>
 هم یک جایگزین سریع‌تر برای s3cmd است. کتابخانه‌های 
<a href="https://github.com/aws/aws-cli">aws</a>
و نسخه بهبود یافته آن 
<a href="https://github.com/donnemartin/saws">saws</a>
برای کار با سرویس‌ها AWS لازم و ضروری هستند.

</li>
<li>

در مورد `sort` و `uniq` مطالعه کنید، مخصوصا گزینه های `-u` و `-d` در `uniq`. همچنین در مورد `comm` مطالعه کنید.

</li>
<li>

در مورد `cut` `paste` و `join` مطالعه کنید. این دستورات برای کار با فایل‌های داده خیلی مفید هستند. خیلی از افراد از `cut` استفاده می‌کنند ولی `join` را فراموش می‌کنند.

</li>
<li>

در مورد دستور `wc` که برای شمردن تعداد خطوط (`-l`)، کلمات (`-w`)، کاراکتر‌ها (`-m`) و بایت‌ها (`-c`) استفاده می‌شود مطالعه کنید.

</li>
<li>

در مورد دستور `tee` که برای کپی کردن محتویات Stdin به یک فایل یا به Stdout استفاده می‌شود مطالعه کنید (مثلا `ls -al | tee file.txt`). 

</li>
<li>

برای انجام محاسبات نسبتا پیچیده که شامل گروه‌بندی، معکوس کردن و محاسبات اماری می‌شوند می‌توانید از 
<a href="https://www.gnu.org/software/datamash/">datamash</a>
 استفاده کنید. 

</li>
<li>

به خاطر locality، خیلی از دستورات ترمینال تحت تاثیر قرار می‌گیرند، مثلا ترتیب مرتب‌سازی و کارآمدی (performance). خیلی از نسخه‌های لینوکس، مقدار متغیر محیطی `LANG` را به US English تنظیم می‌کنند. اما بدانید که 

</li>
</ul>
</p>


- Know that locale affects a lot of command line tools in subtle ways, including sorting order (collation) and performance. Most Linux installations will set `LANG` or other locale variables to a local setting like US English. But be aware sorting will change if you change locale. And know i18n routines can make sort or other commands run *many times* slower. In some situations (such as the set operations or uniqueness operations below) you can safely ignore slow i18n routines entirely and use traditional byte-based sort order, using `export LC_ALL=C`.

- You can set a specific command's environment by prefixing its invocation with the environment variable settings, as in `TZ=Pacific/Fiji date`.

- Know basic `awk` and `sed` for simple data munging. See [One-liners](#one-liners) for examples.

- To replace all occurrences of a string in place, in one or more files:
```sh
      perl -pi.bak -e 's/old-string/new-string/g' my-files-*.txt
```

- To rename multiple files and/or search and replace within files, try [`repren`](https://github.com/jlevy/repren). (In some cases the `rename` command also allows multiple renames, but be careful as its functionality is not the same on all Linux distributions.)
```sh
      # Full rename of filenames, directories, and contents foo -> bar:
      repren --full --preserve-case --from foo --to bar .
      # Recover backup files whatever.bak -> whatever:
      repren --renames --from '(.*)\.bak' --to '\1' *.bak
      # Same as above, using rename, if available:
      rename 's/\.bak$//' *.bak
```

- As the man page says, `rsync` really is a fast and extraordinarily versatile file copying tool. It's known for synchronizing between machines but is equally useful locally. When security restrictions allow, using `rsync` instead of `scp` allows recovery of a transfer without restarting from scratch. It also is among the [fastest ways](https://web.archive.org/web/20130929001850/http://linuxnote.net/jianingy/en/linux/a-fast-way-to-remove-huge-number-of-files.html) to delete large numbers of files:
```sh
mkdir empty && rsync -r --delete empty/ some-dir && rmdir some-dir
```

- For seeing progress when copying files, use `pv`, [`pycp`](https://github.com/dmerejkowsky/pycp), [`progress`](https://github.com/Xfennec/progress), `rsync --progress`, or, for block-level copying, `dd status=progress`.

- Use `shuf` to shuffle or select random lines from a file.

- Know `sort`'s options. For numbers, use `-n`, or `-h` for handling human-readable numbers (e.g. from `du -h`). Know how keys work (`-t` and `-k`). In particular, watch out that you need to write `-k1,1` to sort by only the first field; `-k1` means sort according to the whole line. Stable sort (`sort -s`) can be useful. For example, to sort first by field 2, then secondarily by field 1, you can use `sort -k1,1 | sort -s -k2,2`.

- If you ever need to write a tab literal in a command line in Bash (e.g. for the -t argument to sort), press **ctrl-v** **[Tab]** or write `$'\t'` (the latter is better as you can copy/paste it).

- The standard tools for patching source code are `diff` and `patch`. See also `diffstat` for summary statistics of a diff and `sdiff` for a side-by-side diff. Note `diff -r` works for entire directories. Use `diff -r tree1 tree2 | diffstat` for a summary of changes. Use `vimdiff` to compare and edit files.

- For binary files, use `hd`, `hexdump` or `xxd` for simple hex dumps and `bvi`, `hexedit` or `biew` for binary editing.

- Also for binary files, `strings` (plus `grep`, etc.) lets you find bits of text.

- For binary diffs (delta compression), use `xdelta3`.

- To convert text encodings, try `iconv`. Or `uconv` for more advanced use; it supports some advanced Unicode things. For example, this command lowercases and removes all accents (by expanding and dropping them):
```sh
      uconv -f utf-8 -t utf-8 -x '::Any-Lower; ::Any-NFD; [:Nonspacing Mark:] >; ::Any-NFC; ' < input.txt > output.txt
```

- To split files into pieces, see `split` (to split by size) and `csplit` (to split by a pattern).

- To manipulate date and time expressions, use `dateadd`, `datediff`, `strptime` etc. from [`dateutils`](http://www.fresse.org/dateutils/).

- Use `zless`, `zmore`, `zcat`, and `zgrep` to operate on compressed files.

- File attributes are settable via `chattr` and offer a lower-level alternative to file permissions. For example, to protect against accidental file deletion the immutable flag:  `sudo chattr +i /critical/directory/or/file`

- Use `getfacl` and `setfacl` to save and restore file permissions. For example:
```sh
   getfacl -R /some/path > permissions.txt
   setfacl --restore=permissions.txt
```

- To create empty files quickly, use `truncate` (creates [sparse file](https://en.wikipedia.org/wiki/Sparse_file)), `fallocate` (ext4, xfs, btrfs and ocfs2 filesystems), `xfs_mkfile` (almost any filesystems, comes in xfsprogs package), `mkfile` (for Unix-like systems like Solaris, Mac OS).

## System debugging

- For web debugging, `curl` and `curl -I` are handy, or their `wget` equivalents, or the more modern [`httpie`](https://github.com/jkbrzt/httpie).

- To know current cpu/disk status, the classic tools are `top` (or the better `htop`), `iostat`, and `iotop`. Use `iostat -mxz 15` for basic CPU and detailed per-partition disk stats and performance insight.

- For network connection details, use `netstat` and `ss`.

- For a quick overview of what's happening on a system, `dstat` is especially useful. For broadest overview with details, use [`glances`](https://github.com/nicolargo/glances).

- To know memory status, run and understand the output of `free` and `vmstat`. In particular, be aware the "cached" value is memory held by the Linux kernel as file cache, so effectively counts toward the "free" value.

- Java system debugging is a different kettle of fish, but a simple trick on Oracle's and some other JVMs is that you can run `kill -3 <pid>` and a full stack trace and heap summary (including generational garbage collection details, which can be highly informative) will be dumped to stderr/logs. The JDK's `jps`, `jstat`, `jstack`, `jmap` are useful. [SJK tools](https://github.com/aragozin/jvm-tools) are more advanced.

- Use [`mtr`](http://www.bitwizard.nl/mtr/) as a better traceroute, to identify network issues.

- For looking at why a disk is full, [`ncdu`](https://dev.yorhel.nl/ncdu) saves time over the usual commands like `du -sh *`.

- To find which socket or process is using bandwidth, try [`iftop`](http://www.ex-parrot.com/~pdw/iftop/) or [`nethogs`](https://github.com/raboof/nethogs).

- The `ab` tool (comes with Apache) is helpful for quick-and-dirty checking of web server performance. For more complex load testing, try `siege`.

- For more serious network debugging, [`wireshark`](https://wireshark.org/), [`tshark`](https://www.wireshark.org/docs/wsug_html_chunked/AppToolstshark.html), or [`ngrep`](http://ngrep.sourceforge.net/).

- Know about `strace` and `ltrace`. These can be helpful if a program is failing, hanging, or crashing, and you don't know why, or if you want to get a general idea of performance. Note the profiling option (`-c`), and the ability to attach to a running process (`-p`). Use trace child option (`-f`) to avoid missing important calls.

- Know about `ldd` to check shared libraries etc — but [never run it on untrusted files](http://www.catonmat.net/blog/ldd-arbitrary-code-execution/).

- Know how to connect to a running process with `gdb` and get its stack traces.

- Use `/proc`. It's amazingly helpful sometimes when debugging live problems. Examples: `/proc/cpuinfo`, `/proc/meminfo`, `/proc/cmdline`, `/proc/xxx/cwd`, `/proc/xxx/exe`, `/proc/xxx/fd/`, `/proc/xxx/smaps` (where `xxx` is the process id or pid).

- When debugging why something went wrong in the past, [`sar`](http://sebastien.godard.pagesperso-orange.fr/) can be very helpful. It shows historic statistics on CPU, memory, network, etc.

- For deeper systems and performance analyses, look at `stap` ([SystemTap](https://sourceware.org/systemtap/wiki)), [`perf`](https://en.wikipedia.org/wiki/Perf_%28Linux%29), and [`sysdig`](https://github.com/draios/sysdig).

- Check what OS you're on with `uname` or `uname -a` (general Unix/kernel info) or `lsb_release -a` (Linux distro info).

- Use `dmesg` whenever something's acting really funny (it could be hardware or driver issues).

- If you delete a file and it doesn't free up expected disk space as reported by `du`, check whether the file is in use by a process:
`lsof | grep deleted | grep "filename-of-my-big-file"`


## One-liners

A few examples of piecing together commands:

- It is remarkably helpful sometimes that you can do set intersection, union, and difference of text files via `sort`/`uniq`. Suppose `a` and `b` are text files that are already uniqued. This is fast, and works on files of arbitrary size, up to many gigabytes. (Sort is not limited by memory, though you may need to use the `-T` option if `/tmp` is on a small root partition.) See also the note about `LC_ALL` above and `sort`'s `-u` option (left out for clarity below).
```sh
      sort a b | uniq > c   # c is a union b
      sort a b | uniq -d > c   # c is a intersect b
      sort a b b | uniq -u > c   # c is set difference a - b
```

- Use `grep . *` to quickly examine the contents of all files in a directory (so each line is paired with the filename), or `head -100 *` (so each file has a heading). This can be useful for directories filled with config settings like those in `/sys`, `/proc`, `/etc`.


- Summing all numbers in the third column of a text file (this is probably 3X faster and 3X less code than equivalent Python):
```sh
      awk '{ x += $3 } END { print x }' myfile
```

- To see sizes/dates on a tree of files, this is like a recursive `ls -l` but is easier to read than `ls -lR`:
```sh
      find . -type f -ls
```

- Say you have a text file, like a web server log, and a certain value that appears on some lines, such as an `acct_id` parameter that is present in the URL. If you want a tally of how many requests for each `acct_id`:
```sh
      egrep -o 'acct_id=[0-9]+' access.log | cut -d= -f2 | sort | uniq -c | sort -rn
```

- To continuously monitor changes, use `watch`, e.g. check changes to files in a directory with `watch -d -n 2 'ls -rtlh | tail'` or to network settings while troubleshooting your wifi settings with `watch -d -n 2 ifconfig`.

- Run this function to get a random tip from this document (parses Markdown and extracts an item):
```sh
      function taocl() {
        curl -s https://raw.githubusercontent.com/jlevy/the-art-of-command-line/master/README.md |
          pandoc -f markdown -t html |
          xmlstarlet fo --html --dropdtd |
          xmlstarlet sel -t -v "(html/body/ul/li[count(p)>0])[$RANDOM mod last()+1]" |
          xmlstarlet unesc | fmt -80
      }
```


## Obscure but useful

- `expr`: perform arithmetic or boolean operations or evaluate regular expressions

- `m4`: simple macro processor

- `yes`: print a string a lot

- `cal`: nice calendar

- `env`: run a command (useful in scripts)

- `printenv`: print out environment variables (useful in debugging and scripts)

- `look`: find English words (or lines in a file) beginning with a string

- `cut`, `paste` and `join`: data manipulation

- `fmt`: format text paragraphs

- `pr`: format text into pages/columns

- `fold`: wrap lines of text

- `column`: format text fields into aligned, fixed-width columns or tables

- `expand` and `unexpand`: convert between tabs and spaces

- `nl`: add line numbers

- `seq`: print numbers

- `bc`: calculator

- `factor`: factor integers

- [`gpg`](https://gnupg.org/): encrypt and sign files

- `toe`: table of terminfo entries

- `nc`: network debugging and data transfer

- `socat`: socket relay and tcp port forwarder (similar to `netcat`)

- [`slurm`](https://github.com/mattthias/slurm): network traffic visualization

- `dd`: moving data between files or devices

- `file`: identify type of a file

- `tree`: display directories and subdirectories as a nesting tree; like `ls` but recursive

- `stat`: file info

- `time`: execute and time a command

- `timeout`: execute a command for specified amount of time and stop the process when the specified amount of time completes.

- `lockfile`: create semaphore file that can only be removed by `rm -f`

- `logrotate`: rotate, compress and mail logs.

- `watch`: run a command repeatedly, showing results and/or highlighting changes

- [`when-changed`](https://github.com/joh/when-changed): runs any command you specify whenever it sees file changed. See `inotifywait` and `entr` as well.

- `tac`: print files in reverse

- `shuf`: random selection of lines from a file

- `comm`: compare sorted files line by line

- `strings`: extract text from binary files

- `tr`: character translation or manipulation

- `iconv` or `uconv`: conversion for text encodings

- `split` and `csplit`: splitting files

- `sponge`: read all input before writing it, useful for reading from then writing to the same file, e.g., `grep -v something some-file | sponge some-file`

- `units`: unit conversions and calculations; converts furlongs per fortnight to twips per blink (see also `/usr/share/units/definitions.units`)

- `apg`: generates random passwords

- `xz`: high-ratio file compression

- `ldd`: dynamic library info

- `nm`: symbols from object files

- `ab` or [`wrk`](https://github.com/wg/wrk): benchmarking web servers

- `strace`: system call debugging

- [`mtr`](http://www.bitwizard.nl/mtr/): better traceroute for network debugging

- `cssh`: visual concurrent shell

- `rsync`: sync files and folders over SSH or in local file system

- [`wireshark`](https://wireshark.org/) and [`tshark`](https://www.wireshark.org/docs/wsug_html_chunked/AppToolstshark.html): packet capture and network debugging

- [`ngrep`](http://ngrep.sourceforge.net/): grep for the network layer

- `host` and `dig`: DNS lookups

- `lsof`: process file descriptor and socket info

- `dstat`: useful system stats

- [`glances`](https://github.com/nicolargo/glances): high level, multi-subsystem overview

- `iostat`: Disk usage stats

- `mpstat`: CPU usage stats

- `vmstat`: Memory usage stats

- `htop`: improved version of top

- `last`: login history

- `w`: who's logged on

- `id`: user/group identity info

- [`sar`](http://sebastien.godard.pagesperso-orange.fr/): historic system stats

- [`iftop`](http://www.ex-parrot.com/~pdw/iftop/) or [`nethogs`](https://github.com/raboof/nethogs): network utilization by socket or process

- `ss`: socket statistics

- `dmesg`: boot and system error messages

- `sysctl`: view and configure Linux kernel parameters at run time

- `hdparm`: SATA/ATA disk manipulation/performance

- `lsblk`: list block devices: a tree view of your disks and disk partitions

- `lshw`, `lscpu`, `lspci`, `lsusb`, `dmidecode`: hardware information, including CPU, BIOS, RAID, graphics, devices, etc.

- `lsmod` and `modinfo`: List and show details of kernel modules.

- `fortune`, `ddate`, and `sl`: um, well, it depends on whether you consider steam locomotives and Zippy quotations "useful"


## OS X only

These are items relevant *only* on OS X.

- Package management with `brew` (Homebrew) and/or `port` (MacPorts). These can be used to install on OS X many of the above commands.

- Copy output of any command to a desktop app with `pbcopy` and paste input from one with `pbpaste`.

- To enable the Option key in OS X Terminal as an alt key (such as used in the commands above like **alt-b**, **alt-f**, etc.), open Preferences -> Profiles -> Keyboard and select "Use Option as Meta key".

- To open a file with a desktop app, use `open` or `open -a /Applications/Whatever.app`.

- Spotlight: Search files with `mdfind` and list metadata (such as photo EXIF info) with `mdls`.

- Be aware OS X is based on BSD Unix, and many commands (for example `ps`, `ls`, `tail`, `awk`, `sed`) have many subtle variations from Linux, which is largely influenced by System V-style Unix and GNU tools. You can often tell the difference by noting a man page has the heading "BSD General Commands Manual." In some cases GNU versions can be installed, too (such as `gawk` and `gsed` for GNU awk and sed). If writing cross-platform Bash scripts, avoid such commands (for example, consider Python or `perl`) or test carefully.

- To get OS X release information, use `sw_vers`.

## Windows only

These items are relevant *only* on Windows.

- On Windows 10, you can use [Bash on Ubuntu on Windows](https://msdn.microsoft.com/commandline/wsl/about), which provides a familiar Bash environment with Unix command line utilities. On the plus side, this allows Linux programs to run on Windows. On the other hand this does not support the running of Windows programs from the Bash prompt.

- Access the power of the Unix shell under Microsoft Windows by installing [Cygwin](https://cygwin.com/). Most of the things described in this document will work out of the box.

- Install additional Unix programs with the Cygwin's package manager.

- Use `mintty` as your command-line window.

- Access the Windows clipboard through `/dev/clipboard`.

- Run `cygstart` to open an arbitrary file through its registered application.

- Access the Windows registry with `regtool`.

- Note that a `C:\` Windows drive path becomes `/cygdrive/c` under Cygwin, and that Cygwin's `/` appears under `C:\cygwin` on Windows. Convert between Cygwin and Windows-style file paths with `cygpath`. This is most useful in scripts that invoke Windows programs.

- You can perform and script most Windows system administration tasks from the command line by learning and using `wmic`.

- Another option to get Unix look and feel under Windows is [Cash](https://github.com/dthree/cash). Note that only very few Unix commands and command-line options are available in this environment.

- An alternative option to get GNU developer tools (such as GCC) on Windows is [MinGW](http://www.mingw.org/) and its [MSYS](http://www.mingw.org/wiki/msys) package, which provides utilities such as bash, gawk, make and grep. MSYS doesn't have all the features compared to Cygwin. MinGW is particularly useful for creating native Windows ports of Unix tools.

## More resources

- [awesome-shell](https://github.com/alebcay/awesome-shell): A curated list of shell tools and resources.
- [awesome-osx-command-line](https://github.com/herrbischoff/awesome-osx-command-line): A more in-depth guide for the OS X command line.
- [Strict mode](http://redsymbol.net/articles/unofficial-bash-strict-mode/) for writing better shell scripts.
- [shellcheck](https://github.com/koalaman/shellcheck): A shell script static analysis tool. Essentially, lint for bash/sh/zsh.
- [Filenames and Pathnames in Shell](http://www.dwheeler.com/essays/filenames-in-shell.html): The sadly complex minutiae on how to handle filenames correctly in shell scripts.
- [Data Science at the Command Line](http://datascienceatthecommandline.com/#tools): More commands and tools helpful for doing data science, from the book of the same name

## Disclaimer

With the exception of very small tasks, code is written so others can read it. With power comes responsibility. The fact you *can* do something in Bash doesn't necessarily mean you should! ;)


## License

[![Creative Commons License](https://i.creativecommons.org/l/by-sa/4.0/88x31.png)](http://creativecommons.org/licenses/by-sa/4.0/)

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/).
