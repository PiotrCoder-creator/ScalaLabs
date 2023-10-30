# ScalaLabs
---
## Лабораторные работы по дисциплине "ф-прог" (Функциональное программирование) Scala 3, 3 курс 5 семестр БГУИР КСиС ВМСиС 2023. Конспект лекций ниже, после лабораторных работ.
## Мною выполнялись следующие лабораторные работы по варинатам соответственно: лр 1 вар 3, лр 2 вар 2, лр 3 вар 1, лр 4 вар 1, лаб 5 вар общий.
 ---
### Лабораторная работа 1. Создание простых S-проектов на основе классов

#### Вариант 1. 
 Построить генератор случайных чисел по следующей схеме. Вводите 10-значное число  с клавиатуры. Формируете два новых целых числа A и B: 
 первое  A состоит из первых пяти цифр, второе B  – из последних  цифр введенного числа, начиная с шестой.    
 Перемножаете числа A и B друг на друга. Первые три цифры результата С, будучи поделенными на 1000, дают первое случайное число REZ.  
 Чтобы сформировать следующее случайное число, прибавляете к Z число  С и повторяете процесс. Формируете два новых целых числа A и B: 
 первое  A состоит из первых пяти цифр, второе B  – из последних  цифр числа Z, начиная с шестой.    
 Перемножаете числа A и B друг на друга. Первые три цифры результата С, будучи поделенными на 1000, дают второе случайное число.  
 Чтобы сформировать следующее случайное число, прибавляете к Z число  С и повторяете процесс. Сформируйте 5 случайных чисел.
Если z отрицателен, то это значит, что надо заменить первую цифру единицы на ноль и убрать знак “минус”, кроме того,
нужно поддерживать длину строки не меньше 10 символов. Сказанное, демонстрируется следующим примером:
   
    object Main234 {
      def main(args: Array[String]): Unit = {
       print("Enter the number: ")
   
     var numberString =""
     var a =0
     var b=0
     var c=0
     var rez: Float =0.0
     var z=0
     numberString = scala.io.StdIn.readLine()
      if ( (numberString.length() <= 10)) {
       println("Incorrect number");
       sys.exit(0)  }
      for (i <- 1 to 10) {
      a = numberString.substring(0, 5).toInt
      //println(numberString.length()); 
      b=  numberString.substring(5, 10).toInt
      c= a*b
      rez=c.toString().substring(0,3).toFloat / 1000
      z+=c 
      println(a);
      println(b);
      println(c);
      println(rez); 
      println("z="+ z)
      numberString= numberString.substring(1,numberString.length()-1)
      numberString="011"+z 
       } 
      } 
    }

#### Вариант 2. 
Использовать предыдущий пример, но только число А получается из цифр, стоящих на четных позициях, а В-на нечетных.

    def substringFromSymbolsAtEvenPositions(str: String): String = {
      val result = new StringBuilder
      for (i <- str.indices if i % 2 == 1) {
        result.append(str(i))
      }
      result.toString()
    }
    
     object Main234 {
      def main(args: Array[String]): Unit = {
        val originalString = "1234567890"
        val substring = substringFromSymbolsAtEvenPositions(originalString)
        println(substring)
    }
    }
    // Сформируйте по этой схеме 5 случайных чисел.
            
#### Вариант 3. 
Построить генератор случайных чисел по следующей схеме. Вводите 10-значное число Z с клавиатуры. Формируете два новых целых числа A и B: 
первое  A состоит из первых пяти цифр, второе B  – из последних  цифр числа Z, начиная с шестой.   
Дописываете к числу В число А. Получаете число W. Находите С= Z*W. Первые три цифры результата С, будучи поделенными на 1000, дают первое случайное число REZ.  
Чтобы сформировать следующее случайное число, формируете два новых целых числа A и B: первое  A состоит из первых пяти цифр, второе B  – из последних  цифр числа C,
начиная с шестой.    Дописываете к числу В число А. Получаете число W. Находите C= C*W. Первые три цифры результата C, будучи поделенными на 1000, 
дают второе случайное число REZ. 
Сформируйте 3 случайных чисел по этой схеме.

#### Вариант 4.       
Построить генератор случайных чисел по следующей схеме. Вводите 16-значное число Z с клавиатуры. Формируете два новых целых числа A и B: 
первое  A состоит из первых восьми цифр, второе B  – из последних  цифр числа Z, начиная с девятой.    
Перемножаете числа A и B друг на друга, получаем число С. Первые три цифры результата С, будучи поделенными на 1000, дают первое случайное число REZ. 
Чтобы сформировать следующее случайное число, умножаете Z  на число  С  и оставляете 16 цифр в результате. Повторяете процесс для сформированного таким образом числа Z. 
Формируете два новых целых числа A и B: первое  A состоит из первых восьми цифр, второе B  – из последних  цифр числа Z, начиная с девятой.    
Перемножаете числа A и B друг на друга. Первые три цифры результата С, будучи поделенными на 1000, дают второе случайное число. 
Чтобы сформировать следующее случайное число, умножаете  Z  на число  С и повторяете процесс. Сформируйте 5 случайных чисел.

---

### Лабораторная работа 2. Работа со списками и функциями

