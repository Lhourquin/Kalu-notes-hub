## Exemple de structure idéal pour un projet next

app/
├── api/                    # Routes API Next.js
│   ├── auth/
│   │   ├── login/
│   │   │   └── route.ts
│   │   ├── logout/
│   │   │   └── route.ts
│   │   └── me/
│   │       └── route.ts
├── (auth)/                # Routes publiques (login, register)
│   ├── login/
│   │   └── page.tsx
│   └── register/
│       └── page.tsx
├── (protected)/           # Routes protégées
│   ├── dashboard/
│   │   └── page.tsx
│   └── layout.tsx        # Layout pour routes protégées
├── components/
│   ├── auth/             # Composants d'authentification
│   │   ├── AuthProvider.tsx
│   │   └── LoginForm.tsx
│   └── ui/              # Composants UI réutilisables
├── lib/
│   ├── auth.ts          # Fonctions d'aide pour l'auth
│   └── api.ts           # Configuration API
└── types/
    └── auth.ts          # Types pour l'authentification
