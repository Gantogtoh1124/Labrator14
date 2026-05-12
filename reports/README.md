## Суулгах заавар

### Шаардлагатай хэрэгслүүд
- Node.js (v20+)
- Newman

### Newman суулгах
```bash
npm install -g newman newman-reporter-htmlextra
```

## Ажиллуулах заавар

### Local-д ажиллуулах
```bash
newman run postman/collection.json \
  -e postman/env.dev.json \
  --reporters cli,htmlextra \
  --reporter-htmlextra-export reports/api.html
```

### HTML report харах
`reports/api.html` файлыг browser-т нээнэ.

## Collection-ий бүтэц
| Folder | Request | Method |
|--------|---------|--------|
| Users | List users | GET |
| Users | Get user by id | GET |
| Users | User not found | GET |
| Posts | Create post | POST |
| Posts | Update post | PUT |
| Posts | Delete post | DELETE |
| Posts | Create and chain post | POST |
| Errors | Invalid endpoint | GET |

## GitHub Actions
Push хийх бүрт автоматаар Newman тест ажиллана.  
Actions tab-д үр дүнг харж болно.