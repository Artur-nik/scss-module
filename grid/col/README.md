# Columns - breakpoints
<p>Принимает переменные:</p>
<ul>
    <li>$columns - количество колонок;</li>
    <li>$gutters - отступы между колонками;</li>
    <li>$media-breakpoints - map;</li>
</ul>
<br>
<pre><code>Микс col() принимает значения:
@include col(
    1 value - 0 - $columns (12), auto
    2 value - null, $media-breakpoints 
    3 value - extend, no-extend
    4 value - gutters, gutters-left, gutters-right, no-gutters, off-gutters
    5 value - width or off-width
    6 value - true or false (important)
);
</code></pre>
<p>Default значение:</p>
<pre><code>.test-col-1{
	@include col(1);
}
.test-col-value{
	@include col(1, null, extend, gutters, width, false); 
}
CSS:  
.test-col-1,
.test-col-value {
	width: 100%;
}
.test-col-1,
.test-col-value {
	padding-left: 15px;
	padding-right: 15px;
}
.test-col-1,
.test-col-value {
	flex: 0 0 8.33333%;
	max-width: 8.33333%;
}
</code></pre>
<p>С отключенным Sass Placeholder Selectors:</p>
<pre><code>.test-col-1 {
	@include col(1, null, no-extend);
} 
.test-col-value {
	@include col(1, null, no-extend);
} 
CSS:         
.test-col-1 {
	width: 100%;
	padding-left: 15px;
	padding-right: 15px;
	flex: 0 0 8.33333%;
	max-width: 8.33333%;
}
  
.test-col-value {
	width: 100%;
	padding-left: 15px;
	padding-right: 15px;
	flex: 0 0 8.33333%;
	max-width: 8.33333%;
}
</code></pre>
<p>Работа с $gutters (Работает с no-extend и extend):</p>
<pre><code>off-gutters - отключает вывод gutters:
.test-col-value {
    @include col(1, null, no-extend, no-gutters);
} 
CSS:  
.test-col-value {
    width: 100%;
    flex: 0 0 8.33333%;
    max-width: 8.33333%;
}
gutters-left - выводить только padding-left:
.test-col-value {
    @include col(1, null, no-extend, gutters-left);
} 
CSS:  
.test-col-value {
	width: 100%;
	padding-left: 15px;
	flex: 0 0 8.33333%;
	max-width: 8.33333%;
}
gutters-right - выводить только padding-right:
.test-col-value {
    @include col(1, null, no-extend, gutters-right);
} 

CSS:  
.test-col-value {
	width: 100%;
	padding-right: 15px;
	flex: 0 0 8.33333%;
	max-width: 8.33333%;
}
no-gutters - Вывод 0 значения:
.test-col-value {
    @include col(1, null, no-extend, no-gutters);
} 
CSS:
.test-col-value {
	width: 100%;
	padding-right: 0;
	padding-left: 0;
	flex: 0 0 8.33333%;
	max-width: 8.33333%;
  }
</code></pre>
<p>Работа с $width (Работает с no-extend и extend):</p>
<pre><code>Default значение $width:
.test-col-value {
	@include col(1, null, no-extend, gutters, width);
} 
CSS:
.test-col-value {
	width: 100%;
	padding-left: 15px;
	padding-right: 15px;
	flex: 0 0 8.33333%;
	max-width: 8.33333%;
}
no-width - отключает вывод width: 100%;
.test-col-value {
	@include col(1, null, no-extend, gutters, no-width);
} 
CSS:
.test-col-value {
	padding-left: 15px;
	padding-right: 15px;
	flex: 0 0 8.33333%;
	max-width: 8.33333%;
}

</code></pre>	
<p>Работа с $important:</p>
<pre><code>Default значение $important - false (изменить можно в _config.scss):
.test-col-value {
	@include col(1, null, no-extend, gutters, width, false);
} 
CSS:
.test-col-value {
	width: 100%;
	padding-left: 15px;
	padding-right: 15px;
	flex: 0 0 8.33333%;
	max-width: 8.33333%;
}
true - включает вывод "!important";
.test-col-value {
	@include col(1, null, no-extend, off-gutters, off-width, true);
} 
CSS:
.test-col-value {
	padding-left: 15px;
	padding-right: 15px;
	flex: 0 0 8.33333% !important;
	max-width: 8.33333% !important;
}
</code></pre>	
<p>Работа с $media (Работает с no-extend и extend)</p>
<pre><code>.test-col-value {
	@include col(1, null, no-extend);
	@include col(2, sm, no-extend);
	@include col(3, md, no-extend);
	@include col(4, lg, no-extend);
	@include col(5, xl, no-extend);
} 
CSS:		
.test-col-value {
	width: 100%;
	padding-left: 15px;
	padding-right: 15px;
	flex: 0 0 8.33333%;
	max-width: 8.33333%;
 }
 
@media (min-width: 576px) {
	.test-col-value {
	  	width: 100%;
	  	padding-left: 15px;
	  	padding-right: 15px;
	  	flex: 0 0 16.66667%;
	  	max-width: 16.66667%;
	}
}
 
@media (min-width: 768px) {
	.test-col-value {
	  	width: 100%;
	  	padding-left: 15px;
	  	padding-right: 15px;
	  	flex: 0 0 25%;
	  	max-width: 25%;
	}
 }
 
@media (min-width: 992px) {
	.test-col-value {
	  	width: 100%;
	  	padding-left: 15px;
	  	padding-right: 15px;
	  	flex: 0 0 33.33333%;
	  	max-width: 33.33333%;
	}
}
 
@media (min-width: 1200px) {
	.test-col-value {
		width: 100%;
		padding-left: 15px;
	  	padding-right: 15px;
	  	flex: 0 0 41.66667%;
	  	max-width: 41.66667%;
	}
}
</code></pre>
