# Условия выборки

__Параметр cond__

Свойство с множественным отношением является массивом. То как множественное отношение реализуется в 
базе данных не влияет на способ получения этого свойства. Обычно возращается весь массив. Но
бывает надобность выполнить кастомный запрос - отфильтровать, отсортировать, ограничить выборку
массива свойств.
```
GET /users?query=email,phone,profile(surname,avatar(url))
GET /users?query=email,phone,profile(surname,avatar(url))&limit=10&filter[name]=вова
```
```
GET /users?fields=items(email,favorites(date,relative|limit=10|filter[name]=fff))
GET /users
?fields=items(email,favorites(date,relative))
&limit[items]=10,
&limit[favorites]=50
&sort[items]=-email
&sort[favorites]=-date
&filter[favorites][date]=>100
```
