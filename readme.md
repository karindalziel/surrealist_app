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
