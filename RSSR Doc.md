---


---

<h1 id="rssr-structure">RSSR Structure</h1>
<h2 id="provider">Provider</h2>
<p>Head of the app, fundamental settings for starting the app are here.</p>
<h2 id="public">Public</h2>
<p>Location of public files ( all the file in this folder will be accessible directly).</p>
<h2 id="src">SRC</h2>
<p>Body of the app, 90% of the expected goals of the app will be defined in this folder.</p>
<h2 id="babelrc">.babelrc</h2>
<p>Settings of babel</p>
<h2 id="env">.env</h2>
<p>Contains environmental variables for different modes</p>
<h2 id="eslint">eslint</h2>
<p>Eslint settings which help us code easier and cleaner</p>
<h2 id="gitignore-package.json--readme">gitignore, package.json &amp; readme</h2>
<p>Fundamental requirements</p>
<h2 id="rssrproviderserverdevelopment.js">RSSR/provider/server/development.js</h2>
<h1 id="development.js">development.js</h1>
<p>This file has three parts. The first part includes some “import” commands. The second part includes some definitions.</p>
<blockquote>
<p><code>const express = require('express')</code><br>
<code>const app = express()</code></p>
</blockquote>
<p>here we are creating an express app from <code>Express.js</code> framework. This app helps us to make a <code>nodejs</code> web server for handling the requests to the server and their responses.</p>
<blockquote>
<p><code>const cookieParser = require('cookie-parser')</code><br>
<code>app.use(cookieParser())</code></p>
</blockquote>
<p>calling the <code>cookieParser</code> middleware. This middleware parses cookie header and populate <code>req.cookies</code> with an object keyed by the cookie names. In RSSR the user authentications are done by using cookies.</p>
<blockquote>
<p><code>const {DIST_ROUTE, PUBLIC_PATH} = require('../setup/constant')</code></p>
</blockquote>
<p>importing <code>constant.js</code> file which contains project configs and constants.</p>
<blockquote>
<p><code>app.use(express.static(PUBLIC_PATH))</code></p>
</blockquote>
<p>serving static files by using the<code>express.static</code> built-in middleware function in Express in a directory named <code>PUBLIC_PATH</code>.</p>
<blockquote>
<p><code>const webpack = require('webpack')</code><br>
<code>const config = require('../webpack/development')</code><br>
<code>const compiler = webpack(config)</code></p>
</blockquote>
<p>configuring a compiler with development’s config of <code>webpack</code>. This compiler is sent to  <code>webpackDevMiddleware</code> in the following lines.</p>
<blockquote>
<p><code>const webpackDevMiddleware = require('webpack-dev-middleware') app.use(webpackDevMiddleware(compiler, { serverSideRender: true, publicPath: DIST_ROUTE }))</code></p>
</blockquote>
<p>by using <code>webpackDevMiddleware</code>, there would not be any delays for compiling because this middleware can recognize the changed packages and build at the same time.<br>
we can only use <code>webpackDevMiddleware</code> for development.</p>
<blockquote>
<p><code>app.use(webpackHotMiddleware(compiler.compilers.find(compiler =&gt; compiler.name === 'client')))</code></p>
</blockquote>
<p>in case of any change in imported files, refreshes the project in client side (refreshes the browser).</p>
<blockquote>
<p><code>app.use(webpackHotServerMiddleware(compiler))</code></p>
</blockquote>

