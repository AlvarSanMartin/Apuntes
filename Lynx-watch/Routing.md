El modo de routing de la aplicación parece que no es correcto, revisar:
- https://stackoverflow.com/questions/76630406/angular-nx-mono-repo-dynamic-module-federation-is-it-possible-for-a-remote
- https://nx.dev/recipes/angular/dynamic-module-federation-with-angular

#### Archivos implicados:

- `host/module-federation.config.js` 
	- revisar si hay que convertirlo a TS
- `host/webpack.*.config.js`
	 - pasar a TS
	 - ahora la configuracion se carga desde module-federation.config.js
- `*/main.ts` -> hay que añadir las definiciones del remote [ref](https://nx.dev/recipes/angular/dynamic-module-federation-with-angular#fetch-and-set-the-remote-definitions)
- `host/src/app/modules/host/host.routing.module.ts` 
	 - se define la ubicacion de los remotes de module federation
	 - hay que cambiar los input por loadRemoteModule [ref](https://stackoverflow.com/questions/76630406/angular-nx-mono-repo-dynamic-module-federation-is-it-possible-for-a-remote)
