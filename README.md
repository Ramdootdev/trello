# trello

A modern Trello-like project management application for organizing work with boards, lists, and cards.

✨ Features

📋 Boards

- Create and manage multiple boards
- Organize boards by workspace
- Invite team members
- Control board access
- Manage board members and permissions

📝 Lists

- Create lists
- Rename lists
- Delete lists
- Reorder lists
- Organize workflow stages such as "To Do", "In Progress", and "Done"

🎴 Cards

- Create and edit tasks
- Drag and drop cards between lists
- Reorder cards
- Assign members
- Add labels
- Set due dates
- Add descriptions
- Create checklists
- Add comments
- Archive completed cards

👥 Collaboration

- Shared workspaces and boards
- Team member management
- Board invitations
- Member assignments
- Activity history
- Real-time board updates

🔎 Search & Organization

- Search cards and boards
- Filter cards by member
- Filter cards by label
- Filter cards by due date
- Sort and organize work efficiently

---

🏗️ Architecture

The application is planned around three main layers:

┌─────────────────────────────┐
│         Web Client          │
│      React / TypeScript     │
│                             │
│  Boards • Lists • Cards     │
└──────────────┬──────────────┘
               │
               │ HTTP / WebSocket
               ▼
┌─────────────────────────────┐
│         API Server          │
│                             │
│ Authentication              │
│ Workspaces                  │
│ Boards & Lists              │
│ Cards & Members             │
│ Collaboration               │
└──────────────┬──────────────┘
               │
               │ Database Queries
               ▼
┌─────────────────────────────┐
│          Database           │
│                             │
│ Users                       │
│ Workspaces                  │
│ Boards                      │
│ Lists                       │
│ Cards                       │
│ Members                     │
│ Labels                      │
│ Comments                    │
└─────────────────────────────┘

---

📦 Core Data Model

User
 │
 ├── Workspace Membership
 │        │
 │        └── Workspace
 │              │
 │              └── Board
 │                    │
 │                    ├── Board Member
 │                    │
 │                    └── List
 │                          │
 │                          └── Card
 │                               │
 │                               ├── Label
 │                               ├── Member
 │                               ├── Checklist
 │                               └── Comment
 │
 └── Activity

Entity| Purpose
User| Application account
Workspace| Container for teams and boards
Board| Project or Kanban board
BoardMember| User permissions on a board
List| Workflow column
Card| Individual task
Label| Card categorization
Checklist| Subtasks within a card
Comment| Discussion on a card
Activity| History of board changes

---

🗺️ Development Plan

Phase 1 — Foundation & MVP

- [ ] Project setup
- [ ] Configure TypeScript
- [ ] Configure linting and formatting
- [ ] Configure environment variables
- [ ] Configure PostgreSQL
- [ ] Configure database migrations
- [ ] Authentication
- [ ] User registration
- [ ] User login
- [ ] Session management
- [ ] Workspace creation
- [ ] Workspace membership
- [ ] Board creation
- [ ] Board management
- [ ] List management
- [ ] Card management
- [ ] Drag-and-drop cards
- [ ] Card details
- [ ] Responsive UI

Phase 2 — Collaboration

- [ ] Board invitations
- [ ] Member management
- [ ] Member assignment
- [ ] Board permissions
- [ ] Workspace permissions
- [ ] Comments
- [ ] Labels
- [ ] Activity history
- [ ] Real-time board updates

Phase 3 — Productivity

- [ ] Checklists
- [ ] Due dates
- [ ] Search
- [ ] Filters
- [ ] Notifications
- [ ] Keyboard shortcuts
- [ ] Loading states
- [ ] Empty states
- [ ] Error handling

Phase 4 — Advanced Features

- [ ] Calendar view
- [ ] Analytics
- [ ] Custom workflows
- [ ] Automation rules
- [ ] File attachments
- [ ] Public board sharing
- [ ] API integrations
- [ ] Advanced permissions

---

🚀 Getting Started

