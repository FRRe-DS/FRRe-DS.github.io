---
title: Definición de APIs
weight: 2
---

## Objetivos

Este documento define las interfaces entre los diferentes sub-sistemas del TP Final.


<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>apis.md</title>
  <link rel="stylesheet" href="https://stackedit.io/style.css" />
</head>

<body class="stackedit">
  <div class="stackedit__html"><h3 id="ministerio-de-desarrollo-productivo-📋">Ministerio de Desarrollo Productivo 📋</h3>
<ul>
<li><strong>Esquemas de Datos</strong>
<ul>
<li>
<p>Reportes</p>
<pre class=" language-typescript"><code class="prism  language-typescript">	<span class="token keyword">const</span> reporteSchema <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">Schema</span><span class="token operator">&lt;</span>IReport<span class="token operator">&gt;</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
		infoEmpresa<span class="token punctuation">:</span> <span class="token punctuation">{</span>
			<span class="token keyword">type</span><span class="token punctuation">:</span> Schema<span class="token punctuation">.</span>Types<span class="token punctuation">.</span>ObjectId<span class="token punctuation">,</span>
			 ref<span class="token punctuation">:</span> <span class="token string">"Business"</span><span class="token punctuation">,</span>
		 <span class="token punctuation">}</span><span class="token punctuation">,</span>
		listaRegistro<span class="token punctuation">:</span> <span class="token punctuation">{</span>
			 <span class="token keyword">type</span><span class="token punctuation">:</span> <span class="token punctuation">[</span>
				<span class="token punctuation">{</span>
					<span class="token keyword">type</span><span class="token punctuation">:</span> Schema<span class="token punctuation">.</span>Types<span class="token punctuation">.</span>ObjectId<span class="token punctuation">,</span>
					ref<span class="token punctuation">:</span> <span class="token string">"Products"</span><span class="token punctuation">,</span>
				 <span class="token punctuation">}</span><span class="token punctuation">,</span>
			 <span class="token punctuation">]</span><span class="token punctuation">,</span>
		<span class="token punctuation">}</span><span class="token punctuation">,</span>
		date_upload <span class="token punctuation">:</span> <span class="token punctuation">{</span>
  				<span class="token keyword">type</span> <span class="token punctuation">:</span> Date<span class="token punctuation">,</span>
  				<span class="token keyword">default</span> <span class="token punctuation">:</span> Date<span class="token punctuation">.</span><span class="token function">now</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
		<span class="token punctuation">}</span><span class="token punctuation">,</span>
		day_limit <span class="token punctuation">:</span> <span class="token punctuation">{</span>
  				<span class="token keyword">type</span> <span class="token punctuation">:</span> Number<span class="token punctuation">,</span>
  				<span class="token keyword">default</span> <span class="token punctuation">:</span> <span class="token number">10</span>
		<span class="token punctuation">}</span><span class="token punctuation">,</span>
		periodo<span class="token punctuation">:</span> <span class="token punctuation">{</span>
			year<span class="token punctuation">:</span> <span class="token punctuation">{</span>
  				<span class="token keyword">type</span><span class="token punctuation">:</span> String<span class="token punctuation">,</span>
				<span class="token keyword">require</span><span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
				trim<span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
		<span class="token punctuation">}</span><span class="token punctuation">,</span>
			month<span class="token punctuation">:</span> <span class="token punctuation">{</span>
			    <span class="token keyword">type</span><span class="token punctuation">:</span> String<span class="token punctuation">,</span>
		    	<span class="token keyword">require</span><span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
				trim<span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
		<span class="token punctuation">}</span><span class="token punctuation">,</span>
	<span class="token punctuation">}</span><span class="token punctuation">,</span>
	<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
</li>
<li>
<p>Empresas</p>
<pre class=" language-typescript"><code class="prism  language-typescript"><span class="token keyword">const</span> businessSchema <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">Schema</span><span class="token operator">&lt;</span>IBusiness<span class="token operator">&gt;</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
	cuit<span class="token punctuation">:</span> <span class="token punctuation">{</span>
		 <span class="token keyword">type</span><span class="token punctuation">:</span> Number<span class="token punctuation">,</span>
			<span class="token keyword">require</span><span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
			trim<span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
	<span class="token punctuation">}</span><span class="token punctuation">,</span>
	razon_social<span class="token punctuation">:</span> <span class="token punctuation">{</span>
		<span class="token keyword">type</span><span class="token punctuation">:</span> String<span class="token punctuation">,</span>
		<span class="token keyword">require</span><span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
		trim<span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
	<span class="token punctuation">}</span><span class="token punctuation">,</span>
	 report<span class="token punctuation">:</span> <span class="token punctuation">{</span>
		 <span class="token keyword">type</span><span class="token punctuation">:</span> <span class="token punctuation">[</span>
			<span class="token punctuation">{</span>
				<span class="token keyword">type</span><span class="token punctuation">:</span> Schema<span class="token punctuation">.</span>Types<span class="token punctuation">.</span>ObjectId<span class="token punctuation">,</span>
				ref<span class="token punctuation">:</span> <span class="token string">"Report"</span><span class="token punctuation">,</span>
			 <span class="token punctuation">}</span><span class="token punctuation">,</span>
		<span class="token punctuation">]</span><span class="token punctuation">,</span>
	<span class="token punctuation">}</span><span class="token punctuation">,</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
