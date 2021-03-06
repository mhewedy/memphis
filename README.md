# Memphis
A Mocked JDBC Driver for Stored Procedures

### using classpath resources
```java
Class.forName("memphis.Driver");
Connection connection = DriverManager.getConnection("jdbc:memphis:csv:classpath", "", "");
CallableStatement callableStatement = connection.prepareCall("{call sp_test(?)}");
callableStatement.execute();

String fistname = callableStatement.getString("fistname");
String lastname = callableStatement.getString(2);
Integer age = callableStatement.getInt("age");

assertThat(fistname, is("abdullah"));
assertThat(lastname, is("mohammad"));
assertThat(age, is(5));
```

### using filesystem resources
```java
Class.forName("memphis.Driver");
Connection connection = DriverManager.getConnection("jdbc:memphis:csv:file:///Users/mhewedy", "", "");
CallableStatement callableStatement = connection.prepareCall("{call sp_test(?)}");
callableStatement.execute();

```

#### Nulls handling:
nulls should be represented in CSV files as `NULL`
example:
```csv
fistname,lastname,age,nullInt,nullDate
abdullah,mohammad,5  ,NULL   ,NULL
farida  ,mohammad,3  ,NULL   ,NULL
```

### TODO
1. `MockSupport.determineCsvFile`
