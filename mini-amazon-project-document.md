---


---

<h1 id="techstack"><strong>TechStack</strong></h1>
<ul>
<li><strong>Front-end</strong>: React with Vite and typescipt</li>
<li><strong>Back-end</strong>: Express.js with typescipt</li>
<li><strong>Database</strong>: MongoDB</li>
<li><strong>Auth</strong>: JWT</li>
<li><strong>State Mangament</strong>: Redux (for state management)</li>
<li><strong>UI Lib</strong>: Ant Design</li>
</ul>
<hr>
<h1 id="features"><strong>Features</strong></h1>
<h2 id="phase-1-done">Phase 1 (done)</h2>
<ul>
<li>Sign in Page</li>
<li>Sign up Page</li>
<li>Password recover Page</li>
<li>Auth APIs</li>
</ul>
<h2 id="phase-2">Phase 2</h2>
<ul>
<li>Product list Page</li>
<li>Product edit/create Page</li>
<li>Product detail Page</li>
<li>!!! Redux state management Middleware</li>
<li>Product list pagination Feature (backend)</li>
<li>Product list sorting Feature</li>
<li>Role related Feature (buttons)</li>
<li>Product APIs</li>
</ul>
<h2 id="phase-3">Phase 3</h2>
<ul>
<li>Cart Component / Page</li>
<li>Search bar Component ?</li>
<li>Cart price calculation &amp; promo Feature</li>
<li>State storage Feature (for user status)</li>
<li>Error Page &amp; Handler</li>
<li>Cart API</li>
<li>Promo API</li>
<li>Code Review &amp; Clean Up</li>
<li>Any others</li>
</ul>
<h1 id="schema"><strong>Schema</strong></h1>
<h2 id="user">User</h2>

<table>
<thead>
<tr>
<th>Attribute</th>
<th>Type</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>Email</td>
<td>string</td>
<td>yes</td>
</tr>
<tr>
<td>Password</td>
<td>string</td>
<td>yes</td>
</tr>
<tr>
<td>Role</td>
<td>string</td>
<td>yes</td>
</tr>
</tbody>
</table><h2 id="product">Product</h2>

<table>
<thead>
<tr>
<th>Attribute</th>
<th>Type</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>Name</td>
<td>string</td>
<td>yes</td>
</tr>
<tr>
<td>Description</td>
<td>string</td>
<td>yes</td>
</tr>
<tr>
<td>Category</td>
<td>string</td>
<td>yes</td>
</tr>
<tr>
<td>Price</td>
<td>number</td>
<td>yes</td>
</tr>
<tr>
<td>InStockQuant</td>
<td>number</td>
<td>yes</td>
</tr>
<tr>
<td>ImageURI</td>
<td>string</td>
<td>yes</td>
</tr>
<tr>
<td>CreateAt</td>
<td>Date</td>
<td>yes</td>
</tr>
<tr>
<td>UpdateAt</td>
<td>Date</td>
<td>no</td>
</tr>
</tbody>
</table><h2 id="cart">Cart</h2>

<table>
<thead>
<tr>
<th>Attribute</th>
<th>Type</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>UserId</td>
<td><a href="http://Obj.id">Obj.id</a></td>
<td>yes</td>
</tr>
<tr>
<td>Items</td>
<td>string</td>
<td>yes</td>
</tr>
<tr>
<td>Subtotal</td>
<td>number</td>
<td>yes</td>
</tr>
<tr>
<td>Discount</td>
<td>number</td>
<td>yes</td>
</tr>
<tr>
<td>total</td>
<td>number</td>
<td>yes</td>
</tr>
<tr>
<td>UpdateAt</td>
<td>Date</td>
<td>no</td>
</tr>
</tbody>
</table><h2 id="items">Items</h2>

