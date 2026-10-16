# Combine Data Hibernate Layer with Upper Service(Bottom up)

Basic Services

Person:
id, name, email,
homepage,
publications,
topic

Publication:
id, title, authors,
conference,
citation number

Conference:
id, full_name,
short_name,
rank_score,
publications

New(), delete(),
modify(), search()

PersonService

Publication Service

Conference Service

UserManager Service

Database
Connect pool
Component

Database