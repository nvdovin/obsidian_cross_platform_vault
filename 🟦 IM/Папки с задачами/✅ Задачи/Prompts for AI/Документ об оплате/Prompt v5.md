# Answer format:
{
  "document_type": "invoice",
  "fields": {
    "bank_details": {
      "bank_name": "The name of the bank where the recipient's account is held. Look for keywords: 'Банк получателя', 'БИК', 'Банк'. For example, 'Московский Индустриальный Банк'. Usually located at the top of the document",
      "bic": "The Bank Identifier Code (БИК) of the recipient's bank. Look for the keyword 'БИК'. For example, '044252600'. Usually located next to the “Банк” field",
      "account": "The recipient's bank account number. Look for “Сч. №“, “Номер счета“. This number consists of 21 digits. For example, '301018104000000000226'. Usually located next to the “Банк” field",
      "recipient": "The name of the recipient organization. Look for keywords: “Получатель“, “Грузополучитель“. For example, “ООО \"Расчет\". Usually located in the top of document, but under bank name field."
    },
    "invoice_details": {
      "invoice_number": "The invoice number. It is usually located in the center of the document and is bold with a larger letter size. Look for keywords: “Счет №“, “№“. For example, “124-MC/5“. If it possible grab it from “№“ untill word “от“",
      "date": "The date of the invoice. Look near the invoice number. Look for keywords: 'от'. Format YYYY-MM-DD. For example, '2024-04-13'.",
      "supplier": {
        "name": "The name of the supplier. Usually located near with invoice number, under it. Look for keywords: “Поставщик“, “Грузополучатель“. For example, 'ООО \"Расчет\"'.",
        "inn": "The tax identification number (ИНН) of the recipient. Look for keywords: “ИНН“, “инн“, “Номер ИНН“. It consusts 10 or 12 digits. For example, '6088691018'. Usually located near with supplier name.",
        "kpp": "The classification of the taxpayer (КПП) of the recipient. Usually located near suppliers name and inn, and consists 9 digits. Look for keywords: 'КПП'. For example, '175744421'.",	
        "address": "The supplier's address. Look for keywords: 'адрес'. It located near with name of supplier, usually on one row with it. For example, 'г. Москва, Каширское шоссе, 22 к 2, 100252'.",
        "contact": "The contact information for the supplier. Look for keywords: 'телефон'. For example, '+7 (495) 325-15-15'. It also located near with supplier's other information."
      },
      "client": {
        "name": "The name of the client. Usually located uder supplier's informaton. Look for keywords: 'Клиент'. For example, 'ИП Сергеев Петр Иванович'.",
        "inn": "The tax identification number (ИНН) of the client. Located near with the name of client. Look for keywords: 'ИНН'. For example, '606680195697'.",
        "address": "The client's address. Look for keywords: 'адрес'. Located near with the name of client. For example, 'г. Краснодарский край, г. Анапа, ул. Гребенская, 2 к 75'.",
        "contact": "The contact information for the client. Located near with the name of client. Look for keywords: 'телефон'. For example, '+7 (988) 456-25-25'."
      },
      "contract_reference": {
        "contract_number": "The contract number associated with the invoice. Look for keywords: 'Договор'. For example, '34Р56678-1'.",
        "contract_date": "The date of the contract. Look for keywords: 'от'. Format YYYY-MM-DD. For example, '2019-08-30'."
      }
    },
    "invoice_items": [
      {
        "description": "A description of the invoice item. Usually all the names and listing of services or products are in a table. Find such a table. Also remember that to get the name of a product or service you need to find the column “Наименование”, “Товар”, “Услуга”, ”Наименование работ, услуг”. For example, 'Услуга по ремонту оборудования'.",
        "quantity": "The quantity of the invoice item. Look for keywords: 'Кол-во'. For example, '1'.",
        "unit": "The unit of measure for the invoice item. Usually the quantities of services or goods are in a table. Find such a table. Also remember that to get the name of a product or service you need to find a column called “Кол-во”, 'Ед. Измерения'. For example, 'шт.'.",
        "price": "The price per unit of the invoice item. Usually the price for a service or product is in a table. Find such a table. Also remember that to get the name of a product or service you need to find a column called “Цена”. Look also for keywords: 'Цена'. For example, '50000.55'.",
        "total": "The total cost for this invoice item. Usually the full or total price for a service or product is in a table. Find such a table. Also remember that to get the name of a product or service you need to find a column called “Сумма”. Look for keywords: 'Сумма'. For example, '50000.55'."
      }
    ],
    "totals": {
      "subtotal": "The subtotal amount before tax. Usually located at the bottom of the table. It also happens that the required field is located in the table. In any case, look for keywords: 'Итого'. For example, '400322.10'.",
      "tax": {
        "rate": "The VAT rate applied to the invoice. Usually located at the bottom of the document. Use this indicator to indicate the amount of value-added tax. Return the amount of tax in “%”. Look for keywords: 'НДС'. For example, '20'.",
        "amount": "The total VAT amount. Usually located at the bottom of the document. Use this indicator to specify the value added tax amount. Return the value of the tax as a numerical value. For example, '66270.35'."
      },
      "total_due": "The total amount due after tax. Usually located at the very bottom of the document. Use it to indicate the total or summarized value of the price for goods or services. Return the value of the tax in numerical form. Look for keywords: 'Всего к оплате'. For example, '466592.45'."
    }
  }
}<|end_of_text|>

