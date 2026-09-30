# רשימת משימות - אתר הכנסת הישראלית

רשימת משימות מסודרת לפי סדר עדיפויות הגיוני, ממחקר ועד deployment

## Phase 1: מחקר ותכנון (Priority: גבוה)

### מחקר API
- [ ] 1.1 בדיקת זמינות של Knesset OData API
- [ ] 1.2 בדיקת מבנה הנתונים של KNS_Person
- [ ] 1.3 בדיקת מבנה הנתונים של KNS_Faction
- [ ] 1.4 בדיקת מבנה הנתונים של KNS_Committee
- [ ] 1.5 בדיקת מבנה הנתונים של KNS_Bill
- [ ] 1.6 בדיקת אם יש CORS issues
- [ ] 1.7 בדיקת rate limits
- [ ] 1.8 בדיקת תדירות עדכון
- [ ] 1.9 תיעוד מבנה הנתונים
- [ ] 1.10 החלטה על אסטרטגיית fetching (Server vs Client)

### תכנון טכני
- [ ] 1.11 החלטה סופית על ספריית גרפים (Recharts vs Chart.js)
- [ ] 1.12 החלטה סופית על ספריית אנימציה (Framer Motion)
- [ ] 1.13 החלטה סופית על פונט עברי (Heebo)
- [ ] 1.14 החלטה סופית על data fetching library (SWR vs React Query)
- [ ] 1.15 החלטה סופית על i18n (i18next)

## Phase 2: תשתית (Priority: גבוה)

### הגדרת סביבה
- [ ] 2.1 יצירת מבנה תיקיות מלא (lib, components, hooks, types)
- [ ] 2.2 הגדרת Tailwind CSS (תצורה מלאה)
- [ ] 2.3 הגדרת RTL ב-globals.css
- [ ] 2.4 התקנת פונט Heebo מ-Google Fonts
- [ ] 2.5 הגדרת פונט ב-layout.tsx
- [ ] 2.6 עדכון metadata ב-layout.tsx (כותרת בעברית)
- [ ] 2.7 הגדרת צבעים מותאמים (primary colors)
- [ ] 2.8 הגדרת dark mode support

### TypeScript Types
- [ ] 2.9 יצירת types/knesset.ts
- [ ] 2.10 יצירת types/member.ts
- [ ] 2.11 יצירת types/faction.ts
- [ ] 2.12 יצירת types/committee.ts
- [ ] 2.13 יצירת types/legislation.ts
- [ ] 2.14 יצירת types/index.ts (exports)

## Phase 3: Data Layer (Priority: גבוה)

### API Client
- [ ] 3.1 יצירת lib/api/knesset.ts (base URL)
- [ ] 3.2 יצירת fetchCurrentKnesset()
- [ ] 3.3 יצירת fetchMembers(knessetNum)
- [ ] 3.4 יצירת fetchFactions(knessetNum)
- [ ] 3.5 יצירת fetchCommittees(knessetNum)
- [ ] 3.6 יצירת fetchBills(knessetNum)
- [ ] 3.7 יצירת fetchMemberById(id)
- [ ] 3.8 יצירת fetchFactionById(id)
- [ ] 3.9 יצירת fetchCommitteeById(id)
- [ ] 3.10 יצירת fetchBillById(id)

### Error Handling & Utils
- [ ] 3.11 יצירת lib/api/utils.ts (fetchWithErrorHandling)
- [ ] 3.12 יצירת lib/utils/formatting.ts (תאריכים עבריים)
- [ ] 3.13 יצירת lib/utils/validation.ts
- [ ] 3.14 יצירת lib/constants/data.ts (קבועים)

### Caching
- [ ] 3.15 הגדרת ISR לדפים סטטיים
- [ ] 3.16 הגדרת revalidate times
- [ ] 3.17 שיקול והחלטה על SWR/React Query

## Phase 4: רכיבי UI בסיסיים (Priority: גבוה)

### Layout Components
- [ ] 4.1 יצירת components/layout/Header.tsx
- [ ] 4.2 יצירת components/layout/Footer.tsx
- [ ] 4.3 יצירת components/layout/Navigation.tsx
- [ ] 4.4 יצירת components/layout/Sidebar.tsx (אם נדרש)
- [ ] 4.5 אינטגרציה של Header ב-layout.tsx
- [ ] 4.6 אינטגרציה של Footer ב-layout.tsx
- [ ] 4.7 אינטגרציה של Navigation ב-layout.tsx

### UI Components
- [ ] 4.8 יצירת components/ui/Button.tsx
- [ ] 4.9 יצירת components/ui/Card.tsx
- [ ] 4.10 יצירת components/ui/SearchInput.tsx
- [ ] 4.11 יצירת components/ui/FilterBar.tsx
- [ ] 4.12 יצירת components/ui/Tooltip.tsx
- [ ] 4.13 יצירת components/ui/Modal.tsx (אם נדרש)
- [ ] 4.14 יצירת components/ui/LoadingSpinner.tsx

