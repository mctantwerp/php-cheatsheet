# PHP-Cheatsheet
Handy if you can't remember all the PHP stuff!

Spotted a mistake? Nice addition? Open a PR!

## Variables

```php
$myFirstVariable = "Test"; //string
$mySecondVariable = 1; //int
$myThirdVariable = 1.1; //float
$myFirstArray = ["Alessandro","Bram","Sam"]; //array 
$myFirstArray = array("Alessandro","Bram","Sam"); //array
$isWrong = true; //boolean
```

## Conditionals

### If/Else If/Else

```php
//If loop
if($isWrong) {
    echo "This is wrong";
}

//If/else loop
if(!$isWrong) {
    echo "This is not wrong";
}else{
    echo "This is wrong";
}

//If/Else If/Else loop
$x = "M";
if($x === "Z"){
    echo "x is the last letter of the alphabet";
}else if($x === "A"){
    echo "x is the first letter of the alphabet";
}else{
    echo "x is not the first and not the last letter of the alphabet";
}
```

### Switch

```php
//Switch
$x = 1;
switch ($x){
    case 1:
        echo "x is equal to 1";
        break;
    case 2:
        echo "x is equal to 2";
        break;
    case 3:
        echo "x is equal to 3";
        break;
    default:
        echo "x is not 1,2 or 3";
        break;
}
```

## Loops

```php
//Foreach
$teachers = ["Alessandro","Sam"];
foreach ($teachers as $key => $teacher){
    echo "$key $teacher <br>";
}
//=> 0 Alessandro
//=> 1 Sam

//For
$teachers = ["Alessandro","Sam"];
for($i = 0;$i < count($teachers);$i++){
    echo "$i $teachers[$i] <br>";
}
//=> 0 Alessandro
//=> 1 Sam

//While
$i = 0;
$teachers = ["Alessandro","Sam"];
while($i < count($teachers)){
    echo "$i $teachers[$i] <br>";
    $i++;
}
//=> 0 Alessandro
//=> 1 Sam

$i = 0;
$teachers = ["Alessandro","Sam"];
do {
    echo "$i $teachers[$i] <br>";
    $i++;
} while($i < count($teachers));
//=> 0 Alessandro
//=> 1 Sam
//=> 2 null
```

## Functions

### Normal

```php
$x = 1;
$y = 2;
echo addNumbers($x,$y);

function addNumbers($firstParam,$secondParam){
    return $firstParam + $secondParam;
}

//=> 3
```

### Recursive

```php
$x = 0;
echo addTen($x);

function addTen($param){
    $param = $param + 10;
    echo $param;
    if($param < 100){
        addTen($param); //Calls itself
    }
}
//=> 10 20 30 40 50 60 70 80 90 100
```

## Debugging

```php
var_dump(["Alessandro","Sam"]);
//=> array(2) { [0]=> string(10) "Alessandro" [1]=> string(3) "Sam" }
```

## HTTP Methods

### GET

```php
//url: https://alessandroaussems.be?name=Alessandro&age=23
echo $_GET["name"];
echo $_GET["age"];
//=> Alessandro 23
```

### POST

```html
<form method="POST">
    <input type="text" name="first_name" value="Alessandro">
    <input type="text" name="age" value="23">
</form>
```

```php
echo $_POST["first_name"];
echo $_POST["age"];
//=> Alessandro 23
```

## Session

```php
session_start();
$_SESSION["first_name"] = "Alessandro";
```

```php
session_start();
echo $_SESSION["first_name"];
//=> Alessandro
```

## Cookie
```php
setcookie("first_name","Alessandro",time() + 3600); //Expires after 1h
```

```php
echo $_COOKIE["first_name"];
//=> Alessandro
```

## Database connection (PDO)
```php
$connection = new PDO(
    'mysql:host=127.0.0.1;dbname=your_database_name',
    'username',
    'password'
);
```

## Prepared statements
```php
$insertStatement = $connection->prepare('INSERT INTO students (first_name, last_name, note) VALUES (:firstName,:lastName,:note)');
$insertStatement->bindParam('firstName', $_POST['first_name']);
$insertStatement->bindParam('lastName', $_POST['last_name']);
$insertStatement->bindParam('note', $_POST['note']);
```

## Try/Catch
```php
try {
    $connection = new PDO(
        'mysql:host=127.0.0.1;dbname=your_database_name',
        'username',
        'password'
    );
} catch(\Exception $exception) {
    echo $exception->getMessage();
}
```
