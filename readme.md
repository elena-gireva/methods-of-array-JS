Методы массивов и оператор spread (...)

Приводим вам еще некоторые практические примеры, которые могут быть полезны для тестировщиков, особенно когда дело доходит до манипулирования тестовыми данными
или анализа результатов тестов (и очень рекомендуем выполнить данные примеры и сохранить для будущего использования в отдельный репозиторий):

1. push() & pop():

Добавление идентификатора нового тестового случая в список и удаление последнего добавленного.

   let testCaseIds = [101, 102, 103];
   testCaseIds.push(104); // [101, 102, 103, 104]
   let lastAdded = testCaseIds.pop();// 104
   
2. shift() & unshift():

Запуск первого теста в очереди и добавление теста на более высокий приоритет.

 let testQueue = ["lowPriorityTest1", "lowPriorityTest2"];<br> let nextTest = testQueue.shift(); <br> testQueue.unshift("highPriorityTest");
3. splice():

Вставка критического теста на вторую позицию.

 let testRunOrder = ["testA", "testB", "testC"];<br> testRunOrder.splice(1, 0, "criticalTest");
 
4. slice():

Извлечение подмножества из массива тестов для параллельного запуска.

  let allTests = ["test1", "test2", "test3", "test4"];<br>   let testsForParallelRun = allTests.slice(0, 2);


5. concat():

Объединение результатов юнит-тестов и интеграционных тестов.
   let unitTestResults = ["Pass", "Fail"];<br>   let integrationTestResults = ["Pass", "Pass"];<br>   let combinedResults = unitTestResults.concat(integrationTestResults);


6. forEach():

Логирование результатов тестов.

   let testResults = [{id: 1, status: "Pass"}, {id: 2, status: "Fail"}];<br>   testResults.forEach(result => {<br>      console.log(`Test ID: ${result.id}, Status: ${result.status}`);<br>   });

7. filter():

Фильтрация тестовых кейсов, которые требуют ручной проверки.


   let testCases = [<br>       {id: 1, type: "automatic"},<br>       {id: 2, type: "manual"},<br>       {id: 3, type: "automatic"}<br>   ];<br>   let manualTests = testCases.filter(test => test.type === "manual");
8. some():

Проверка наличия критических ошибок.


   let testErrors = ["minor", "critical", "minor"];<br>   if (testErrors.some(error => error === "critical")) {<br>       console.log("Critical error found!");<br>   }
9. find():

Поиск конкретного тестового кейса по ID.


   let testCases = [<br>       {id: 1, name: "LoginTest"},<br>       {id: 2, name: "RegistrationTest"}<br>   ];<br>   let specificTest = testCases.find(test => test.id === 2);
10. sort():

Сортировка тестов по приоритету выполнения.


   let testPriorities = ["low", "high", "medium"];
   testPriorities.sort(); // ["high", "low", "medium"]
11. includes():

Проверка наличия определенного теста в наборе.


   let testSuite = ["LoginTest", "DashboardTest", "ProfileTest"];<br>   if (testSuite.includes("LoginTest")) {<br>       console.log("Login test is part of the suite.");<br>   }



Отдельно еще несколько полезных вариантов использования Spread-оператора `...`:



1. Слияние массивов:

Если у вас есть несколько массивов с тестовыми данными и вы хотите объединить их в один массив:


   let basicTests = ['login', 'logout'];
   let advancedTests = ['profileEdit', 'dashboardAccess'];
   let allTests = [...basicTests, ...advancedTests]; // ["login", "logout", "profileEdit", "dashboardAccess"]
2. Копирование массивов:

Для создания копии массива, чтобы избежать изменения оригинала:


   let originalTests = ['testA', 'testB', 'testC'];<br>   let copiedTests = [...originalTests];
3. Использование строк:

Spread-оператор может быть использован для разделения строки на отдельные символы:


   let testName = "login";
   let chars = [...testName]; // ['l', 'o', 'g', 'i', 'n']
4. Слияние объектов:

Если у вас есть несколько объектов с тестовыми настройками, и вы хотите объединить их:


   let defaultSettings = { timeout: 5000, retries: 3 };
   let customSettings = { retries: 5, mode: 'strict' };
   let mergedSettings = { ...defaultSettings, ...customSettings };
   // { timeout: 5000, retries: 5, mode: 'strict' }

Обратите внимание, что свойство `retries` было переопределено значением из `customSettings`.



5. Функции с переменным числом аргументов:

Spread-оператор может использоваться для передачи элементов массива как отдельных аргументов функции:


   let testIds = [1, 2, 3];
   function runTests(id1, id2, id3) {
       console.log(`Running tests: ${id1}, ${id2}, ${id3}`);
   }
   runTests(...testIds); // Running tests: 1, 2, 3
