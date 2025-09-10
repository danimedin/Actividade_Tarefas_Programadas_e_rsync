# Actividade - Tarefas programadas, tar e rsync

## Exercicio 1

Investiga como crear un arquivo que no seu nome incorpore a data e a hora de **hoxe**. Por exemplo:

```bash
dani@lnx-inf-e02:~$ comando1
Arquivo-2022-09-26-16-18-26
dani@lnx-inf-e02:~$ comando2
Arquivo-2022-09-26-16-18-31
dani@lnx-inf-e02:~$ comando3
Arquivo-2022-09-26-16-18-36
dani@lnx-inf-e02:~$ comando4
Arquivo-2022-09-26-16-18-41
```

Tes que utilizar **command substitution** co comando date.  O contido do arquivo é irrelevante.

**PISTA**:

```bash
dani@lnx-inf-e02:~$ date +%Y-%m
2025-09
dani@lnx-inf-e02:~$ touch CopiaSeg-$(date +%Y-%m) # Isto é command substitution
dani@lnx-inf-e02:~$ ls CopiaSeg*
CopiaSeg-2025-09
```

## Exercicio 2

Escribe un comando que replique con rsync os directorios principais (/etc /home /var/ /root)  do teu sistema en /media/DIURNO. Cada vez que executes o rsync debe gardala copia en /media/DIURNO/backup.

Serve este sistema como copia de seguridade?

## Exercicio 3

No exercicio anterior, que pasa executo o rsync unha vez, borro uns arquivos na orixe e volvo a executar o rsync? Bórranse os arquivos en /media/DIURNO/backup? 
Próbao.

Inclúe os modificadores necesarios no comando rsync para a copia sexa exacta ao orixinal se executo o comando varias veces.

## Exercicio 4

Modifica o comando anterior para que cada vez que se execute o rsync cree un directorio diferente en /media/DIURNO. O directorio ten que chamarse backup-DATA-HORA

Se executo 5 veces o comando debería crear en /media/DIURNO uns directorios similares a:

```
backup-2023-09-14-18-15-41
backup-2023-09-16-19-21-01
backup-2023-09-17-11-17-32
backup-2023-09-20-18-16-33
backup-2023-09-20-18-17-06

```

Vale como sistema de copias?

## Exercicio 5

Programa un sistema de copias mediante crontab para que se realicen as copias todos os días ás 8:30. 

Cada copia debe estar nun directorio diferente en /media/DIURNO.

## Exercicio 6

Engade unha comprobación previa antes de facer a copia:
ten que comprobar que /media/DIURNO está montado (mount | grep /media/DIURNO). Se non o está non debe realizar a copia. 

Lémbrate das execucións condicionais:

- &&
- ||
- ;

## Exercicio 7

Cambia a periodicidade da copia para que se execute dez minutos despois de iniciar o equipo.

## Exercicio 8

Quero que ás XX:XX se realice unha **única copia** pero posiblemente a esa hora non vou a estar diante do ordenador. Que teño que facer para programala?

## Exercicio 9

#### Apartado A)



Quero asegurar o meu almacén de copias /media/DIURNO. Para iso, xusto antes de facer a copia programada con crontab se monte /media/DIURNO (comando mount /media/DIURNO). Xusto ao finalizar a copia debe desmontarse (comando umount). 

A copia ten que facerse todos os días ás 11:00.

#### Apartado B)

Desactiva a copia do apartado A. 

Quero asegurar o meu almacén de copias /media/DIURNO. Para iso, xusto antes de facer a copia programada se monte /media/DIURNO (comando mount /media/DIURNO). Xusto ao finalizar a copia debe desmontarse (comando umount).

A copia ten que realizarse cada 5 días. Se pasados eses 5 días o equipo estaba apagado, terá que realizarse pasados 10 minutos despois de iniciar o equipo. 





## Exercicio 10

- [ ] Importa a máquina virtual de tipo Debian Server chamada Máquina-A dende o cartafol do módulo.
- [ ] Pon a máquina na mesma rede que o teu anfitrión para que se comuniquen (bridge).
- [ ] Executa o comando rsync que sincronice todas as copias de seguridade que tes en /media/DIURNO no directorio /home/administrador/ da máquina virtual. 

**PISTA**:

```bash 
rsync -av --delete --progress CARTAFOL_ORIXE usuario@IPMaquina-A:CARTAFOL_DESTINO 
```

## Exercicio 11

- [ ] Importa unha máquina virtual de tipo Ubuntu Server 24.04 e chámaa Máquina-B.
- [ ] Pon esta máquina na mesma rede que Máquina-A para que se comuniquen (bridge).
- [ ] Crea o directorio /copias (*mkdir*) e fai que o propietario sexa o usuario local chamado administrador sexa o propietario desta carpeta (*chown*) 
- [ ] Fai segura a máquina virtual Máquina-B facendo que o súa tarxteta de rede esta caído (DOWN) permanentemente. Mediante unha única tarefa programada na **Máquina-B** terás que: 
  - [ ] Levantar a tarxeta de rede (UP).  Investiga o comando *ip link* 
  - [ ] Facer que colla unha IP do servidor dhcp. Investiga o comando *dhclient*.
  - [ ] Realizar rsync  que copie o que está en /home/administrador da máquina A ao directorio /copias.
  - [ ] Tumbar a tarxeta de rede (DOWN).  Investiga o comando *ip link*.

## Exercicio 12

- [ ] Analiza o contido que hai no directorio /var/www/html da MáquinaA.
- [ ] Accede ao navegador e pon a IP da MáquinaA. Que ves?

Imos supoñer que queremos **migrar** a sinxela aplicación Web da Máquina-A á Máquina-B. 

- [ ] Instala o servidor web apache na Máquina-B.
- [ ] Leva con rsync o contido da aplicación web dende a Máquina-B.
- [ ] Obtén unha captura de pantalla onde se vexan dúas ventás de navegador. Na ventá da esquerda debe mostrar o contido da aplicación web albergada na Máquina-A. Na ventá da dereita debe mostrarse a aplicación web albergada na Máquina-B. Na captura debe verse as URL dos dous navegadores.
- [ ] Avisa ao profesor cando o teñas feito. 

## Exercicio 13

Dende o teu equipo en Windows repite o exercicio 2 co comando robocopy pero do directorio C:\Users

## Exercicio 14

Crea unha tarefa programada a través do entorno gráfico para realizar as copias do directorio Users\teulogin en DIURNO. A tarefa ténse que executar todos os días ás 10:00.



## Referencias

* boxbot6. (25 Marzo, 2025). create-image-gallery-from-the-contents-of-a-website-folder. In *https://github.com/*. Retrieved 20:29, Sep 10, 2026, from [https://github.com/boxbot6/create-image-gallery-from-the-contents-of-a-website-folder](https://github.com/boxbot6/create-image-gallery-from-the-contents-of-a-website-folder)



## Autor

Daniel Medina Méndez

[www.linkedin.com/in/daniel-medina-méndez](www.linkedin.com/in/daniel-medina-méndez)

## Licenza do documento

[![Creative Commons License](https://i.creativecommons.org/l/by-sa/4.0/88x31.png)](http://creativecommons.org/licenses/by-sa/4.0/)

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/)
