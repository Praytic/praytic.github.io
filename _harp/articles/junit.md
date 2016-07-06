# JUnit 4

### 1. Общее

1. **Юнит-тестирование** или **модульное тестирование** - тип тестирования, при котором проверяется корректность отдельных модулей программы. Юнит-тесты пишутся для каждой нетривиальной функциональности.
  - Целью юнит-тестирования является изолированное тестирование отдельных частей программы, чтобы показать, что по отдельности эти части являются работоспособными.
  
1. **Интеграционное тестирование** - тип тестирования, при котором отдельные программные модули объединяются и тестируются в группе. Обычно интеграционное тестирования проводится после модульного.
  - Целью интеграционного тестирования является проверка связей между компонентами, а также взаимодействия с различными частями системы.
    
1. **Системное тестирование** - тип тестирования, при котором проверяются как функциональные, так и нефункциональные требования к системе в целом, используя окружение, максимально приближенное к тому, в котором она будет развернута.
  - Целью системного тестирования является выявление дефектов, связанных с использованием ресурсов системы, результатами ее работы, удобством использования и т.д.
  
1. **JUnit** - фреймворк для юнит-тестирования Java кода. 
  - Он является одним из семества xUnit фреймворков для различных языков программирования.
  - JUnit пропогандирует TDD.
  
1. **TDD (Test-Driven Development)** - техника разработки, которая основывается на идее "сначала тестирование, потом кодинг". Подразумевается, что в первую очередь нужно написать тест для будущей функциональности, а затем саму функциональность. Такой подход увеличивает стабильность написанного кода и сводит к минимуму время, потраченное на отладку программы.

### 2. Аннотации

1. **`@Test`** - любые тесты должны быть помечены этой аннотацией.
  - С помощью данной аннотации не нужно наследоваться от TestCase класса.
  - Параметры:
    + __`expected`__ - указывает тип исключения, которое должно быть брошено из данного теста. Например `@Test(expected = IndexOutOfBoundsException.class)`.
    + __`timeout`__ - указывает время в миллисекундах, после истечения которого тест помечается как непройденный. Например `@Test(timeout = 100)`.
  - Пример:
  ```Java
  @Test
  public void addition() {
      assertEquals(12, simpleMath.add(7, 5));
  }
  ```
  
1. **`@Before`** - аннотация позволяет выполнять логику перед выполнением каждого теста.
  - Пример:
  ```Java
  @Before
  public void runBeforeEveryTest() {
      simpleMath = new SimpleMath();
  }
  ```

1. **`@After`** - аннотация позволяет выполнять логику после выполнения каждого теста.
  - Пример:
  ```Java
  @After
  public void runAfterEveryTest() {
      simpleMath = null;
  }
  ```

1. **`@BeforeClass`** - аннотация позволяет выполнять логику перед выполнением всех тестов в данном классе.
  - Пример:
  ```Java
  @BeforeClass
  public static void runBeforeClass() {
      // run for one time before all test cases
  }
  ```

1. **`@AfterClass`** - аннотация позволяет выполнять логику после выполнения всех тестов в данном классе.
  - Пример:
  ```Java
  @AfterClass
  public static void runAfterClass() {
      // run for one time after all test cases
  }
  ```
  
1. **`@Ignore`** - тест, помеченный данной аннотацией, будет пропускаться.
  - Параметры:
    + Параметром служит строка - причина пропуска теста.
  - Пример:
  ```Java
  @Ignore(“Not Ready to Run”)
  @Test
  public void multiplication() {
      assertEquals(15, simpleMath.multiply(3, 5));
  }
  ```
  
1. **`@RunWith`** - если класс содержит данную аннотацию, JUnit будет запускать тесты в классе, который указан в параметрах этой аннотации, вместо стандартного раннера, встроенного в JUnit.
  - Стандартный класс раннера - `BlockJUnit4ClassRunner`, который заменяет старый класс - `JUnit4ClassRunner`.
  - Разновидность раннеров:
    + __`Suite`__ - позволяет вручную составить набор из тестов разных классов.
    + __`Parameterized`__ - реализует параметризованные тесты.
    + __`Categories`__ - включает подвид тестов, принадлежащих той или иной категории.
    + __Enclosed__ - запуская класс с этой аннотацией, можно будет запускать тесты из внутренних классов.
  - Пример:
  ```Java
  @RunWith(Suite.class)
  @SuiteClasses({ATest.class, BTest.class, CTest.class})
      public class ABCSuite {
  }
  ```

1. **`@Suite.SuiteClasses`** - с помощью данной аннотации, тестовый класс совмещает в себе другие тестовые классы, указанные в параметрах.
  - Пример:
  ```Java
  @RunWith(Suite.class)
  @SuiteClasses({ATest.class, BTest.class, CTest.class})
      public class ABCSuite {
  }
  ```
  