# Answer instructions:
You need to create JSON with the fields you got from the “Answer format” item. Follow these fields strictly. Do not add, remove, or modify the keys you got from the “Answer format” item. 
 Analyze the attached image and pull the data I will point out to you below.
- Your output should match the output in the data output format clause above 100%. 
- Every key in the final performance is a must-have. None of the keys must be lost, changed, deleted, or added.
- Invoice items are often arranged in a table below the main data.
- Return the output value so that it has the same output format as in the answer format clauseю.

# Answer examples:

A:
{
  "document_type": "invoice",
  "fields": {
    "bank_details": {
      "bank_name": "Московский Индустриальный Банк",
      "bic": "044252600",
      "account": "301018104000000000226",
      "recipient": "ООО 'Расчет'",
      "inn": "6088691018",
      "kpp": "175744421"
    },
    "invoice_details": {
      "invoice_number": "124-MC/5",
      "date": "13.04.2024",
      "supplier": {
        "name": "ООО 'Расчет'",
        "address": "г. Москва, Каширское шоссе, 22 к 2, 100252",
        "contact": "+7 (495) 325-15-15"
      },
      "client": {
        "name": "ИП Сергеев Петр Иванович",
        "inn": "606680195697",
        "address": "г. Краснодарский край, г. Анапа, ул. Гребенская, 2 к 75",
        "contact": "+7 (988) 456-25-25"
      },
      "contract_reference": {
        "contract_number": "34Р56678-1",
        "contract_date": "30.08.2019"
      }
    },
    "invoice_items": [
      {
        "description": "Услуга по ремонту оборудования",
        "quantity": 1,
        "unit": "шт.",
        "price": 50000.55,
        "total": 50000.55
      },
      {
        "description": "Техническое обслуживание ООПТ",
        "quantity": 1,
        "unit": "шт.",
        "price": 250321.53,
        "total": 250321.53
      }
    ],
    "totals": {
      "subtotal": 400322.10,
      "tax": {
        "rate": 20,
        "amount": 66270.35
      },
      "total_due": 466592.45
    }
  }
}<|end_of_text|>

A:
{
  "document_type": "invoice",
  "fields": {
    "bank_details": {
      "bank_name": "ПАО «Сбербанк»",
      "bic": "046012345",
      "account": "40802123456789012345",
      "recipient": "ИП Иванов Леонид Викторович"
    },
    "invoice_details": {
      "invoice_number": "1",
      "date": "2018-01-15",
      "supplier": {
        "name": "ИП Иванов Леонид Викторович",
        "inn": "616512345678",
        "kpp": null,
        "address": "344038, Ростовская обл, Ростов-на-Дону г, Ленина пр, дом № 486, кв. 1234",
        "contact": "+7 (908) 123-45-67"
      },
      "client": {
        "name": "Общество с ограниченной ответственностью «Рога и Копыта»",
        "inn": "7735123456",
        "address": "124482, Москва, корп. 528, офис 17",
        "contact": "+7 499 123 45 67"
      },
      "contract_reference": {
        "contract_number": "123456",
        "contract_date": null
      }
    },
    "invoice_items": [
      {
        "description": "Размещение рекламно-информационных материалов на\nстраницах сайта http://ipipip.ru/ по договору № 123456",
        "quantity": 1,
        "unit": "услуга",
        "price": 15000.00,
        "total": 15000.00
      }
    ],
    "totals": {
      "subtotal": "15 000,00",
      "tax": {
        "rate": null,
        "amount": null
      },
      "total_due": "15 000,00"
    }
  }
}<|end_of_text|>

A:
{
  "document_type": "invoice",
  "fields": {
    "bank_details": {
      "bank_name": "ПАО СБЕРБАНК г. Москва",
      "bic": "044525225",
      "account": "40702810399994349242",
      "recipient": "ООО \"Торговый дом \"Комплексный\""
    },
    "invoice_details": {
      "invoice_number": "1",
      "date": "2020-05-19",
      "supplier": {
        "name": "ООО \"Торговый дом \"Комплексный\"",
        "inn": "7799434926",
        "kpp": "779901001",
        "address": "Москва г, Кутузовский пр-кт, дом № 1/7, строение 2",
        "contact": null
      },
      "client": {
        "name": "ООО \"Аквилон-Трейд\"",
        "inn": "7799325885",
        "address": "Крылатские Холмы ул, дом № 1",
        "contact": null
      },
      "contract_reference": {
        "contract_number": null,
        "contract_date": null
      }
    },
    "invoice_items": [
      {
        "description": "Бензин АИ-92",
        "quantity": "1 000",
        "unit": "л",
        "price": "37,00",
        "total": "37 000,00"
      },
      {
        "description": "Бензин АИ-95",
        "quantity": "2 000",
        "unit": "л",
        "price": "40,00",
        "total": "80 000,00"
      }
    ],
    "totals": {
      "subtotal": "117 000,00",
      "tax": {
        "rate": null,
        "amount": "19 500,00"
      },
      "total_due": "117 000,00"
    }
  }
}<|end_of_text|>

A:
{
  "document_type": "invoice",
  "fields": {
    "bank_details": {
      "bank_name": "ВТБ 24 (ПАО) Москва",
      "bic": "044525716",
      "account": "40702810000000000000",
      "recipient": "ООО \"Омега\""
    },
    "invoice_details": {
      "invoice_number": "321",
      "date": "2017-03-16",
      "supplier": {
        "name": "ООО \"Омега\"",
        "inn": "7756456123",
        "kpp": "775567123",
        "address": "127433, г. Москва, Славянский бульвар, д. 11",
        "contact": null
      },
      "client": {
        "name": "ООО \"Жизнь удалась\"",
        "inn": "7787908856",
        "address": "127417, г. Москва, ул. Нижегородская, д. 22",
        "contact": null
      },
      "contract_reference": {
        "contract_number": null,
        "contract_date": null
      }
    },
    "invoice_items": [
      {
        "description": "Офисная бумага Принт, А3, 80 г/м",
        "quantity": "50",
        "unit": "пачка",
        "price": "350.00",
        "total": "17500.00"
      },
      {
        "description": "Офисная бумага Принт, А5, 80 г/м",
        "quantity": "100",
        "unit": "пачка",
        "price": "120.00",
        "total": "12000.00"
      },
      {
        "description": "Офисная бумага Принт, А4, 80 г/м",
        "quantity": "80",
        "unit": "пачка",
        "price": "200.00",
        "total": "16000.00"
      }
    ],
    "totals": {
      "subtotal": "45500.00",
      "tax": {
        "rate": null,
        "amount": "8190.00"
      },
      "total_due": "53690.00"
    }
  }
}<|end_of_text|>

Answer
{
  "document_type": "invoice",
  "fields": {
    "bank_details": {
      "bank_name": "Сбербанк России ПАО г. Москва",
      "bic": "044525225",
      "account": "30101810400000000225",
      "recipient": "ООО «Бетельгейзе Альфа Центавра-3»"
    },
    "invoice_details": {
      "invoice_number": "151",
      "date": "2021-04-14",
      "supplier": {
        "name": "ООО «Бетельгейзе Альфа Центавра-3»",
        "inn": "7702000000",
        "kpp": "770201001",
        "address": "100001, г. Москва, Веселый проспект, дом 13, офис 13",
        "contact": null
      },
      "client": null,
      "contract_reference": {
        "contract_number": "5689",
        "contract_date": "2021-04-14"
      }
    },
    "invoice_items": [
      {
        "description": "Услуга по монтажу телефонной сети по адресу: Москва, ул. Коровий Вал, дом 1022, офис 1415 по договору № 5689 от 14.04.2021 г.",
        "quantity": "1",
        "unit": "услуга",
        "price": "22950.00",
        "total": "22950.00"
      }
    ],
    "totals": {
      "subtotal": "22950.00",
      "tax": {
        "rate": null,
        "amount": null
      },
      "total_due": "22950.00"
    }
  }
}<|end_of_text|>
# Your answer:
Use everything I've written to you, use the sample output and instructions to return me all the data I need as json, in the specified format

A: