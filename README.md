# Micro Lend Connect

A modern peer-to-peer micro lending platform built with React and Firebase. Connect borrowers and lenders in a transparent, efficient, and secure ecosystem.

## Overview

Micro Lend Connect is a full-stack web application that facilitates micro-lending between individuals. The platform features dual dashboards—one for borrowers and one for lenders—with comprehensive loan management, user profiling, and real-time updates powered by Firebase.

### Key Features

- **Dual Role System**: Separate dashboards for borrowers and lenders
- **Loan Management**: 
  - Browse available loans (lenders)
  - Create new loan requests (borrowers)
  - Track active loans and repayment status
  - Repay loans with integrated modal interface
- **User Profiles**: Comprehensive borrower profiles with financial information
- **Authentication**: Secure Firebase Authentication with email/password login
- **Real-time Updates**: Firebase Firestore for instant data synchronization
- **Responsive Design**: Built with modern React and TypeScript

## Tech Stack

- **Frontend**: React 19, TypeScript, Vite
- **Styling**: CSS
- **Backend**: Firebase (Authentication, Firestore Database, Cloud Functions)
- **Charts**: Recharts for data visualization
- **Routing**: React Router v7
- **Build Tool**: Vite
- **Code Quality**: ESLint, TypeScript

## Project Structure

```
micro-lend-connect/
├── src/
│   ├── components/
│   │   ├── Login.tsx              # Login page
│   │   ├── SignUp.tsx             # User registration
│   │   ├── Dashboard.tsx          # Main dashboard router
│   │   ├── BorrowerDashboard.tsx  # Borrower-specific interface
│   │   ├── LenderDashboard.tsx    # Lender-specific interface
│   │   ├── MyLoans.tsx            # Loan history and status
│   │   ├── NewRequestForm.tsx     # Create new loan request
│   │   ├── RepayLoanModal.tsx     # Loan repayment interface
│   │   ├── MyBorrowerProfile.tsx  # Borrower profile management
│   │   └── lender/
│   │       ├── DashboardHome.tsx
│   │       ├── LoanMarketplace.tsx
│   │       ├── MyPortfolio.tsx
│   │       └── BorrowerProfileModal.tsx
│   ├── context/
│   │   └── AuthContext.tsx        # Authentication state management
│   ├── firebase.ts                # Firebase configuration
│   ├── App.tsx                    # Main app router
│   └── main.tsx                   # Entry point
├── public/                        # Static assets
├── scripts/
│   └── seed-test-users.js        # Test data seeding
├── docs/
│   └── test-credentials.md       # Testing documentation
└── vite.config.ts               # Vite configuration
```

## Getting Started

### Prerequisites

- Node.js (v16 or higher)
- npm or yarn
- Firebase project (create free at [firebase.google.com](https://firebase.google.com))

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/ayushgaur475/Micro-lend-project.git
   cd Micro-lend-project
   ```

2. **Install dependencies**
   ```bash
   cd micro-lend-connect
   npm install
   ```

3. **Configure Firebase**
   - Create a Firebase project at [Firebase Console](https://console.firebase.google.com)
   - Update `src/firebase.ts` with your Firebase credentials:
     ```javascript
     const firebaseConfig = {
       apiKey: "YOUR_API_KEY",
       authDomain: "YOUR_AUTH_DOMAIN",
       projectId: "YOUR_PROJECT_ID",
       storageBucket: "YOUR_STORAGE_BUCKET",
       messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
       appId: "YOUR_APP_ID"
     };
     ```

4. **Set up test users** (optional)
   ```bash
   npm run seed:test-users
   ```

### Running the Application

**Development Mode**
```bash
npm run dev
```
The application will be available at `http://localhost:5173`

**Build for Production**
```bash
npm run build
```

**Preview Production Build**
```bash
npm run preview
```

**Run Linter**
```bash
npm lint
```

## Test Credentials

After running `npm run seed:test-users`, use these credentials to test the application:

| Role     | Email                         | Password      |
|----------|-------------------------------|---------------|
| Borrower | `borrower.test@microlend.dev` | `Borrower123!`|
| Lender   | `lender.test@microlend.dev`   | `Lender123!`  |

## Usage

### For Borrowers

1. Sign up or log in with borrower credentials
2. Navigate to "New Request" to create a loan request
3. Specify loan amount, duration, and purpose
4. View all your loans in "My Loans"
5. Use "Repay Loan" modal to make payments
6. Manage your profile in "My Profile"

### For Lenders

1. Sign up or log in with lender credentials
2. Browse available loans in "Loan Marketplace"
3. Review borrower profiles before lending
4. View your loan portfolio in "My Portfolio"
5. Track interest earnings and repayments

## Project Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run lint` - Run ESLint
- `npm run preview` - Preview production build
- `npm run seed:test-users` - Create test users in Firebase

## Firebase Setup

### Required Firebase Services

1. **Authentication**
   - Enable Email/Password provider
   - Configure sign-in methods

2. **Firestore Database**
   - Create collections: `users`, `loans`, `repayments`
   - Set security rules appropriately

3. **Cloud Functions** (optional)
   - For automated interest calculations
   - For loan status updates

### Database Schema (Firestore)

**Users Collection**
```typescript
{
  uid: string;
  email: string;
  role: "borrower" | "lender";
  profile: {
    fullName?: string;
    dateOfBirth?: string;
    businessName?: string;
    businessType?: string;
  };
}
```

**Loans Collection**
```typescript
{
  borrowerId: string;
  amount: number;
  duration: number; // in days
  purpose: string;
  status: "pending" | "active" | "repaid" | "defaulted";
  createdAt: timestamp;
  dueDate: timestamp;
}
```

## Development Guidelines

- **Components**: Keep components focused and reusable
- **Context**: Use AuthContext for global state
- **Styling**: Use CSS files for component styling
- **Types**: Leverage TypeScript for type safety
- **Code Quality**: Run linter before committing

## Deployment

### Vercel (Recommended)
```bash
npm install -g vercel
vercel
```

### Firebase Hosting
```bash
npm install -g firebase-tools
firebase init
firebase deploy
```

## Contributing

1. Create a feature branch
2. Make your changes
3. Test thoroughly
4. Submit a pull request

## License

MIT License - feel free to use this project for personal or commercial purposes.

## Support

For issues, feature requests, or questions:
- GitHub Issues: [Create an issue](https://github.com/ayushgaur475/Micro-lend-project/issues)
- Email: ayushgaur475@gmail.com

## Future Enhancements

- [ ] Mobile app (React Native)
- [ ] Payment gateway integration (Stripe, Razorpay)
- [ ] Advanced analytics dashboard
- [ ] Credit scoring algorithm
- [ ] Document upload and verification
- [ ] SMS/Email notifications
- [ ] Multi-language support
- [ ] KYC verification system

---

**Built with ❤️ for the Hackathon**
