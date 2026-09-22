https://docs.google.com/spreadsheets/d/1FECl_M8wXigE0yHJ4T-vGhY5pjaVrzFF/edit?usp=drivesdk&ouid=108032357089616246657&rtpof=true&sd=true


## Cerfication
https://www.testmuai.com/certifications/selenium-java-101/


```python

import java.sql.*;
import org.openqa.selenium.*;
import org.openqa.selenium.chrome.ChromeDriver;

public class crud {
    public static void main(String[] args) throws Exception{
        ChromeDriver driver=new ChromeDriver();
        driver.manage().window().maximize();
        driver.get("C:\\Users\\gurup\\IdeaProjects\\untitled2\\src\\main\\java\\crud.html");
        //connection bet this log mysql
        Connection con=DriverManager.getConnection(
                "jdbc:mysql://localhost:3306/selcurd",
                "root",
                "yorpassword"
        );
        driver.findElement(By.id("name")).sendKeys("mounesh");
        driver.findElement(By.id("email")).sendKeys("@gmail");
        con.prepareStatement(
                "insert into curd(name,eamil) values ('mounesh','@gmail')").executeUpdate();
        System.out.println("creadted");
        //Update
        driver.findElement(By.id("name")).clear();
        driver.findElement(By.id("email")).clear();

        driver.findElement(By.id("name")).sendKeys("mounesh updated");
        driver.findElement(By.id("email")).sendKeys("@gmail Updated");

        con.prepareStatement(
                "update curd set name='mounesh updated',email='@gamil Updated' where id=1").executeUpdate();
        System.out.println("updated");
        //delete

        con.prepareStatement("delete from curd where id=1").executeUpdate();
        driver.quit();
        //read
        Showcurd(con);
    }
    public static void Showcurd(Connection con) throws Exception{
        ResultSet rs=con.createStatement().executeQuery("select * from curd");
        while (rs.next())
            System.out.println(rs.getInt(1)
                    +" "+rs.getString(2)
                    +" "+rs.getString(3));
    }
}
```

```python

CREATE DATABASE seleniumcru;


CREATE TABLE users
(
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100)
);

INSERT INTO users(name,email)
VALUES
('John','john@gmail.com'),
('Alice','alice@gmail.com');

SELECT * FROM users;

```

## post

```python

<dependencies>

    <dependency>
        <groupId>org.seleniumhq.selenium</groupId>
        <artifactId>selenium-java</artifactId>
        <version>4.34.0</version>
    </dependency>

    <dependency>
        <groupId>org.postgresql</groupId>
        <artifactId>postgresql</artifactId>
        <version>42.7.7</version>
    </dependency>

</dependencies>

```

```python
        Connection con = DriverManager.getConnection(
                "jdbc:postgresql://localhost:5432/seleniumcru",
                "postgres",
                "your_password"
        );

```
