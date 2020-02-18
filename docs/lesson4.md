# Web Packages Configuration

Both development and production files have two configs at their disposal:

☑ **Client Level**

☑ **Server Level**

One part of the configs are the same for both levels, but some places are different

# Mode Development

**I.** **Client Level**

- Entry : It has two entries, one is webpack-hot-middleware and one is our client address inside the src and inside the render directory

- Module => Rules : First we do js and jsx with babel and eslint, then css and scss files with loaders respectively:

        Rssr-namespace

        sass-loader

        css-loader

        miniCssExtractplugin

        css-hot-loader

        And lastly loader for jquery injection

- Plugins : Open Browser Plugin Instead of open, we saw in the previous section that the  new tab would open after the project build

**II.** **Server Level**

- Entry : It has two entries, one is webpack-hot-middleware and one is our server address inside the src and inside the render directory

- Module => Rules : The js and jsx files are the same as the client level,

The css and scss sections are completely ignored because they are already produced and this is for the server part

- Plugins :  We only have the webpack hmr plugin

# Mode Productions

**I.** **Client Level**

- Entry : Only our client file address

- Module => Rules : Remove the linters and the css-hot-realder has also been deleted.

- Plugins : Open the deleted browser and replace webpack.optimize and add an optimize config section we use from TerserPlugin

**II.** **Server Level**

It's exactly like the client level, except the plugins and optimize are removed and the css and css are ignored.
