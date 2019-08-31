### jbehave
---
https://github.com/jbehave/jbehave-core

https://jbehave.org/

```java
// jbehave-core/src/main/java/org/jbehave/core/i18n/LocalizedKeywords.java

public class LocalizedKeywords extends Keywords {

  private static final Locale  DEFAULT_LOCALE = Locale.ENGLISH;
  private static final String  DEFAULT_BUNDLE_NAME = "i18n/keywords";
  private static ClasLoader DEFAULT_CLASS_LOADER = LocalizedKeywords.class.getClassLoader();
  private final Locale locale;
  
  public LocalizeKeywords() {
    this(DEFAULT_LOCALE);
  }
  
  public LocalizeKeywords(Locale locale) {
    this(locale, DEFAULT_BUNDLE_NAME, DEFAULT_CLASS_LOADER);
  }
  
  
  
}

```

```sh
mvn install -s settings.xml
mvn install
mvn install -Pexamples
mvn install -Preporting.distribution
mvn release:prepare -Preporting.distribution
mvn relase:perform -Preporting.distribution
```

```
```


