<h1>Translation Simple Asset</h1>

Blog - Simple-Assets supporters - Contract - Game example - Documentation - NFT Creator - Market - Overview

Contact us - Join us on Telegram - © All Rights Reserved - See more

What are Blockchain Based Digital Assets? 

What is Simple Assets?

Token Types


A simple standard for digital assets (ie. Non-Fungible Tokens)
for EOSIO blockchains by <a href="https://cryptolions.io/home">CryptoLions</a>.


<h3 style="text-align: center;">Our Philosophy</h3>
Simple Assets started with the idea that a digital asset is a promise from the asset creator to the entire community of possible owners. What is the promise? It has four parts:
<p style="text-align: left;">1. that a chunk of the asset’s data will never change — <code>idata</code> .</p>
<p style="text-align: left;">2. that the asset author reserves the right to modify another chunk of the asset’s data — <code>mdata</code> — or to transfer this privilege to another party.</p>
<p style="text-align: left;">3. that ownership functions (transferring, offering, lending, burning) are expressed entirely outside the control of the author.</p>
<p style="text-align: left;">4. that the code controlling assets is transparent and overseen by reputable parties.</p>


Welcome to the Simple Assets documentation Hub.

For additional technical information, please also see the <a href="https://github.com/CryptoLions/SimpleAssets/blob/master/README.md">README</a> file in our <a href="https://github.com/cryptolions/SimpleAssets">Github</a> and the action and parameter descriptions in <a href="https://github.com/CryptoLions/SimpleAssets/blob/master/include/SimpleAssets.hpp">SimpleAssets.hpp</a>.


<ul>
 	<li><a href="https://simpleassets.io/overview/what-are-blockchain-based-digital-assets-and-why-should-we-care/#the_basics">The Basics: What are Blockchain Based Digital Assets?</a></li>
 	<li><a href="https://simpleassets.io/overview/what-are-blockchain-based-digital-assets-and-why-should-we-care/#why_should_games_care">Why Should Games care about Blockchain Based Digital Assets?</a></li>
 	<li><a href="https://simpleassets.io/what-is-simple-assets/#what_is_simple_assets">What is Simple Assets?</a></li>
 	<li><a href="https://simpleassets.io/what-is-simple-assets/#types_of_digital_assets">Types of Digital Assets: NFTs, FTs, and NTTs</a></li>
 	<li><a href="https://simpleassets.io/what-is-simple-assets/#ways_to_integrate">Different Ways to Integrate Simple Assets</a></li>
</ul>

________________________________________________________________________________________________________________________________________________________________________________

What are Blockchain Based Digital Assets?  And why should we care?

<ul>
 	<li><a href="#the_basics">The Basics: What are Blockchain Based Digital Assets?</a></li>
 	<li><a href="#why_should_games_care">Why Should Games care about Blockchain Based Digital Assets?</a></li>

</ul>
 

 

<hr />

<h2 id="the_basics">The Basics: What are Blockchain Based Digital Assets?</h2>
They are digital things whose ownership is expressed and controlled on a blockchain.


 

 

<hr />

<h2 id="why_should_games_care">Why Should Games care about Blockchain Based Digital Assets?</h2>
Because they can create new business models and new relationships with players.


________________________________________________________________________________________________________________________________________________________________________________
 
What is Simple Assets?

<ul>
 	<li><a href="#what_is_simple_assets">What is Simple Assets?</a></li>
 	<li><a href="#types_of_digital_assets">Types of Digital Assets: NFTs, FTs, and NTTs</a></li>
 	<li><a href="#ways_to_integrate">Different Ways to Integrate Simple Assets</a></li>
</ul>


<hr />

<h2 id="what_is_simple_assets">What is Simple Assets?</h2>
The best and most popular digital asset standard for EOSIO blockchains.



 

 

<hr />

<h2 id="types_of_digital_assets">Types of Digital Assets: NFTs, FTs, and NTTs</h2>
NFTs = Non Fungible Tokens
FTs = Fungible Tokens
NTTs = Non-Transferable Tokens



 

 

<hr />

<h2 id="ways_to_integrate">Different Ways to Integrate Simple Assets</h2>
The big design decision is whether leave items with players and check their inventories, or to have players transfer items into the game.


________________________________________________________________________________________________________________________________________________________________________________

Token Types - NFTs, FTs, NTTs

<iframe src="https://www.youtube.com/embed/YjLoeT88UFA" width="560" height="315" frameborder="0" allowfullscreen="allowfullscreen"><span style="display: inline-block; width: 0px; overflow: hidden; line-height: 0;" data-mce-type="bookmark" class="mce_SELRES_start">﻿</span></iframe>

<h3>Non-Fungible Tokens (NFTs)</h3>

NFTs are the most common type of digital assets. They are used to express unique tokens.

<strong>NFT Structure</strong>

Simple Asset NFTs are divided into <span class="codeblock">mdata</span> (data which the author can update at any time, regardless of ownership), and <span class="codeblock">idata</span> (data which is set upon the NFT's creation and can never be updated).

Both are stringified JSONs. For example: <span class="codeblock">{\"key1\":\"some-string\", \"key2\":5}</span>

<span class="codeblock">Category</span> is an optional field that lets you group your NFTs for convenience. Category names must be less than or equal to 12 characters (a-z, 1-5).

<strong>Offer/Claim versus Transfer</strong> - If you transfer an NFT, the sender pays for RAM. As an alternative, you can simply offer the NFT, and the user claiming will pay for their RAM. <em>(Note: we are working toward a feature that allows NFT authors to reserve a lot of RAM which will spare users for paying for transfers.)</em>

<strong>RAM usage</strong>

RAM usage for NFTs depends on how much data is stored in the idata and mdata fields. If they both empty, each NFT takes up <strong>276 bytes</strong>.

Each symbol in <span class="codeblock">idata</span> and <span class="codeblock">mdata</span> is +1 byte.

 

<h3>Fungible Tokens (FTs)</h3>

Dapps which need Fungible tokens should decide between using the standard eosio.token contract, and the Simple Assets contract. Here are the differences:

In Simple Assets,
<ul>
 	<li>Scope is Author instead of Symbol</li>
 	<li>Stat table includes also additional data about each FT.</li>
 	<li>For transfers you need to use <span class="codeblock">transferf</span> action from SA contract.</li>
 	<li>If author sets <span class="codeblock">authorcontrol</span> flag, the author can transfers/burn/etc user's FTs independent of user's consent.</li>
 	<li>The table which tracks FTs includes the author's account name, allowing different dapps to have FTs with the same name. (Example: <a href="https://bloks.io/contract?tab=Tables&table=accounts&account=simpleassets&scope=bohdanbohdan&limit=100">https://bloks.io/contract?tab=Tables&table=accounts&account=simpleassets&scope=bohdanbohdan&limit=100</a>)</li>
</ul>
<em>(Note: Fungible Tokens also have offer/claim functionality as an alternative to transfers. For FTs, the only time the sender would pay for RAM would be if the receiver never before held those FTs. It uses approximately 300 bytes to create the FT table.)</em>

 

<h3>Non-Transferrable Tokens (NTTs)</h3>

The two most likely use cases for NTTs are

licenses which can be granted to an account, but not transfered.
prizes and awards given to a particular account.

The reasons for using NTTs are:

the NTTs appearing in third party asset explorers.
some functionality is handled by Simple Assets.

More on NTTs: <a href="https://medium.com/@cryptolions/introducing-non-transferable-tokens-ntts-2f1a532bf170">https://medium.com/@cryptolions/introducing-non-transferable-tokens-ntts-2f1a532bf170</a>


 
 
