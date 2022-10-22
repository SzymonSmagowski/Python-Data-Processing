# Python-Data-Processing
Changing some sql queries to python equivalences.

Queries may be overcomplicated, so my task is also to simplify them.

Data is available somewhere here - https://travel.stackexchange.com/

Can't put it here because of the size.

Written in some version of Anaconda.

Also, it was required to connect to some existing database.

# Queries:
# -- 1 --
SELECT Name,

COUNT(*) AS Number,

MIN(Class) AS BestClass

FROM Badges

GROUP BY Name

ORDER BY Number DESC

LIMIT 10

# -- 2 --
SELECT Location, COUNT(*) AS Count

FROM (

SELECT Posts.OwnerUserId, Users.Id, Users.Location

FROM Users

JOIN Posts ON Users.Id = Posts.OwnerUserId

)

WHERE Location NOT IN ('')

GROUP BY Location

ORDER BY Count DESC

LIMIT 10
# -- 3 --
SELECT

Users.AccountId,

Users.DisplayName,

Users.Location,

AVG(PostAuth.AnswersCount) as AverageAnswersCount

FROM

(

SELECT

AnsCount.AnswersCount,

Posts.Id,

Posts.OwnerUserId

FROM (

SELECT Posts.ParentId, COUNT(*) AS AnswersCount

FROM Posts

WHERE Posts.PostTypeId = 2

GROUP BY Posts.ParentId

) AS AnsCount

JOIN Posts ON Posts.Id = AnsCount.ParentId

) AS PostAuth

JOIN Users ON Users.AccountId=PostAuth.OwnerUserId

GROUP BY OwnerUserId

ORDER BY AverageAnswersCount DESC

LIMIT 10
