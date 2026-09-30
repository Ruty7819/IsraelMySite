# תוכנית ארכיטקטונית - אתר הכנסת הישראלית

מסמך תכנון ארכיטקטוני מפורט לאתר אינטראקטיבי שמנגיש את פעולת הכנסת, הבחירות והמערכת הפוליטית בישראל

## 1. סקירה כללית

### 1.1 מטרה
יצירת אתר Next.js מודרני בעברית שמנגיש מידע על הכנסת והמערכת הפוליטית בישראל לציבור הרחב, תוך שמירה על נייטרליות וביסוס במקורות רשמיים.

### 1.2 סטאק טכנולוגי
- **Framework:** Next.js 16.3.7 (App Router)
- **Frontend:** React 19.2.8
- **Styling:** Tailwind CSS 4
- **Language:** TypeScript
- **Runtime:** Node.js

## 2. מבנה האפליקציה

### 2.1 מבנה תיקיות

```
my-new-project/
├── app/                          # Next.js App Router
│   ├── layout.tsx                # Layout ראשי עם RTL
│   ├── page.tsx                  # דף הבית
│   ├── globals.css               # CSS גלובלי
│   ├── knesset/                   # עמודי הכנסת
│   │   ├── page.tsx              # הכנסת הנוכחית
│   │   └── [knessetNum]/         # כנסת ספציפית
│   │       └── page.tsx
│   ├── members/                   # חברי הכנסת
│   │   ├── page.tsx              # חיפוש ורשימה
│   │   └── [id]/                 # פרופיל חבר כנסת
│   │       └── page.tsx
│   ├── factions/                  # סיעות
│   │   ├── page.tsx              # רשימת סיעות
│   │   └── [id]/                 # פרופיל סיעה
│   │       └── page.tsx
│   ├── committees/                # ועדות
│   │   ├── page.tsx              # רשימת ועדות
│   │   └── [id]/                 # פרופיל ועדה
│   │       └── page.tsx
│   ├── legislation/               # חקיקה
│   │   ├── page.tsx              # חיפוש חקיקה
│   │   └── [id]/                 # פרופיל הצעת חוק
│   │       └── page.tsx
│   ├── elections/                 # בחירות
│   │   └── page.tsx
│   ├── government/                # ממשלה
│   │   └── page.tsx
│   ├── dictionary/                # מילון מושגים
│   │   └── page.tsx
│   ├── history/                   # היסטוריה
│   │   └── page.tsx
│   └── api/                       # API Routes (אם נדרש)
│       └── knesset/
│           └── [...]
├── lib/                           # פונקציות עזר ו-utils
│   ├── api/                       # API clients
│   │   ├── knesset.ts            # פונקציות ל-API של הכנסת
│   │   └── types.ts              # TypeScript types
│   ├── utils/                     # פונקציות עזר
│   │   ├── formatting.ts        # פורמט תאריכים, מספרים
│   │   └── validation.ts        # ולידציה
│   └── constants/                 # קבועים
│       └── data.ts              # נתונים סטטיים
├── components/                    # רכיבי React
│   ├── ui/                        # רכיבי UI בסיסיים
│   │   ├── Button.tsx
│   │   ├── Card.tsx
│   │   ├── SearchInput.tsx
│   │   ├── FilterBar.tsx
│   │   └── Tooltip.tsx
│   ├── layout/                    # רכיבי Layout
│   │   ├── Header.tsx
│   │   ├── Footer.tsx
│   │   ├── Navigation.tsx
│   │   └── Sidebar.tsx
│   ├── knesset/                   # רכיבים ספציפיים לכנסת
│   │   ├── KnessetCard.tsx
│   │   ├── FactionCard.tsx
│   │   ├── CommitteeCard.tsx
│   │   └── MemberCard.tsx
│   ├── data/                      # רכיבי ויזואליזציה
│   │   ├── Chart.tsx
│   │   ├── Timeline.tsx
│   │   └── ProcessDiagram.tsx
│   └── content/                   # רכיבי תוכן
│       ├── TermExplanation.tsx
│       └── SourceBadge.tsx
├── hooks/                         # Custom React hooks
│   ├── useKnessetData.ts
│   ├── useMembers.ts
│   ├── useFactions.ts
│   └── useDebounce.ts
├── types/                         # TypeScript types
│   ├── knesset.ts
│   ├── member.ts
│   ├── faction.ts
│   ├── committee.ts
│   └── legislation.ts
├── public/                        # קבצים סטטיים
│   ├── images/
│   └── fonts/
├── next.config.ts
├── tsconfig.json
├── tailwind.config.ts
└── package.json
```

