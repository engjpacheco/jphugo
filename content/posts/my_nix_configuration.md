+++
title = "Git y el manejo de configuración"
author = ["Javier Pacheco"]
lastmod = 2024-07-02T00:36:05-05:00
categories = ["nix", [",", "flakes"]]
draft = false
+++




## Introducción. {#introducción-dot}

Esta es una explicación de como generar un repositorio con sistema de versiones (git), para almacenar y controlar la configuración de nuestro entorno en `NixOS`.


## Configuraciones iniciales. {#configuraciones-iniciales-dot}

Comencemos con la preparación para poder empezar el repositorio de manera limpia y sin advertencias de ningún tipo.


### Configurando el entorno de git. {#configurando-el-entorno-de-git-dot}

Antes de empezar a generar el repositorio, debemos de declarar nuestro usuario y correo en git, para saber quien esta haciendo los cambios, puede sonar tonto, ya que estamos manejando nuestros propios dotfiles, pero para efectos de trabajo y colaboraciones, estas cosas son necesarias.

```shell
git config --global user.name "John Doe" 			# Definimos nuestro nombre.
git config --global user.email johndoe@example.com 	# Definimos el correo.
git config --global init.defaultBranch main		# Definimos el nombre del repo por defecto a "main"
```

Otra manera de hacerlo es declarándolo desde `home-manager`.

```nix
programs.git = {
  enable = true;
  userName = "John Doe";
  userEmail = "johndoe@example.com";
  extraConfig = {
    init.DefaultBranch = "main";
  };
};
```

Estas configuraciones nos ayudaran para poder iniciar un repositorio sin tener problemas.
Entonces ahora con esto listo, podemos empezar a crear el repositorio en donde queramos manejar nuestra configuración. Una vez estando en la ruta de la carpeta en donde estará el repositorio de git, escribimos en terminal el siguiente comando:


## A escribir comandos. {#a-escribir-comandos-dot}

Ya teniendo listo la configuración tenemos que crear un repositorio, para esto debemos tener configurado github con ssh, y saber como crear un repositorio desde el portal de github.

```shell
git init
```

En este momento podrías agregar tus archivos de configuración como:

1.  /etc/nixos/configuration.nix
2.  /etc/nixos/hardware-confguration.nix
3.  home.nix
4.  flake.nix

y hacer el commit correspondiente.


### Configurando ssh. {#configurando-ssh-dot}

Para tener un poco mas de seguridad es buena practica tener configurado ssh para no tener que estar escribiendo el usuario y la password;


### Crear el repositorio en github. {#crear-el-repositorio-en-github-dot}

Ir a [tu cuenta de github](https:github.com) y crear un nuevo repositorio. Una vez creado el repositorio, en terminal escribiremos el siguiente comando:

```shell
git remote add github git@github.com/<tuusuario>/<nombredelrepostorio>.git
git push github main
```
