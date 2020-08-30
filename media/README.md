# media-breakpoints
<pre><code>@include media(sm, lg, print){
    @content
} </code></pre>
<br>Первый аргумент - данные из переменной $media-breakpoints
<br>Второй аргумент - данные из переменной $media-breakpoints или $modification
<br>Третий аргумент - данные из переменной $media-type
<br>
<h3>Варианты применений</h3>
<pre><code>@include media(sm) {} - (min-width: 576px) Имеет default модификатор min
@include media(sm, min) {} - (min-width: 576px) 
@include media(sm, max) {} - (max-width: 576px)
@include media(sm, only) {} - (min-width: 576px) and (max-width: 767.99px)
@include media(sm, only-max) {} - (min-width: 576px) and (max-width: 1650px)
@include media(sm, lg) {} - (min-width: 576px) and (max-width: 991.99px)
@include media(no, no, screen) {} - screen
@include media(sm, only, screen) {} - screen and (min-width: 576px) and (max-width: 767.99px)
@include media(sm, lg, screen) {} - screen and (min-width: 576px) and (max-width: 991.99px)
</code></pre>
<br>
<br>Можно создавать свои перменные $media-breakpoints и $media-type
<br>
<br>Breakpoint:
<br>
<pre><code>$media-breakpoints: (
    sm: 576rem,       
    md: 768px,          
    lg: 992px,          
    xl: 1200px             
)
</code></pre><br>
Модификации:
<ul>
    <li>min == min-width - задает min-width значение (min-width: 320px)</li>
    <li>max == max-width- задает max-width значение (max-width: 320px)</li>
    <li>only == min-width and max-width - задает значение от sm до md</li>
    <li>only-max == задает значение от указанного breakpoint до максимально значение в  $media-breakpoints</li>
</ul>
<br>
<br> Type
<br> 
<pre><code>$media-type: (
    'screen': 'screen',
    'print': 'print',
    'handheld': 'handheld',
    'landscape': '(orientation: landscape)',
    'portrait': '(orientation: portrait)',
    'retina2x': '(-webkit-min-device-pixel-ratio: 2), (min-resolution: 192dpi), (min-resolution: 2dppx)',
    'retina3x': '(-webkit-min-device-pixel-ratio: 3), (min-resolution: 350dpi), (min-resolution: 3dppx)'
        )
</code></pre><br>
<h3">Ошибки</h3>
<pre><code>@include media(no)() - breakpoint обязателен
@include media(no, no)() -  breakpoint и (модификатор или breakpoint ) обязателен
@include media(sm, sm) {} - не может быть равным второму breakpoint 
@include media(lg, sm) {} - не может быть больше второго breakpoint 
@include media(no, only) {} - не может модификатор быть без breakpoint
Если не правильно задан breakpoint или модификатор, то выведет ошибку
</code></pre>


