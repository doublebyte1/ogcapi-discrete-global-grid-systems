# ogcapi-discrete-global-grid-systems

== OGC Standard Document Template Initialisation (Linux)

Commands to initialise and compile the OGC Metanorma Standard document template. These should be run from the root directory of this github repository.

1. Download/update the Metanorma Docker Container

[NOTE]
====
docker pull metanorma/mn:latest
====

2. Create new Metanorma OGC standard from OGC Template

[NOTE]
====
Example:

docker run -i -v "$(pwd)":/metanorma metanorma/mn  metanorma new -d standard -t ogc  -l https://github.com/metanorma/mn-templates-ogc 21_038_OGC_API_DGGS_Part_1
====

3. Update Docker Instance with data from this github repository

[NOTE]
====
docker cp ./ <Docker_Container_ID>:"/metanorma/21_038_OGC_API_DGGS_Part_1"

Example:

docker cp ./ 2622352e28ed:"/metanorma/21_038_OGC_API_DGGS_Part_1"
====


4. Compile document

[NOTE]
====
Example:

docker run -v "$(pwd)":/metanorma -v ${HOME}/.fontist/fonts/:/config/fonts  metanorma/mn  metanorma compile --agree-to-terms -t ogc -x xml,html,doc 21_038_OGC_API_DGGS_Part_1/document.adoc

====

5. Copy the compiled Metanorma documents back to the github repository local directory.

[NOTE]
====
docker cp <Docker_Container_ID>:"/metanorma/21_038_OGC_API_DGGS_Part_1" .

Example:

docker cp 2622352e28ed:"/metanorma/21_038_OGC_API_DGGS_Part_1" .
====


6. Commit the changes and compiled Metanorma documents to github

[NOTE]
====
Example:

git commit -m "Changes to Conformance Class 1"

git push
====