</li>
<li>
<p>Productos</p>
<pre class=" language-typescript"><code class="prism  language-typescript"><span class="token keyword">const</span> productsSchema <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">Schema</span><span class="token operator">&lt;</span>IProduct<span class="token operator">&gt;</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
	denominacion<span class="token punctuation">:</span> <span class="token punctuation">{</span>
		<span class="token keyword">type</span><span class="token punctuation">:</span> String<span class="token punctuation">,</span>
		<span class="token keyword">require</span><span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
		trim<span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
 <span class="token punctuation">}</span><span class="token punctuation">,</span>
	codigo_ean<span class="token punctuation">:</span> <span class="token punctuation">{</span>
		<span class="token keyword">type</span><span class="token punctuation">:</span> Number<span class="token punctuation">,</span>
		<span class="token keyword">require</span><span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
		trim<span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
	<span class="token punctuation">}</span><span class="token punctuation">,</span>
	precio_unidad<span class="token punctuation">:</span> <span class="token punctuation">{</span>
		<span class="token keyword">type</span><span class="token punctuation">:</span> Number<span class="token punctuation">,</span>
		<span class="token keyword">require</span><span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
		trim<span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
	<span class="token punctuation">}</span><span class="token punctuation">,</span>
	unidad_medida<span class="token punctuation">:</span> <span class="token punctuation">{</span>
		<span class="token keyword">type</span><span class="token punctuation">:</span> String<span class="token punctuation">,</span>
		<span class="token keyword">require</span><span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
		trim<span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
	<span class="token punctuation">}</span><span class="token punctuation">,</span>
	cantidad_prod<span class="token punctuation">:</span> <span class="token punctuation">{</span>
		<span class="token keyword">type</span><span class="token punctuation">:</span> Number<span class="token punctuation">,</span>
		<span class="token keyword">require</span><span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
		trim<span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
	<span class="token punctuation">}</span><span class="token punctuation">,</span>
	cantidad_vend<span class="token punctuation">:</span> <span class="token punctuation">{</span>
			<span class="token keyword">type</span><span class="token punctuation">:</span> Number<span class="token punctuation">,</span>
			<span class="token keyword">require</span><span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
			trim<span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
	<span class="token punctuation">}</span><span class="token punctuation">,</span>
	report<span class="token punctuation">:</span> <span class="token punctuation">{</span>
			<span class="token keyword">type</span><span class="token punctuation">:</span> Schema<span class="token punctuation">.</span>Types<span class="token punctuation">.</span>ObjectId<span class="token punctuation">,</span>
			ref<span class="token punctuation">:</span> <span class="token string">"Report"</span><span class="token punctuation">,</span>
	<span class="token punctuation">}</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
</li>
<li>
<p>Usuarios Empresas</p>
<pre class=" language-typescript"><code class="prism  language-typescript"><span class="token keyword">const</span> userBusinessSchema <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">Schema</span><span class="token operator">&lt;</span>IUserBusiness<span class="token operator">&gt;</span> <span class="token punctuation">(</span><span class="token punctuation">{</span>
		cuit <span class="token punctuation">:</span> <span class="token punctuation">{</span>
				<span class="token keyword">type</span> <span class="token punctuation">:</span> Number<span class="token punctuation">,</span>
				unique <span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
				trim<span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
				<span class="token keyword">require</span><span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
				min <span class="token punctuation">:</span> <span class="token punctuation">[</span><span class="token number">11</span><span class="token punctuation">,</span> <span class="token string">'El CUIT debe tener 11 digitos'</span><span class="token punctuation">]</span>
		<span class="token punctuation">}</span><span class="token punctuation">,</span>
		razon_social <span class="token punctuation">:</span> <span class="token punctuation">{</span>
				<span class="token keyword">type</span> <span class="token punctuation">:</span> String<span class="token punctuation">,</span>
				<span class="token keyword">require</span> <span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
				trim<span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
		<span class="token punctuation">}</span><span class="token punctuation">,</span>
		industria <span class="token punctuation">:</span> <span class="token punctuation">{</span>
				<span class="token keyword">type</span><span class="token punctuation">:</span> String<span class="token punctuation">,</span>
				<span class="token keyword">require</span><span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
				trim<span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
		<span class="token punctuation">}</span><span class="token punctuation">,</span>
		email <span class="token punctuation">:</span> <span class="token punctuation">{</span>
				<span class="token keyword">type</span> <span class="token punctuation">:</span> String<span class="token punctuation">,</span>
				unique <span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
				<span class="token keyword">require</span> <span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
				trim<span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
		<span class="token punctuation">}</span><span class="token punctuation">,</span>
		tel <span class="token punctuation">:</span> <span class="token punctuation">{</span>
				<span class="token keyword">type</span> <span class="token punctuation">:</span> Number<span class="token punctuation">,</span>
				unique <span class="token punctuation">:</span><span class="token keyword">true</span><span class="token punctuation">,</span>
				<span class="token keyword">require</span> <span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
				trim <span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
		<span class="token punctuation">}</span><span class="token punctuation">,</span>
		ciudad <span class="token punctuation">:</span> <span class="token punctuation">{</span>
				<span class="token keyword">type</span> <span class="token punctuation">:</span> String<span class="token punctuation">,</span>
				<span class="token keyword">require</span> <span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
				trim <span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
		<span class="token punctuation">}</span><span class="token punctuation">,</span>
		password <span class="token punctuation">:</span> <span class="token punctuation">{</span>
				<span class="token keyword">type</span> <span class="token punctuation">:</span> String<span class="token punctuation">,</span>
				<span class="token keyword">require</span> <span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
				trim <span class="token punctuation">:</span> <span class="token keyword">true</span><span class="token punctuation">,</span>
				minLength <span class="token punctuation">:</span> <span class="token punctuation">[</span><span class="token number">6</span><span class="token punctuation">,</span> <span class="token string">'¡La constraseña debe tener al menos 6 caracteres!'</span><span class="token punctuation">]</span>
		<span class="token punctuation">}</span>
	<span class="token punctuation">}</span><span class="token punctuation">)</span>
</code></pre>
</li>
</ul>
</li>
</ul>
<ul>
<li>
<p><strong>Rutas</strong><br>
<em>En esta primera entrega solo trabajaremos de forma local, debido a esto se especifican las siguientes rutas</em></p>
<ul>
<li>
<p>Rutas para manipular reportes, todas estas rutas deben llevar en el Header de la petición el token de validación.</p>
<ul>
<li>
<p>Obtengo todos los reportes asociados a la empresa autenticada.</p>
<blockquote>
<p>GET localhost:3000/api/reports</p>
</blockquote>
</li>
<li>
<p>Cargo un reporte asociado a la empresa autenticada.</p>
<blockquote>
<p>POST localhost:3000/api/reports</p>
</blockquote>
</li>
<li>
<p>Actualizo un reporte asociado a la empresa autenticada, se considera solo que se envian nuevos productos. Se pasa por parametro el id del reporte.</p>
<blockquote>
<p>PUT localhost:3000/api/reports/:_id</p>
</blockquote>
</li>
<li>
<p>Elimino un reporte asociado a la empresa autenticada. Se pasa por parametro el id del reporte.</p>
<blockquote>
<p>DELETE localhost:3000/api/reports/:_id</p>
</blockquote>
</li>
</ul>
</li>
<li>
<p>Rutas para manipular la autenticación de empresas, estas rutas devuelven en el Header el token de autenticación necesario para acceder a las rutas arriba mencionadas.</p>
<ul>
<li>
<p>Registro una empresa</p>
<blockquote>
<p>POST localhost:3000/api/signup</p>
</blockquote>
</li>
<li>
<p>Autentica una empresa</p>
<blockquote>
<p>POST localhost:3000/api/login</p>
</blockquote>
</li>
</ul>
</li>
</ul>
</li>
<li>
<p><strong>Ejemplo</strong></p>
<ul>
<li>
<p>De la petición POST a <code>localhost:3000/api/signup</code></p>
<pre class=" language-json"><code class="prism  language-json">	<span class="token punctuation">{</span>
	<span class="token string">"cuit"</span> <span class="token punctuation">:</span> <span class="token number">20391791199</span><span class="token punctuation">,</span>
	<span class="token string">"razon_social"</span> <span class="token punctuation">:</span> <span class="token string">"SANCOR SA"</span><span class="token punctuation">,</span>
	<span class="token string">"industria"</span> <span class="token punctuation">:</span> <span class="token string">"Lacteos"</span><span class="token punctuation">,</span>
	<span class="token string">"email"</span> <span class="token punctuation">:</span> <span class="token string">"sancor@gmail.com"</span><span class="token punctuation">,</span> 
	<span class="token string">"tel"</span> <span class="token punctuation">:</span> <span class="token number">3624771222</span><span class="token punctuation">,</span>
	<span class="token string">"ciudad"</span> <span class="token punctuation">:</span> <span class="token string">"Resistencia"</span><span class="token punctuation">,</span>
	<span class="token string">"password"</span> <span class="token punctuation">:</span> <span class="token string">"sancorelmejor"</span>
	<span class="token punctuation">}</span>
