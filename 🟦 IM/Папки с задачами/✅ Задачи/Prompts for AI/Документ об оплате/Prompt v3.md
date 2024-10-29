#AI 
# Data output format
{
	"bank_name": "You can get the data to fill in this field from the data in the attached file. The field is responsible for the bank name. The following keywords will help you: "Банк получателя", "банк получателя", "Банк_получателя"
This field should be present anyway, whether you find it in the picture or not. If you do not find data to fill this field, or you are not sure if the target location is correct, leave this field empty. Create it, but leave it blank.",
	"supplier": "You can get the data to fill in this field from the data in the attached file. The field is responsible for the supplier. The following keywords will help you: "Поставщик", "поставщик".
This field should be present anyway, whether you find it in the picture or not. If you do not find data to fill this field, or you are not sure if the target location is correct, leave this field empty. Create it, but leave it blank.", 
	"supplier_inn": "You can get the data to fill in this field from the data in the attached file. The field is responsible for the supplier inn. It is usually located near to the supplier information. The following keywords will help you: "ИНН", "инн", "Инн"
Also remember that you need to output the value as a numeric value.
This field should be present anyway, whether you find it in the picture or not. If you do not find data to fill this field, or you are not sure if the target location is correct, leave this field empty. Create it, but leave it blank.",
	"supplier_kpp": "You can get the data to fill in this field from the data in the attached file. The field is responsible for the supplier kpp. The following keywords will help you: "КПП", "Кпп", "кпп"
Also remember that you need to output the value as a numeric value.
This field can be empty If the field "supplier" has words: "ИП", "ип", "Индивидуальный предприниматель".
This field should be present anyway, whether you find it in the picture or not. If you do not find data to fill this field, or you are not sure if the target location is correct, leave this field empty. Create it, but leave it blank.",
	"customer": "In order to fill this field you need to get the data that is responsible for the customer. The following keywords can help you to understand that this is the customer: "Покупатель", "покупатель", "Заказчик".
This field should be present anyway, whether you find it in the picture or not. If you do not find data to fill this field, or you are not sure if the target location is correct, leave this field empty. Create it, but leave it blank.",
	"customer_inn": "In order to fill this field you need to get the data that is responsible for the customer inn. It is usually located near to the customer information. The following keywords can help you to understand that this is the customer inn: "ИНН", "Инн", "инн".
This field should be present anyway, whether you find it in the picture or not. If you do not find data to fill this field, or you are not sure if the target location is correct, leave this field empty. Create it, but leave it blank.",
	"invoice_number": "This is the invoice number for the payment. So it is something that defines the difference between documents, between invoices for payment. Usually, this number is located in the same place where the word "Invoice", "Счёт" or "Bill", "Счет" is written in large print. It starts with a number and everything before the “from” is a number. 
It can look something like this: "*№124-МС/5*".
This field should be present anyway, whether you find it in the picture or not. If you do not find data to fill this field, or you are not sure if the target location is correct, leave this field empty. Create it, but leave it blank.",
	"invoice_date": "This is the date on which the receipt of the invoice for payment was recorded. Usually, it appears in the same place as the invoice number, words: "Счет", "счет", "№". Write data uses format - YYYY-MM-DD.
This field should be present anyway, whether you find it in the picture or not. If you do not find data to fill this field, or you are not sure if the target location is correct, leave this field empty. Create it, but leave it blank.",
	"agreement": "This field is used to indicate the basis of the contract. That is, thanks to which contract this invoice was issued. Usually, it looks like this: "*Договор 34R56678-1 от 30.08.2019 года*.
This field should be present anyway, whether you find it in the picture or not. If you do not find data to fill this field, or you are not sure if the target location is correct, leave this field empty. Create it, but leave it blank.",
	"products": [
	//You can get this field from the table that is in the attached file. You need to get from the table the names of the goods or services that have been provided, the quantity, the units of measurement of the quantity, the price of the service or good per unit, and the amount for all services and goods for all quantities.
In order to determine that you need to get the data from here, note that the data must be in the table. 
The output of the data should be folded into a dictionary “key”: “value” . The dictionary should look like this and have the following fields//
	    {
	        "product_description": "This field should be present anyway, whether you find it in the picture or not. If you do not find data to fill this field, or you are not sure if the target location is correct, leave this field empty. Create it, but leave it blank",
	        "quantity": "This field should be present anyway, whether you find it in the picture or not. If you do not find data to fill this field, or you are not sure if the target location is correct, leave this field empty. Create it, but leave it blank",
	        "units": "This field should be present anyway, whether you find it in the picture or not. If you do not find data to fill this field, or you are not sure if the target location is correct, leave this field empty. Create it, but leave it blank",
	        "price": "//remove all spaces// - This field should be present anyway, whether you find it in the picture or not. If you do not find data to fill this field, or you are not sure if the target location is correct, leave this field empty. Create it, but leave it blank",
	        "amount": "//remove all spaces// - This field should be present anyway, whether you find it in the picture or not. If you do not find data to fill this field, or you are not sure if the target location is correct, leave this field empty. Create it, but leave it blank". Do not change the key names, do not change the number of keys or anything else. If there is no value - still create this key, but leave its value empty."
	        }],
	"total_amount": "In order to fill this field you need to get the data that is responsible for the total amount. The following keywords can help you to understand that this is the total amount: "Итого", "Итог", "включая НДС", "". 
	Also remember that you need to output the value as a numeric value. remove all spaces.
	This field should be present anyway, whether you find it in the picture or not. If you do not find data to fill this field, or you are not sure if the target location is correct, leave this field empty. Create it, but leave it blank",
	"vat": "You can get the data to fill in this field from the data in the attached file, from everything related to value added tax. The following keywords will help you: "НДС", "ндс", "налог", "налог на добавочную стоимость". The "%" symbol can also indirectly indicate that the data can be used to fill in the current field.
	This field should be present anyway, whether you find it in the picture or not. If you do not find data to fill this field, or you are not sure if the target location is correct, leave this field empty. Create it, but leave it blank"
}
<|end_of_text|>


