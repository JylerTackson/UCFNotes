There will be three API endpoints:
1) AddColor
2) Login
3) SearchColors
Each will have its own .php file that is contained within the LAMPAPI directory

**NOTE:** that there is a php statement that must be changed with your database usn, psw, and db name:
```
$conn = new mysqli("localhost", "username", "password", "database");
```

Previewing the different API's:
### AddColor.php:
```
<?php
	$inData = getRequestInfo();

	$color = $inData["color"];
	$userId = $inData["userId"];
	
	$conn = new mysqli("localhost", "username", "password", "database");
	
	if($conn->connect_error)
	{
		returnWithError($conn->connect_error);
	}
	else
	{
		$stmt = $conn->prepare("INSERT into Colors (UserId, Name) VALUES(?,?)");
		$stmt->bind_param("ss", $userId, $color);
		$stmt->execute();
		$stmt->close();
		$conn->close();
		returnWithError("");
	}

	function getRequestInfo()
	{
		return json_decode(file_get_contents('php://input'), true);
	}

	function sendResultInfoAsJson($obj)
	{
		header('Content-type: application/json');
		echo $obj;
	}

	function returnWithError($err)
	{
		$retValue = '{"error":"' . $err . '"}';
		sendResultInfoAsJson($retValue);
	}
?>
```

### Login.php
```
<?php
	$inData = getRequestInfo();

	$id = 0;
	$firstName = "";
	$lastName = "";

	$conn = new mysqli("localhost", "username", "password", "database");

	if($conn->connect_error)
	{
		returnWithError($conn->connect_error);
	}
	else
	{
		$stmt = $conn->prepare("SELECT ID, firstName, lastName, FROM Users WHERE Login=? AND Password =?");
		$stmt->bind_param("ss", $inData["login"], $inData["password"]);
		$result = $stmt->get_result();

		if($row = $result->fetch_assoc())
		{
			returnWithInfo($row['firstName'], $row['lastName'], $row['ID']);
		}
		else
		{
			returnWithError("No Records Found");
		}
		
		$stmt->close();
		$conn->close();
	}

	function getRequestInfo()
	{
		return json_decode(file_get_contents('php://input'), true);
	}

	function sendResultInfoAsJson($obj)
	{
		header('Conent-Type: application/json');
		echo $obj;
	}

	function returnWithError($err)
	{
		$retValue = '{"id":0, "firstName":"","lastName":"","error":"' . $err . '"}';
	}

	function returnWithInfo($firstName, $lastName, $id)
	{
		$retValue = '{"id":' . $id . ',"firstName":"' . $firstName . '","lastName":"' . $lastName . '","error":""}';
		sendResultInfoAsJson($retValue);
	}
?>
```

### SearchColors.php:
```
<?php

?>
```