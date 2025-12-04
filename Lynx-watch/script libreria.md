``` bash
nx g @nx/angular:library \ 
--name=dashboards \
--buildable=true \
--directory=libs/dashboards \ 
--displayBlock=true \
--flat=true \
--importPath=@lynx/dashboards \
--projectNameAndRootFormat=as-provided \
--style=scss
```
nx g @nx/angular:library --buildable=true --projectNameAndRootFormat=as-provided --standalone=false