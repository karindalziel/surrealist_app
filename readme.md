## Variable descriptions

* [Data Repo default or collection](#data-repo-default-or-collection)
  * [`data_base`](#data_base)
  * [`media_base`](#media_base)
  * [xslt  override template `url_builder`](#url_builder-xslt-template)
  * [`es_path`and `es_index`](#es_path-and-es_index)
* [Collection](collection)
  * [`shortname`](#shortname)	
* [API](#api)
  * [`es_path` and `es_index`](#api)
* [Orchid site](#orchid_site)
  * [`production`/`development`](#orchid_site)	

### Data Repo default or collection

**location**

* /data
  * /config/public.yml [prod]
  * /config/private.yml [dev]
  * /collection/Project_Name/config/public.yml [prod]
  * /collection/Project_Name/config/private.yml [dev]

#### `data_base`

* example: `http://cdrhmedia.unl.edu`

Location of data (html, tei, etc.) 

Application will append /data/ to url; can be the same as cdrh_media.

Generally passed to index scripts to build link to html, tei, and other data.

#### `media_base`

* example: `http://cdrhmedia.unl.edu`

Location of the media (audio, video).	

Linking to all media except images in api and html.

#### `url_builder` XSLT template

* private.yml only
* override template via xsl file, store location in:
  * /config/public.yml
      * to change for all projects
  * /collection/Project_Name/config/private.yml
      * to change for only one project 
  * example: https://github.com/CDRH/data/blob/master/scripts/xslt/cdrh_to_html/lib/cdrh.xsl#L115
  
The default XSLT scripts build an IIIF url based from media_base. 

Local override: Store file outside repo, reference location from /Project_Name/config/private.yml."	Used to link to page images in html.

#### `es_path` and `es_index`

* private.yml only
* example es_path: `http://localhost:9200`
* example es_index: `cdrhapi`

Location of elasticsearch instance and index.

Used to post to index.

### Collection

**location**

* /data
  * /collection/Project_Name/config/public.yml [prod]
  * /collection/Project_Name/config/private.yml [dev]

#### `shortname`

* example: `Project_Name`	

Shortname, or ""slug"" of the project.

Generally the same as the folder name in /data/collections and stored in public.yml.

Used to build URL's in index and HTML scripts.

### API

**location:**

* /rails/api
  * /config/config.yml
  
* example es_path: `http://localhost:9200`
* example es_index: `cdrhapi`

location of elasticsearch index and index name.

### Orchid Powered Site

**location:**

* /rails/Project_Name
  * /config/config.yml
* example production or development: `http://localhost:3000` or `http://localhost:3000/collection/Project_Name`

Location of API.








| Folder Structure                                  | url after base(added by scripts) | localhost base        | cdrhdev base                         | cdrh prod base              |
|---------------------------------------------------|----------------------------------|-----------------------|--------------------------------------|-----------------------------|
| 📁 data                                            | /data                            | http://localhost:9999 | http://cdrhdev1.unl.edu/media        | http://cdrhmedia.unl.edu    |
|   &nbsp;📁 collections                                   | /data/Project_Name               | http://localhost:9999 | http://cdrhdev1.unl.edu/media        | http://cdrhmedia.unl.edu    |
| 📁 iiif                                            |                                  |                       |                                      |                             |
|   &nbsp;&nbsp;symlinks for each project                       |                                  |                       |                                      |                             |
|     &nbsp;&nbsp;&nbsp;&nbsp;data/collections/Project_Name -> Project_Name |                                  |                       |                                      |                             |
|     &nbsp;&nbsp;&nbsp;&nbsp;[iiif server] (default url)                   |                                  |                       |                                      |                             |
| 📁 media                                           | root                             | http://localhost:9999 | http://cdrhdev1.unl.edu/media        | http://cdrhmedia.unl.edu    |
|   &nbsp;&nbsp;📁 images                                        | /images                          | http://localhost:9999 | http://cdrhdev1.unl.edu/media        | http://cdrhmedia.unl.edu    |
|     &nbsp;&nbsp;&nbsp;&nbsp;📁 Project_Name (optional)                     | /images/Project_Name             | http://localhost:9999 | http://cdrhdev1.unl.edu/media        | http://cdrhmedia.unl.edu    |
|   &nbsp;&nbsp;symlink                                         |                                  |                       |                                      |                             |
|     &nbsp;&nbsp;&nbsp;&nbsp;data/collections -> data                      |                                  |                       |                                      |                             |
| 📁 rails                                           |                                  |                       |                                      |                             |
|   &nbsp;&nbsp;📁 API                                           |                                  |                       |                                      |                             |
|     &nbsp;&nbsp;&nbsp;&nbsp;[elasticsearch instance]                      | root                             | http://localhost:9200 | http://localhost:9200                | http://localhost:9200       |
|     &nbsp;&nbsp;&nbsp;&nbsp;[rails/api]                                   | root                             | http://localhost:3000 | http://cdrhdev1.unl.edu/api/v1       | http://cdrhapi.unl.edu      |
|   &nbsp;&nbsp;📁 Project_Name                                  |                                  |                       |                                      |                             |
|     &nbsp;&nbsp;&nbsp;&nbsp;[rails/orchid]                                | root                             | http://localhost:3001 | http://cdrhdev1.unl.edu/Project_Name | http://Project_Name.unl.edu |



