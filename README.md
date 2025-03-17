# IISMA Lead Management System

A comprehensive Lead Management System tailored for internal use within a stock market training institute, which operates multiple offline branches and offers online courses. The system is fully client-side with localStorage persistence, making it easy to deploy anywhere without any backend setup.

![Dashboard Screenshot](https://placeholder-for-dashboard-screenshot.png)

## Features

### 1. Advanced Leads Management
- Add, edit, and update lead details with full form validation
- Dedicated notes/remarks field for tracking important information
- Bulk delete functionality for admins (select multiple leads or delete all imported leads)
- Custom filtering system (by status, branch, etc.)
- Horizontal scrollable table for viewing all lead data efficiently
- Import leads from CSV files with preview before import
- Export lead data for backup or analysis
- Indian phone number formatting (+91 XXXXX XXXXX)

### 2. Dashboard and Reports
- Key metrics display including:
  - Total Leads, Open Leads, Converted Leads
  - Conversion Rate
  - Lead to Demo Percentage
  - Scheduled Demos
  - Today's Stats (Leads, Conversions, Demos)
- Visual data representation with multiple chart types:
  - Bar charts
  - Pie charts
  - Line charts
- Data filtering by timeframes (Today, Week, Month, All)
- Ability to switch between chart types

### 3. User Management System
- Role-based access control (Admin and Manager roles)
- Secure login with localStorage persistence
- Admin capabilities to:
  - Create new users
  - Edit existing users
  - Change user passwords
  - Delete users (with protection against deleting own account or last admin)
- User permissions based on roles

### 4. UI/UX Features
- Toast notification system for actionable feedback
- Dark/Light theme mode with persistent preferences
- Responsive design for all devices (mobile, tablet, desktop)
- Smooth animations and transitions with Framer Motion
- Loading states and error handling
- Form validation with React Hook Form

### 5. Security Features
- Password protection for all accounts
- Role-based access control to prevent unauthorized actions
- Session persistence with localStorage
- Dedicated logout page with confirmation

## Tech Stack

- **Frontend**: Next.js 13 App Router, React 18, TypeScript
- **Styling**: Tailwind CSS, Framer Motion for animations
- **State Management**: React Hooks and Context API
- **Storage**: Client-side localStorage for persistence
- **Forms**: React Hook Form for validation
- **Charts**: Chart.js with React-Chartjs-2
- **Icons**: Heroicons
- **Date Handling**: react-datepicker

## Getting Started

### Prerequisites
- Node.js (v14 or later)
- npm or yarn

### Installation

1. Clone the repository
```bash
git clone https://github.com/yourusername/iisma-lms.git
cd iisma-lms
```

2. Install dependencies
```bash
npm install
# or
yarn install
```

3. Run the development server
```bash
npm run dev
# or
yarn dev
```

4. Open [http://localhost:3000](http://localhost:3000) in your browser

### Default Login Credentials
- **Admin**
  - Username: admin
  - Password: admin123
- **Manager**
  - Username: manager
  - Password: manager123

## Role Permissions

### Admin
- Full access to all features
- Create, edit, and delete users
- Manage all leads
- Access dashboard and reports
- Can delete leads in bulk

### Manager
- Can view and manage leads
- Can access dashboard and reports
- Cannot access user management
- Limited ability to perform certain admin actions

## Project Structure

```
iisma-lms/
├── public/                # Static assets
├── src/
│   ├── app/               # Next.js App Router pages
│   │   ├── dashboard/     # Dashboard and reports
│   │   ├── leads/         # Lead management pages
│   │   │   ├── [id]/      # Individual lead pages
│   │   │   ├── import/    # Lead import functionality
│   │   │   └── export/    # Lead export functionality
│   │   ├── admin/         # User management
│   │   ├── logout/        # Logout confirmation
│   │   └── page.tsx       # Login page
│   ├── components/        # Reusable React components
│   │   ├── AppLayout.tsx  # Main application layout
│   │   ├── Toast.tsx      # Toast notification system
│   │   └── ...            # Other components
│   ├── hooks/             # Custom React hooks
│   │   ├── useAuth.tsx    # Authentication hook
│   │   └── ...            # Other hooks
│   ├── lib/               # Core functionality
│   │   └── db.ts          # localStorage database functions
│   ├── models/            # Data models and interfaces
│   │   ├── Lead.ts        # Lead data model
│   │   └── User.ts        # User data model and permissions
│   └── utils/             # Helper functions
├── .gitignore
├── next.config.js
├── package.json
├── postcss.config.js
├── README.md
├── tailwind.config.js
└── tsconfig.json
```

## Screenshots

### Dashboard
![Dashboard](https://placeholder-for-dashboard-screenshot.png)

### Leads Management
![Leads Management](https://placeholder-for-leads-screenshot.png)

### User Management
![User Management](https://placeholder-for-admin-screenshot.png)

## Deployment Options

You can deploy this application using various free and low-cost options:

### Free Options:
1. **Vercel**: Easiest option for Next.js apps with a generous free tier
   - Sign up at [vercel.com](https://vercel.com)
   - Connect your GitHub repository
   - Automatic deployment on push

2. **Netlify**: Similar to Vercel with free tier
   - Sign up at [netlify.com](https://netlify.com)
   - Connect your repository or upload the build folder

3. **GitHub Pages**: Free for public repositories
   - Build your app (`npm run build`)
   - Deploy the static output to GitHub Pages

### Low-Cost Options:
1. **DigitalOcean App Platform**: Starting at $5/month
   - Easy deployment from repository

2. **Shared Hosting**: Many providers offer affordable plans
   - Upload the static build to any web host

### Self-Hosted Options:
1. **Personal Computer/Server**: Deploy on any machine with Node.js
   - Build the app (`npm run build`)
   - Use `npm start` to run a production server

Since the app uses localStorage for data persistence, no database setup is required for deployment. However, note that data will be specific to each user's browser and not shared across devices or users.

## Future Enhancements

- Enhanced authentication with JWT or NextAuth.js
- Email notifications for follow-ups and demos
- Integration with calendar for scheduling
- Progressive Web App (PWA) functionality for offline use
- Advanced reporting and analytics
- Data backup and restore functionality
- Database integration options (MongoDB, Firebase, etc.)

## License

This project is licensed under the MIT License - see the LICENSE file for details. 