#### Вариант 1. 
1. Написать функцию для подсчета суммы элементов списка, значение которых не превосходит 10. Список задать самостоятельно.
2. Написать функцию для подсчета суммы первых трех элементов списка из 10 элементов. Список задать самостоятельно.
3. Написать функцию для отыскания (минимального) индекса максимального элемента списка. Список задать самостоятельно.
4. Написать функцию для проверки того, что список упорядочен по возрастанию. Список задать самостоятельно.
5. Написать функцию для проверки наличия одинаковых элементов в списке. Список задать самостоятельно. Функция возвращает значение Да или Нет

#### Вариант 2. 
1. Написать функцию для подсчета суммы отрицательных элементов списка. Список задать самостоятельно.
2. Написать функцию для подсчета суммы последних трех элементов списка из 10 элементов. Список задать самостоятельно.
3. Написать функцию для отыскания  индексов всех максимальных элементов списка. Список задать самостоятельно.
4. Написать функцию для проверки того, что список не упорядочен  ни по возрастанию, ни по убыванию. Список задать самостоятельно.
5. Написать функцию для проверки наличия  трех одинаковых элементов в списке. Список задать самостоятельно. Функция возвращает значение такого элемента.
           
#### Вариант 3. 
1. Написать функцию для подсчета суммы элементов списка, значение которых лежит в диапазоне [0,5]. Список задать самостоятельно.
2. Написать функцию для подсчета суммы элементов списка с номерами, содержащимися в другом списке. Список задать самостоятельно.
3. Написать функцию для отыскания индекса минимального элемента списка. Список задать самостоятельно.
4. Написать функцию для проверки того, что элементы списка не превосходят заданной величины. Список задать самостоятельно.
5. Написать функцию для подсчета числа  элементов списка, которые не превосходят заданной величины. Список задать самостоятельно.

#### Вариант 4.     
1. Написать функцию для подсчета суммы элементов списка, значение которых по модулю не превосходит 5. Список задать самостоятельно.
2. Написать функцию для подсчета суммы каждого второго элемента списка из 10 элементов. Список задать самостоятельно.
3. Написать функцию для отыскания  индекса элемента списка, наименее отклоняющегося от среднего значения по списку. Список задать самостоятельно.
4. Написать функцию для проверки того, что список содержит квадрат одного из своих элементов. Список задать самостоятельно.
5. Написать функцию для проверки наличия трех разных элементов в списке. Список задать самостоятельно. Функция возвращает значение Да или Нет

---

### Лабораторная работа 3. Работа со строками

#### Вариант 1. 
1. Дан текст: ‘Hello to everybody’. C помощью техники регулярных выражений заменить латинские буквы на русские (или на цифры, если русский шрифт не поддерживается)
2. Найти в тексте “When executing the exercise extract all extra words” все слова, начинающиеся на ext.
2. В тексте ‘A big round ball fall to the ground’  заменить артикль the на a.
3. Записать все слова в тексте в обратном порядке.
4. Дан текст: ‘Hello to everybody’. Выбросить все гласные.
5. Дан текст: ‘Hello to everybody’. Удвоить каждую букву в слове
6. Дан текст: ‘Hello to everybody’. Удалить все вхождения буквы y
7. Дан текст: ‘Hello to everybody’. Вставить слова with heartness чтобы получить
8. Hello with heartness  to everybody

#### Вариант 2. 
1. Дан текст: ‘1+1=2’. C помощью техники регулярных выражений заменить цифры на слова: 1- one, 2 - two
2. Найти в тексте ‘Being quiet buetiful girl she never thought of buety’ все слова, начинающиеся на bue.
3. В тексте ‘one plus one is something’  заменить one на two.
4. Поменять местами первое и последнее слово в тексте  world is nice.
5. Дан текст: ‘Hello to all my friends’. Выбросить все согласные.
6. Дан текст: ‘Hello to everybody’. Удалить каждую вторую букву в слове
7. Дан текст: ‘Hello to everybody’. Удалить все вхождения буквы e
8. Дан текст: ‘Be healthy’. Вставить слова always чтобы получить Be always healthy

            
#### Вариант 3. 
1. Дан текст: ‘Passport AB-123-456’. C помощью техники регулярных выражений  найти числа в этом тексте
2. Найти в тексте ‘Being strong means nothing’ все слова, заканчивающиеся на ing.
3. В тексте ‘123+723=846’  заменить 3 на 4, 6 – на 8.
4. Записать все слова в тексте в случайном порядке. Текст: big dreadful dog runs after small poor cat. Всех слов 8. Номера 1,2,3, …,8. 
5. Заменить слово с номером 1 на слово с номером 7, слово с номером 2 на слово с номером 6, слово с номером 4 на слово с номером 5. 
Замена обоюдная, то есть слова просто меняются местами.
6. Дан текст: ‘Hello to everybody’. Выбросить каждую третью букву.
7. Дан текст: ‘Hello to everybody’. Удвоить каждую букву в слове
8. Дан текст: ‘Hello to everybody’. Удалить все вхождения буквы o
9. Дан текст: ‘Hello to everybody Katty, Mikky’. Вывести все слова, начинающиеся с заглавной буквы.


#### Вариант 4. 
1. Дан текст: ‘Passport AB-123-436’. C помощью техники регулярных выражений найти число вхождений цифры 3.
2. Дан текст: ‘Passport AB-123-436’. C помощью техники регулярных выражений найти сумму всех цифр в тексте.
3. В тексте ‘123+723=846’  выделить все символы арифметических операций.
4. Записать все слова в тексте в случайном порядке. Текст: big black cat runs after small poor catty. Всех слов 8. Номера 1,2,3, …,8. 
5. Заменить слово с номером 1 на слово с номером 4, слово с номером 2 на слово с номером 7, слово с номером 3 на слово с номером 6. 
Замена обоюдная, то есть слова просто меняются местами.
6. Дан текст: ‘Hello to Ronny old nail’. Найти удвоенные вхождения согласных.
7. Дан текст: ‘Hello to Ronny old nail’. Найти число слов, записанных с большой буквы.
8. Дан текст: ‘Hello to everybody’. Подсчитать число всех вхождений буквы o
9. Дан текст: ‘Hello agaiN to everybody Katty, Mikky’. Вывести все слова, начинающиеся со строчной буквы.

---

### Лабораторная работа 4. Работа с пакетом SPARK

#### Вариант 1. 
1. Создать собственный текстовый файл на английском или немецком языке – 4-5 предложений.
2. Вывести все слова из текстового файла, исключая stop-слова
3. Вывести все слова, содержащие букву t
4. Вывести все слова, заканчивающиеся на ing
5. Вывести все слова вторая буква которых а
6. Вывести все слова, последняя буква которых s
7. Вывести каждое второе слово

#### Вариант 2. 
1. Создать собственный текстовый файл на английском или немецком языке – 4-5 предложений. Тема - программирование
2. Вывести все слова из текстового файла, исключая stop-слова
3. Вывести все слова, содержащие вхождение prog
4. Вывести все слова, заканчивающиеся на ion
5. Вывести все слова третья буква которых r
6. Вывести все слова, содержащие как минимум две буквы e
7. Вывести последнее слово
            
#### Вариант 3. 
1. Создать собственный текстовый файл на английском или немецком языке – 4-5 предложений. Тема - спорт
2. Вывести все слова из текстового файла, исключая stop-слова
3. Вывести все слова, содержащие вхождение ball или sport
4. Вывести все слова, заканчивающиеся на ion
5. Вывести все слова третья буква которых c
6. Вывести все слова, длина которых больше 4
7. Вывести предпоследнее слово

#### Вариант 4.         
1. Создать собственный текстовый файл на английском или немецком языке – 4-5 предложений. Тема - авто
2. Вывести все слова из текстового файла, исключая stop-слова
3. Вывести все слова, содержащие вхождение car или avto
4. Вывести все слова, заканчивающиеся на my
5. Вывести все слова третья буква которых d
6. Вывести все слова, у которых три и более гласных
7. Вывести второе слово

### Доп задания: 
1-е задание: написать 2 предложения на английском языке и удалить оттуда все пробелы между словами через регулярные выражения двумя разными способами.
________________________________________________________________________________________

	val sentences = Seq("This is the first sentence.", "Here is the second sentence.")
	val sentenceRDD = spark.sparkContext.parallelize(sentences)
	
	val sentenceWithoutSpaces1 = sentenceRDD.map(sentence => sentence.replaceAll(" ", ""))
	sentenceWithoutSpaces1.collect().foreach(println)
	
	val sentenceWithoutSpaces2 = sentenceRDD.map(sentence => sentence.split(" ").mkString(""))
	sentenceWithoutSpaces2.collect().foreach(println)

________________________________________________________________________________________

	val sentences = Seq("This is the first sentence.", "Here is the second sentence.")
	val sentenceRDD = spark.sparkContext.parallelize(sentences)
	
	val sentencesWithoutSpaces = sentenceRDD.map(sentence => sentence.replaceAll("\\s", ""))
	sentencesWithoutSpaces.collect().foreach(println)

________________________________________________________________________________________

2-е задание: в слове mother утроить букву t.
________________________________________________________________________________________

	val word = "mother"
	val wordWithTripleT = word.replace("t", "ttt")
	println(wordWithTripleT)

3-e задание: удалить все гласные во всех словах из двух английских предложений из 1-го задания.
________________________________________________________________________________________

	val sentences = Seq("This is the first sentence.", "Here is the second sentence.")
	val sentenceRDD = spark.sparkContext.parallelize(sentences)
	
	val vowels = "aeiouAEIOU"
	val wordsWithoutVowels = sentenceRDD.flatMap(sentence => {
	  val words = sentence.split(" ")
	  words.map(word => word.replaceAll(s"[$vowels]", ""))
	})
	wordsWithoutVowels.collect().foreach(println)
____________________________________________________________________________________

---