</code></pre>
</li>
<li>
<p>De la petición POST a <code>localhost:3000/api/login</code></p>
<pre class=" language-json"><code class="prism  language-json"><span class="token punctuation">{</span>
	<span class="token string">"email"</span> <span class="token punctuation">:</span> <span class="token string">"sancor@gmail.com"</span><span class="token punctuation">,</span>
	<span class="token string">"password"</span> <span class="token punctuation">:</span> <span class="token string">"sancorelmejor"</span>
<span class="token punctuation">}</span>
</code></pre>
</li>
<li>
<p>De la petición POST a <code>localhost:3000/api/reports</code></p>
<pre class=" language-json"><code class="prism  language-json"><span class="token punctuation">{</span>
	<span class="token string">"infoEmpresa"</span><span class="token punctuation">:</span> <span class="token punctuation">{</span>
			<span class="token string">"cuit"</span><span class="token punctuation">:</span> <span class="token number">20391791199</span><span class="token punctuation">,</span>
			<span class="token string">"razon_social"</span> <span class="token punctuation">:</span> <span class="token string">"SANCOR SA"</span>
			<span class="token punctuation">}</span><span class="token punctuation">,</span>
	<span class="token string">"listaRegistro"</span><span class="token punctuation">:</span> <span class="token punctuation">[</span>
			<span class="token punctuation">{</span>
			<span class="token string">"denominacion"</span> <span class="token punctuation">:</span> <span class="token string">"Yogurt"</span><span class="token punctuation">,</span>
			<span class="token string">"codigo_ean"</span><span class="token punctuation">:</span> <span class="token number">9523113131251</span><span class="token punctuation">,</span>
			<span class="token string">"precio_unidad"</span><span class="token punctuation">:</span> <span class="token number">1</span><span class="token punctuation">,</span>
			<span class="token string">"unidad_medida"</span><span class="token punctuation">:</span> <span class="token string">"Lt"</span><span class="token punctuation">,</span>
			<span class="token string">"cantidad_prod"</span><span class="token punctuation">:</span> <span class="token number">2</span><span class="token punctuation">,</span>
			<span class="token string">"cantidad_vend"</span><span class="token punctuation">:</span> <span class="token number">1</span>
		 <span class="token punctuation">}</span><span class="token punctuation">,</span> 
			<span class="token punctuation">{</span>
			<span class="token string">"denominacion"</span> <span class="token punctuation">:</span> <span class="token string">"Yogurt"</span><span class="token punctuation">,</span>
			<span class="token string">"codigo_ean"</span><span class="token punctuation">:</span> <span class="token number">9217131934313</span><span class="token punctuation">,</span>
			<span class="token string">"precio_unidad"</span><span class="token punctuation">:</span> <span class="token number">1</span><span class="token punctuation">,</span>
			<span class="token string">"unidad_medida"</span><span class="token punctuation">:</span> <span class="token string">"Lt"</span><span class="token punctuation">,</span>
			<span class="token string">"cantidad_prod"</span><span class="token punctuation">:</span> <span class="token number">2</span><span class="token punctuation">,</span>
			<span class="token string">"cantidad_vend"</span><span class="token punctuation">:</span> <span class="token number">1</span>
		<span class="token punctuation">}</span>
	<span class="token punctuation">]</span><span class="token punctuation">,</span>
	<span class="token string">"periodo"</span><span class="token punctuation">:</span> <span class="token punctuation">{</span>
			<span class="token string">"year"</span><span class="token punctuation">:</span> <span class="token string">"2021"</span><span class="token punctuation">,</span>
			<span class="token string">"month"</span><span class="token punctuation">:</span> <span class="token string">"12"</span>
	<span class="token punctuation">}</span>
<span class="token punctuation">}</span>
</code></pre>
</li>
</ul>
</li>
<li>
<p><strong>Algunas validaciones importantes que deben tener los datos enviados.</strong></p>
<ul>
<li>CUIT de 11 digitos.</li>
<li>PASSWORD de 6 digitos como minimo.</li>
<li>CODIGO EAN de 13 digitos.</li>
<li>EMAIL debe tener el formato correcto. <a href="mailto:example@gmail.com">example@gmail.com</a></li>
</ul>
</li>
</ul>
</div>
</body>

</html>