1. **`@Parameterized.Parameters`** - статический метод, содержащий данную аннотацию создает и возвращает коллекцию из массивов элементов, которые являются параметрами для тестового метода. 
  - Также можно повесить аннотацию __`@Parameter`__ на public поле, чтобы сразу инжектить значения, вместо того, чтобы передавать их через конструктор. Параметр __`value`__ - указывает значение по дефолту для поля, на котором висит эта аннотация.
  - Параметры:
    + __`name`__ - изменяет имя параметризованного теста. Допускается использование таких плейсхолдоров, как {index}, {0}, {1} и так далее.
  - Пример:
  ```Java
  @RunWith(Parameterized.class)
  public class FibonacciTest {
      @Parameters(name = "{index}: fib({0})={1}")
      public static Iterable<Object[]> data() {
          return Arrays.asList(new Object[][] { 
                  { 0, 0 }, { 1, 1 }, { 2, 1 }, { 3, 2 }, { 4, 3 }, { 5, 5 }, { 6, 8 }
          });
      }

      @Parameter // first data value (0) is default
      public /* NOT private */ int fInput;

      @Parameter(value = 1)
      public /* NOT private */ int fExpected;

      @Test
      public void test() {
          assertEquals(fExpected, Fibonacci.compute(fInput));
      }
  }
  ```

1. **`@Category`** - разновидность раннера, который запускает только те тестовые классы и методы, которые аннотированы `@IncludeCategory` аннотацией или ее расширениями.
  - Категориями могут быть как классы, так и интерфейсы.
  - `@IncludeCategory` - включает указанную в параметрах категорию.
  - `@ExcludeCategory` - исключает указанную в параметрах категорию.
  - Пример:
  ```Java
  public interface FastTests { /* category marker */ }
  public interface SlowTests { /* category marker */ }
  
  public class A {
    @Test
    public void a() {}
  
    @Category(SlowTests.class)
    @Test
    public void b() {}
  }
  
  @Category({SlowTests.class, FastTests.class})
  public class B {
    @Test
    public void c() {}
  }

  @RunWith(Categories.class)
  @IncludeCategory(SlowTests.class)
  @SuiteClasses( { A.class, B.class }) // Note that Categories is a kind of Suite
  public class SlowTestSuite {
    // Will run A.b and B.c, but not A.a
  }
  
  @RunWith(Categories.class)
  @IncludeCategory(SlowTests.class)
  @ExcludeCategory(FastTests.class)
  @SuiteClasses( { A.class, B.class }) // Note that Categories is a kind of Suite
  public class SlowTestSuite {
    // Will run A.b, but not A.a or B.c
  }
  ```

1. **`@Rule`** - с помощью этой аннотации можно создавать специальные объекты, которые используются в тестовых методах. Тестеры могут реиспользовать или расширять эти объекты или создавать свои.
  - Стандартные правила:
    + __`TemporaryFolder`__ - позволяет создавать файлы или папки, которые удаляются по окончании работы метода. По дефолту не выбрасывается исключений, если ресурс не может быть удален.
    + __`ExternalResource`__ - базовый класс, который устанавливает внешние ресурсы перед тестом, такие как: файлы, сокеты, сервера, соединения с базами данных и другие.
    + __`ErrorCollector`__ - позволяет выполнять тест до конца, собирая всевозможные ошибки, которые встретятся во время его выполнения.
    + __`Verifier`__ - ???.
    + __`TestWatcher`__ - данное правило позволяет выполнять логику на определенных событиях теста (succeeded, failed, skipped, starting, finished), не изменяя сам тест. Например, этот класс может вести кастомные логи каждого пройденного или упавшего теста.
    + __`TestName`__ - позволяет выводить название текущего тестового метода.
    + __`Timeout`__ - устанавливает ограничение по времени выполнения на все методы в тестовом классе.
    + __`ExpectedException`__ - позволяет вставлять в тесты ожидания исключений или сообщений.
    + __`RuleChain`__ - устанавливает порядок правил.
    + __`ExpectedException`__ - позволяет вставлять в тесты ожидания исключений или сообщений.
  - Пример:
  ```Java
  public class DigitalAssetManagerTest {
    @Rule
    public TemporaryFolder tempFolder = new TemporaryFolder();
  
    @Rule
    public ExpectedException exception = ExpectedException.none();
  
    @Test
    public void countsAssets() throws IOException {
      File icon = tempFolder.newFile("icon.png");
      File assets = tempFolder.newFolder("assets");
      createAssets(assets, 3);
  
      DigitalAssetManager dam = new DigitalAssetManager(icon, assets);
      assertEquals(3, dam.getAssetCount());
    }
  
    private void createAssets(File assets, int numberOfAssets) throws IOException {
      for (int index = 0; index < numberOfAssets; index++) {
        File asset = new File(assets, String.format("asset-%d.mpg", index));
        Assert.assertTrue("Asset couldn't be created.", asset.createNewFile());
      }
    }
  
    @Test
    public void throwsIllegalArgumentExceptionIfIconIsNull() {
      exception.expect(IllegalArgumentException.class);
      exception.expectMessage("Icon is null, not a file, or doesn't exist.");
      new DigitalAssetManager(null, null);
    }
  }
  ```