### Лабораторная работа 5. Работа с базой данных

	import java.awt.event.{ActionEvent, ActionListener}
	import javax.swing.{JButton, JFrame, JPanel, SwingUtilities}
	
	object  ButtonModule {
	  def main(args: Array[String]): Unit = {
	    SwingUtilities.invokeLater(() => {
	      val frame = new JFrame("My Application")
	      frame.setSize(300, 200)
	      frame.setLocationRelativeTo(null)
	      val panel = new JPanel()
	      val button = new JButton("Click me!")
	      panel.add(button)
	
	      button.addActionListener(new ActionListener {
	        override def actionPerformed(e: ActionEvent): Unit = {
	          println("Hello, world!")
	        }
	      })
	
	      frame.add(panel)
	      frame.setVisible(true)
	    })
	  }
	}

 Наше  приложение таково
	
	import java.awt.event.{ActionEvent, ActionListener}
	import javax.swing.{JButton, JFrame, JPanel, SwingUtilities}
	import java.awt.Dimension
	import javax.swing.{JFrame, JLabel,JTextField, JPanel, SwingUtilities}
	import java.sql.{Connection, DriverManager, ResultSet}
	import java.awt.Color
	
	object ButtonModule  {
	   val frame = new JFrame("My Application")
	  frame.setSize(800, 600)
	  frame.setLayout(null)
	  
	  def main(args: Array[String]): Unit = {
	       SwingUtilities.invokeLater(() => {
      
     // val panel = new JPanel()
      val label1=new JLabel("Title")
      val label2=new JLabel("Price")
      label1.setBounds(50,120,100,20)
      label2.setBounds(200,120,70,20)
      val button1 = new JButton("Insert")
      val button2 = new JButton("Select")
      val textField = new JTextField(20)
      val textField2 = new JTextField(20)
      button1.setBounds(20,80,120,20)
      button2.setBounds(150,80,250,20)
      textField.setBounds(20,150,130,20)
      textField2.setBounds(160,150,130,20)
      frame.add(button1)
      frame.add(button2)
      frame.add(label1)
      frame.add(textField)
      frame.add(label2)
      frame.add(textField2)
      
      button1.addActionListener(new ActionListener {
        override def actionPerformed(e: ActionEvent): Unit = {
          val url = "jdbc:mysql://localhost:3306/mydb"
    val username = "root"
    val password = "1"
          Class.forName("com.mysql.jdbc.Driver")
      // Class.forName("org.gjt.mm.mysql.Driver")

          val conn = DriverManager.getConnection(url, username, password)
   
          try {
           val stmt = conn.createStatement()
        val rs = stmt.execute("INSERT INTO sclad VALUES ('" + textField.getText + "'," + textField2.getText + ")")
          
         
           textField2.setText("")
           
          textField.setText("Added record")
         }
          finally {
            conn.close()
                 }

          
          
       //   textField.setText("problems")
        }
      })
        
      
      
      button2.addActionListener(new ActionListener {
        override def actionPerformed(e: ActionEvent): Unit = {
          ////////
          {
    val url = "jdbc:mysql://localhost:3306/mydb"
    val username = "root"
    val password = "1"

    Class.forName("com.mysql.jdbc.Driver")
    val conn = DriverManager.getConnection(url, username, password)

    try {
       val stmt = conn.createStatement()
       val prod_name= textField.getText().toString().trim()
       val rs = stmt.executeQuery("SELECT * FROM sclad WHERE product = '"+prod_name+"'")
       while (rs.next()) {
         
         val name = rs.getString("product")
         val price = rs.getInt("price")
        // println(s"name=$name, price=$price")
         textField2.setText(""+price)
         }
       } finally {
    conn.close()
                 }
}
    
          ///////
          
          
       //   textField.setText("Hello World, You say")
        }
      })

    
      frame.setBackground(Color.BLUE)
      frame.setLocationRelativeTo(null)
      frame.setVisible(true)
      
      })
  }
}
Разберитесь с этим приложением.

#### Вариант Общий.
1. Расширить количество столбцов таблицы sclad, добавив поле количество товара на складе.
2. Вывести товар, дающий максимальную прибыль (количество*цену).
3. Выбрать товар по ограничению (не меньше такой-то величины).

---

# Лекции Scala 

## первая лекция 
## ЛК1 ФПрогр Принципы функциональной парадигмы (ФП). Обзор. Современное состояние ФП.

### Функциональное программирование - это парадигма программирования, в которой основное внимание уделяется использованию функций как основных строительных блоков программного обеспечения.

Языки ФП обычно предоставляют такие ф-ии, как ф-ии высшего порядка, лямбда выражения. Примеры языков ФП включают Hаskel, Lisp, ML и Scala. Однако многие другие языки, такие как Python, JavaScrypt и Java, также в некоторой степени поддерживают ФП. В том числе андроид студия поддерживает скала. 
ФП уходит своими корнями в лямбда исчисления математическую нот ацию разработанную черчем в 30 года 50-60 годы был разработан язык лисп который считается первым языком функционального программирования 70-80 фп приобркло популярность в академичесокм сообщестьве (языки мирандар, мл и тд.), в 90-ч годах в связи с развитием промышленности получили развитие как хаскел и scheme. Сегодня уже используются скала фшарп кложуре. ФП используется на практике например в обработке больших данных поскольку делает упор на неизменяемость и параллелизм. Второе это вэб разработка чаще используетяс для создания интерфейсых приложений треть е фигнансовое моделирование разработка игр(например юнити использует фп для своего языка сценариев). Машинное обучение.

