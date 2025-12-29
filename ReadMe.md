# AutoEcole - Car Rental Management System

## Project Overview

AutoEcole is a comprehensive car rental management platform developed as a full-stack web application with an accompanying Windows desktop client. The system provides an integrated solution for managing vehicle inventory, customer information, and rental transactions through both web-based and desktop interfaces. This dual-platform approach offers flexibility for different operational scenarios, allowing businesses to manage their car rental operations efficiently across multiple access points.

## Author

**Fahchouch Mohammed**
**Anas Lezaar**

## Technical Architecture

### Backend Infrastructure

The application is built on a modern Node.js stack utilizing Express.js as the core web framework. The backend architecture follows a modular design pattern with clear separation of concerns between routing, database operations, and business logic. The server runs on port 3000 and implements middleware for static file serving, body parsing, and template rendering.

The application uses MongoDB Atlas as its cloud-based database solution, providing scalability and remote accessibility. The database connection is established through Mongoose ODM (Object Data Modeling), which provides a structured schema-based approach to modeling application data with built-in validation and query building capabilities.

### Database Architecture

The system implements three primary data models representing the core entities of a car rental business:

**Client Schema**

- Stores customer information including full name (first and last name)
- Contact information with validated phone number field (maximum 10 digits)
- All fields are required to ensure data integrity

**Voiture (Vehicle) Schema**

- Comprehensive vehicle information including make, model, and color
- Registration details with license plate number (Matricule)
- Operational status tracking including current condition and availability
- Mileage tracking (Kil) for maintenance scheduling
- Pricing information per rental period
- Availability flag (Disp) indicating whether the vehicle is currently available
- Transmission type specification (Vitesse)
- Image storage capability with content type and binary data buffer for visual presentation

**Commande (Order) Schema**

- Relational references to Client and Vehicle collections using MongoDB ObjectIds
- Rental duration tracking in number of days (NJour)
- Calculated total price field (PTotale) for the complete rental transaction
- Implements MongoDB references to maintain data relationships and integrity

### Frontend Architecture

The presentation layer is constructed using EJS (Embedded JavaScript) templating engine, enabling server-side rendering with dynamic content injection. The template structure follows a component-based architecture with reusable modules for common UI elements.

**Component Structure:**

- **header.ejs**: Contains the HTML document declaration, meta tags for responsive viewport configuration, and CSS stylesheet links
- **nav.ejs**: Implements the main navigation header with logo, responsive hamburger menu, and navigation links for Home, Cars, About Us, and Contact sections
- **Begin.ejs**: Hero section featuring dynamic background image rotation between two variants (bg.jpg and bg-light.jpg) using JavaScript intervals, includes call-to-action button for vehicle reservations
- **cards.ejs**: Vehicle showcase section displaying available cars with representative images (Dacia Duster, Renault Clio, Audi A4)
- **footer.ejs**: Closing HTML tags and document structure completion

The main view (main.ejs) orchestrates these components in a logical flow, creating a cohesive single-page application experience.

### Styling and Responsive Design

The application implements comprehensive CSS styling with mobile-first responsive design principles. The stylesheet includes:

**Navigation Styling:**

