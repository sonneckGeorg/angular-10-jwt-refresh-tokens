# angular-10-jwt-refresh-tokens

Angular 10 - JWT Authentication with Refresh Tokens

For a demo and further details see https://jasonwatmore.com/post/2020/07/25/angular-10-jwt-authentication-with-refresh-tokens


# Auf Openshift crc deployen:
- ist in fhel_linuxContainers auch beschrieben beschrieben. 
- Folder openshiftio angelegt und von Demo application.yaml kopiert

CRC starten:
- Den Container wie folgt starten
crc start -p /Users/sonneck/Documents/git_repos/rhel_linuxContainers/crc-macos-1.21.0-amd64/pull-secret
crc oc-env
eval $(crc oc-env)
oc login -u developer -p developer https://api.crc.testing:6443

-- get application.yaml: danach wird damit oc apply aufgerufen (oc apply -f application.yaml) -> das fügt die API objects dem Cluster hinzu!!!!
find . | grep openshiftio | grep application | xargs -n 1 oc apply -f 

-> Ergebnis ist Anlage des Templates von application.yaml
- Templates in project auflisten mit: (globale Templates mit: oc get templates -n openshift)
oc get templates

-- deploy on openshift -> 2 Parameter gibt man direkt an (Source-Rep), OUTPUT_DIR muss bei Angular dist/ sein!!
oc new-app --template angular-web-app -p SOURCE_REPOSITORY_URL=https://github.com/sonneckGeorg/angular-10-jwt-refresh-tokens -p OUTPUT_DIR=dist/angular-jwt-refresh-tokens

oc new-app --template angular-web-app -p SOURCE_REPOSITORY_URL=https://github.com/lholmquist/angular-web-app -p OUTPUT_DIR=dist/angular-web-app


# TODO: TODO in angular-10-jwt-refresh-tokens: Multiple configs with configMap
https://developers.redhat.com/blog/2019/11/27/handling-angular-environments-in-continuous-delivery-with-red-hat-openshift/