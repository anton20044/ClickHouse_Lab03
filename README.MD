Задачи для построения отчетов:
 - Найти жанры для каждого фильма
  Запрос: select m.name, groupArray(g.genre) from movies m inner join genres g on m.id = g.movie_id group by m.name	
 - Запросить все фильмы, у которых нет жанра
  Запрос:  select m.name, g.genre from movies m left join genres g on m.id = g.movie_id where genre = ''
 - Объединить каждую строку из таблицы “Фильмы” с каждой строкой из таблицы “Жанры”
  Запрос: select m.name, g.genre from movies m cross join genres g 
 - Найти жанры для каждого фильма, НЕ используя INNER JOIN
  Запрос: select m.name, g.genre from movies m left join genres g on m.id = g.movie_id
 - Найти всех актеров и актрис, снявшихся в фильме в 2023 году (т.к. нет фильмов за 2023 год, в запрсе использован 2003 год)
  Запрос: select m.name , groupArray(CONCAT(a.first_name,' ', a.last_name) )  from actors a inner join roles r on a.id = r.actor_id 
	inner join movies m on r.movie_id = m.id 
		where m.year = 2003 group by m.name
 - Запросить все фильмы, у которых нет жанра, через ANTI JOIN
  Запрос: select m.name, g.genre from movies m anti join genres g on m.id = g.movie_id
