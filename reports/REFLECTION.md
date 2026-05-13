# REFLECTION — Бие даалт 14

## 1. Хамгийн үнэ цэнэтэй assertion
Schema validation assertion хамгийн үнэ цэнэтэй санагдсан. Учир нь зөвхөн status code шалгахаас гадна response-ийн бүтэц, өгөгдлийн төрөл зөв эсэхийг баталгаажуулдаг. Жишээ нь `email` field байгаа эсэх, түүний утга `@` тэмдэгт агуулсан эсэхийг шалгах нь API-ийн contract зөв мөрдөгдөж байгааг батална.

## 2. Negative test
`User not found` request-д `GET /users/999999` явуулж 404 status ирэхийг шалгасан. Энэ тест нь байхгүй resource-ийг хүсэхэд API зөв алдааны код буцааж байгааг шалгадаг. Хэрэв 404 биш 200 буцаавал API-ийн error handling буруу байна гэсэн үг.

## 3. Postman дотор pass, Newman-д fail
Тийм тохиолдол гарсан. `baseUrl` environment variable-ийн утга export хийхэд хоосон болсон учир Newman-д `Invalid URI "http:///users"` алдаа гарсан. `env.dev.json` файлд гараар утгыг оруулж засав.

## 4. Token болон secret зохицуулалт
JSONPlaceholder auth шаардахгүй учир token байхгүй. Гэхдээ environment variable-ийн соёлыг дагаж `baseUrl`-ийг `env.dev.json`-д хадгалсан. Token шаардсан API бол `env.dev.json`-д `REPLACE_THIS` placeholder бичиж, README-д тайлбарлах нь зөв арга.

## 5. Collection-ийн эмзэг газар
`{{baseUrl}}` variable хамгийн эмзэг газар. API-ийн base URL өөрчлөгдвөл бүх request эвдэрнэ. Үүнийг бууруулахын тулд environment variable ашиглах, collection-level variable тохируулах нь чухал. Мөн response-ийн schema өөрчлөгдвөл schema validation тестүүд бүгд fail болно.