# database

Домашнее задание к занятию «2.6 База данных и хранение данных»

1. запрос(ы) для вставки данных минимум о двух книгах в коллекцию books

db.books.insertMany([
    { title: 'Война и мир', description: 'Роман великого русского писателя Льва Толстого «Война и мир»', authors: 'Л.Н. Толстой' }, 
    { title: 'Метро 2033', description: 'постапокалиптический роман Дмитрия Глуховского, описывающий жизнь людей в московском метро после ядерной войны на Земле', authors: 'Д. Глуховский' }, 
    { title: 'Пикник на обочине', description: 'увлекательная история сталкеров - отчаянно смелых людей', authors: 'А. Стругацкий, Б. Стругацкий' }
])

Операция возвращает

{
    "acknowledged" : true,
    "insertedIds" : [
        ObjectId("62bd818f8cd3ad11e69eb474"),
        ObjectId("62bd818f8cd3ad11e69eb475"),
        ObjectId("62bd818f8cd3ad11e69eb476")
    ]
}

2. запрос для поиска полей документов коллекции books по полю title

db.books.find(
    { title: 'Пикник на обочине' }
)

Операция возвращает

{ "_id" : ObjectId("62bd818f8cd3ad11e69eb476"), "title" : "Пикник на обочине", "description" : "увлекательная история сталкеров - отчаянно смелых людей", "authors" : "А. Стругацкий, Б. Стругацкий" }

3. запрос для редактирования полей: description и authors коллекции books по _id записи

 db.books.updateOne( 
    { '_id': ObjectId('62bd818f8cd3ad11e69eb476') }, 
    { $set: { description: 'Жесткая, бесконечно увлекательная и в то же время бесконечно философская книга.', authors: 'Братья Стругацкие' }}
)

Операция возвращает

{ "acknowledged" : true, "matchedCount" : 1, "modifiedCount" : 1 }
