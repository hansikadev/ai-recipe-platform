# 🍳 Servd - AI-Powered Recipe & Meal Planning Application

> **Turn your leftovers into masterpieces.** Snap a photo of your fridge. We'll tell you what to cook. Save money, reduce waste, and eat better tonight.

Servd is a modern, full-stack web application that combines AI-powered image recognition with a comprehensive recipe discovery platform. Users can browse thousands of recipes, scan their pantry to get AI-generated recipe suggestions, and save their favorite meals.

## ✨ Key Features

### 🤖 AI Pantry Scanning
- Upload a photo of your fridge contents
- Google Generative AI (Gemini Vision) analyzes the image
- Get personalized recipe suggestions based on available ingredients
- Rate-limited by subscription tier (free vs Pro)

### 📚 Recipe Discovery
- Browse recipes by **category** (Seafood, Dessert, Breakfast, etc.)
- Filter by **cuisine** (Italian, Asian, American, etc.)
- **Recipe of the Day** feature
- Search and filter capabilities
- Recipe details with instructions and ingredients

### ❤️ Save & Organize
- Save favorite recipes to your collection
- Organize saved recipes for quick access
- Track cooking preferences

### 👤 User Authentication
- Secure authentication via Clerk
- User profiles with personalized data
- Subscription tier management (Free vs Pro)

### 💳 Tiered Access Model
- **Free Tier**: Limited monthly pantry scans (5 scans/month)
- **Pro Tier**: Unlimited pantry scans + premium features
- Arcjet-powered rate limiting and security

### 🔍 Additional Features
- Dark/Light mode support
- Responsive design (mobile-first)
- Real-time rate limit tracking
- Security-first architecture with Arcjet

---

## 🏗️ Project Structure

### Frontend (`/frontend`)
```
frontend/
├── app/                    # Next.js App Router
│   ├── (auth)/            # Authentication pages (sign-in, sign-up)
│   ├── (main)/            # Main app routes
│   │   ├── dashboard/     # Home dashboard
│   │   ├── pantry/        # Pantry management
│   │   ├── recipe/        # Recipe details
│   │   └── recipes/       # Recipe browsing (by category/cuisine)
│   └── page.jsx           # Landing page
├── components/            # Reusable React components
│   ├── ui/               # shadcn/ui components (button, card, dialog, etc.)
│   └── [Component].jsx   # Feature components
├── actions/              # Server actions (Gemini, MealDB, Pantry)
├── hooks/                # Custom React hooks
├── lib/                  # Utilities (checkUser, data, arcjet)
└── public/               # Static assets
```

### Backend (`/backend`)
```
backend/
├── src/
│   ├── api/              # Content type API endpoints
│   │   ├── pantry-item/
│   │   ├── recipe/
│   │   └── saved-recipe/
│   ├── extensions/       # Strapi extensions (user permissions)
│   └── types/            # Generated TypeScript types
├── config/               # Server configuration
│   ├── admin.js         # Admin panel config
│   ├── api.js           # API config
│   ├── database.js      # Database config (PostgreSQL)
│   ├── middlewares.js   # Middleware setup
│   └── server.js        # Server config
└── database/             # Migrations
```

---

## 🛠️ Tech Stack

### Frontend
- **Framework**: Next.js 16.1.6
- **Runtime**: React 19.2.3, React DOM 19.2.3
- **Styling**: TailwindCSS 4, PostCSS 4
- **UI Components**: shadcn/ui, Radix UI, Lucide Icons
- **Authentication**: Clerk 6.37.4
- **AI Integration**: Google Generative AI SDK
- **Security**: Arcjet Next.js plugin
- **Notifications**: Sonner
- **Theme Management**: next-themes
- **Linting**: ESLint 9

### Backend
- **Framework**: Strapi 5.36.1 (Headless CMS)
- **Database**: PostgreSQL (pg 8.8.0)
- **Authentication**: Strapi Users & Permissions plugin
- **Deployment**: Strapi Cloud plugin
- **UI**: React, React DOM, React Router, Styled Components

### External APIs
- **MealDB API**: Recipe database (10,000+ recipes from around the world)
- **Google Generative AI**: Gemini Vision for image analysis
- **Clerk**: Authentication and user management
- **Arcjet**: Rate limiting and security

---

## 📋 Prerequisites

- **Node.js**: v20.0.0 - v24.x.x
- **npm**: v6.0.0 or higher
- **PostgreSQL**: Database setup required
- **Environment Variables**: See `.env` setup below

---

## 🚀 Getting Started

### 1. Clone the Repository
```bash
git clone <repository-url>
cd servd
```

### 2. Install Dependencies

#### Backend
```bash
cd backend
npm install
```

#### Frontend
```bash
cd frontend
npm install
```

### 3. Environment Variables Setup

#### Backend (`backend/.env`)
```bash
# Database Configuration
DATABASE_CLIENT=postgres
DATABASE_HOST=localhost
DATABASE_PORT=5432
DATABASE_NAME=servd
DATABASE_USERNAME=postgres
DATABASE_PASSWORD=<your-password>

# JWT Token
JWT_SECRET=<your-jwt-secret>

# Admin Panel
ADMIN_JWT_SECRET=<your-admin-jwt-secret>
API_TOKEN_SALT=<your-api-token-salt>
APP_KEYS=<your-app-keys>
```

#### Frontend (`frontend/.env`)
```bash
# Clerk Authentication
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=<your-clerk-key>
CLERK_SECRET_KEY=<your-clerk-secret>
NEXT_PUBLIC_CLERK_SIGN_IN_URL=/sign-in
NEXT_PUBLIC_CLERK_SIGN_UP_URL=/sign-up

# Strapi Backend
NEXT_PUBLIC_STRAPI_API_URL=http://localhost:1337
STRAPI_API_TOKEN=<your-strapi-api-token>

# AI & Security
GEMINI_API_KEY=<your-gemini-api-key>
ARCJET_KEY=<your-arcjet-key>
```

---

## 💻 Running the Application

### Backend Development Server
```bash
cd backend
npm run dev
# Server runs on http://localhost:1337
# Admin panel: http://localhost:1337/admin
```

### Frontend Development Server
```bash
cd frontend
npm run dev
# App runs on http://localhost:3000
```

### Backend Production Build
```bash
cd backend
npm run build
npm start
```

### Frontend Production Build
```bash
cd frontend
npm run build
npm start
```

---

## 📦 Available Scripts

### Backend
| Command | Description |
|---------|-------------|
| `npm run dev` | Start development server with hot reload |
| `npm run develop` | Alias for `dev` |
| `npm run build` | Build admin panel |
| `npm start` | Start production server |
| `npm run console` | Open Strapi console |
| `npm run deploy` | Deploy to Strapi Cloud |
| `npm run upgrade` | Upgrade Strapi to latest version |

### Frontend
| Command | Description |
|---------|-------------|
| `npm run dev` | Start Next.js development server |
| `npm run build` | Build production bundle |
| `npm start` | Start production server |
| `npm run lint` | Run ESLint |

---

## 📚 Content Types (Data Models)

### Pantry Item
```json
{
  "id": "unique-id",
  "name": "string",
  "quantity": "number",
  "unit": "string",
  "expiryDate": "date",
  "userId": "relation",
  "createdAt": "timestamp"
}
```

### Recipe
```json
{
  "id": "unique-id",
  "title": "string",
  "description": "string",
  "ingredients": "text",
  "instructions": "text",
  "cookTime": "number",
  "servings": "number",
  "difficulty": "enum (easy|medium|hard)",
  "category": "string",
  "cuisine": "string",
  "imageUrl": "string",
  "externalId": "string (MealDB ID)"
}
```

### Saved Recipe
```json
{
  "id": "unique-id",
  "userId": "relation",
  "recipe": "relation",
  "savedAt": "timestamp",
  "rating": "number"
}
```

---

## 🔐 Authentication & Authorization

### User Registration Flow
1. User signs up via Clerk
2. User data is synced with Strapi via Clerk webhooks
3. User is assigned a subscription tier (Free by default)

### Subscription Tiers
- **Free**: 5 pantry scans per month
- **Pro**: Unlimited scans + priority support

### Rate Limiting
- Powered by Arcjet
- Per-user rate limits via Clerk ID
- Automatic tier-based enforcement

---

## 🧠 AI Features

### Gemini Vision Integration
The app uses Google's Generative AI (Gemini Vision) to:
- Analyze images of food/pantry items
- Identify ingredients
- Generate recipe suggestions based on available items
- Provide nutritional information

**Implementation**: `/frontend/actions/pantry.actions.js`

---

## 🌍 External API Integrations

### MealDB API
- Source for 10,000+ recipes
- Provides recipes by category and cuisine
- Used for "Recipe of the Day" feature
- Free public API

**Actions**: `/frontend/actions/mealdb.actions.js`

### Clerk Authentication
- User management
- Session handling
- Integration with frontend

### Arcjet Security
- Rate limiting (per user, per tier)
- Bot protection
- Anomaly detection

---

## 🎨 UI/UX

### Design System
- **Color Scheme**: Stone/Warm neutrals with orange accents
- **Typography**: Modern sans-serif with serif headings
- **Components**: shadcn/ui + custom components
- **Icons**: Lucide React icons
- **Animations**: TailwindCSS animations

### Responsive Design
- Mobile-first approach
- Tailored layouts for all screen sizes
- Touch-friendly UI

---

## 📊 Database Schema

### PostgreSQL Setup
```bash
# Connect to PostgreSQL
psql -U postgres

# Create database
CREATE DATABASE servd;

# Run migrations (automated by Strapi)
npm run migrate
```

---

## 🚢 Deployment

### Backend Deployment (Strapi Cloud)
```bash
npm run deploy
```

### Frontend Deployment (Vercel/Others)
```bash
npm run build
npm start
```

---

## 🔧 Configuration

### Middleware Configuration
Located in `backend/config/middlewares.js`:
- CORS settings
- Security headers
- Request logging

### API Configuration
Located in `backend/config/api.js`:
- API prefix
- Version management

---

## 📝 License

This project is licensed under the terms specified in `backend/license.txt`.

---

## 🤝 Contributing

1. Create a feature branch (`git checkout -b feature/AmazingFeature`)
2. Commit changes (`git commit -m 'Add AmazingFeature'`)
3. Push to branch (`git push origin feature/AmazingFeature`)
4. Open a Pull Request

---

## 🐛 Troubleshooting

### Backend Issues
- **Port Already in Use**: Change port in `backend/config/server.js`
- **Database Connection Error**: Verify PostgreSQL is running and credentials are correct
- **Migration Errors**: Run `npx strapi migrate:refresh` to reset

### Frontend Issues
- **Clerk Auth Errors**: Check `.env` keys are correct
- **API Connection**: Verify backend is running on `http://localhost:1337`
- **Build Errors**: Clear `.next` folder and rebuild

### Common Solutions
```bash
# Clear all caches and reinstall
rm -rf node_modules package-lock.json
npm install

# Backend database reset (development only!)
cd backend
npm run strapi migrate:refresh

# Frontend cache clear
rm -rf .next
npm run build
```

---

## 📞 Support & Resources

### Documentation
- [Next.js Docs](https://nextjs.org/docs)
- [Strapi Documentation](https://docs.strapi.io)
- [Clerk Documentation](https://clerk.com/docs)
- [Arcjet Documentation](https://arcjet.com/docs)

### External APIs
- [MealDB API](https://www.themealdb.com/api.php)
- [Google Generative AI](https://ai.google.dev)

---

## 📈 Future Enhancements

- [ ] Advanced recipe filtering (allergies, dietary restrictions)
- [ ] User-generated recipes
- [ ] Social sharing features
- [ ] Recipe ratings and reviews
- [ ] Nutritional analysis
- [ ] Grocery list integration
- [ ] Meal planning calendar
- [ ] Mobile app (React Native)

---

## 👨‍💻 Development Team

Built with ❤️ by the Servd team.

---

**Last Updated**: June 2026