# Instructions
You need to create JSON with the fields you got from the “Data output format” item. Follow these fields strictly. do not add, remove, or modify the keys you got from the “Data Output Format” item. 
The JSON view must have these fields:
 - "bank_name";
 - "supplier";
 - "supplier_inn";
 - "supplier_kpp";
 - "customer";
 - "customer_inn";
 - "invoice_number";
 - "invoice_date";
 - "agreement";
 - "products";
 - "total_amount";
 - "vat";

 Analyze the attached image and pull the data I will point out to you below.
 
---

Remember that you only need to return JSON with the specified fields. Return the result according to the “Data output format” clauses, rely on the “Instructions” clause.
do not add anything new to the json or remove anything else. It should remain static.

Your picture for analysis is in the attachment:

# Examples
{
	"bank_name": "МОСКОВСКИЙ ИНДУСТРИАЛЬНЫЙ БАНК",
	"supplier": "ООО \"Рассвет\"", 
	"supplier_inn": "6088691018",
	"supplier_kpp": "175744421",
	"customer": "ИП Сергеев Петр Иванович",
	"customer_inn": "606680195697",
	"invoice_number": "№124-МС/5",
	"invoice_date": "27.05.2020 г.",
	"agreement": "Договор 34R56678-1 от 30.08.2019 года",
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
<|end_of_text|>


---
{
	"bank_name": "ПАО «Сбербанк»",
	"supplier": "ИП Иванов Леонид Викторович",
	"supplier_inn": 616512345678,
	"supplier_kpp": null,
	"customer": "Общество с ограниченной ответственностью «Рога и Копыта»",
	"customer_inn": 7735123456,
	"invoice_number": "1",
	"invoice_date": "2018-01-15",
	"agreement": "№ 123456",
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
<|end_of_text|>

---
{
	"bank_name": "ПАО СБЕРБАНК г. Москва",
	"supplier": "ООО \"Торговый дом \"Комплексный\"", 
	"supplier_inn": 7799434926,
	"supplier_kpp": 779901001,
	"customer": "ООО \"Аквилон-Трейд\"",
	"customer_inn": 7799325885,
	"invoice_number": "1",
	"invoice_date": "2020-05-19",
	"agreement": "С покупателем - руб.",
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
<|end_of_text|>

---
{
	"bank_name": "Сбербанк России ПАО г. Москва",
	"supplier": "ООО «Бетельгейзе Альфа Центавра-3»", 
	"supplier_inn": 7702000000,
	"supplier_kpp": 770201001,
	"customer": "ООО «Бетельгейзе Альфа Центавра-3»",
	"customer_inn": 7702000000,
	"invoice_number": "151",
	"invoice_date": "2021-04-14",
	"agreement": "№ 5689 от\n14.04.2021 г.",
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
<|end_of_text|>

---
{
	"bank_name": "ВТБ 24 (ПАО)",
	"supplier": "ООО \"Омега\"", 
	"supplier_inn": 7756456123,
	"supplier_kpp": 775567123,
	"customer": "ООО \"Жизнь удалась\"",
	"customer_inn": 7787908856,
	"invoice_number": "321",
	"invoice_date": "2017-03-16",
	"agreement": null,
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
<|end_of_text|>

---
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
<|end_of_text|>

---
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
<|end_of_text|>

---
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
<|end_of_text|>

---
{  
  "bank_name": "Санкт-Петербургский РФ ОАО «Россельхозбанк»",  
  "supplier": "ООО \"СП Тандем\"",  
  "supplier_inn": 4711012441,  
  "supplier_kpp": 471101001,  
  "customer": null,  
  "customer_inn": null,  
  "invoice_number": "17699",  
  "invoice_date": "2022-03-04",  
  "agreement": null,  
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
<|end_of_text|>

---

Anyway your input must be same with data output format. Check it and compare with it before you will return the answer!

---
# Your mail to analyze
Return the answer as in the data output example, using and relying on the instructions, and using examples. Your picture for researching in attached files.

# Your answer
Answer: