#Reaction Theme Customization Exercise for version 1.5.10







### Old information based on my previous excercise using an older version of reaction over at [reaction-hydrotik-plugin](https://github.com/hydrotik/reaction-hydrotik-plugin)

This is based off of Brent Hover's [reaction example plugin](https://github.com/reactioncommerce/reaction-example-plugin) starter. Brent is very helpful and hopefully this minimizes the questions he gets asked in the future;) Images in this project are large files, they have yet to be optimized for responsive. Until then, use as is.

Photography/Product Images/Editorials royalty free by:
* [pixabay](https://pixabay.com)
* [pexels](https://www.pexels.com)
* [unsplash](https://unsplash.com)

```bash
reaction reset -n && reaction
```


### React Slick Installation (Better process for installing plugin deps?)

```bash
npm install react-slick
```

Also install slick-carousel for css and font

```bash
npm install slick-carousel
```

**Move files in public to your root public folder**
You should move some of the react slick static assets into public as well. Not sure of a practical solution to this yet. (See Wants list below)


### Some helpful things to be aware of:

**Update your project to get the latest from Reaction master:**
```bash
reaction pull
```


**Update your Reaction dependencies (like a ```meteor update```):**
```bash
reaction update
```

Do the ```reaction pull``` first to make sure there are no git merge conflicts. If you encounter an error then run:
```bash
git reset HEAD --hard
```


### More helpful things...

* I suggest using [RoboMongo](https://robomongo.org) 
* Connect with Roboongo and delete the <blank> document under the Shops Collection to see the aboutus.html static template. When you have more than one Document in the Shop Collection, Reaction will insert a shop name into the url path.
* Git submodules are most helpful when working with Heroku. Reaction Commerce will be your upstream and your instantiated Reaction project will be your origin master. Your plugin will be your submodule and should be editied in .gitmodules. For example:
```
[submodule "reaction-hydrotik-plugin"]
    path = imports/plugins/custom/reaction-hydrotik-plugin
    url = git://github.com/hydrotik/reaction-hydrotik-plugin.git
```
* Be sure to use the github url format in your submodule as there might be a known conflict with Heroku.
* Don't forget to commit changes to your Reaction instance after you commit your submodule changes before pushing to Heroku.
* productsLanding in templates/layouts has two templates in it. The later is designed to show a best sellers product display only on the homepage. The default is set in register.js for the site, but for the homepage we override this template. This is set in client/defaults.js:
```javascript
Session.set("INDEX_OPTIONS", {
  template: "productsLandingIndex"
});
```


### Heroku things...

**Deploy to Heroku**
```bash
git push heroku master
```

* For build caching problems:
```bash
heroku config:set --app appname BUILDPACK_CLEAR_CACHE=1
```

* For mongo connectivity ENV:
```bash
heroku config:set MONGO_URL=mongodb://[username]:[password]@pathtodb.com:[port],pathtodb.com:[port]/heroku_qhm1pvcm?replicaSet=rs-[rsid]
```


### Roadmap
- [x] CTA in Hero
- [x] Hero only on INDEX
- [ ] Category Left Hand Nav
- [x] Promo on all pages DEFAULT
- [ ] Reskin PDP
- [ ] Image optimization for responsive through Reaction or just as static assets
- [ ] Category Landing Pages
- [ ] Hero on Category Landing Pages

### Wants/Hopes from Reaction Commerce
- [ ] Process for installing NPM deps in plugin as well as static assets to root of Reaction project through Registry settings. (See my stab in register.js - settings)
- [ ] Membership
- [ ] Recently Viewed
- [ ] Product Ratings
- [ ] Product Reviews
- [ ] Faceted Search
- [ ] Group Orders
- [ ] Ability to create non product content (CMS)
- [ ] Content Management System from external or internal source that maps to URL structure
- [ ] SASS
- [ ] Promo Manager
- [ ] Category Landing Pages