«The application is currently under development. The setup instructions below describe the planned development environment and will be updated as implementation progresses.»

Prerequisites

Make sure you have the following installed:

- Node.js 20+
- npm, pnpm, or yarn
- PostgreSQL
- Git

Clone the Repository

git clone https://github.com/Ramdootdev/trello.git
cd trello

Install Dependencies

npm install

Environment Variables

Create a ".env" file:

cp .env.example .env

Configure the required environment variables:

DATABASE_URL=
AUTH_SECRET=
API_URL=

Database

Run database migrations:

npm run db:migrate

Start Development Server

npm run dev

The application will be available at:

http://localhost:3000

---

🛠️ Development

Run the Development Server

npm run dev

Run Tests

npm test

Run Linting

npm run lint

Format the Project

npm run format

Build for Production

npm run build

---

🧪 Testing Strategy

The project will use multiple levels of testing.

Unit Tests

Unit tests should cover business logic such as:

- Card ordering
- List ordering
- Permissions
- Validation
- Board operations
- Card operations

Integration Tests

Integration tests should cover:

- API endpoints
- Database operations
- Authentication
- Authorization
- Workspace operations
- Board operations

End-to-End Tests

Critical user flows should include:

1. Sign in
2. Create a workspace
3. Create a board
4. Create lists
5. Create a card
6. Move a card between lists
7. Edit card details
8. Assign a member
9. Add a comment
10. Add a label
11. Invite a member

---

🔐 Security

The application should:

- Hash passwords securely
- Validate all API input
- Authorize every workspace operation
- Authorize every board operation
- Prevent unauthorized board access
- Protect against XSS attacks
- Protect against SQL injection
- Protect against CSRF where applicable
- Store secrets only in environment variables
- Rate-limit sensitive endpoints
- Validate uploaded files
- Follow the principle of least privilege
- Avoid exposing sensitive information in API responses

---

📁 Planned Project Structure

trello/
├── src/
│   ├── components/
│   ├── pages/
│   ├── features/
│   │   ├── auth/
│   │   ├── workspaces/
│   │   ├── boards/
│   │   ├── lists/
│   │   └── cards/
│   ├── hooks/
│   ├── services/
│   ├── utils/
│   ├── types/
│   └── App.tsx
│
├── public/
│
├── tests/
│   ├── unit/
│   ├── integration/
│   └── e2e/
│
├── .env.example
├── .gitignore
├── package.json
├── tsconfig.json
└── README.md

---

🔄 Card Workflow

The initial board workflow will use:

┌──────────────┐
│    To Do     │
└──────┬───────┘
       │
       ▼
┌──────────────┐
│  In Progress │
└──────┬───────┘
       │
       ▼
┌──────────────┐
│     Done     │
└──────────────┘

Cards can be moved between lists using drag and drop.

---

🎯 MVP Goals

The first working version should allow a user to:

1. Create an account
2. Sign in
3. Create a workspace
4. Create a board
5. Create lists
6. Create cards
7. Edit cards
8. Delete cards
9. Move cards between lists
10. Reorder cards
11. Search cards
12. View card details
13. Persist board data

The MVP should prioritize a clean, responsive, and easy-to-use Kanban experience.

---

🚧 Current Status

The project is currently in the planning and development stage.

Current Focus

- Project architecture
- Repository setup
- Frontend foundation
- Board UI
- List management
- Card management
- Drag-and-drop functionality

More features will be implemented incrementally according to the development roadmap.

---

🤝 Contributing

Contributions are welcome.

Development Workflow

1. Fork the repository.
2. Create a feature branch.

git checkout -b feature/your-feature

3. Make your changes.
4. Add or update tests.
5. Run linting and tests.

npm run lint
npm test

6. Commit your changes.

git commit -m "feat: add your feature"

7. Push the branch.

git push origin feature/your-feature

8. Open a pull request.

Keep pull requests focused and use descriptive commit messages.

---

📄 License

This project does not currently have a finalized license.

Add an appropriate open-source license before distributing the project publicly.