- Fixed header with dark theme (#11101b background)
- Responsive hamburger menu for mobile devices (below 900px viewport width)
- Smooth transitions and hover effects on navigation elements
- Active state indication with contrasting colors

**Hero Section:**

- Full viewport height (100vh) hero banner with background image
- Centered text content with typographic hierarchy
- Responsive font sizing across different viewport breakpoints
- Dynamic background image rotation creating visual interest
- Call-to-action button with hover state transitions

**Vehicle Cards:**

- Flexbox-based grid layout with automatic wrapping
- Card hover effects with image scaling transformations
- Overlay text elements with category labels
- Consistent spacing using gap property for modern layout control

**Responsive Breakpoints:**

- 1320px: Initial responsive adjustments for medium screens
- 1100px: Further layout refinements
- 900px: Mobile layout activation with hamburger menu

### Routing System

The routing module (router.js) implements Express Router for handling HTTP requests:

**Defined Routes:**

- **GET /**: Root endpoint rendering the main view with sample vehicle data (Audi R8 demonstration)
- **GET \***: Wildcard route for 404 error handling, returning "Page Not Found" with appropriate HTTP status

The router also includes database query implementation using Mongoose's find() method to retrieve vehicle records, with results logged to console for debugging purposes.

### Desktop Application Component

The project includes a Visual Basic .NET desktop application targeting .NET 6.0 Framework for Windows:

**Application Structure:**

- Windows Forms-based GUI application named "BMCar"
- Form1 (Home) provides the main user interface with button controls
- MongoDB driver integration for database connectivity
- Uses the same MongoDB Atlas connection string for data consistency
- Compiled as a Windows executable (WinExe output type)

This desktop component allows for offline access and integration with Windows-specific features, providing an alternative interface for staff members who prefer traditional desktop applications.

## Dependencies and Package Management

### Node.js Dependencies:

**Core Framework:**

- **express** (^4.18.2): Web application framework providing routing, middleware, and HTTP utility methods
- **ejs** (^3.1.9): Embedded JavaScript templating for dynamic HTML generation

**Database Layer:**

- **mongodb** (^5.6.0): Official MongoDB driver for Node.js
- **mongoose** (^7.2.4): MongoDB object modeling tool with schema validation

**Middleware and Utilities:**

- **body-parser** (^1.20.2): Request body parsing middleware for POST requests
- **multer** (^1.4.5-lts.1): Middleware for handling multipart/form-data for file uploads
- **fs** (^0.0.1-security): File system operations wrapper

**Module System:**

- **esm** (^3.2.25): ECMAScript module loader for Node.js

**File Type Detection:**

- **file-type** (^18.5.0): Detect file type and MIME type
- **file-type-stream** (^1.0.0): Stream-based file type detection

## Database Configuration

**Connection Details:**

- Database Type: MongoDB Atlas (Cloud-hosted)
- Connection Protocol: MongoDB+srv (DNS seedlist connection)
- Database Name: AUTO
- Cluster: auto.cxriz3e.mongodb.net
- Connection Options:
  - useNewUrlParser: true (handles MongoDB connection string parsing)
  - useUnifiedTopology: true (uses new server discovery and monitoring engine)
  - retryWrites: true (enables automatic retry for write operations)
  - w: majority (write concern requiring acknowledgment from majority of replica set members)

## Project Structure Analysis

### Directory Organization:

**Root Level:**

- **app.js**: Application entry point and server initialization
- **package.json**: Project metadata and dependency management
- **ReadMe.md**: Project documentation

**database/**: Data access layer containing all database-related code

- **Connecting.js**: MongoDB connection establishment and configuration
- **Schema.js**: Mongoose schema definitions for all data models
- **Fdata.js**: Data fixtures or seed data imports (minimal implementation)

**img/**: Static image assets for vehicle presentations and background imagery

**public/style/**: Client-side styling assets

- **style.css**: Complete stylesheet with responsive design rules

**routes/**: Application routing logic

- **router.js**: Express router configuration with endpoint definitions

**views/**: EJS template files for server-side rendering

- **main.ejs**: Primary view orchestrating all component includes
- **Begin.ejs**: Hero section template with interactive JavaScript
- **cards.ejs**: Vehicle showcase section
- **nav.ejs**: Navigation header with responsive menu
- **components/**: Reusable partial templates
  - **header.ejs**: HTML document head and metadata
  - **footer.ejs**: Document closing tags

**VB app/AUTO/**: Windows desktop application

- **AUTO.sln**: Visual Studio solution file
- **AUTO.vbproj**: VB.NET project configuration
- **Form1.vb**: Main form code-behind with MongoDB integration
- **Form1.Designer.vb**: Generated form designer code
- **Form1.resx**: Form resource definitions
- **My Project/**: VB.NET project properties and application events
- **obj/**: Build artifacts and intermediate compilation files

## Current Implementation Status

The project represents an early-stage development with foundational infrastructure in place:

**Completed Features:**

- Database schema design and connection implementation
- Basic Express server configuration with routing
- Frontend template structure with responsive design
- Desktop application skeleton with database connectivity
- Static vehicle showcase with three example cars

**Partial Implementations:**

- Database querying (implemented but results only logged to console)
- Sample data rendering (hardcoded values in router)
- File upload infrastructure (Multer configured but not actively used)

**Development Opportunities:**

- Full CRUD operations for all entities (Create, Read, Update, Delete)
- Dynamic vehicle listing from database
- Booking system implementation with date range selection
- User authentication and authorization
- Payment processing integration
- Rental history and reporting features
- Vehicle availability calendar
- Admin dashboard for management operations
- Integration between web and desktop applications
- Image upload functionality for vehicles
- Search and filter capabilities
- Customer profile management

## Installation and Setup

### Prerequisites:

- Node.js (version 14.x or higher recommended)
- MongoDB Atlas account with configured cluster
- Visual Studio 2019 or later (for desktop application)
- .NET 6.0 SDK (for desktop application)

### Web Application Setup:

1. Install Node.js dependencies:

   ```bash
   npm install
   ```

2. Verify MongoDB connection string in database/Connecting.js and database/Schema.js

3. Start the development server:

   ```bash
   node app.js
   ```

4. Access the application at: http://localhost:3000

### Desktop Application Setup:

1. Navigate to VB app/AUTO directory
2. Open AUTO.sln in Visual Studio
3. Restore NuGet packages
4. Build and run the solution

## Configuration Notes

**Database Credentials:** The current implementation uses embedded credentials in the connection string. For production deployment, these should be moved to environment variables using a package like dotenv for security purposes.

**Port Configuration:** The application is configured to run on port 3000. This can be modified in app.js if a different port is required.

**Static File Serving:** Images are served from the img directory, and CSS files from the public/style directory through Express static middleware configuration.

## French Language Implementation

The application interface is designed for French-speaking users, with all UI text, labels, and content presented in French:

- "LOCATION NOM" (Rental Name)
- "MEILLEURE EXPÉRIENCE" (Best Experience)
- "Tout les Voitures" (All Cars)
- "À propos de nous" (About Us)
- "RÉSERVER UNE VOITURE" (Book a Car)

This localization makes the platform suitable for deployment in French-speaking markets or regions with French-speaking customer bases.

## Future Development Roadmap

To transform this foundation into a production-ready car rental system, the following enhancements are recommended:

1. **Backend API Development:** Implement RESTful API endpoints for all CRUD operations
2. **Authentication System:** Add user registration, login, and session management
3. **Booking Engine:** Create reservation system with date pickers and availability checking
4. **Payment Integration:** Implement payment gateway for online transactions
5. **Admin Panel:** Develop comprehensive administrative interface for operations management
6. **Customer Portal:** Create user accounts with booking history and profile management
7. **Reporting System:** Generate business intelligence reports on rentals, revenue, and fleet utilization
8. **Notification System:** Email/SMS confirmations for bookings and reminders
9. **Vehicle Management:** Complete vehicle lifecycle tracking including maintenance schedules
10. **Search and Filter:** Advanced search capabilities with multiple criteria
11. **Image Gallery:** Full vehicle photo galleries with upload management
12. **Mobile Responsiveness:** Enhanced mobile experience with touch-optimized interactions
13. **Multi-language Support:** Expand beyond French to support multiple languages
14. **API Documentation:** Generate comprehensive API documentation using tools like Swagger
15. **Testing Suite:** Implement unit tests, integration tests, and end-to-end tests

## Technology Stack Summary

**Frontend:** HTML5, CSS3, JavaScript (ES6+), EJS Templating
**Backend:** Node.js, Express.js
**Database:** MongoDB Atlas with Mongoose ODM
**Desktop:** Visual Basic .NET 6.0, Windows Forms
**Development Tools:** npm, Visual Studio
**Version Control:** Git (repository: fahchouchsm/AutoEcole)

## License

ISC License

---

This project demonstrates full-stack development capabilities with both web and desktop application integration, modern database design, and responsive frontend implementation. The modular architecture allows for straightforward expansion and feature addition as business requirements evolve.
