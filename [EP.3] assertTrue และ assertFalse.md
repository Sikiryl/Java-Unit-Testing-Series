## สิ่งที่ได้เรียนรู้ในครั้งนี้:
- เริ่มสร้างตัวอย่างสำหรับทำความเข้าใจในว่าทำไมเราถึงต้อง mock
- สร้าง Application สำหรับจัดการ action ของผู้ใช้
- ทำตัวกรองสำหรับ action ในการตะโกน

## Files List
### /pom.xml
```
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<parent>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-parent</artifactId>
		<version>2.2.1.RELEASE</version>
		<relativePath/> <!-- lookup parent from repository -->
	</parent>
	<groupId>kakkai</groupId>
	<artifactId>studio</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<name>studio</name>
	<description>Demo project for Spring Boot JUnit Test Created by KAKKAI Studio</description>

	<properties>
		<java.version>1.8</java.version>
	</properties>

	<dependencies>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter</artifactId>
		</dependency>

		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-test</artifactId>
			<scope>test</scope>
			<exclusions>
				<exclusion>
					<groupId>org.junit.vintage</groupId>
					<artifactId>junit-vintage-engine</artifactId>
				</exclusion>
			</exclusions>
		</dependency>
	</dependencies>

	<build>
		<plugins>
			<plugin>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-maven-plugin</artifactId>
			</plugin>
		</plugins>
	</build>

</project>
```
### /src/main/java/kakkai/studio/business/ActionBusiness.java
```
package kakkai.studio.business;

import kakkai.studio.service.ActionService;

import java.util.ArrayList;
import java.util.List;

public class ActionBusiness {

    private ActionService actionService;

    public ActionBusiness(ActionService actionService) {
        this.actionService = actionService;
    }

    public List<String> retrieveActionRelatedToShout(String user) {
        List<String> filteredActions = new ArrayList<String>();
        List<String> allAction = actionService.retriveAction(user);
        for (String action : allAction) {
            if (action.contains("Shout")) {
                filteredActions.add(action);
            }
        }
        return filteredActions;
    }

}

```
### /src/main/java/kakkai/studio/service/ActionService.java
```
package kakkai.studio.service;

import java.util.List;

public interface ActionService {

    public List<String> retriveAction(String action);

}
```
### /src/test/java/kakkai/studio/mockito/MockitoTest.java
```
package kakkai.studio.mockito;

import org.junit.jupiter.api.Test;

import static org.junit.jupiter.api.Assertions.assertTrue;

public class MockitoTest {

    @Test
    public void test() {
        assertTrue(true);
    }
    
}
```