### Ключевые Концепции ФП
1 Использование чистых функций - которая не имеет побочных эффектов возвращают одни и теже выходные данные при одних и тех жке входных. 
2 Неизменяемость, ФП отдаёт предпочтение неизменяемым структурам данных, те кот нельзя изменить после создания, это упрозает код анализ кода
3 Ф-ии высшего порядка, это ф-ии кот принимают др ф-иив качве входных данных или возвращает ф-ии в качве выходных данных 
4 Рекурсия, вызов ф-ии самой себя 
5 Ленивые вычисления, это метод при кот выражения не вычисяются до тех пор пока они не будут востребованы это может сэкономить время вычисления и память
6 Монады, это способ вычисления в виде последовательности шагов при этом гарантируется что каждый шаг выполняется в опрерделенном порядке и определенном контексте 

Скала является масшабируемым языком программирования потому что он был разраотан с нуля для крупномасштабной разработки ПО. Способен справляться с растущим объёмом данных без ущерба для производительнрости или надёжности, в час ности используется в больших данных и облачных вычислениях. сочетает в себе ф-ии ООП, ФП. В скала есть
1 строгая статическая типизация то есть позволяет компилятору обнаружить ошибки ещё до выполнения программы 
2 поддержка параллелизма, позволяет упрощать нааписание кода способного асинхронно обрабатывать несколько потоков и событий 
3 совместимость с джава, работает на джэвээм может взаимодействовать с кодом и библиотеками джава 

пример 1:

	object Main22{
	
	val f:(Int=>Int) = {
		val p=10
		val q=20
		x=> p+q*x
	}
	
	def main(args: Array[String]): Unit = {
		val t=f(4)
		println(t)
	}
	
	}


### Прогназирование

### Простейшие примеры программ на Scala

Пример программы, вычисляющей сумму двух числе:

object 

### 2 тема 
Существует несколько тем интегрированных сред разработки IDE поддерживающих разработку программ на скала Интелиж идея, Эклипс, ВС код,  Скала ИДЕ. Object  это считается как целый класс
Модули обычно используются в скала для и др глобальных обьектов 

Пример взаимодействия класов внутри модуля

    object MyModule {
      class MyClassA(val name: String){
        def greet(): Unit = println(s"Hello from $name!")
    
        def callB(b: MyClassB): Unit = {
          println(s"name is calling $(b.name)")
          b.greet()
        }
      }
    }

    class MyClassB(val name: String){
      def greet():Unit = println(s"Hello from $name!")
    
      def callA(a: MyClassA):Unit = {
        println(s"$name is calling ${a.name}!")
        a.greet()
      }
    }
    
    object Main {
      def main(args:Array[String]):Unit = {
        val a = new MyModule.MyClassA("Alice")
        val b = new MyModule.MyClassB("Bob")
    
        a.callB(b)
        b.callA(a)
      }
    }

---

В Scala конструкторы используются для создания экземпляров классов
Бывают два типа:
1) Первичные (основные)
2) Вспомогательные 

Первичный конструктор определяется, как часть определения класса и выполняется при создании экземпляра класса
Параметры основного конструктора определены в определении класса (Имя конструктора = имени класса)

    // Пример с первичным конструктором
    class MyClass(val name: String, val age: Int) {
      println("Creating instance of MyClass")
      def greet():Unit = println()
    
      // .....
    }

Вспомогательный конструктор могут иметь другие списки параметров, чем у основного. Определеются с помощью ключевого слова this, должны вызывать либо первичный конструктор, либо другой вспомогательный конструктор в качестве своего первого оператора

    // Пример со вспомогательным конструктором
    class MyClass(val name: String, val age: Int) {
      def this(name:String) = this(name, 0)
    
      println("Creating instance of MyClass")
      def greet():Unit = println(s"Hello, $name and $age years old")
    }

Вспомогательный конструктор вызывает основной конструктор с параметром name и значением по умолчанию (0)

    // Со вспомогательным конструктором
    
    object Main {
        def main(args: Array[String]):Unit = {
        val myObject2 = new MyClass("Jane")
        myObject2.greet() // print greet
      }
    }

Чтобы создать экземпляр класса с помощью вспомогательного конструктора можно использовать ключевое слово new за которым следует имя класса и параметры вспомогательного конструктора.

