```

232
│
├── pom.xml
│
├── src
│   │
│   ├── main
│   │   └── java
│   │       │
│   │       ├── base
│   │       │    └── BaseTest.java
│   │       │
│   │       ├── pages
│   │       │    └── WikipediaPage.java
│   │       │
│   │       └── utils
│   │            └── ConfigReader.java
│   │
│   └── test
│       │
│       ├── java
│       │    └── tests
│       │         └── WikiTest.java
│       │
│       └── resources
│            └── config.properties


```

```python


mkdir src\main\java\base
mkdir src\main\java\pages
mkdir src\main\java\utils

```

```python

mkdir src\test\java\tests
mkdir src\test\resources

```


```python

New-Item src\main\java\base\BaseTest.java
New-Item src\main\java\pages\WikipediaPage.java
New-Item src\main\java\utils\ConfigReader.java

New-Item src\test\java\tests\WikiTest.java

New-Item src\test\resources\config.properties
```



## dependency
```python

<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>org.example</groupId>
    <artifactId>untitled2</artifactId>
    <version>1.0-SNAPSHOT</version>

    <properties>
        <maven.compiler.source>26</maven.compiler.source>
        <maven.compiler.target>26</maven.compiler.target>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    </properties>
    <dependencies>
        <dependency>
            <groupId>org.seleniumhq.selenium</groupId>
            <artifactId>selenium-java</artifactId>
            <version>4.33.0</version>
        </dependency>
        <dependency>
            <groupId>org.testng</groupId>
            <artifactId>testng</artifactId>
            <version>7.11.0</version>
        </dependency>

        <dependency>
            <groupId>org.apache.logging.log4j</groupId>
            <artifactId>log4j-api</artifactId>
            <version>2.23.1</version>
        </dependency>
        <dependency>
            <groupId>org.apache.logging.log4j</groupId>
            <artifactId>log4j-core</artifactId>
            <version>2.23.1</version>
        </dependency>

        <dependency>
            <groupId>com.aventstack</groupId>
            <artifactId>extentreports</artifactId>
            <version>4.1.7</version>
        </dependency>

        <dependency>
            <groupId>commons-io</groupId>
            <artifactId>commons-io</artifactId>
            <version>2.16.1</version>
        </dependency>

        <dependency>
            <groupId>org.xerial</groupId>
            <artifactId>sqlite-jdbc</artifactId>
            <version>3.50.3.0</version>
        </dependency>

        <dependency>
            <groupId>com.h2database</groupId>
            <artifactId>h2</artifactId>
            <version>2.3.232</version>
        </dependency>
        <dependency>
            <groupId>com.mysql</groupId>
            <artifactId>mysql-connector-j</artifactId>
            <version>9.3.0</version>
        </dependency>

    </dependencies>
</project>

```

# 1.BaseTest

```python
package base;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import utils.ConfigReader;
public class BaseTest {
    public static WebDriver driver;
    public void start() throws Exception {
        driver = new ChromeDriver();
        driver.manage().window().maximize();
        Thread.sleep(2000);
        driver.get(ConfigReader.get("url"));
        Thread.sleep(3000);
    }
    public void end(){
        driver.quit();

    }
}

```

##2. Wikipediapage

```python
package pages;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;

public class WikipediaPage {
    WebDriver driver;

    public WikipediaPage(WebDriver driver){
        this.driver=driver;
    }
    public void search(String text) throws Exception{
        driver.findElement(By.id("searchInput")).sendKeys(text);
        driver.findElement(By.xpath("//button[@type='submit']")).click();

    }


}

```
3.ConfigReader

```python

package utils;

import java.io.FileInputStream;
import java.util.Properties;

public class ConfigReader {
    static Properties p = new Properties();
    static {
        try {
            p.load(new FileInputStream(
                    "src/test/resources/config.properties"));
        }
        catch(Exception e){
            e.printStackTrace();
        }
    }
    public static String get(String key){

        return p.getProperty(key);

    }

}

```

4.WikiTest

```python

package tests;
import org.testng.annotations.Test;
import base.BaseTest;
import pages.WikipediaPage;
import utils.ConfigReader;
public class WikiTest extends BaseTest{
    @Test
    public void search()throws Exception{
        start();
        WikipediaPage page=new WikipediaPage(driver);
        page.search(ConfigReader.get("search"));
        end();
    }
}

```