1. **@FixMethodOrder** - класс, помеченный данной аннотацией, сможет запускать тесты в некотором установленном порядке, так как изначально их порядок устанавливается через рефлексию.
  - Параметры:
    + Параметром является тип сортировки тестовых методов. Возможные типы: DEFAULT, JVM, NAME_ASCENDING.

### 3. Asserts & Assumes

1. **Assert** — это конструкция, позволяющая проверять предположения о значениях произвольных данных в произвольном месте программы. 
  - Пример:
  ```Java
  @Test
  public void testAssertEquals() {
    assertEquals("failure - strings are not equal", "text", "text");
  }
  ```

1. **Assume** - это конструкция, позволяющая проверять корректность теста перед его выполнением. 
  - По дефолту JUnit воспринимает тесты, которые не прошли какую-то assume проверку, как проигнорированные.
  - Упавший на assume проверке метод, помеченный аннотацией `@Before` пометит все тестовые методы в данном классе как проигнорированные.
  - Пример:
  ```Java
  @Test public void filenameIncludesUsername() {
      assumeThat(File.separatorChar, is('/'));
      assertThat(new User("optimus").configFileName(), is("configfiles/optimus.cfg"));
  }
  ```

1. **JUnit Asserts**. JUnit предоставляет перегруженные ассерты для наиболее распространенных действий:
  - __`assertArrayEquals`__ - проверяет два массива на равенство.
  - __`assertEquals`__ - проверяет два примитива/объекта на равенство.
  - __`assertFalse`__ - проверяет условие на ложность.
  - __`assertTrue`__ - проверяет условие на истинность.
  - __`assertNotNull`__ - проверяет, что объект не null.
  - __`assertNull`__ - проверяет, что объект null.
  - __`assertNotSame`__ - проверяет, что два объекта не ссылаются на одну область памяти.
  - __`assertSame`__ - проверяет, что два объекта ссылаются на одну область памяти.
  - __`assertThat`__ - специальный ассерт, исполользующий матчеры.

1. **`assertThat`** - механизм ассертов, основанный на JMock 1. Преимущество нового метода в том, что он более читаем за счет матчеров, которые можно расширять.
  - Список матчеров из Hamcrest фреймворка, которые заменяют стандартные JUnit-овские ассерты:
    + anything - всегда удовлетворяет условию.
    + describedAs - пустышка, чтобы добавлять описание ошибки.
    + is - пустышка, чтобы улучшить читемость.
    + allOf - аналогия оператору "и".
    + anyOf - аналогия оператору "или".
    + not - аналогию оператору отрицания.
    + equalTo - проверка на равенство объектов, используя `Object.equals`.
    + hasToString - проверяет на равенство с помощью `Object.toString`.
    + instanceOf, isCompatibleType - проверка совпадения типов.
    + notNullValue, nullValue - проверка на null.
    + sameInstance - проверка инстансов объектов.
    + hasProperty - проверка JavaBeans пропертей.
    + array - позволяет устанавливать несколько матчеров.
    + hasEntry, hasKey, hasValue - проверка мапы на содержания ключа, значения или кортежа.
    + hasItem, hasItems - проверка коллекции на содержание элемента/ов.
    + hasItemInArray - проверка массива на содержание элемента.
    + closeTo - проверка чисел с плавающей запятой на близость по значению к заданному числу.
    + greaterThan, greaterThanOrEqualTo, lessThan, lessThanOrEqualTo - аналогия операторам неравенства.
    + equalToIgnoringCase - проверка на равенство строке, игнорируя регистр букв.
    + equalToIgnoringWhiteSpace - проверка равенство строке, игнорируя пробелы.
    + containsString, endsWith, startsWith - проверка на содержание вхождения строки.

### 4. Mockito

1. **Mock** - объект-пустышка, предназначенный для проверки ожидаемого поведения тестируемого объекта.

1. **Stub** - объект-пустышка, предназначенный для получения нужного состояния тестируемого объекта. Они моделируют внешнее окружение тестового класса.

1. **Mockito** - фреймворк для тестирования, который используется в сочитании с JUnit. Он позволяет создавать и настраивать моки.

### Источники

1. https://github.com/junit-team/junit4/wiki
1. http://www.vogella.com/tutorials/JUnit/article.html
1. http://www.vogella.com/tutorials/Mockito/article.html
1. https://code.google.com/archive/p/hamcrest/wikis/Tutorial.wiki
1. http://www.tutorialspoint.com/junit/index.htm
1. https://en.wikipedia.org/wiki/Unit_testing
1. https://habrahabr.ru/post/134836/
