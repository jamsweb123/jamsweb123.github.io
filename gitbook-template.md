# GitBook Template



## GitBook Template

Proyecto 'plantilla' para la generación de documentación haciendo uso de markdown y GitBook [GitBook](https://github.com/GitbookIO/gitbook)

Puedes ver esta documentación online en [https://inyenia.github.io/gitbook-template/](https://inyenia.github.io/gitbook-template/) y descargarla en formato pdf desde [https://inyenia.github.io/gitbook-template/book\_es.pdf](https://inyenia.github.io/gitbook-template/book_es.pdf)

Para modificar la documentación solo hay que añadir o modificar uno de los fichero .md existentes dentro de la carpeta doc de este proyecto, puedes consultar la sintasis desde [Markdown Guide](https://guides.github.com/features/mastering-markdown/)

Puedes descargar el editor de GitBook para tu sistema operativo desde [https://github.com/GitbookIO/editor-legacy/releases](https://github.com/GitbookIO/editor-legacy/releases) una vez instalada solo tienes que abrir la carpeta doc del proyecto con la app.

**Snippets de código**

Haciendo uso del script **snippets.sh** puedes añadir snippets de código direntamente del código o los JUnit de tu aplicación a la documentación.

Para crear un snippet en la clase java tenemos añadir lo siguiente

```java
//BEGIN-SNIPPET: example1
System.out.println("Hello, World snippet 1");
//END-SNIPPET
```

Para generar los snippets en formato markdown tienes que ejecutar los siguiente:

```text
./snippets.sh java src doc/es/snippets
```

Una vez ejecutado el script **snippets.sh** se creará el fichero example1.md en el directorio doc/es/snippets para usar este snippet en nuestra documentación tenemos que añadir el siguiente código

```text
{% include "./snippets/example1.md" %}
```

**Añadir imágenes**

Puedes añadirlas dentro de la carpeta resources. Añadir dentro de esta carpeta el fuente de la imagen por si es necesario modificarla.

Puedes añadir la imágenes con el siguiente código

```text
![Image demo](resources/keep-calm-portada.jpg)
```

Si añades una nueva sección al documento recuerda que tienes que añadirla en el fichero ./doc/SUMMARY.md si no utilizas el editor de GitBook.

#### Generar documentación en formato PDF y HTML

Esta documentación esta genereda con la versión 2.1.0 de GitBook si tienes instalado en tu equipo una versión inferior a la 2.0.0 necesitas desistalar la antigua versión de GitBook con el siguiente comando.

**Desistalar GitBook con NPM**

```text
$ npm uninstall -g gitbook
```

**Instalar versión de GitBook con NPM**

```text
$ npm install -g gitbook-cli
```

**Instalación de Calibre**

Se necesita tener instalada la app Calibre para poder generar la documentación en formato pdf.

* Descargar desde: [http://code.calibre-ebook.com/dist/osx](http://code.calibre-ebook.com/dist/osx)
* Instalar Calibre
* Añadir Calibre al PATH \(puedes añadirlo a ~/.zshrc\)

```text
export PATH=$PATH:/Applications/calibre.app/Contents/MacOS
```

**Actualizar documentación**

Para facilitar la integración con GitBook se ha preparado el shell script ./doc-build.sh que realiza lo siguiente:

* Añade en el README.md la versión del pom de tu proyecto o la versión indicada como parámetro y la fecha actual
* Genera páginas html
* Genera PDF

Por los que si tienes instalado GitBook y Calibre en tu equipo según lo explicado anteriormente puedes ejecutar el shell script doc-build.sh en tu equipo.

```text
./doc-build.sh
```

Puedes insdicar la versión de la documentación a generar

```text
./doc-build.sh 1.0.1
```

**Configuración de GitBook**

Desde el siguiete enlace se puede acceder a toda la documentación de GitBook [http://help.gitbook.com](http://help.gitbook.com)

Los siguiente puntos son solo una pequeña ayuda.

* La portada del pdf es la imagen ./doc/cover.jpg
* Todos los .md tienen que estar enlazados en ./doc/SUMMARY.md
* La generación de html y pdf se configura en el fichero ./doc/book.json
* En la carpeta ./doc/styles/ se pueden modificar los ficheros pdf.css y html.css que configuran los estilos del pdf y html generado.
* En el fichero LANGS.md se configuran los idiomas disponibles, esta documentación está solo en español si la quisieramos traducir a inglés tendriamos que copiar el contenido de la carpeta ./doc/es a la carpeta ./doc/en traducirlo todo y añadir lo siguiente en el fichero LANGS.md

```text
* [English](en)
```

