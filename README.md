
<!--#echo json="package.json" key="name" underline="=" -->
anno-doi-bot-23-adapter-datacite
================================
<!--/#echo -->

<!--#echo json="package.json" key="description" -->
DataCite adapter for anno-doi-bot-23.
<!--/#echo -->


* [DataCite metadata schema kernel 4.5
  ](https://schema.datacite.org/meta/kernel-4.5/)



Installation
------------

1.  Ensure you have the prerequisites:
    * Ubuntu 22.04 or later
    * Node.js v20 or later
    * A clone of the `anno-doi-bot-23`.
      (This adapter module is mostly useless without the DOI bot itself.)
1.  Clone this repo and chdir to your clone's top directory.
1.  Create a symlink `botfuncs` that points to the `funcs` directory
    of your `anno-doi-bot-23`.
    Usually they should be sibling directories, so the command would be:
    `ln --symbolic --no-target-directory -- ../anno-doi-bot-23/funcs botfuncs`
1.  Run `npm install .`
1.  Continue at chapter "Configuration".



Configuration
-------------

* You can modify the configuration at any time.
  Changes will take effect the next time the DOI bot runs.
* The available config options can be found (not: modified)
  in the [default settings file](src/cfg.default.rc).
* To customize configuration, create a subdirectory named `config`,
  and in there, one or more text files whose name ends in `.rc`
  (e.g. `basics.rc`).
  * All these files are read in your locale's sorting order,
    which may or may not be case-sensitive.
    For reliable ordering, start all filenames with a fixed number of
    digits, e.g. `010_basics.rc`, `023_doi_format.rc`, `080_hotfixes.rc`.
* Once the DataCite adapter itself is configured, you need to configure
  your DOI bot to actually use the DataCite adapter.
  To do so, add these settings to your DOI bot config:

  ```bash
  CFG[doibot_adapter_name]='datacite'
  CFG[doibot_adapter_prog]= # <- Clear potential example values that may
  CFG[doibot_adapter_args]= # <- have been set by the default config.
  ```

  * An empty value for `doibot_adapter_prog` means to search in the default
    paths, assuming the adapter is installed as a peer dependency.
    If you installed it somewhere else, or the automatic path detection fails,
    put the absolute path to `adapter.sh`.






Usage
-----

In production, this adapter is not meant to be used directly.
Instead, it should be invoked by your DOI bot.

For debugging, however, there are some useful invocations:

* [`download_meta_for_dois`](src/download_meta_for_dois.sh)




<!--#toc stop="scan" -->



Known issues
------------

* Needs more/better tests and docs.




&nbsp;


License
-------
<!--#echo json="package.json" key=".license" -->
MIT
<!--/#echo -->
