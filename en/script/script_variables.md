Script variables
====================

There is standard rule - any variables such as global report's variables, engine's variables or any local script variable are script objects. The difference is only naming. Renderer uses prefix "\_" for engine's variables and "\_\_" for global variables. So they all can be accessible using this logic. But some of them can also have other more specific name, like global variables do.

### Local script variables

Variables can be declared and used locally within a script. Once declared a script vaariable can have value assigned to it. Here you can see an example:
```JavaScript
var myVar = "Hello, World!";
```
After you have variable created you can use it in any report objects, for example in Memo by writting "[myVar]" to the **"text"** property.
For more detailed information about script variables read documentation about JavaScript language.

### Global report's variables

Any global variable that is defined in a report could be accessed from a script. The variable name should be writen in such way: ${my\_variable} without spaces between rounding signs and within variable name. There are 2 recommended way to go if you want to give your variable some complex name like "my super duper variable". First way is to replace spaces with "\_" sign. And second one is to remove spaces and use capital letter on the beginnning of every word within variable name. Internally script engine use special named object to represent global variables. So using "\_" in begin of your variable name is highly not recommended. On the other hand you can have local script variable and global report variable with the same name:
```JavaScript
var myVar = 5;
print(${myVar});
print(myVar);
```
Withing script variables "myVar" and "${myVar}" are totally diferent objects. You can safely get/put values to/from global variable like you do with regular JavaScript variables:
```JavaScript
print(${myNumber});
${myNumber} = 10;
```

Once you mentioned you global variable in the script it will be automatically added to the report variable list if it's not still exists there. Lets try it.
Open new empty report, go to the "Script" tab and enter {$test}. Now switch to the "Reports" tab. You will see your variable in the list of variables and could test your script by setting any test value for te variable.

![GlobalVariablesList]

### Renderer variables

Renderer module has it's own variables and the full list of variables depends of renderer itself.
There are list of Standard renderer's variable:
 * __LINE__ - current dataset line starting from 1
 * __PAGE__ - current page number starting from 1
 * __PAGES__ - total pages (require report double pass)
 * __PASSES__ - report pass number
 * __TPAGE__ - current page of template: means number of page in designer
 * __TPAGES__ - total pages of template: means number of pages in designer (starting from 1)
 * __DATE__ - the date when report generating was started (commercial version only). QDate.currentDate() can be used instead.
 * __TIME__ - the time when report generator was started (commercial version only). QTime.currentTime() can be used instead.




[GlobalVariablesList]:../images/script_2.png
