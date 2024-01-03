# TartarSauce-HTB

## Nmap

![image](https://github.com/gecr07/TartarSauce-HTB/assets/63270579/c7ffdab0-afe6-4080-938b-002e3fc39235)

## Dirbuster

Para encontrar lo que sea es de las mejores tools aunque aveces de tantas peticiones llena los logs lo que hace que las maquinas no funcionen como deberian.

```
dirbuster -u http://10.129.1.185/ -t 200 -l /usr/share/wordlists/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt -r dirout.ext -e php,txt,html
```

Todo lo demas que se encuentra en robots.txt son rabbit holes porquen o se puede hacer nada. Se encontro un WP 

### WP scan

Esta herramienta ayuda a enumerar el WP sin embargo, en esta ocacion no me detecto nada!

```
wpscan --detection-mode aggressive -e u,p --url http://10.129.1.185/webservices/wp 
```

Un check que siempre tienes que hacer es ver si tiene plugins aunque no encontro nada wpscan checa a ver si estan en el directorio donde siempre estan  aparte fuzzea 


```

```




































