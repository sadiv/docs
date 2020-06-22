# GREEN API DOCUMENT PORTAL BASED ON MKDOCS

![`media/exampleDocs.png`](media/exampleDocs.png)

## Installing

1.Install Python by downloading an installer appropriate for your system from python.org and running it.
2. Install pip for the first time, download [get-pip.py](https://bootstrap.pypa.io/get-pip.py). Then run the following command to install it:

```
python get-pip.py
```

3.Install the mkdocs package using pip:

```
pip install mkdocs
```
You should now have the mkdocs command installed on your system. Run ``mkdocs --version`` to check that everything worked okay.

```
$ mkdocs --version
mkdocs, version 0.15.3
```

4. Install needed theme and plugins

```
pip install mkdocs-material
pip install mkdocs-awesome-pages-plugin
pip install mkdocs-minify-plugin
```


## Run a built-in dev-server

It lets you preview your documentation as you work on it. Make sure you're in the same directory as the mkdocs.yml configuration file, and then start the server by running the mkdocs serve command:

```
$ mkdocs serve
INFO    -  Building documentation...
INFO    -  Cleaning site directory
[I 160402 15:50:43 server:271] Serving on http://127.0.0.1:8000
[I 160402 15:50:43 handlers:58] Start watching changes
[I 160402 15:50:43 handlers:60] Start detecting changes
```

Open up http://127.0.0.1:8000/ in your browser, and you'll see the default home page being displayed:

## Adding pages
1. Open file [mkdocs.yml](mkdocs.yml)
2. Create new list element to related pages together under a section title. For example:
```
 'Аккаунт':
    - 'getData': 'account/getData.md'
```
3. Add new md file by path relative to docs. For example: docs/account/getData.md


## Building the site
```
mkdocs build
```
This will create a new directory, named site.

## Additional docs:

* [mkdocs](https://www.mkdocs.org/)
* [mkdocs-material](https://squidfunk.github.io/mkdocs-material/getting-started/)




