<h1>Traducción de Simple Asset</h1>

Blog - Seguidores de Simple-Assets - Contacto - Ejemplo de juego - Documentación - Creador de NFT - Mercado - Resumen

Contáctenos - Únase a nuestro Telegram - © Todos los derechos reservados - Ver más

¿Qué son los activos digitales basados en blockchain? 

¿Qué es Simple Assets?

Tipos de tokens

Un estándar simple para activos digitales (por ejemplo, Tokens No Fungibles (NFT) para blockchains EOSIO por <a href="https://cryptolions.io/home">CryptoLions</a>.

<h3 style="text-align: center;">Nuestra filosofía</h3>

Simple Assets inició con la idea de que un activo digital es una promesa de un creador de activos hacia la comunidad de posibles titulares. ¿Cuál es esta promesa? Cuenta con cuatro partes:
<br><nr>
<p style="text-align: left;">1. Que una porción de la información del activo no va a cambiar nunca — <code>idata</code> .</p>.
<p style="text-align: left;">2. Que el autor del activo se reserva el derecho de modificar otra porción de la información del activo — <code>mdata</code> — o a transferir el privilegio de otra de las partes.</p>
<p style="text-align: left;">3. Que las funciones de titularidad (transferir, ofrecer, prestar, quemar) se expresan enteramente fuera del control del autor.</p>
<p style="text-align: left;">4. Que el código que controla los activos es transparente y supervisado por partes con reputación.</p>


Le damos la bienvenida al Hub de documentación de Simple Assets.

Para información técnica adicional, puede ver el archivo <a href="https://github.com/CryptoLions/SimpleAssets/blob/master/README.md">README</a> en nuestro <a href="https://github.com/cryptolions/SimpleAssets">Github</a> y las descripciones de acciones y parámetros en <a href="https://github.com/CryptoLions/SimpleAssets/blob/master/include/SimpleAssets.hpp">SimpleAssets.hpp</a>.


<ul>
 	<li><a href="https://simpleassets.io/overview/what-are-blockchain-based-digital-assets-and-why-should-we-care/#the_basics"> Fundamentos: ¿Qué son los activos digitales basados en blockchain?</a></li>
 	<li><a href="https://simpleassets.io/overview/what-are-blockchain-based-digital-assets-and-why-should-we-care/#why_should_games_care">¿Por qué los juegos deberían prestar atención a los activos digitales basados en blockchain?</a></li>
 	<li><a href="https://simpleassets.io/what-is-simple-assets/#what_is_simple_assets">¿Qué es Simple Assets?</a></li>
 	<li><a href="https://simpleassets.io/what-is-simple-assets/#types_of_digital_assets">Tipos de activos digitales: NFTs, FTs y NTTs.</a></li>
 	<li><a href="https://simpleassets.io/what-is-simple-assets/#ways_to_integrate">Formas distintas de integrar Simple Assets.</a></li>
</ul>

________________________________________________________________________________________________________________________________________________________________________________

¿Qué son los activos digitales basados en blockchain y por qué deberíamos prestarles atención?

<ul>
 	<li><a href="#the_basics">Fundamentos: ¿Qué son los activos digitales basados en blockchain y por qué deberíamos prestarles atención?</a></li>
 	<li><a href="#why_should_games_care">¿Por qué los juegos deberían prestar atención a los activos digitales basados en blockchain?</a></li>

</ul>
 

 

<hr />

<h2 id="the_basics">Fundamentos: ¿Qué son los activos digitales basados en blockchain?</h2>
Son cosas digitales cuya titularidad se expresa y controla en una blockchain.


 

 

<hr />

<h2 id="why_should_games_care">¿Por qué los juegos deberían prestar atención a los activos digitales basados en blockchain?</h2>
Porque pueden crear nuevos modelos de negocios y nuevas relaciones con los jugadores. 


________________________________________________________________________________________________________________________________________________________________________________
 
¿Qué es Simple Assets?

<ul>
 	<li><a href="#what_is_simple_assets">¿Qué es Simple Assets?</a></li>
 	<li><a href="#types_of_digital_assets">Tipos de activos digitales: NFTs, FTs y NTTs.</a></li>
 	<li><a href="#ways_to_integrate">Formas distintas de integrar Simple Assets.</a></li>
</ul>


<hr />

<h2 id="what_is_simple_assets">¿Qué es Simple Assets?</h2>
El mejor y más popular estándar para activos digitales para blockchains EOSIO.



 

 

<hr />

<h2 id="types_of_digital_assets">Tipos de activos digitales: NFTs, FTs y NTTs</h2>
NTFs = Tokens No Fungibles 
FTs = Tokens Fungibles 
NTTs = Tokens No Transferibles



 

 

<hr />

<h2 id="ways_to_integrate">Formas distintas de integrar Simple Assets</h2>
La decisión principal sobre diseño fue si mantener los ítems con los jugadores y revisar sus inventarios, o si los jugadores transfieren los ítems al juego.


________________________________________________________________________________________________________________________________________________________________________________

Tipos de tokens - NFTs, FTs, NTTs


<h3>Tokens No Fungibles (NFTs)</h3>

Los NFTs son el tipo más común de activos digitales. Son usados para expresar tokens únicos.

<strong>Estructura de NFT</strong>

Los NFTs de Simple Assets se dividen en <span class="codeblock">mdata</span> (información que el autor puede actualizar en cualquier momento, sin importar su titularidad), y <span class="codeblock">idata</span> (información que se incluye en la creación del NFT y que no puede ser actualizada).

Ambos son stringified JSONs. Por ejemplo: <span class="codeblock">{\"key1\":\"some-string\", \"key2\":5}</span>

<span class="codeblock">Category</span> es un campo adicional que permite agrupar los NFTs a conveniencia. Los nombres de categorías deben contener menos o igual a 12 caracteres (a-z, 1-5).

<strong>Oferta/Solicitud versus Transferencia</strong> - Si se transfiere un NFT, el emisor paga por el RAM. Como alternativa, se puede simplemente ofrecer un NFT, y el usuario solicitante pagará por el RAM. <em>(Nota: estamos trabajando en una función que permitirá a los autores de NFT a reservar un lote de RAM que podrá librar a los usuarios del pago por transferencias.)</em>

<strong>Uso de RAM</strong>

El uso de RAM para NFTs depende de cuánta información se guarda en los campos idata y mdata. Si ambos están vacíos, cada NFT tomará hasta <strong>276 bytes</strong>.

Cada símbolo en <span class="codeblock">idata</span> y <span class="codeblock">mdata</span> es +1 byte.

 

<h3>Tokens Fungibles (FTs)</h3>

Las dapps que necesitan Tokens Fungibles deberán decidir entre usar el contrato estándar eosio.token, o el contrato de Simple Assets. Estas son las diferencias:

En Simple Assets,
<ul>
 	<li>Scope es Author en vez de Symbol</li>
 	<li>Tablas de estadísticas incluyen también información adicional sobre cada FT.</li>
 	<li>Para transferencias se debe usar la acción <span class="codeblock">transferf</span> del contrato de SA.</li>
 	<li>Si el autor marca como <span class="codeblock">authorcontrol</span>, el autor puede transferir/quemar/etc. los FTs del usuario independientemente del consentimiento del usuario.</li>
 	<li>La tabla que monitorea FTs incluye el nombre de la cuenta del autor, permitiendo a diferentes apps tener FTs con el mismo nombre. (Ejemplo: <a href="https://bloks.io/contract?tab=Tables&table=accounts&account=simpleassets&scope=bohdanbohdan&limit=100">https://bloks.io/contract?tab=Tables&table=accounts&account=simpleassets&scope=bohdanbohdan&limit=100</a>)</li>
</ul>
<em>(Nota: Los Tokens Fungibles también tienen funciones de ofrecer/solicitar como alternativa a transferencias. Para FTs, el único momento en que el emisor deberá pagar por RAM es cuando el receptor nunca ha tenido esos FTs. Se usan aproximadamente 300 bytes para crear una tabla FT.)</em>

 

<h3>Tokens No Transferibles (NTTs)</h3>

Los dos casos de uso más conocidos para NTTs son

licencias que pueden ser otorgadas a una cuenta, pero no transferidas. 
premios y reconocimientos otorgados a una cuenta en particular.

Las razones para usar NTTs son:

los NTTs aparecen en exploradores de activos de terceros. 
alguna funcionalidad es manejada por Simple Assets.

Más sobre NTTs: <a href="https://medium.com/@cryptolions/introducing-non-transferable-tokens-ntts-2f1a532bf170">https://medium.com/@cryptolions/introducing-non-transferable-tokens-ntts-2f1a532bf170</a>


 
 
