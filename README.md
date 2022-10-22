# Python-Data-Processing
Changing some sql queries to python equivalences.

Queries may be overcomplicated, so my task is also to simplify them.

Data is available somewhere here - https://travel.stackexchange.com/

Can't put it here because of the size.

Written in some version of Anaconda.

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

# -- 3 --
