# angular-10-jwt-refresh-tokens

Angular 10 - JWT Authentication with Refresh Tokens

For a demo and further details see https://jasonwatmore.com/post/2020/07/25/angular-10-jwt-authentication-with-refresh-tokens


# Auf Openshift deployen:
- ist in fhel_linuxContainers beschrieben. 
- Folder openshiftio angelegt und von Demo application.yaml kopiert
-- get application.yaml
find . | grep openshiftio | grep application | xargs -n 1 oc apply -f 
-- deploy on openshift (davor muss man crc starten und sich einloggen!) -- 2 Parameter gibt man direkt an (Source-Rep), OUTPUT_DIR muss bei Angular dist/ sein!!
oc new-app --template angular-web-app -p SOURCE_REPOSITORY_URL=https://github.com/lholmquist/angular-web-app -p OUTPUT_DIR=dist/angular-web-app