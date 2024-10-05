# Data output format

{
	"bank_name": "The name of the bank that appears on the document. Key words, after which the searched value is usually located: Bank, PJSC, bank, Банк, ПАО, банк. For example: МОСКОВыСКИЙ ИНВЕСТИЦИОННЫЙ БАНК, Сбербанк, ВТБ, Т-банк",
	"supplier": "The name of the supplier, which can be found after the keyword - Поставщик, поставщики. For example - ИП Соловьев Максим Андреевич, ООО Рога и Копыта, Magnit, Blooming Dales", 
	"supplier_inn": "Individual Vendor Number. It is usually located next to and close to the name of the supplier. It may be 10 or 12 numbers. The key words to understand are: ИНН, инн, номер ИНН. For example: 781633333333, 7816333333.",
	"supplier_kpp": "A number that can be found next to the name of the supplier. It consists of 9 digits. The keywords to identify the required field are: КПП, кпп, номер КПП. For example: 123456789, 111122555",
	"customer": "Client Name. This field is usually located near the supplier field. The keywords to locate the required field are - Клиент, заказчик, Заказчик, клиент. For example: ООО Северный ветер, ИП Петров Игорь Павлович, ПАО ПМК",
	"customer_inn": "A field that contains a customized number for the customer. It can contain 10 or 12 digits. Keywords to locate the right field are: ИНН, ИНН клиента, инн. For example: 1234567891, 121212356547",
	"invoice_number": "Invoice number for payment. This is usually the largest text on the submission. The key words to determine the correct number are: Счет, СЧЕТ, документ, номер документа, № документа, № счета, оплата, номер. Take everything that goes from symbol '№' to the word 'от'. For example: №124-МС/5.",
	"invoice_date": "The date of the invoice. This is usually found where the invoice number is, right on the same line. The key words that will help you decide which line to use are: Счет, номер счета, документ об оплате. The part of the string you need to get the data from is from the words: с, от, дата, Дата. For example: от 20.12.2022, с 16.10.2012. Return date by format YYYY-MM-DD",
	"products": [
	    {
	        "product_description": "A description of the product or service for which payment is being made. Usually, the place where the required data is located is a table. Look at the table and extract the name of the service or product from it. The name of the column in the table that contains the information you need has the words - Навзание товара или услуги, наименование товара или услуги. For examlpe: 'Размещение рекламно-информационных материалов', 'USB-накопители Toshiba'",
	        "quantity": "A designation of the quantity of goods or services. Located on the same row of the table as the name. A column in the table that will help you understand that this is the field you are looking for that contains words: Количесто, Кол-во, количество, кол-во",
	        "units": "Unit of measure quantity of the product. Located on the same table row as the name. A column in the table that will help you understand that this is the field you are looking for that contains words: единицы, Ед. Единица",
	        "price": "The price per unit of a good or service. Located on the same table row as the name. A column in the table that will help you understand that this is the field you are looking for that contains words: Цена, цена, ц.",
	        "amount": "The sum for product or service. Located on the same table row as the name. A column in the table that will help you understand that this is the field you are looking for that contains words: Сумма, общая сумма, итог"
		}
	],
	"total_amount": "Amount for all items in the table. Usually, this field is located at the bottom of the attached file. The keywords to find the values in this field, are: Итог, Итого, В итоге. Всего, всего. The currency designation does not need to be picked up. For example: 120 000.",
	"vat": "The amount of value-added tax. It is usually found at the bottom of the attached document, next to the 'total_amount' field. Usually it is below it. The keywords to find the value in this field are: НДС, ндс, налог на добавочную стоимость, налог, %. For example: 20000, 20 000"
}

# Answer instructions
You need to create JSON with the fields you got from the “Data output format” item. Follow these fields strictly. Do not add, remove, or modify the keys you got from the “Data Output Format” item. 
The JSON view must have these fields:
 - "bank_name"
 - "supplier"
 - "supplier_inn"
 - "supplier_kpp"
 - "customer"
 - "customer_inn"
 - "invoice_number"
 - "invoice_date"
 - "products"
 - "total_amount"
 - "vat"

 Analyze the attached image and pull the data I will point out to you below.
- Your output should match the output in the data output format clause above 100%. 
- Every key in the final performance is a must-have. None of the keys must be lost, changed, deleted, or added.
- The “products” field should be a nested list of dictionaries. In this case, it should contain as many items as the total number of products or services you found in the table. One for each field.
---

Remember that you only need to return JSON with the specified fields. Return the result according to the “Data output format” clauses, rely on the “Instructions” clause.
do not add anything new to the json or remove anything else. It should remain static.

# Examples

Answer:

