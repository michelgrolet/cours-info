# COO

[Retour à l'accueil](./../README.md)

Les bases de la conception objet en Java.

## Menu

- [COO](#coo)
	- [Menu](#menu)
- [Tests Unitaires avec JUnit](#tests-unitaires-avec-junit)

# Tests Unitaires avec JUnit

Les tests unitaires associent à chaque classe de l’application une classe jumelle de test, permettant de tester toutes les méthodes publiques de la classe applicative.

```java
import static org.junit.Assert.*;
import org.junit.After;
import org.junit.Before;
import org.junit.Test;


class TestMaClasse {
	MaClasse x;

	//Pour initialiser les objets pour tous les tests :
	@Before
	public void init {
		x=...
	}

	@Ignore("Test non prêt")
	@Test(expected=MonException.class)
	public void testMaMethode {
		// attendu et actuel :
		// Objet ou Objet[].
		assertEquals("maMethode devrait ...", attendu, actuel); 
		assertTrue(msg, booleen);
	}
}
```

On peut lancer les tests dans un terminal java avec : `java junit.textui.TestRunner AllTests`
