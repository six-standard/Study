### Define
- 웹 크롤러 봇이 페이지를 탐색하는 데 제한을 두는 가이드 파일
- 보통 `robots.txt` 파일과 `sitemap.xml` 파일을 동시에 사용하는 편
- `robots.txt`: 허용된 봇의 종류와 페이지, 허용되지 않은 페이지를 정의하는 파일
- `sitemap.xml`: 모든 페이지를 나열한 페이지 목록 파일 **(보통 대규모 페이지에서만 쓰이는 편)** 

### Robots
#### Format
```text
User-agent: *
Disallow: /
Allow: /
```

#### Usage: NextJS 14
- app 폴더 하위에 `robots.ts` 파일을 생성한 후, 아래와 같은 형태로 입력하면 빌드 시 자동으로 적용되게 됨
```typescript
import { MetadataRoute } from 'next';
import { BASE } from './layout';

export default function robots(): MetadataRoute.Robots {
  return {
    rules: {
	  userAgent: '*', // 봇의 종류
	  allow: '/', // 허용된 페이지의 경로 (블랙리스트 방식으로 동작함)
	  disallow: '/private/' // 허용되지 않은 페이지의 경로 (동일하게 블랙리스트 방식)
	},
    sitemap: BASE + '/sitemap.xml', // 사이트맵 파일의 위치
  };
}
```

### Sitemap
#### Format
```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
     <loc>http://www.example.com/</loc>
     <lastmod>2023-01-01</lastmod>
     <changefreq>daily</changefreq>
     <priority>1.0</priority>
  </url>
  <url>
     <loc>http://www.example.com/about.html</loc>
     <lastmod>2023-01-10</lastmod>
     <changefreq>monthly</changefreq>
     <priority>0.8</priority>
  </url>
  <url>
     <loc>http://www.example.com/contact.html</loc>
     <lastmod>2023-01-15</lastmod>
     <changefreq>yearly</changefreq>
     <priority>0.5</priority>
  </url>
  <!-- 추가적인 페이지 URL들을 계속 나열 -->
</urlset>
```
### Usage: NextJS 14
- 이것도 app 폴더 하위에 `sitemap.ts` 파일을 생성한 후, 아래와 같은 형태로 입력하면 빌드 시 자동으로 적용되게 됨
```typescript
import { MetadataRoute } from 'next';
import { BASE } from './layout';

export default function sitemap(): MetadataRoute.Sitemap {
  return [
    // 각각 페이지 URL, 마지막 크롭 날짜, 크롭 빈도
	{ url: BASE, lastModified: new Date(), changeFrequency: 'monthly' },
	{
	  url: BASE + '/main',
	  lastModified: new Date(),
	  changeFrequency: 'monthly',
	},
	{
	  url: BASE + '/leaderboards',
	  lastModified: new Date(),
	  changeFrequency: 'monthly',
	},
	{
	  url: BASE + '/compare',
	  lastModified: new Date(),
	  changeFrequency: 'monthly',
	},
  ];
}
```