### 2.2 החלטות ארכיטקטוניות

#### רינדור: Server Components vs Client Components

**Server Components (ברירת מחדל):**
- דפים סטטיים שלא דורשים אינטראקציה
- דפים שמביאים נתונים מ-API ולא משתנים לעיתים קרובות
- דפי פרופיל של חברי כנסת, סיעות, ועדות
- דף הבית עם נתונים דינמיים

**Client Components:**
- רכיבי UI אינטראקטיביים (חיפוש, פילטרים)
- רכיבים עם state מקומי
- רכיבים שמשתמשים ב-browser APIs
- רכיבי ויזואליזציה עם אינטראקציה

#### Data Fetching Strategy

**שימוש ב-Server Components עם fetch:**
- הטעינה הראשונית של נתונים
- דפים שלא משתנים לעיתים קרובות
- SEO חשוב

**שימוש ב-API Routes כ-proxy:**
- כאשר יש בעיות CORS
- כאשר צריך להסתיר API keys
- כאשר צריך לעבד נתונים ב-server

**שימוש ב-Client-side fetching:**
- נתונים שמשתנים לעיתים קרובות
- חיפוש ופילטור דינמי
- עדכונים real-time (אם נדרש)

## 3. Data Layer

### 3.1 מקורות נתונים

**מקור ראשי:** Knesset OData API
- URL: https://knesset.gov.il/Odata/ParliamentInfo.svc
- סטטוס: רשמי
- תדירות עדכון: יומית

**מקור משני:** Open Knesset API
- URL: https://api.oknesset.org
- גישה: חופשית
- תדירות עדכון: יומית

### 3.2 API Client Layer

```typescript
// lib/api/knesset.ts
const KNESSET_API_BASE = 'https://knesset.gov.il/Odata/ParliamentInfo.svc';

export async function fetchCurrentKnesset() {
  const response = await fetch(`${KNESSET_API_BASE}/KNS_Knesset`);
  return response.json();
}

export async function fetchMembers(knessetNum: number) {
  const response = await fetch(
    `${KNESSET_API_BASE}/KNS_Person?$filter=IsCurrent eq true`
  );
  return response.json();
}

export async function fetchFactions(knessetNum: number) {
  const response = await fetch(
    `${KNESSET_API_BASE}/KNS_Faction?$filter=KnessetNum eq ${knessetNum}`
  );
  return response.json();
}

export async function fetchCommittees(knessetNum: number) {
  const response = await fetch(
    `${KNESSET_API_BASE}/KNS_Committee?$filter=KnessetNum eq ${knessetNum}`
  );
  return response.json();
}
```

### 3.3 Caching Strategy

**Server-side caching:**
- שימוש ב-cache של Next.js (ISR)
- revalidate כל 24 שעות לנתונים שלא משתנים לעיתים קרובות
- revalidate כל שעה לנתונים דינמיים

**Client-side caching:**
- שיקול לשימוש ב-SWR או React Query
- caching ב-memory
- stale-while-revalidate

### 3.4 Error Handling

```typescript
// lib/api/utils.ts
export async function fetchWithErrorHandling<T>(
  url: string,
  options?: RequestInit
): Promise<T> {
  try {
    const response = await fetch(url, options);
    
    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    }
    
    return await response.json();
  } catch (error) {
    console.error('Fetch error:', error);
    throw error;
  }
}
```

## 4. State Management

### 4.1 URL State

לפילטרים וחיפוש נשתמש ב-URL state:
- שמירת פילטרים ב-URL query params
- אפשרות לשתף קישורים עם פילטרים
- Back/Forward navigation עובד אוטומטית

```typescript
// URL State example
/members?search=netanyahu&faction=likud&knesset=25
```

### 4.2 Local State

ל-state מקומי נשתמש ב-React useState:
- state של רכיבים בודדים
- state של modal/dialog
- state של tooltips

### 4.3 Global State

אם נדרש global state:
- שימוש ב-Context API
- או שיקול ל-Zustand/Redux

## 5. רכיבי UI

### 5.1 רכיבי Layout

**Header:**
- Logo
- Navigation
- חיפוש גלובלי
- קישור למילון מושגים

**Footer:**
- מקורות
- קישורים
- זכויות

**Navigation:**
- מנו ראשי
- קישורים לעמודים מרכזיים
- Mobile menu

### 5.2 רכיבי UI בסיסיים

**Button:**
- וריאציות: primary, secondary, ghost
- גדלים: sm, md, lg
- disabled state

**Card:**
- container להצגת מידע
- hover effects
- responsive

**SearchInput:**
- input עם icon
- debounce
- clear button

**FilterBar:**
- רשימת פילטרים
- active states
- clear all

**Tooltip:**
- hover tooltip
- click popover
- RTL support

### 5.3 רכיבי תוכן

**TermExplanation:**
- הסבר מושג עם tooltip
- קישור למילון מושגים
- אנימציה עדינה

**SourceBadge:**
- הצגת מקור המידע
- קישור למקור
- תאריך עדכון

### 5.4 רכיבי ויזואליזציה

**Chart:**
- Bar chart להצגת מנדטים
- Pie chart להצגת התפלגות
- Line chart להצגת מגמות

**Timeline:**
- ציר זמן להיסטוריה
- אירועים עם תאריכים
- scroll horizontal

**ProcessDiagram:**
- תרשים תהליך להסברת חקיקה
- steps עם אנימציה
- RTL support

## 6. עיצוב ו-Styling

### 6.1 Tailwind CSS Configuration

```typescript
// tailwind.config.ts
import type { Config } from 'tailwindcss';

const config: Config = {
  content: [
    './pages/**/*.{js,ts,jsx,tsx,mdx}',
    './components/**/*.{js,ts,jsx,tsx,mdx}',
    './app/**/*.{js,ts,jsx,tsx,mdx}',
  ],
  theme: {
    extend: {
      colors: {
        primary: {
          50: '#f0f9ff',
          100: '#e0f2fe',
          200: '#bae6fd',
          300: '#7dd3fc',
          400: '#38bdf8',
          500: '#0ea5e9',
          600: '#0284c7',
          700: '#0369a1',
          800: '#075985',
          900: '#0c4a6e',
        },
      },
      fontFamily: {
        hebrew: ['Heebo', 'sans-serif'],
      },
    },
  },
  plugins: [],
};

export default config;
```

### 6.2 RTL Support

```css
/* globals.css */
@import "tailwindcss";

:root {
  --background: #ffffff;
  --foreground: #171717;
  direction: rtl;
}

@theme inline {
  --color-background: var(--background);
  --color-foreground: var(--foreground);
  --font-hebrew: var(--font-heebo);
}

body {
  background: var(--background);
  color: var(--foreground);
  font-family: var(--font-hebrew);
  direction: rtl;
}
```

### 6.3 פונט עברי

```typescript
// app/layout.tsx
import { Heebo } from 'next/font/google';

const heebo = Heebo({
  subsets: ['hebrew'],
  variable: '--font-heebo',
  display: 'swap',
});
```

## 7. אינטרנציונליזציה

### 7.1 i18next Configuration

```typescript
// lib/i18n.ts
import i18n from 'i18next';
import { initReactI18next } from 'react-i18next';

i18n
  .use(initReactI18next)
  .init({
    resources: {
      he: {
        translation: {
          // Hebrew translations
        },
      },
    },
    lng: 'he',
    fallbackLng: 'he',
  });

export default i18n;
```

### 7.2 שימוש ברכיבים

```typescript
import { useTranslation } from 'react-i18next';

function MyComponent() {
  const { t } = useTranslation();
  return <h1>{t('welcome')}</h1>;
}
```

## 8. Performance Optimization

### 8.1 Code Splitting

- Dynamic imports לרכיבים כבדים
- Lazy loading לעמודים
- Tree shaking אוטומטי

### 8.2 Image Optimization

- שימוש ב-Next.js Image component
- WebP format
- Lazy loading

### 8.3 Font Optimization

- Subset fonts
- Display swap
- Preload critical fonts

### 8.4 Caching

- Static generation לדפים סטטיים
- ISR לדפים דינמיים
- Client-side caching

## 9. Accessibility

### 9.1 ARIA Labels

- הוספת aria-labels לכל האלמנטים האינטראקטיביים
- Semantic HTML
- Keyboard navigation

### 9.2 Color Contrast

- WCAG AA compliance
- Dark mode support
- Color blind friendly

### 9.3 Screen Reader

- תוכן alternativ לתמונות
- Live regions לעדכונים דינמיים
- Skip to content link

## 10. Testing Strategy

### 10.1 Unit Tests

- Jest + React Testing Library
- בדיקת רכיבי UI
- בדיקת hooks
- בדיקת פונקציות עזר

### 10.2 Integration Tests

- Playwright
- בדיקת flows מלאים
- בדיקת navigation
- בדיקת forms

### 10.3 E2E Tests

- Playwright
- בדיקת user flows
- בדיקת cross-browser
- בדיקת mobile

## 11. Deployment

### 11.1 Environment Variables

```env
NEXT_PUBLIC_API_URL=https://knesset.gov.il/Odata/ParliamentInfo.svc
NEXT_PUBLIC_SITE_URL=https://mysite.com
```

### 11.2 Build Process

```bash
npm run build
npm run start
```

### 11.3 Deployment Options

- Vercel (מומלץ ל-Next.js)
- Netlify
- Docker container
- Self-hosted

## 12. Monitoring

### 12.1 Error Tracking

- Sentry ל-error tracking
- Log לשגיאות
- Alerts לשגיאות קריטיות

### 12.2 Performance Monitoring

- Web Vitals
- Lighthouse CI
- Analytics

### 12.3 API Monitoring

- Track API calls
- Monitor response times
- Alert on failures

## 13. Security

### 13.1 API Security

- HTTPS only
- Rate limiting
- Input validation
- Output encoding

### 13.2 Content Security

- CSP headers
- XSS protection
- Sanitization

### 13.3 Data Privacy

- No personal data collection
- Cookie policy
- Privacy policy

## 14. Maintenance

### 14.1 Code Quality

- ESLint
- Prettier
- TypeScript strict mode
- Pre-commit hooks

### 14.2 Documentation

- README
- Code comments
- API documentation
- Component documentation

### 14.3 Updates

- Regular dependency updates
- Security patches
- Feature updates
- Bug fixes

## 15. שלבי יישום

### Phase 1: תשתית (שבוע 1-2)
- [ ] הגדרת מבנה התיקיות
- [ ] הגדרת Tailwind CSS
- [ ] הגדרת פונט עברי
- [ ] הגדרת RTL
- [ ] יצירת רכיבי Layout בסיסיים
- [ ] יצירת רכיבי UI בסיסיים

### Phase 2: Data Layer (שבוע 2-3)
- [ ] חקר API של הכנסת
- [ ] יצירת API client
- [ ] יצירת TypeScript types
- [ ] יצירת פונקציות fetch
- [ ] הוספת error handling
- [ ] הוספת caching

### Phase 3: דף הבית (שבוע 3-4)
- [ ] יצירת דף הבית
- [ ] הצגת נתונים דינמיים
- [ ] הוספת קישורים
- [ ] הוספת ויזואליזציות
- [ ] Testing

### Phase 4: עמודי ראשיים (שבוע 4-6)
- [ ] עמוד הכנסת
- [ ] עמוד חברי הכנסת
- [ ] עמוד סיעות
- [ ] עמוד ועדות
- [ ] Testing

### Phase 5: עמודים נוספים (שבוע 6-8)
- [ ] עמוד חקיקה
- [ ] עמוד בחירות
- [ ] עמוד ממשלה
- [ ] עמוד מילון מושגים
- [ ] עמוד היסטוריה
- [ ] Testing

### Phase 6: שיפורים (שבוע 8-10)
- [ ] הוספת אנימציות
- [ ] שיפור עיצוב
- [ ] אופטימיזציה
- [ ] Accessibility
- [ ] Testing

### Phase 7: Deployment (שבוע 10-11)
- [ ] הגדרת environment
- [ ] Build
- [ ] Deployment
- [ ] Monitoring setup
- [ ] Testing production

### Phase 8: Launch (שבוע 11-12)
- [ ] Final testing
- [ ] Launch
- [ ] Monitoring
- [ ] Bug fixes
