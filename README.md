# Laravel_Sqlsrv
Using pure SQLSRV driver for Non Query request using Default DB as


When using Microsoft SQL Server as Database in Laravel and use sqlsrv drivers [insert/update/delete] queries occassionally takes too long to execute. I have done all the idexes and it didnt fix the problem.

Tested raw SQLSRV_PDO execution and same slow execution result.

Tested raw SQLSRV and surprisingly the execution was way faster than SQLSRV_PDO.

When using this library be sure to use both SQLSRV*.dll and SQLSRV_PDO*.dll.

I have added the file to App/Models, you are free to move it anywhere.

Example Syntax:

use App\Models\Sqlsrv;

// on Controller
$sqlsrv = new Sqlsrv();

$sqlsrv->insert('tablename', ['arrayOfFields'=>'andValues'] );

$sqlsrv->update('tablename',['whereField'=>'whereValue] , ['fieldsToUpdate'=>'updateValues'] );

//uses update if no rows affected use insert
//be mindful when using triggers, add 'SET NOCOUNT ON'
$sqlsrv->updateOrInsert('tablename',
    ['whereField1'=>'whereValue1','whereField2'=>'whereValue2'],
    ['updField1'=>'updVal1','updField2'=>'updVal2']);
