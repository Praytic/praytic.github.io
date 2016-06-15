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

1. **@Test** - любые тесты должны быть помечены этой аннотацией.
  - С помощью данной аннотации не нужно наследоваться от TestCase класса.
  - Параметры:
    + __expected__ - указывает тип исключения, которое должно быть брошено из данного теста. Например `@Test(expected = IndexOutOfBoundsException.class)`.
    + __timeout__ - указывает время в миллисекундах, после истечения которого тест помечается как непройденный. Например `@Test(timeout = 100)`.
  - Пример:
  ```Java
  @Test
  public void addition() {
      assertEquals(12, simpleMath.add(7, 5));
  }
  ```
  
1. **@Before** - аннотация позволяет выполнять логику перед выполнением каждого теста.
  - Пример:
  ```Java
  @Before
  public void runBeforeEveryTest() {
      simpleMath = new SimpleMath();
  }
  ```

1. **@After** - аннотация позволяет выполнять логику после выполнения каждого теста.
  - Пример:
  ```Java
  @After
  public void runAfterEveryTest() {
      simpleMath = null;
  }
  ```

1. **@BeforeClass** - аннотация позволяет выполнять логику перед выполнением всех тестов в данном классе.
  - Пример:
  ```Java
  @BeforeClass
  public static void runBeforeClass() {
      // run for one time before all test cases
  }
  ```

1. **@AfterClass** - аннотация позволяет выполнять логику после выполнения всех тестов в данном классе.
  - Пример:
  ```Java
  @AfterClass
  public static void runAfterClass() {
      // run for one time after all test cases
  }
  ```
  
1. **@Ignore** - тест, помеченный данной аннотацией, будет пропускаться.
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
  
1. **@RunWith** - если класс содержит данную аннотацию, JUnit будет запускать тесты в классе, который указан в параметрах этой аннотации, вместо стандартного раннера, встроенного в JUnit.
  - Стандартный класс раннера - `BlockJUnit4ClassRunner`, который заменяет старый класс - `JUnit4ClassRunner`.
  - Разновидность раннеров:
    + __Suite__ - позволяет вручную составить набор из тестов разных классов.
    + __Parameterized__ - реализует параметризованные тесты.
    + __Categories__ - включает подвид тестов, принадлежащих той или иной категории.
    + __Enclosed__ - запуская класс с этой аннотацией, можно будет запускать тесты из внутренних классов.
  - Пример:
  ```Java
  @RunWith(Suite.class)
  @SuiteClasses({ATest.class, BTest.class, CTest.class})
      public class ABCSuite {
  }
  ```

1. **@Suite.SuiteClasses** - с помощью данной аннотации, тестовый класс совмещает в себе другие тестовые классы, указанные в параметрах.
  - Пример:
  ```Java
  @RunWith(Suite.class)
  @SuiteClasses({ATest.class, BTest.class, CTest.class})
      public class ABCSuite {
  }
  ```
  
1. **@Parameterized.Parameters** - статический метод, содержащий данную аннотацию создает и возвращает коллекцию из массивов элементов, которые являются параметрами для тестового метода. 
  - Также можно повесить аннотацию __@Parameter__ на public поле, чтобы сразу инжектить значения, вместо того, чтобы передавать их через конструктор. Параметр __value__ - указывает значение по дефолту для поля, на котором висит эта аннотация.
  - Параметры:
    + __name__ - изменяет имя параметризованного теста. Допускается использование таких плейсхолдоров, как {index}, {0}, {1} и так далее.
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
  
1. **@Rule** - с помощью этой аннотации можно создавать специальные объекты, которые используются в тестовых методах. Тестеры могут реиспользовать или расширять эти объекты или создавать свои.
  - Стандартные правила:
    + __TemporaryFolder__ - позволяет создавать файлы или папки, которые удаляются по окончании работы метода. По дефолту не выбрасывается исключений, если ресурс не может быть удален.
    + __ExternalResource__ - базовый класс, который устанавливает внешние ресурсы перед тестом, такие как: файлы, сокеты, сервера, соединения с базами данных и другие.
    + __ErrorCollector__ - позволяет выполнять тест до конца, собирая всевозможные ошибки, которые встретятся во время его выполнения.
    + __Verifier__ - ???.
    + __TestWatcher__ - данное правило позволяет выполнять логику на определенных событиях теста (succeeded, failed, skipped, starting, finished), не изменяя сам тест. Например, этот класс может вести кастомные логи каждого пройденного или упавшего теста.
    + __TestName__ - позволяет выводить название текущего тестового метода.
    + __Timeout__ - устанавливает ограничение по времени выполнения на все методы в тестовом классе.
    + __ExpectedException__ - позволяет вставлять в тесты ожидания исключений или сообщений.
    + __RuleChain__ - устанавливает порядок правил.
    + __ExpectedException__ - позволяет вставлять в тесты ожидания исключений или сообщений.
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
  
1. 