### Content Components
- [ ] 4.15 יצירת components/content/TermExplanation.tsx
- [ ] 4.16 יצירת components/content/SourceBadge.tsx
- [ ] 4.17 יצירת components/content/ErrorMessage.tsx

### Custom Hooks
- [ ] 4.18 יצירת hooks/useDebounce.ts
- [ ] 4.19 יצירת hooks/useKnessetData.ts
- [ ] 4.20 יצירת hooks/useMembers.ts
- [ ] 4.21 יצירת hooks/useFactions.ts
- [ ] 4.22 יצירת hooks/useCommittees.ts

## Phase 5: דף הבית (Priority: גבוה)

### דף הבית
- [ ] 5.1 עדכון app/page.tsx (הסרת תוכן default)
- [ ] 5.2 יצירת Hero section עם הסבר קצר על הכנסת
- [ ] 5.3 הצגת נתונים דינמיים (מספר כנסת, סיעות, ועדות)
- [ ] 5.4 הוספת קישורים לעמודים מרכזיים
- [ ] 5.5 הוספת כרטיסים למידע מהיר
- [ ] 5.6 הוספת גרף מנדטים (אם זמין)
- [ ] 5.7 RTL testing
- [ ] 5.8 Responsive testing

## Phase 6: עמוד הכנסת (Priority: גבוה)

### עמוד הכנסת
- [ ] 6.1 יצירת app/knesset/page.tsx
- [ ] 6.2 הצגת מספר הכנסת ותאריכים
- [ ] 6.3 הצגת סיעות עם מנדטים
- [ ] 6.4 הצגת ועדות
- [ ] 6.5 הוספת מידע פרלמנטרי
- [ ] 6.6 יצירת components/knesset/KnessetCard.tsx
- [ ] 6.7 יצירת app/knesset/[knessetNum]/page.tsx
- [ ] 6.8 מעבר בין כנסות
- [ ] 6.9 הצגת היסטוריה של הכנסת

## Phase 7: חברי הכנסת (Priority: גבוה)

### עמוד חברי הכנסת
- [ ] 7.1 יצירת app/members/page.tsx
- [ ] 7.2 יצירת SearchInput עם debounce
- [ ] 7.3 יצירת FilterBar (סיעה, כנסת, ועדה, תפקיד)
- [ ] 7.4 יצירת components/knesset/MemberCard.tsx
- [ ] 7.5 הצגת רשימת חברי כנסת
- [ ] 7.6 URL state לפילטרים
- [ ] 7.7 Pagination (אם נדרש)

### פרופיל חבר כנסת
- [ ] 7.8 יצירת app/members/[id]/page.tsx
- [ ] 7.9 הצגת שם, תמונה, סיעה, תפקיד
- [ ] 7.10 הצגת ועדות
- [ ] 7.11 הצגת קדנציות קודמות
- [ ] 7.12 הצגת הצעות חוק
- [ ] 7.13 הצגת פעילות פרלמנטרית
- [ ] 7.14 הוספת SourceBadge לכל נתון
- [ ] 7.15 הוספת TermExplanation למושגים

## Phase 8: סיעות (Priority: בינוני)

### עמוד סיעות
- [ ] 8.1 יצירת app/factions/page.tsx
- [ ] 8.2 יצירת components/knesset/FactionCard.tsx
- [ ] 8.3 הצגת רשימת סיעות עם מנדטים
- [ ] 8.4 הצגת גרף התפלגות מנדטים
- [ ] 8.5 הסבר ההבדל בין סיעה למפלגה

### פרופיל סיעה
- [ ] 8.6 יצירת app/factions/[id]/page.tsx
- [ ] 8.7 הצגת שם הסיעה, מנדטים
- [ ] 8.8 הצגת חברי הכנסת בסיעה
- [ ] 8.9 הצגת יו"ר הסיעה
- [ ] 8.10 הצגת היסטוריה (אם זמין)

## Phase 9: ועדות (Priority: בינוני)

### עמוד ועדות
- [ ] 9.1 יצירת app/committees/page.tsx
- [ ] 9.2 יצירת components/knesset/CommitteeCard.tsx
- [ ] 9.3 הצגת רשימת ועדות
- [ ] 9.4 סינון לפי סוג (קבועות, זמניות, חקירה)
- [ ] 9.5 הסבר מה עושה כל סוג ועדה

### פרופיל ועדה
- [ ] 9.6 יצירת app/committees/[id]/page.tsx
- [ ] 9.7 הצגת שם הוועדה, סוג
- [ ] 9.8 הצגת חברי הוועדה
- [ ] 9.9 הצגת יו"ר הוועדה
- [ ] 9.10 הצגת ישיבות אחרונות
- [ ] 9.11 הצגת נושאים שנדונו

## Phase 10: חקיקה (Priority: בינוני)

### עמוד חקיקה
- [ ] 10.1 יצירת app/legislation/page.tsx
- [ ] 10.2 הסבר איך הצעת חוק הופכת לחוק
- [ ] 10.3 יצירת SearchInput להצעות חוק
- [ ] 10.4 יצירת FilterBar (סטטוס, סיעה, תחום)
- [ ] 10.5 הצגת רשימת הצעות חוק
- [ ] 10.6 הצגת חוקים שעברו

### פרופיל הצעת חוק
- [ ] 10.7 יצירת app/legislation/[id]/page.tsx
- [ ] 10.8 הצגת שם ההצעה
- [ ] 10.9 הצגת מציעים
- [ ] 10.10 הצגת סטטוס נוכחי
- [ ] 10.11 הצגת שלבי החקיקה
- [ ] 10.12 הצגת תקציר ההצעה
- [ ] 10.13 הצגת הצבעות
- [ ] 10.14 הוספת SourceBadge

## Phase 11: בחירות (Priority: בינוני)

### עמוד בחירות
- [ ] 11.1 יצירת app/elections/page.tsx
- [ ] 11.2 הסבר איך עובדות הבחירות בישראל
- [ ] 11.3 הסבר מהו אחוז החסימה
- [ ] 11.4 הסבר איך מתחלקים 120 המנדטים
- [ ] 11.5 הסבר על שיטת הבחירות (יחסית)
- [ ] 11.6 הסבר על הבדל בין בחירות לכנסת למקומיות
- [ ] 11.7 הצגת תוצאות בחירות היסטוריות (אם זמין)
- [ ] 11.8 יצירת components/data/ProcessDiagram.tsx להסברת תהליך

## Phase 12: ממשלה (Priority: נמוך)

### עמוד ממשלה
- [ ] 12.1 יצירת app/government/page.tsx
- [ ] 12.2 הסבר מהי ממשלה
- [ ] 12.3 הסבר ההבדל בין ממשלה לכנסת
- [ ] 12.4 הצגת הממשלה הנוכחית (אם זמין מ-API)
- [ ] 12.5 הצגת שרים ומשרדים (אם זמין מ-API)
- [ ] 12.6 הצגת היסטוריה של ממשלות קודמות (אם זמין)

## Phase 13: מילון מושגים (Priority: בינוני)

### עמוד מילון מושגים
- [ ] 13.1 יצירת app/dictionary/page.tsx
- [ ] 13.2 יצירת רשימה אלפביתית של מושגים
- [ ] 13.3 כתיבת הסברים למושגים:
  - [ ] 13.3.1 סיעה
  - [ ] 13.3.2 מפלגה
  - [ ] 13.3.3 מנדט
  - [ ] 13.3.4 קואליציה
  - [ ] 13.3.5 אופוזיציה
  - [ ] 13.3.6 ועדה
  - [ ] 13.3.7 הצעת חוק
  - [ ] 13.3.8 קריאה ראשונה/שנייה/שלישית
  - [ ] 13.3.9 אחוז החסימה
  - [ ] 13.3.10 ממשלה
  - [ ] 13.3.11 כנסת
  - [ ] 13.3.12 חבר כנסת
  - [ ] 13.3.13 שר
  - [ ] 13.3.14 יו"ר הכנסת
  - [ ] 13.3.15 ראש הממשלה
- [ ] 13.4 הוספת דוגמאות
- [ ] 13.5 הוספת קישורים לעמודים רלוונטיים
- [ ] 13.6 יצירת פונקציית חיפוש במילון

### אינטגרציה באתר
- [ ] 13.7 הוספת TermExplanation למושגים בכל העמודים
- [ ] 13.8 הוספת קישורים למילון מכל מקום

## Phase 14: היסטוריה (Priority: נמוך)

### עמוד היסטוריה
- [ ] 14.1 יצירת app/history/page.tsx
- [ ] 14.2 הצגת כנסות קודמות
- [ ] 14.3 הצגת חברי כנסת לשעבר
- [ ] 14.4 הצגת תוצאות בחירות קודמות (אם זמין)
- [ ] 14.5 הצגת ממשלות קודמות (אם זמין)
- [ ] 14.6 יצירת components/data/Timeline.tsx
- [ ] 14.7 הצגת ציר זמן של הכנסת מאז הקמתה

## Phase 15: ויזואליזציה (Priority: בינוני)

### רכיבי ויזואליזציה
- [ ] 15.1 התקנת ספריית גרפים (Recharts או Chart.js)
- [ ] 15.2 יצירת components/data/Chart.tsx
- [ ] 15.3 יצירת Bar chart למנדטים
- [ ] 15.4 יצירת Pie chart להתפלגות
- [ ] 15.5 יצירת Line chart למגמות (אם רלוונטי)
- [ ] 15.6 אינטגרציה בדפים הרלוונטיים

## Phase 16: אנימציות (Priority: נמוך)

### אנימציות
- [ ] 16.1 התקנת Framer Motion
- [ ] 16.2 הוספת אנימציות ל-Button
- [ ] 16.3 הוספת אנימציות ל-Card
- [ ] 16.4 הוספת אנימציות ל-Tooltip
- [ ] 16.5 הוספת אנימציות ל-TermExplanation
- [ ] 16.6 הוספת page transitions
- [ ] 16.7 אופטימיזציה של אנימציות

## Phase 17: אופטימיזציה (Priority: בינוני)

### Performance
- [ ] 17.1 Code splitting לרכיבים כבדים
- [ ] 17.2 Lazy loading לעמודים
- [ ] 17.3 Image optimization
- [ ] 17.4 Font optimization
- [ ] 17.5 Caching optimization
- [ ] 17.6 Lighthouse audit
- [ ] 17.7 תיקון בעיות performance

## Phase 18: Accessibility (Priority: בינוני)

### A11y
- [ ] 18.1 הוספת ARIA labels לכל האלמנטים האינטראקטיביים
- [ ] 18.2 Semantic HTML
- [ ] 18.3 Keyboard navigation
- [ ] 18.4 Color contrast check
- [ ] 18.5 Dark mode accessibility
- [ ] 18.6 Screen reader testing
- [ ] 18.7 Skip to content link

## Phase 19: Testing (Priority: בינוני)

### Unit Tests
- [ ] 19.1 התקנת Jest + React Testing Library
- [ ] 19.2 כתיבת tests ל-Button
- [ ] 19.3 כתיבת tests ל-Card
- [ ] 19.4 כתיבת tests ל-SearchInput
- [ ] 19.5 כתיבת tests ל-FilterBar
- [ ] 19.6 כתיבת tests ל-hooks

### Integration Tests
- [ ] 19.7 התקנת Playwright
- [ ] 19.8 כתיבת test ל-navigation
- [ ] 19.9 כתיבת test לחיפוש
- [ ] 19.10 כתיבת test לפילטרים

### E2E Tests
- [ ] 19.11 כתיבת E2E test לדף הבית
- [ ] 19.12 כתיבת E2E test לדף חברי כנסת
- [ ] 19.13 כתיבת E2E test לפרופיל חבר כנסת
- [ ] 19.14 Cross-browser testing
- [ ] 19.15 Mobile testing

## Phase 20: Deployment (Priority: גבוה)

### Environment
- [ ] 20.1 יצירת .env.local
- [ ] 20.2 הגדרת NEXT_PUBLIC_API_URL
- [ ] 20.3 הגדרת NEXT_PUBLIC_SITE_URL
- [ ] 20.4 הגדרת environment variables

### Build
- [ ] 20.5 npm run build
- [ ] 20.6 תיקון build errors
- [ ] 20.7 בדיקת build output
- [ ] 20.8 npm run start (local test)

### Deployment
- [ ] 20.9 בחירת platform (Vercel מומלץ)
- [ ] 20.10 הגדרת repository
- [ ] 20.11 הגדרת build settings
- [ ] 20.12 Deployment
- [ ] 20.13 בדיקת production
- [ ] 20.14 הגדרת custom domain (אם נדרש)

## Phase 21: Monitoring (Priority: נמוך)

### Monitoring Setup
- [ ] 21.1 הגדרת Sentry ל-error tracking
- [ ] 21.2 הגדרת analytics
- [ ] 21.3 הגדרת Web Vitals
- [ ] 21.4 הגדרת API monitoring
- [ ] 21.5 הגדרת alerts

## Phase 22: Documentation (Priority: נמוך)

### Documentation
- [ ] 22.1 עדכון README.md
- [ ] 22.2 כתיבת API documentation
- [ ] 22.3 כתיבת component documentation
- [ ] 22.4 כתיבת deployment guide
- [ ] 22.5 כתיבת contribution guide

## סה"כ: 22 Phase, כ-220 משימות

### Priority Summary:
- **גבוה:** Phases 1-7, 20 (כ-70 משימות)
- **בינוני:** Phases 8-11, 13, 15, 17-19 (כ-90 משימות)
- **נמוך:** Phases 12, 14, 16, 21-22 (כ-60 משימות)

### המלצה להתחלה:
התחל עם Phases 1-7 (תשתית, Data Layer, דפים מרכזיים) כדי לקבל MVP עובד, ואז המשך לשאר המשימות.