<table>
<thead>
<tr>
<th>Attribute</th>
<th>Type</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td>ProductId</td>
<td><a href="http://Obj.id">Obj.id</a></td>
<td>yes</td>
</tr>
<tr>
<td>Quantity</td>
<td>number</td>
<td>yes</td>
</tr>
<tr>
<td>PriceSnapShot</td>
<td>number</td>
<td>yes</td>
</tr>
</tbody>
</table><h1 id="apis"><strong>APIs</strong></h1>
<ul>
<li>Server Side Port Number: 5200</li>
</ul>
<h2 id="auth">Auth</h2>
<ul>
<li>
<p><strong>Sign up API</strong></p>
<ul>
<li>POST  /api/auth/signup
<ul>
<li>BODY: EMAIL + PASSWORD</li>
</ul>
</li>
<li>Response
<ul>
<li>SUCESS 200
<ul>
<li>BODY JSON Schema:
<ul>
<li>role: string (enum type: ADMIN/REGULAR)</li>
<li>token: string</li>
</ul>
</li>
</ul>
</li>
<li>FAILURE 1 409 Email exists</li>
<li>FAILURE 2 500 Server Error</li>
</ul>
</li>
</ul>
</li>
<li>
<p><strong>Sign in API</strong></p>
<ul>
<li>POST  /api/auth/login
<ul>
<li>BODY: EMAIL + PASSWORD</li>
</ul>
</li>
<li>Response
<ul>
<li>SUCESS 201
<ul>
<li>BODY JSON Schema:
<ul>
<li>role: string (enum type: ADMIN/REGULAR)</li>
<li>token: string</li>
</ul>
</li>
</ul>
</li>
<li>FAILURE 1 404 NOT FOUND USER</li>
<li>FAILURE 2 400 EMAIL AND PASSWORD NOT MATCH</li>
<li>FAILURE 3 500  Server Error</li>
</ul>
</li>
</ul>
</li>
<li>
<p><strong>Recover password API</strong></p>
<ul>
<li>POST  /api/auth/recover
<ul>
<li>BODY  email</li>
</ul>
</li>
<li>Response
<ul>
<li>SUCESS 201 Email Sent</li>
</ul>
</li>
</ul>
</li>
<li>
<p><strong>Sign out API</strong></p>
<ul>
<li>POST /api/auth/signout</li>
<li>Response
<ul>
<li>SUCESS 200 OK</li>
<li>FAILURE 500  Server Error</li>
</ul>
</li>
</ul>
</li>
</ul>
<h2 id="product-1">Product</h2>
<p><strong>Retrive all products</strong></p>
<ul>
<li>GET /api/products</li>
<li>Response
<ul>
<li>SUCESS 200 Retreived
<ul>
<li>BODY JSON Schema:<br>
[{<br>
id: string,<br>
name: string,<br>
description: string,<br>
category: string,<br>
price: number,<br>
inStockQuant: number,<br>
imageURI: string<br>
createAt: Date<br>
updateAt: Date<br>
},<br>
…<br>
]</li>
</ul>
</li>
<li>FAILURE 500 Server Error</li>
</ul>
</li>
</ul>
<p><strong>Retrive one product</strong></p>
<ul>
<li>GET /api/products/{id}/</li>
<li>Response
<ul>
<li>SUCESS 200 Retreived
<ul>
<li>BODY JSON Schema:<br>
{<br>
id: string,<br>
name: string,<br>
description: string,<br>
category: string,<br>
price: number,<br>
inStockQuant: number,<br>
imageURI: string<br>
createAt: Date<br>
updateAt: Date<br>
}</li>
</ul>
</li>
<li>FAILURE 404 Product Not Found</li>
<li>FAILURE 500 Server Error</li>
</ul>
</li>
</ul>
<p><strong>Retrive product list paginated &amp; sorted</strong></p>
<ul>
<li>GET /api/products?offset={}&amp;limit={}&amp;sortby={}
<ul>
<li>SortType: ‘Last’ | ‘PriceAsc’ | ‘PriceDes’</li>
</ul>
</li>
<li>Response
<ul>
<li>SUCESS 200
<ul>
<li>BODY JSON Schema:<br>
[{<br>
_id: string,<br>
name: string,<br>
description: string,<br>
category: string,<br>
price: number,<br>
inStockQuant: number,<br>
imageURI: string<br>
createAt: Date<br>
updateAt: Date<br>
},<br>
…<br>
] (based on sorted result)</li>
</ul>
</li>
<li>FAILURE 500 Server Error</li>
</ul>
</li>
</ul>
<p><strong>Add product</strong></p>
<ul>
<li>POST /api/products
<ul>
<li>HEADER Authorization: Bearer TOKEN</li>
<li>BODY Product JSON Schema:
<ul>
<li>{<br>
name: string,<br>
description: string,<br>
category: string,<br>
price: number,<br>
inStockQuant: number,<br>
imageURI: string<br>
}</li>
</ul>
</li>
</ul>
</li>
<li>Response
<ul>
<li>SUCESS 201 Product Added
<ul>
<li>BODY JSON Schema:<br>
{<br>
_id: string,<br>
name: string,<br>
description: string,<br>
category: string,<br>
price: number,<br>
inStockQuant: number,<br>
imageURI: string<br>
createAt: Date<br>
updateAt: Date<br>
}</li>
</ul>
</li>
<li>FAILURE 403 You don’t have permission</li>
<li>FAILURE 500 Server Error</li>
</ul>
</li>
</ul>
<p><strong>Update product</strong></p>
<ul>
<li>PUT /api/products/{id}/
<ul>
<li>HEADER Authorization: Bearer TOKEN</li>
<li>BODY Product</li>
</ul>
</li>
<li>Response
<ul>
<li>SUCESS 201 Product updated
<ul>
<li>BODY JSON Schema:<br>
{<br>
_id: string,<br>
name: string,<br>
description: string,<br>
category: string,<br>
price: number,<br>
inStockQuant: number,<br>
imageURI: string<br>
createAt: Date<br>
updateAt: Date<br>
}</li>
</ul>
</li>
<li>FAILURE 404 Product not found</li>
<li>FAILURE 403 You don’t have permission</li>
<li>FAILURE 500 Server Error</li>
</ul>
</li>
</ul>
<p><strong>Delete product</strong></p>
<ul>
<li>DELETE /api/products/{id}/
<ul>
<li>HEADER Authorization: Bearer TOKEN</li>
</ul>
</li>
<li>Response
<ul>
<li>SUCESS 204 Product deleted</li>
<li>FAILURE 404 Product not found</li>
<li>FAILURE 403 You don’t have permission</li>
<li>FAILURE 500 Server Error</li>
</ul>
</li>
</ul>
<p><strong>Retrive products count</strong></p>
<ul>
<li>GET /api/products/count</li>
<li>Response
<ul>
<li>SUCESS 200 Retreived
<ul>
<li>BODY JSON Schema:
<ul>
<li>Count: number</li>
</ul>
</li>
</ul>
</li>
<li>FAILURE 500 Server Error</li>
</ul>
</li>
</ul>
<p><strong>Search for specific products (WIP)</strong></p>
<ul>
<li>GET /api/products/search?q={}</li>
<li>Response
<ul>
<li>SUCESS 200 Filtered product list (could be empty)</li>
<li>FAILURE 400 Bad Input</li>
<li>FAILURE 500 Server Error</li>
</ul>
</li>
</ul>
<h2 id="cart-1">Cart</h2>
<p><strong>Retrive cart</strong></p>
<ul>
<li>GET /api/cart
<ul>
<li>HEADER bearer TOKEN</li>
</ul>
</li>
<li>Response
<ul>
<li>SUCESS 200
<ul>
<li>BODY JSON Schema:<br>
{<br>
products: cartItem[]:<br>
{<br>
product_id: string<br>
product_name: string<br>
product_imgUri: string<br>
quantity: number<br>
price_snapshot: number<br>
}<br>
subtotal: number<br>
discount: number<br>
total: number<br>
updateAt: Date<br>
}</li>
</ul>
</li>
<li>FAILURE 403 You don’t have access</li>
<li>FAILURE 500 Server Error</li>
</ul>
</li>
</ul>
<p><strong>Add cart item (triggered when add new item)</strong></p>
<ul>
<li>POST /api/cart/items
<ul>
<li>HEADER bearer TOKEN</li>
<li>BODY {product_id: string}</li>
</ul>
</li>
<li>Response
<ul>
<li>SUCESS 200 Item added</li>
<li>FAILURE 403 You don’t have access</li>
<li>FAILURE 404 Product not found</li>
<li>FAILURE 500 Server Error</li>
</ul>
</li>
</ul>
<p><strong>Update cart item</strong></p>
<ul>
<li>PUT /api/cart/items/:productId
<ul>
<li>HEADER bearer TOKEN</li>
<li>BODY {quantity: number}</li>
</ul>
</li>
<li>Response
<ul>
<li>SUCESS 200 Item updated</li>
<li>FAILURE 403 You don’t have access</li>
<li>FAILURE 404 Product not found</li>
<li>FAILURE 500 Server Error</li>
</ul>
</li>
</ul>
<p><strong>Delete cart item  (triggered when remove last quantity)</strong></p>
<ul>
<li>PUT /api/cart/items/:productId
<ul>
<li>HEADER bearer TOKEN</li>
</ul>
</li>
<li>Response
<ul>
<li>SUCESS 204 Item removed</li>
<li>FAILURE 403 You don’t have access</li>
<li>FAILURE 404 Product not found</li>
<li>FAILURE 500 Server Error</li>
</ul>
</li>
</ul>
<p><strong>Empty cart</strong></p>
<ul>
<li>DELETE /api/cart
<ul>
<li>HEADER bearer TOKEN</li>
</ul>
</li>
<li>Response
<ul>
<li>SUCESS 204 Cleared</li>
<li>FAILURE 403 You don’t have access</li>
<li>FAILURE 500 Server Error</li>
</ul>
</li>
</ul>
<p>** Apply promotion code **</p>
<ul>
<li>POST /api/cart/promo
<ul>
<li>HEADER bearer TOKEN</li>
<li>BODY {Promocode: string}</li>
</ul>
</li>
<li>Response
<ul>
<li>SUCESS 200 Applied</li>
<li>FAILURE 403 You don’t have access</li>
<li>FAILURE 404 Promocode not found</li>
<li>FAILURE 409 Promocode already used</li>
<li>FAILURE 500 Server Error</li>
</ul>
</li>
</ul>

