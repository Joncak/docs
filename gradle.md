Gradle Fundamentals
===================
* No necesitamos ser expertos de groovy porque gradle usa un DSL la mayor info
la conseguimos en docs.gradle.org/current/dsl/
docs.gradle.org/current/userguide/
* Existe un gvm para Groovy environment manager.
* Aprendere lo minimo de groovy para gradle y jenkins.
* << es un shortcut a doLast.
* hello { doLast } = hello.dLast
* EL DSL reference nos ayuda a entender lo que esta en los build gradle, util
para lo que hare.
* el comando gtadle dep, es interesante.


Java Projects
-------------
gradle init --type java-library
gradle build
gradle clean // delete the build folder.

Groovy Projects
---------------
Usamos un groovy plugin lo demas es identico a java.
Si tenemos cross languaje  (groovy, java) lo mejor es dictar el groovy
compiler para que compile todo el codigo.
sourceSets para cuando no tenemos el codigo con la estructura oficial.


Groovy Fundamentals
===================
* println name.getClass().getName()
* En groovy si no defines el tipo public o private entonces por defecto se
  vuelve el package = public, attribute = private, class = public, methods
  = publics.
* Los set y gets son creados automaticos por ti.
* Un poco complicado pero entendible.
* No Soy un Groovy DEV no me importa el in deep.
* nums.each { println it } utiliza closures.
* Todos los closures tienen 1 arg.
* nums.each { n -> println n }
* Esto no deberia usarse asi porque seria dificil en concurrency
  - nums.each { doubles << it * 2 }
  - SoLUtion: println nums.collect { it * 2 }
  - println cities.collect { it.toLowerCase().reverse()}