Пример чтения файлов и вывода его содержимого на консоль

    import java.io._
    
    class MyClass {
      // Initialize resources
      val fileHandle = new File("data.txt") // открывает файл для чтения
      val fis = new FileInputStream(fileHandle)
      val bis = new BufferedInputStream(fis) // читается блок байтов в память
      val dis = new DataInputStream(bis) // чтение данных
    
      try {
        while(dis.available() != 0) {
          val line = dis.readLine()
          println(line)
        } } catch {
          case e: IOException =>
            println("An error occured while reading the file:" + e.getMessage)
        }
        finally {
          dis.close()
          println("reading closed")
        }
      }
    
      override def finalize(): Unit = {
        super.finalize()
      }
    }
    
    object Main {
      def main(args: Array[String]): Unit = {
        val myObjest2 = new MyClass
        myObject2.finalize()
        println("ok")
      }
    }
    
    Пример смешения трейтов
    
    trait Flyable {
      def fly(): Unit = {
        println("Flying...")
      }
    }
    
    trait Swimmable {
      def swim(): Unit = {
        println("Swimming...")
      }
    }
    
    trait Walkable {
      def walk(): Unit = {
        println("Walking...")
      }
    }
    
    class Animal extends Flyable with Swimmable with Walkable
    
    object Main {
      def main(args: Array[String]): Unit = {
        val animal = new Animal
        animal.fly
        animal.swim
        animal.walk
      }
    }
    
    Функции и мтоды для работы со списками
    \(\bullet\) :: добавляет элемент в начало списка 
    \(\bullet\) :+ добавляет элемент в конец списка 
    \(\bullet\) ++ объединение списков 
    \(\bullet\) head элемент начала списка 
    \(\bullet\) tail список без головы
    \(\bullet\) isEmpty проверяет список на пустоту (true or false)
    \(\bullet\) length возвращает длину списка 
    \(\bullet\) contains проверяет существует ли в списке заданный элемент (true or false)
    \(\bullet\) distinct возвращает новый список, содержащий уникальные элементы списка 
    
    Map (карта, отображение) 
    функция применяет заданную функцию к каждому элементу списка и возвращает новый список
    
    def double(x: Int): Int = x * 2
    
    def main(args: Array[])
    
  ---
    
    filter: функция фильтер отбирает элементы списка удовоетворяющие заданному условию
    
    filter 
    object Main22 {
    def isEven(x: int): Boolean = x
    
    reverse возвращает список в обратном порядке
    
    object Main51 {
    
    def main(args: Array[st
    
    foldLeft:
    
    Синтаксис следующий
    
    collection.foldLeft(initialValue)(binaryOperator)

Функция поледовательно пр меняется к элементам списка слева направо накапливая результат
Collection эта коллекция над которой выполняется операция свёртки. initial value  это начальное значение аккумудятора или результата, бинарный оператор который обьеденяет каждый элемент коллекции и аккумулятор, работает с разными видами коллекций. 

пример суммы элементов списка:
	
	object Main22 {
	def main(args: Array[String]): Unit = {
	val myList
…

### zip: функция обьеденяет 2 списка н апримере словаря ключ-значение

	val a = List(1, 2, 3)
	
	
	object Main22 {
	def main(args: Array[String]): Unit = {
	 val a = List(1, 2, 3)
	 val b = List(«one», «two», «three»)
	 val zipped = a
…

zip применяем при  элементы двух списков обьеденяется в пары в результате получается список кортежей дальше применяется фильтрация каждому элементу списка если условие выполняется true мы оставляем эту пару в списке

Можно выводить элементы вот так:

	zipped.foreach {case (a,b) => println…
	// one
	//two
	//three

Примеры

Сумма элементов списка 

	object Main 22 {
		def sumLIst(Ist: List[Int]): Int = {
			if(Ist:isEmpty) 0
			else Ist.head + sumList(Ist.tail
	…
при работе со списками используется рекурсия практически всегда, для этого у нас есть несколько веток для работы со списками первая ветка относится к простейшим случаям, к пустым спискам, к спискам с одним элементом, с головой списка. Последующие ветки относятся к более общему случаю и имеют следующее назначение: если список нее соответствует простейшему случаю, то следует уменьшить его на один элемент и применить рекурсию к укороченному списку и при этом в памяти сохраняется информацию о том что обработка предыдущего вызова функции ещё не закончена. 

Примеры:

Подсчёт кол-ва эл-ов списка

object Main22 {

def sizeList
…

Минимальный элемент списка:
	
	import scala.io.Stdln
	
	object Main28 {
		def minList(Ist: List[Int], minval: Int): Int = {
			if (Ist.isEmpty) minval
			else if (Ist.head < minval) minList(Ist.tail, Ist.head)
			else minList(Ist.tail, minval)  }

Минимальный элемент списка: 

def main(args: Array[String]): Unit = {
	var myList = List.empty[Int]
	
	var input = Stdln.readLine()
	while (input.nonEmpty) {
		val element = input.toInt
		myList = element :: myList
		input = Stdln.readLine() }

	if (myList.isEmpty) {
		println(«The list is empty»)
	} else {
	val minw = minList(myList, myList.head)
	println(minw)  } }}

Отыскание элемента по индексу:
	
	object Main22 {
	def posList(Ist: List[Int], pos: Int): Int = {
	…
	
	
	Строки
	
	Операции со строками 
	
	val s1 = «hello»
	val s2 = «world»
	
	// Concetanation
	val s3 = s1 + «» + s2 // «hello world»
	
	// Length
	val len = s3.length // 11
	
	// Substring
	val sub = s3.substring(0, 5) // «hello»
	
	// Replace
	val replaced = s3.replace(«hello», «hi») // «hi world»
	
	// Split
	val parts = s3.split(«») // hello, world

### String это неизменяемый класс это значит что после создания строки её значение нельзя изменить. Строки мы можем передавать и возвращать как аргумент функции.


## Развитые типы функций. Операторы

Класс содержащий 1 или несколько абстрактных методов должен быть обьявлен как абстрактный. Абстрактные классы также могут иметь не абстрактные методы с реализацией. Абстрактный метод - метод который обьявлен и не имеет реализации в том же классе вместо этого реализация метода откладывается до подкласса, ключевое слово abstract. 

	abstract class Animal {
		def makeSound(): Unit
	}
	class Dog extends Animal {
		def makeSound(): Unit = {
		println(«Woof-fff»)
		}
	}
	class Cat extends Animal {
		def makeSound(): Unit = {
		println(«Mia-uuu»)
		} 
	}
	
	object Main22 {
	
	def main(args: Array[String]: Unit = {
		val myDog = new Dog
		myDog.makeSound()
		val MyCat = newCat
		myCat.makeSound()
	
	
	abstarct class Animal {
		def makeSound1 (): Unit = {
			println(«Po»)
		}
	}
	class Dog extends Animal


Частично применимые ф-ии можно создавать, т.е. ф-ии которые  принимают некоторые, но не все свои аргументы, то есть она применяется к части своих аргументов

	object Main22 {
	
	def add(x: Int, y: Int, z: Int): Int = { // частично применимая ф-я
		x + y + z
	}
	
	def main(args: Array[String]): Unit = {
		val addTwo = add(_: Int, 2, _: Int)
	
		val result2 = addTwo(3, 5) // result is 10
		println(result2)
		}
	}

Частично применимые ф-ии можно создавать при помощи лямбда выражений которые являются анонимными ф-ями

	val multiplyByTwo: Int => int = _ * 2
	val result = multiplyByTwo(5)

Частично применимые ф-ии полезны когда хотим создать ф-ии которые похожи но имеют некоторые различия в своих аргументах. Их используют для создания ф-ий более высокого порядка и для передачи ф-ий в кач-ве аргумента другим функциям. Ленивые вычисления тоже есть в Scala, они определяются ключевым словом lazy val. lazу val - это значение которое оценивается только при первом доступе к нему. Полезно когда есть затратная вычислительная операция которую мы не хотим выполнять пока она не потребуется. 

### Ленивые вычисления

    object Main22 {
    
    def main(args: Array[String]): Unit = {
    	def expensiveOperation(param: Int): Int = {
    		println(«Выполняется дорогостоящая операция для параметра» + param)
    	// Возвращаем результат
    	factorial(param)
    }
    def  factorial(n: Int): Int = {
    if (n <= 1) 1
    else n * factorial(n - 1)
    }

Определяем в примере две переменны result1 и result2 обе из которых ссылаются на expensive operation. В первый раз когда осуществляется вызов expensive operation  когда выполняется эта операция второвй раз когд аввызывается наша дорогостоящая операция она больше не выполняется а из памяти возвращается результат // 42.  Как только лейзи вал оценивается его значение фиксируется и его значение не может быть изменено если нужно выплниьт дорогостоящ операцию несколько раз с разными параметрами нужно использовать функцию вместо отложенного val. 

Когда фиксируеся лейзи вал то его значение нельзя изменить.
Если нужно выыполнить какую-то дорогостоящую операцию несокльок раз с разнными параметрами, то необходимо использовать функцию вмест val.

     object main22 {
      def main(args: Array[String]): Unit = {
       def expenseiveOperarion(param:Int):Int = {
        println("Выполняется дорогостоящая операция для параметра" + param)
        // Возвращаем результат
           factorial(param)
         }
         def factorial(n: Int):Int = {
          if(n <= 1)1
          else n * factorial(n - 1)
        }
        // Функция, которая будет вызывать дорогостоящую операцию с разными параметрами
        def perfomOperations():Unit = {
         val params = List[5, 7, 10]

         params.foreach { param => 
          val result = expensiveOperation(param)
          println("Результат для параметра" + param + ":" + result)
          }
         }
         perfomOperations()
        }
       }

## Операторы

операторы...
побитвые ...
& (bitwise AND)
| (bitwise OR)
^ (bitwise XOR)
~ bitwise complement)
<< (left shift)
>> (right shift)

Операторы пользователя
   
    object main22 {
    def main(args:Array[String]: Unit = {
     case class MyClass(x:Int) {
      def @@(y: Int):Int = x + y
     }
    
     val a = MyClass(10)
     val b = a@@5 // equivalent to a.@@5
    
     println(b) // outputs 15
     }
    }

Пользовательские операторы можно определять с помощью символических имён, определяются точно также через def. 

### Замыкания 
Замыкание - это функция, которая захватывает среду в которой она определена включая любые переменные и функции находящяеся в области видимости во время её определения.
В Scala можно определять замыкания с помощью анонимных функций, например:

    val x = 10
    val addX = (y:Int) => x + y
    
    println(addX(5)) // outputs 15

Здесь addX которое захватывает значение x из внешней области и возвращает сумму этого значения и аргумента y. Символ => для анонимных функций используется, не только для лямбда выражений.

    object main22 {
    
    def add(x:Int, y:Int) = x + y 
    
    def main(args:Array[String]):Unit = {
     val add5 = (x:Int) => add(x, 5)
     println(add5(10)) // outputs 15
     }
    }

В этом примере add5 это замыкание которое захватывает функцию и возвращает результат, возвращает функцию которая добавляет 10 к 5, сложенеи x и y (add5 можно и в мейен и не в мейн).


### Функции для рабоыты со строками 

#### Класс StringBuilder и класс String представляют разные подходы к работе с текстовыми данными в Java. 
Отличия между ними: 
1. объекты класса String являются неизменяемыми. Такие операции надо строкой как компетинация, замена символа создаёт новый объект строки, в то время как объекты класса StringBuilder являются изменяемыми, их можно изменять не создавая новые объекты, что позволяет сэкономить памить.
2. Отличаются своими методами, StringBuilder помимо базовых (ужаление, добавление) содержит свои методы для вставки, удаления, добавлени.

#### Например: (методы StringBuilder)
1. append(x:Any):StringBuilder добавляет строковое представление заданного значения x в конец строки.
2. insert(index: Int, x:Any):StringBuilder вставяляет строковое представление заданного значения x по указанному индексу, возвращает уже изменённое значение StringBuilder.
3. delete(start: Int, end:Int):StringBuilder удаляет значения в диапазоне от start до end (start включительно, end не включительно), возвращает уже изменённое значение.
4. replace(start: Int, end: Int, str:String):StringBuilder заменяет символы в диапазоне от start до end заданной строки (start включительно, end не включительно), возвращает уже изменённое значение.
5. reverse

		object main22{
		def main(args:Array[String]):Unit = {
		 val sb = new StringBuilder()
		 sb.append("hello")
		 sb.append("")
		 sb.append("world")
		 sb.appendAll(Seq('!', '!', '!'))
		 sb.insert(5, "there")
		 sb.delete(0, 6)
		 sb.replace(5, 11, "Scala")
		 val reversed = sb.toString.reverse
		
		 println(reversed) = sb.toString.reverse !!!alacSereht

 Класс String предоставляет следующий набор функций для работы со строками:
 ##### replaceAll
 Используется для замен ывсех вхождений в  строку другой строкой имеет 2 аргумента заменяемое и строка замены
 Пример:

    val str = "Hello Wolrd"
    val newStr = str.replaceAll("o", "a")
    println(newStr) // "Hella, Warld!"

##### split 
Используется строки на массив подстрок на основе разделителя. Аргумент у функциии 1 - раделитель
Пример:

    val str = "Hello Wolrd"
    val arr = str.split(",")
    println(arr.mkString(" ") // "apple banan orange"

##### startsWith, enddsWith
Функция используется для проверки того начинается или закнчивается строка заданной полстрокой. В качестве аргумента заменяемая строка
Пример:

    val str = "apple,banana,orange"
    println(str.startsWith("Hello")) // true
    println(str.endsWith("!") // true

##### subString
 Выделяет подстроку из строки (нумерация идё с 0)
 Пример:

    val str = "Hello Wolrd"
    val subStr = str.substring(7, 12)
    println(sub.Str)

##### toLowerCase, toUpperCase
Изменяет регистры из верхнего к нижнему и наоборот.
 Пример:

    val str = "Hello Wolrd" 
    println(str.toLowerCase) // "hello world"
    println(str.toUpperCase) // "HELLO WORLD"

##### trim
Отсекает концевые пробелы из конца строки и из начала строки
 Пример:

    val str = " Hello Wolrd "
    println(str.trim) // "Hello World"

##### indexOf, lastIndexOf
Получает 1-й и последний индекс подстроки в строке (то есть номер позиции с которой начинается подстрока).
 Пример:

    val str = "Hello Wolrd"
    println(str.indexOf("o")) // 4
    println(str.lastIndexOf("o")) // 8

##### toCharArray
Преобразует строку в массив символов.
Пример:

	 val str = "Hello Wolrd"
	 val arr = str.toCharArray
	 println(arr.mkstring("")) // [Hello World]

##### charAt
Определяет символ стоящий на указанной позиции (нумерация с нуля, пробел учитывается).
Пример:

	val str = "Hello, World!"
	println(str.charAt(7)) // 'W'

##### stripMargin
Используется для удаления отступов (марген) из многострочных строк. При исползовании этой функции каждая строка в многострочной строке должна начинаться с символа вертекальной черты, отступы в этом случае будут удалены, вертикальная черта даёт выравнивание по левому краю.
Пример: 

	val str = 
	"""
	| Hello
	| World

##### toInt
Используется для пареобразования строки в целое число. При преобразовании может возникнуть ошибка если строка например не 123 а abc тогда будет ошибка которую необходимо перехватить
Пример:

	object Main22{
	def main(args:Array[String]):Unit = {
	val str = "123"
	val num = str.toInt
	println(num) // 123

##### toDouble
Преобразует строку в число с плавающей точкой.
Пример:

	object Main22 {
	def main(args:Array[String]):Unit = {
	val str = "3.14"
	val num = str.toDouble
	println(num) // 3.14
	val str2 = "abc"
	try {
	val num = str2.toDouble
	println(num)
	} catch {
	case e = NumberFormatException => println("Envalid Number Format") }}}

##### getBytes()
Пркобразует строку в массив байт.
Пример: 

	val str = "Hello World"
	val bytes = str.getBytes()
	println(bytes.mkString("")) // 72 101 108 108 111 44 32 87 111 114 108 100 33

И наоборот из массива байтов в строку. 
Пример: 

	object Main22 {
	def main(args:Array[String]):Unit = {
	val bytes = Array[Byte](72, 101, 108, 108, 111, 44, 32, 87, 111, 114, 108, 100, 33) // bytes corresponding to hello
	val str = new String(bytes, "UTF-8")
	println(str)
	}
	}

