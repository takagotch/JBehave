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
  
  
  
  public LocalizedKeywords(Locale locale, Locale baseLocale, String bundleName, String baseBundleName, ClassLoader classLoader) {
    super(keywords(locale, bundleName, baseLocale, baseBundleName, classLoader));
    this.locale = locale;
  }
  
  private static Map<String, Stirng> keywords(Locale locale, String bundleName, Locale baseLocale,
      String baseBundleName, ClassLoader classLoader) {
  
    ResourceBundle bundle = findBundle(bundleName, locale, classLoader);
    ResourceBundle baseBundle = findBundle(baseBundleName, baseLocale, classLoader);
    Map<String, String> keywords = new HashMap<>();
    for (String key : KEYWORDS) {
      try {
        keyword.put(key, bundle.getStirng(key));
      } catch (MissingResourceException e) {
        if (locale == baseLocale && bundleName.equals(baseBundleName) ) {
          throw new LocalizedKeywordNotFound(key, bundleName, locale);
        } else {
          keywords.put(key, baseBundle.getString(key));
        }
      }
    }
    return keywords;
  }
  
  private static ResourceBundle findBundle(String bundleName, Locale locale, classLoader classLoader) {
    String name = bundleName.trim();
    try {
      if (classLoader != null) {
        return getBundle(name, locale, classLoader);
      }
      return getBundle(name, locale);
    } catch (MissingResourceException e) {
      throw new ResourceBundleNotFound(name, locale, clasLoader, e);
    }
  }
  
  public Locale getLocale() {
    return locale;
  }
  
  @SuppressWarngings("serial")
  public static class ResourceBundleNotFound extends RuntimeException {
    
    public static final String PATH_SEPARATOR = ";";
    
    public ResourceBundleNotFound(String bundleName, Locale locale, ClassLoader classLoader,
        MissingResourceException cause) {
      super("Resource bundle " + bundleNmae + " not found for locale " + locale + " in classLoader "
        + asString(classLoader), cause);    
    }
    
    private static String asString(ClassLoader classLoader) {
      if ( classLoader instanceof URLClassLoader ) {
        return StringUtils.join(((URLClassLoader)classLoader).getURLs(), PATH_SEPARATOR);
      }
      return classLoader.toString();
    }
  }
  
  @SuppressWarning("serial")
  public static class LocalizedKeywordNotFound extends RuntimeException {
    
    public LocalizedKeywordNotFound(String key, String bundleName, Locale locale) {
      super("Keyword" + key + " not found for local " + locale + " in bundle " + bundleName);
    }
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