{
	"bank_name": "МОСКОВСКИЙ ИНДУСТРИАЛЬНЫЙ БАНК",
	"supplier": "ООО Рассвет", 
	"supplier_inn": "6088691018",
	"supplier_kpp": "175744421",
	"customer": "ИП Сергеев Петр Иванович",
	"customer_inn": "606680195697",
	"invoice_number": "№124-МС/5",
	"invoice_date": "27.05.2020 г.",
	"products": [
	    {
	        "product_description": "Услуги за ремонт оборудования",
	        "quantity": "1",
	        "units": "шт",
	        "price": "150 000,55",
	        "amount": "150 000,55"
	        },
	    {
	        "product_description": "Техническое обслуживание ООПТ",
	        "quantity": "1",
	        "units": "шт",
	        "price": "250 321,55",
	        "amount": "250 321,55"
	    }],
	"total_amount": "400 322,10",
	"vat": "66 720,35"
}

---
Answer:

{
	"bank_name": "ПАО «Сбербанк»",
	"supplier": "ИП Иванов Леонид Викторович",
	"supplier_inn": 616512345678,
	"supplier_kpp": null,
	"customer": "Общество с ограниченной ответственностью «Рога и Копыта»",
	"customer_inn": 7735123456,
	"invoice_number": "№ 123456",
	"invoice_date": "2018-01-15",
	"products": [
		{
			"product_description": "Размещение рекламно-информационных материалов на\nстраницах сайта http://ipipip.ru/ по договору",
			"quantity": "1",
			"units": "услуга",
			"price": "15000,00",
			"amount": "15000,00"
		}
	],
	"total_amount": "15000,00",
	"vat": null
}

---
Answer:

{
	"bank_name": "ПАО СБЕРБАНК г. Москва",
	"supplier": "ООО \"Торговый дом \"Комплексный\"", 
	"supplier_inn": 7799434926,
	"supplier_kpp": 779901001,
	"customer": "ООО \"Аквилон-Трейд\"",
	"customer_inn": 7799325885,
	"invoice_number": "№ 124432-1",
	"invoice_date": "2020-05-19",
	"products": [
	    {
	        "product_description": "Бензин АИ-92",
	        "quantity": "1000",
	        "units": "л",
	        "price": "37.00",
	        "amount": "37000.00"
	        },
	    {
	        "product_description": "Бензин АИ-95",
	        "quantity": "2000",
	        "units": "л",
	        "price": "40.00",
	        "amount": "80000.00"
		}
	],
	"total_amount": "117000.00",
	"vat": "19500.00"
}

---
Answer:

{
	"bank_name": "Сбербанк России ПАО г. Москва",
	"supplier": "ООО «Бетельгейзе Альфа Центавра-3»", 
	"supplier_inn": 7702000000,
	"supplier_kpp": 770201001,
	"customer": "ООО «Бетельгейзе Альфа Центавра-3»",
	"customer_inn": 7702000000,
	"invoice_number": "№ 5689 ",
	"invoice_date": "2021-04-14",
	"products": [
	    {
	        "product_description": "Услуга по монтажу телефонной сети по\nадресу: Москва, ул. Коровий Вал, дом\n1022, офис 1415 по договору № 5689 от\n14.04.2021 г.",
	        "quantity": "1",
	        "units": "услуга",
	        "price": "22950-00",
	        "amount": "22950-00"
	        }],
	"total_amount": "22950-00",
	"vat": null
}

---
Answer:

{
	"bank_name": "ВТБ 24 (ПАО)",
	"supplier": "ООО \"Омега\"", 
	"supplier_inn": 7756456123,
	"supplier_kpp": 775567123,
	"customer": "ООО \"Жизнь удалась\"",
	"customer_inn": 7787908856,
	"invoice_number": "321",
	"invoice_date": "2017-03-16",
	"products": [
	    {
	        "product_description": "Офисная бумага Принт, А3, 80 г/м",
	        "quantity": "50",
	        "units": "пачка",
	        "price": "350.00",
	        "amount": "17500.00"
	        },
	    {
	        "product_description": "Офисная бумага Принт, А5, 80 г/м",
	        "quantity": "100",
	        "units": "пачка",
	        "price": "120.00",
	        "amount": "12000.00"
		},
	    {
	        "product_description": "Офисная бумага Принт, А4, 80 г/м",
	        "quantity": "80",
	        "units": "пачка",
	        "price": "200.00",
	        "amount": "16000.00"
		}
	],
	"total_amount": "45500.00",
	"vat": "8190.00"
}

---
Answer:

{
	"bank_name": "АО \"Стоун банк\" Г. МОСКВА",
	"supplier": "ООО\"ВАСИЛЕК\"", 
	"supplier_inn": 7722737733,
	"supplier_kpp": 773303001,
	"customer": "ООО ЛАГУНА",
	"customer_inn": 7714037338,
	"invoice_number": "82",
	"invoice_date": "2016-07-01",
	"agreement": "№ 20023316 от 13.02.2016",
	"products": [
	    {
	        "product_description": "Разработка творческих идей для продуктовой линейки",
	        "quantity": "1",
	        "units": "",
	        "price": "2500000.00",
	        "amount": "2500000.00"
	        }
	],
	"total_amount": "2500000.00",
	"vat": "381355.93"
}

---
Answer:

{
  "bank_name": "ОАО АКБ \"АВАНГАРД\" Г. МОСКВА",
  "supplier": "ООО \"Вент Корпорация\"",
  "supplier_inn": 7719812212,
  "supplier_kpp": 771901001,
  "customer": "ООО \"Бест Клайм\"",
  "customer_inn": 7734645735,
  "invoice_number": "ВК-214",
  "invoice_date": "2012-06-21",
  "agreement": null,
  "products": [
    {
      "product_description": "Воздуховод (Пр)- 300x400 - L1250",
      "quantity": "1",
      "units": "шт",
      "price": "89215.33",
      "amount": "89215.33"
    }
  ],
  "total_amount": "89215,33",
  "vat": "13609,12"
}

---
Answer:

{  
  "bank_name": "ПАО Сбербанк Москва",  
  "supplier": "ООО \"Продавец\"",  
  "supplier_inn": 7701001234,  
  "supplier_kpp": 770101001,  
  "customer": "ИП Иванов Иван Иванович",  
  "customer_inn": 770100123456,  
  "invoice_number": "00001",  
  "invoice_date": "2019-11-14",  
  "agreement": null,  
  "products": [  
    {  
      "product_description": "Процессор Intel Core i9-9900KF OEM",  
      "quantity": "1",  
      "units": "шт",  
      "price": "155724.00",  
      "amount": "155724.00"  
    }  
  ],  
  "total_amount": 155724.00,  
  "vat": "25954.00"  
}

---
Answer:

{  
  "bank_name": "Санкт-Петербургский РФ ОАО «Россельхозбанк»",  
  "supplier": "ООО \"СП Тандем\"",  
  "supplier_inn": 4711012441,  
  "supplier_kpp": 471101001,  
  "customer": null,  
  "customer_inn": null,  
  "invoice_number": "17699",  
  "invoice_date": "2022-03-04",  
  "products": [  
    {  
      "product_description": "Силиконовый ремешок для Xiaomi Mi band 3/4\nфиолетовый (11)",  
      "quantity": "1,00",  
      "units": null,  
      "price": "220,00",  
      "amount": "220.00"  
    },  
    {  
      "product_description": "LD01-310-9R99993-Лента-держатель Космический\nгрейпфрут",  
      "quantity": "1,00",  
      "units": null,  
      "price": "300,00",  
      "amount": "300.00"  
    },  
    {  
      "product_description": "Чехол-книга Clear View для iPhone 7/8/SE2\nсеребро",  
      "quantity": "1,00",  
      "units": null,  
      "price": "320,00",  
      "amount": "320,00"  
    },  
    {  
      "product_description": "Накладка силиконовая матовая с перламутровой\nокантовкой для Huawei Y7P/P40 Lite E 2020\nчерная",  
      "quantity": "1,00",  
      "units": null,  
      "price": "190,00",  
      "amount": "190,00"  
    },  
    {  
      "product_description": "Защитное стекло для Samsung Galaxy A01 Core\n0.3 mm, Buckler, прозрачное",  
      "quantity": "1,00",  
      "units": null,  
      "price": "142,50",  
      "amount": "142,50"  
    },  
    {  
      "product_description": "Защитная пленка РЕТ для Huawei Honor 10 Lite/ P\nSmart 2019, Buckler, Черный",  
      "quantity": "4,00",  
      "units": null,  
      "price": "300,00",  
      "amount": "1200,00"  
    },  
    {  
      "product_description": "Лампа св/д Космос в ассорт.",  
      "quantity": "1,00",  
      "units": null,  
      "price": "90,00",  
      "amount": "90,00"  
    },  
    {  
      "product_description": "Силиконовый чехол для iPhone 11 Pro, 1 мм,\nпрозрачный",  
      "quantity": "1,00",  
      "units": null,  
      "price": "150,00",  
      "amount": "150,00"  
    },  
    {  
      "product_description": "Силиконовый чехол \"soft touch\" для Honor 8X\nЖёлтый",  
      "quantity": "1,00",  
      "units": null,  
      "price": "200.00",  
      "amount": "200,00"  
    }  
  ],  
  "total_amount": "2812.50",  
  "vat": null  
}

---

Anyway your input must be same with data output format. Check it and compare with it before you will return the answer!

---
# Your mail to analyze
Return the answer as in the data output example, using and relying on the instructions, and using examples. Your picture for researching in attached files.

# Your answer
Answer:
