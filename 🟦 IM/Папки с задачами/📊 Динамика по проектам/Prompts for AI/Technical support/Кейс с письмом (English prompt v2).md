# Instructions

You need to create a task based on the email presented below. Study this email, analyze it, extract its main essence, and fill in the JSON based on the email you have reviewed. Do not create extra fields, i.e., fields that are not in the original JSON structure. Everything enclosed in // is a comment for you and should not be transferred to the final answer. Also, do not wrap your answer in these symbols. Fill in the JSON in **Russian** language. Think in the paradigm of B2B relationships. You are a company providing services. Analyze the attached email below and create a JSON output with the following mandatory keys:

- task_name,
- summary,
- subtasks,
- deadlines,
- notes,
- response,
- response_required,
- task_required.

Fill in the values for each key based on the analysis of the received email.

1. **task_name** - //Identify the main task based on the email content.//,
    
2. **summary** - summary text; //Briefly and succinctly summarize the essence of the letter received for analysis//
       
3. **subtasks**: ["subtask name 1", "subtask name 2"] //Break down the main task into specific actions, using the imperative mood.//
    
4. **deadlines** - //Always set the deadline for 3 days later than today (UTC+3 timezone). Ensure it does not exceed 2024-09-27. Double-check the current date for accuracy.//
    
5. **notes** - //Write what you think should be paid special attention to. Highlight potential risks, opportunities for growth or improvement, and important deadlines or milestones. Keep it concise and relevant. The output should be no more than three sentences. Prioritize the following:
   - Potential risks or threats
   - Opportunities for growth or improvement
   - Important deadlines or milestones//
    
6. **response** - //Analyze the content of the email and give a response to the sender if required or appropriate. Use the business communication style. Replace all line breaks with the \n or \n\n symbol. 
   A response is required if the email is related to technical support, such as troubleshooting, maintenance, repair, technical inquiry, or error resolution. Look for keywords and phrases like "Error", "Issue", "Problem", "Troubleshooting", "Maintenance", "Repair", "Technical question", "Help", "Support", "Assistance", "Bug", "Fault", "Fix", "Resolution"  (and in Russian - "Ошибка", "Проблема", "Проблема", "Устранение неполадок", "Обслуживание", "Ремонт", "Технический вопрос", "Помощь", "Поддержка", "Содействие", "Ошибка", "Неисправность", "Исправление", "Решение") to identify technical support themes. 
   If is it do not require an answer - send "".
   Write on behalf of the company "Infomaximum". Format:
```
   	Greeting
	Body of the letter, stating that we will be happy to take your request into work. Write on behalf of the company "Infomaximum"
	Signature ()
```

7. **response_required** - //Record the flag true or false depending on whether a response to this message is needed. Set to false if the content of the email is of an advertising nature, offers services, suggests connecting, buying, downloading, etc. Use stop words to better identify messages that do not resemble B2B relationships. Stop words include: "Buy", "Download", "Subscribe", "Offer", "Promotion", "Discount", "Sale", "Special offer", "Limited time", "Exclusive", "Free trial", "Sign up", "Join now", "Click here", "Learn more", and in Russian ("Купить", "Скачать", "Подписаться", "Предложение", "Акция", "Скидка", "Распродажа", "Специальное предложение", "Ограниченное время", "Эксклюзив", "Бесплатная пробная версия", "Зарегистрироваться", "Присоединиться сейчас", "Нажмите здесь", "Узнать больше").//

8. **task_required** - //Value true/false. Set to true if the email is related to technical support, such as troubleshooting, maintenance, repair, technical inquiry, or error resolution. Look for keywords and phrases like "Error", "Issue", "Problem", "Troubleshooting", "Maintenance", "Repair", "Technical question", "Help", "Support", "Assistance", "Bug", "Fault", "Fix", "Resolution" and in Russian ("Ошибка", "Проблема", "Проблема", "Устранение неполадок", "Обслуживание", "Ремонт", "Технический вопрос", "Помощь", "Поддержка", "Содействие", "Ошибка", "Неисправность", "Исправление", "Решение") to identify technical support themes. Set to false if the email is an initial inquiry, sales inquiry, general information request, or contains stop words listed in point 7.//

## Keywords and Features of Advertising Emails:
**English**: Buy, Download, Subscribe, Offer, Promotion, Discount, Sale, Special offer, Limited time, Exclusive, Free trial, Sign up, Join now, Click here, Learn more, Best price, Save now, Don't miss out, Act fast, Limited stock, New arrival, Hot deal, Free shipping, Order now, Get started, Bonus, Gift, Win, Prize, Deal of the day, Flash sale, Hurry up, Last chance

**Russian**: Купить, Скачать, Подписаться, Предложение, Акция, Скидка, Распродажа, Специальное предложение, Ограниченное время, Эксклюзивный, Бесплатная пробная версия, Зарегистрироваться, Присоединяйтесь сейчас, Нажмите здесь, Узнать больше, Лучшая цена, Экономьте сейчас, Не пропустите, Действуйте быстро, Ограниченный запас, Новинка, Горячая сделка, Бесплатная доставка, Заказать сейчас, Начать, Бонус, Подарок, Выиграть, Приз, Сделка дня, Молниеносная распродажа, Поторопитесь, Последний шанс

## Features of Advertising Emails:
1. **Promotional Language**:
    - Focuses on promoting products, services, or events.
    - Highlights benefits, discounts, and special offers.
2. **Calls to Action (CTAs)**:    
    - Phrases like "Click here," "Buy now," "Sign up," and "Learn more".
    - Encourages immediate action.
3. **Visual Appeal**:    
    - Uses images, banners, and colorful designs.
    - Includes logos, product images, and promotional graphics.
4. **Limited Time Offers**:    
    - Emphasis on urgency with phrases like "Limited time," "Act fast," and "Don't miss out".
    - Often includes countdowns or deadlines for offers.
5. **Special Deals and Discounts**:    
    - Highlights discounts, sales, and special offers.
    - Uses percentages off, free trials, and exclusive deals.
6. **Personalization**:    
    - Personalized greetings and offers based on the recipient's past behavior or preferences.
    - Uses the recipient's name and tailored recommendations.
7. **Contact Information**:    
    - Includes contact details, social media links, and ways to reach the company.
    - Often provides unsubscribe options to comply with regulations.

## How to Identify Advertising Emails:

- **Look for promotional keywords and phrases** listed above.
- **Check for calls to action** that encourage immediate engagement.
- **Examine the visual elements** for promotional graphics and designs.
- **Identify any urgency or limited-time offers** emphasized in the email.
- **Notice any special deals or discounts** prominently highlighted.
- **Observe the level of personalization** and whether the email is tailored to the recipient.
- **Review the contact information** and any options to unsubscribe.

Please fill in the JSON output based on the analysis of the received email.