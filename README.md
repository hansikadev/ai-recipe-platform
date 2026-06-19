# Servd - AI-Powered Recipe & Pantry Management

![Node.js Version](https://img.shields.io/badge/node-%3E%3D20.0.0-green)
![License](https://img.shields.io/badge/license-MIT-blue)

Servd is a full-stack web application that helps users discover, manage, and cook recipes while tracking their pantry inventory. Powered by AI, it provides intelligent cooking assistance, recipe recommendations, and pantry management features.

## 🌟 Features

### 🍳 Recipe Management
- **Browse Recipes**: Explore recipes from various cuisines (Italian, Chinese, Mexican, Indian, American, Thai, Japanese, and more)
- **Detailed Recipe View**: Access complete recipes with descriptions, instructions, and ingredients
- **Recipe Categories**: Filter recipes by cuisine type and category
- **Save Recipes**: Bookmark your favorite recipes for quick access
- **Recipe PDF Export**: Generate and download recipes as PDFs

### 📦 Pantry Management
- **Track Inventory**: Keep track of ingredients and pantry items with quantities
- **Image Upload**: Add images to pantry items for easy identification
- **Add to Pantry Modal**: Quick-add interface for new items
- **Pantry Dashboard**: Visual overview of all pantry items

### 🤖 AI Cooking Assistant
- **Google Generative AI Integration**: AI-powered cooking guidance
- **How-to Guidance**: Get cooking instructions and tips powered by AI
- **Smart Recommendations**: Receive recipe suggestions based on available pantry items

### 👤 User Management
- **Clerk Authentication**: Secure user sign-up and sign-in
- **User Profiles**: Personalized user accounts
- **Subscription Tiers**: Free and Pro plan options with different features
- **User Dropdown Menu**: Quick access to user settings and profile

### 🔐 Security & Performance
- **Arcjet Security**: Advanced protection against bots and abuse
- **Dark Mode Support**: Theme customization with `next-themes`
- **Responsive Design**: Mobile-friendly interface using Tailwind CSS
- **Real-time Notifications**: Toast notifications with Sonner

## 🏗️ Tech Stack

### Backend
- **Framework**: [Strapi](https://strapi.io/) v5.36.1 - Headless CMS
- **Database**: PostgreSQL
- **Node.js**: v20.x - v24.x
- **Authentication**: Strapi Users & Permissions Plugin
- **Cloud Deployment**: Strapi Cloud Support

### Frontend
- **Framework**: [Next.js](https://nextjs.org/) v16.1.6 - React framework
- **UI Framework**: [React](https://react.dev/) v19.2.3
- **Styling**: [Tailwind CSS](https://tailwindcss.com/) v4
- **Component Library**: [Radix UI](https://www.radix-ui.com/), shadcn/ui
- **Authentication**: [Clerk](https://clerk.com/)
- **AI Integration**: [Google Generative AI](https://ai.google.dev/)
- **Security**: [Arcjet](https://arcjet.com/)
- **Icons**: [Lucide React](https://lucide.dev/)
- **Notifications**: [Sonner](https://sonner.emilkowal.ski/)
- **Theme Management**: [next-themes](https://github.com/pacocoursey/next-themes)

## 📋 Project Structure

```
servd/
├── backend/                          # Strapi CMS Backend
│   ├── config/
│   │   ├── admin.js
│   │   ├── api.js
│   │   ├── database.js              # Database configuration
│   │   ├── middlewares.js
│   │   ├── plugins.js
│   │   └── server.js
│   ├── src/
│   │   ├── index.js
│   │   ├── admin/
│   │   ├── api/
│   │   │   ├── pantry-item/         # Pantry item API
│   │   │   │   ├── controllers/
│   │   │   │   ├── routes/
│   │   │   │   ├── services/
│   │   │   │   └── content-types/
│   │   │   ├── recipe/              # Recipe API
│   │   │   │   ├── controllers/
│   │   │   │   ├── routes/
│   │   │   │   ├── services/
│   │   │   │   └── content-types/
│   │   │   └── saved-recipe/        # Saved recipe API
│   │   ├── extensions/
│   │   │   └── users-permissions/   # User permissions
│   │   └── types/
│   ├── database/
│   │   └── migrations/              # Database migrations
│   ├── public/
│   │   ├── robots.txt
│   │   └── uploads/                 # Uploaded files
│   ├── package.json
│   └── README.md
│
├── frontend/                         # Next.js Frontend
│   ├── app/
│   │   ├── globals.css
│   │   ├── layout.js
│   │   ├── page.jsx                 # Landing page
│   │   ├── (auth)/                  # Auth routes
│   │   │   ├── sign-in/
│   │   │   └── sign-up/
│   │   └── (main)/                  # Main app routes
│   │       ├── dashboard/
│   │       ├── pantry/
│   │       ├── recipe/
│   │       └── recipes/             # Recipe browsing
│   ├── components/
│   │   ├── ui/                      # Shadcn UI components
│   │   ├── AddToPantryModal.jsx
│   │   ├── RecipeCard.jsx
│   │   ├── RecipeGrids.jsx
│   │   ├── RecipePDF.jsx
│   │   ├── PricingSection.jsx
│   │   ├── ProLockedSection.jsx
│   │   └── ...
│   ├── actions/
│   │   ├── mealdb.actions.js        # MealDB API integration
│   │   ├── pantry.actions.js        # Pantry operations
│   │   └── recipe.actions.js        # Recipe operations
│   ├── hooks/
│   │   └── use-fetch.js             # Custom fetch hook
│   ├── lib/
│   │   ├── arcjet.js                # Arcjet security
│   │   ├── checkUser.js             # User validation
│   │   ├── data.js                  # Static data
│   │   └── utils.js
│   ├── public/
│   ├── config files (next.config.mjs, tailwind.config.js, etc.)
│   ├── package.json
│   └── README.md
│
└── README.md                         # This file
```

## 🚀 Getting Started

### Prerequisites

- **Node.js**: v20.0.0 or higher (up to v24.x)
- **npm**: v6.0.0 or higher
- **Git**: For version control
- **Database**: PostgreSQL (for production)
- **Environment Variables**: Required API keys (see Configuration section)

### Installation

#### 1. Clone the repository

```bash
git clone <repository-url>
cd servd
```

#### 2. Install Backend Dependencies

```bash
cd backend
npm install
```

#### 3. Install Frontend Dependencies

```bash
cd ../frontend
npm install
```

### Configuration

#### Backend Configuration

1. Create a `.env` file in the `backend/` directory:

```env
# Database Configuration
DATABASE_CLIENT=postgres
DATABASE_HOST=localhost
DATABASE_PORT=5432
DATABASE_NAME=servd_db
DATABASE_USERNAME=postgres
DATABASE_PASSWORD=your_password

# Strapi Admin Panel
ADMIN_JWT_SECRET=your-secret-key-here
API_TOKEN_SALT=your-token-salt-here

# Server Configuration
NODE_ENV=development
PORT=1337
```

2. Configure database in `backend/config/database.js` (already set up to use PostgreSQL)

#### Frontend Configuration

1. Create a `.env.local` file in the `frontend/` directory:

```env
# Clerk Authentication
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=your_clerk_publishable_key
CLERK_SECRET_KEY=your_clerk_secret_key

# Google Generative AI
NEXT_PUBLIC_GOOGLE_AI_API_KEY=your_google_ai_key

# Arcjet Security
NEXT_PUBLIC_ARCJET_KEY=your_arcjet_key

# API Configuration
NEXT_PUBLIC_API_URL=http://localhost:1337
```

2. Get your API keys from:
   - [Clerk Dashboard](https://dashboard.clerk.com/)
   - [Google AI Studio](https://aistudio.google.com/)
   - [Arcjet Dashboard](https://app.arcjet.com/)

### Running the Application

#### Development Mode

**Terminal 1 - Start Backend:**
```bash
cd backend
npm run develop
```
Backend will be available at `http://localhost:1337`

**Terminal 2 - Start Frontend:**
```bash
cd frontend
npm run dev
```
Frontend will be available at `http://localhost:3000`

#### Production Build

**Backend:**
```bash
cd backend
npm run build
npm run start
```

**Frontend:**
```bash
cd frontend
npm run build
npm run start
```

## 📚 API Documentation

### Base URL
- Development: `http://localhost:1337/api`
- Production: `https://your-domain.com/api`

### Main Endpoints

#### Recipes
- `GET /recipes` - Get all recipes
- `GET /recipes/:id` - Get recipe by ID
- `POST /recipes` - Create recipe (admin only)
- `PUT /recipes/:id` - Update recipe (admin only)
- `DELETE /recipes/:id` - Delete recipe (admin only)

#### Pantry Items
- `GET /pantry-items` - Get user's pantry items
- `POST /pantry-items` - Add item to pantry
- `PUT /pantry-items/:id` - Update pantry item
- `DELETE /pantry-items/:id` - Remove from pantry

#### Saved Recipes
- `GET /saved-recipes` - Get user's saved recipes
- `POST /saved-recipes` - Save a recipe
- `DELETE /saved-recipes/:id` - Remove saved recipe

#### Authentication
- `POST /auth/local` - Login
- `POST /auth/local/register` - Register
- `GET /users/me` - Get current user (requires token)

## 🔧 Available Scripts

### Backend

```bash
npm run dev         # Start development server with auto-reload
npm run develop     # Alias for dev
npm run build       # Build admin panel
npm run start       # Start production server
npm run strapi      # Access Strapi CLI
npm run console     # Start Strapi console
npm run deploy      # Deploy to Strapi Cloud
```

### Frontend

```bash
npm run dev         # Start development server
npm run build       # Build for production
npm run start       # Start production server
npm run lint        # Run ESLint
```

## 🎨 Features in Detail

### User Authentication & Profiles
- Powered by Clerk for secure authentication
- Support for email/password and social login
- User profile management
- Subscription tier tracking (Free/Pro)

### Recipe Discovery
- Browse recipes by cuisine (Italian, Chinese, Mexican, Indian, American, Thai, Japanese, etc.)
- Category-based filtering
- Search functionality
- Recipe details with ingredients and instructions

### Pantry Tracking
- Add/edit/delete pantry items
- Upload item images
- Track quantities and expiration dates
- Quick access modal for adding items

### Saved Recipes & Collections
- Save favorite recipes for later
- Organize saved recipes
- Export recipes as PDF
- Share recipes with others

### AI-Powered Features
- Cooking assistance powered by Google Generative AI
- Smart recipe recommendations based on pantry inventory
- AI-generated how-to guides for cooking techniques
- Real-time cooking tips and suggestions

### Security & Performance
- Arcjet integration for bot prevention and abuse protection
- Secure API authentication with JWT tokens
- Role-based access control (User/Admin)
- Optimized image loading with Next.js Image component

## 📦 Database Schema

### Collections

#### Recipes
```
- id: UUID
- title: String (required)
- description: Rich Text
- cuisine: Enum (italian, chinese, mexican, indian, american, thai, japanese, etc.)
- category: Enum
- ingredients: JSON
- instructions: Rich Text
- prepTime: Number
- cookTime: Number
- servings: Number
- difficulty: Enum
- image: Media
- createdAt: DateTime
- publishedAt: DateTime
```

#### Pantry Items
```
- id: UUID
- name: String (required)
- quantity: String
- imageUrl: String
- owner: Relation (User)
- createdAt: DateTime
```

#### Saved Recipes
```
- id: UUID
- recipe: Relation (Recipe)
- user: Relation (User)
- savedAt: DateTime
```

#### Users (Strapi Users & Permissions)
```
- id: UUID
- username: String
- email: String
- provider: String
- confirmed: Boolean
- pantry_items: Relation (Pantry Items)
- saved_recipes: Relation (Saved Recipes)
```

## 🔐 Environment Variables Reference

### Backend (.env)
| Variable | Description | Example |
|----------|-------------|---------|
| `DATABASE_CLIENT` | Database type | `postgres` |
| `DATABASE_HOST` | Database host | `localhost` |
| `DATABASE_PORT` | Database port | `5432` |
| `DATABASE_NAME` | Database name | `servd_db` |
| `DATABASE_USERNAME` | Database user | `postgres` |
| `DATABASE_PASSWORD` | Database password | `password123` |
| `ADMIN_JWT_SECRET` | JWT secret for admin panel | `your-secret-key` |
| `API_TOKEN_SALT` | Token salt for API tokens | `your-salt` |
| `NODE_ENV` | Environment | `development` or `production` |
| `PORT` | Server port | `1337` |

### Frontend (.env.local)
| Variable | Description | Example |
|----------|-------------|---------|
| `NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY` | Clerk public key | `pk_test_...` |
| `CLERK_SECRET_KEY` | Clerk secret key | `sk_test_...` |
| `NEXT_PUBLIC_GOOGLE_AI_API_KEY` | Google AI API key | `AIza...` |
| `NEXT_PUBLIC_ARCJET_KEY` | Arcjet security key | `ajk_...` |
| `NEXT_PUBLIC_API_URL` | Backend API URL | `http://localhost:1337` |

## 🚀 Deployment

### Backend Deployment

#### Strapi Cloud (Recommended)
```bash
cd backend
npm run deploy
```

#### Traditional Hosting (Heroku, AWS, etc.)
1. Build the application: `npm run build`
2. Set environment variables on your host
3. Start the server: `npm run start`

### Frontend Deployment

#### Vercel (Recommended for Next.js)
1. Push your code to GitHub
2. Connect repository to Vercel
3. Set environment variables in Vercel dashboard
4. Deploy automatically on push

#### Other Platforms (AWS, DigitalOcean, etc.)
1. Build the application: `npm run build`
2. Set environment variables
3. Start the server: `npm run start`

## 🐛 Troubleshooting

### Backend Issues

#### Port Already in Use
```bash
# Kill process on port 1337
# On Windows:
netstat -ano | findstr :1337
taskkill /PID <PID> /F

# On macOS/Linux:
lsof -i :1337
kill -9 <PID>
```

#### Database Connection Error
- Verify PostgreSQL is running
- Check database credentials in `.env`
- Ensure database exists: `createdb servd_db`

#### Node Version Error
```bash
# Check Node version
node --version

# Update Node using nvm (if installed)
nvm install 20
nvm use 20
```

### Frontend Issues

#### Clerk Authentication Error
- Verify `NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY` is correct
- Check Clerk Dashboard for configured URLs
- Clear browser cookies and try again

#### API Connection Error
- Ensure backend is running on correct port
- Verify `NEXT_PUBLIC_API_URL` is correct
- Check browser console for CORS errors

#### Build Failed
```bash
# Clear cache and reinstall dependencies
rm -rf node_modules package-lock.json
npm install
npm run build
```

## 📝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [Strapi](https://strapi.io/) for the powerful headless CMS
- [Next.js](https://nextjs.org/) for the React framework
- [Clerk](https://clerk.com/) for authentication
- [Google AI](https://ai.google.dev/) for AI capabilities
- [Tailwind CSS](https://tailwindcss.com/) for styling
- [Arcjet](https://arcjet.com/) for security

## 📧 Support

For support, email support@servd.app or create an issue in the repository.

## 🎯 Roadmap

- [ ] Mobile app (React Native)
- [ ] Meal planning calendar
- [ ] Nutrition tracking
- [ ] Recipe ratings and reviews
- [ ] Social sharing features
- [ ] Recipe video tutorials
- [ ] Grocery list integration
- [ ] Restaurant recommendations
- [ ] Multi-language support

---

**Last Updated**: June 19, 2026

**Version**: 0.1.0
