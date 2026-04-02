# 3DS eShop Clone

A web-based Nintendo 3DS eShop clone with file management, QR code generation, homebrew support, and FBI seed management.

## Description

This project recreates the Nintendo 3DS eShop experience as a web application. Browse games, DLC, apps, Virtual Console titles, and homebrew applications. Upload and download files with automatic QR code generation for easy installation via FBI on a modded 3DS console.

## Features

### Content Sections
- **Home** - Featured carousel, featured games, and recent homebrew
- **Games** - 3DS game library with region filtering (USA/EUR/JPN)
- **DLC** - Downloadable content for games
- **Apps** - System applications
- **Virtual Console** - Classic games with system filtering (NES, SNES, Game Boy, GBC, GBA, N64, Genesis)
- **Homebrew** - Community apps (emulators, utilities, games, themes, CFW tools)
- **Seeds** - FBI seed database for CIA installation
- **Hack Guide** - 3DS hacking guides and tutorials
- **Upload** - File upload interface

### File Management
- Upload CIA, 3DSX, 3DS, ZIP files (up to 5GB)
- Automatic SHA256 hash calculation
- Download count tracking
- Product code support (CTR-P-XXXX format)
- Title ID support
- Uploaded by user tracking
- Block size display (1 block = 128KB)
- Files organized by category in data folder

### QR Code System
- Generate QR codes for any title
- Scan with FBI for remote installation
- Download QR code as PNG image
- Copy direct download links

### Admin Panel (`/admin.html`)
- Dashboard with statistics cards
- Activity charts (Chart.js)
  - Uploads & Downloads (7 days)
  - Files by category (doughnut)
  - Uploads by user (bar)
- File management (edit, delete)
- Activity logs with filtering
- Uploaders leaderboard
- Most downloaded files

### 3DS Hack Guide
- Getting Started guide
- CFW installation instructions
- FBI usage tutorial
- FAQ section

### Additional Features
- Dark mode toggle with persistence
- Search across all titles
- Region filtering
- Game icons from GitHub repository
- Responsive design (Bootstrap 5)
- Toast notifications
- Loading indicators

## Installation

### Prerequisites
- Node.js 16+ ([download](https://nodejs.org/))
- npm (included with Node.js)

### Steps

1. Clone or download the repository:
```bash
git clone https://github.com/your-username/3ds-eshop-clone.git
cd 3ds-eshop-clone
```

2. Install dependencies:
```bash
npm install
```

3. Start the server:
```bash
npm start
```

4. Open in browser:
- **eShop:** http://localhost:4000
- **Admin Panel:** http://localhost:4000/admin.html

### Development Mode
For auto-restart on file changes:
```bash
npm run dev
```

## Default Admin Credentials
- **Username:** `admin`
- **Password:** `admin123`

Change these after first login via the profile dropdown.

## File Structure

```
3ds-eshop-clone/
├── server.js           # Express backend server
├── index.html          # Main eShop frontend
├── admin.html          # Admin panel
├── package.json        # Dependencies
├── README.md           # This file
├── css/
│   └── styles.css      # Custom styles + dark mode
├── js/
│   └── app.js          # Frontend logic
└── data/
    ├── db/             # JSON database files
    │   ├── files.json
    │   ├── logs.json
    │   ├── stats.json
    │   └── seeds.json
    ├── games/          # Game CIA files
    ├── dlc/            # DLC files
    ├── apps/           # App files
    ├── virtual-console/
    │   ├── nes/
    │   ├── snes/
    │   ├── gb/
    │   ├── gbc/
    │   ├── gba/
    │   ├── n64/
    │   └── genesis/
    ├── homebrew/
    │   ├── emulators/
    │   ├── utilities/
    │   ├── games/
    │   ├── themes/
    │   └── tools/
    └── seeds/          # Seed files
```

## API Endpoints

### Files
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/files` | List files (paginated, filterable) |
| GET | `/api/files/:id` | Get file details |
| POST | `/api/files/upload` | Upload new file |
| PUT | `/api/files/:id` | Update file metadata |
| DELETE | `/api/files/:id` | Delete file |
| GET | `/api/download/:id` | Download file (tracks count) |

### Seeds
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/seeds` | List seeds (paginated, searchable) |
| GET | `/api/seeds/stats` | Get seed statistics |
| GET | `/api/seeds/:titleId` | Get seed by title ID |
| GET | `/api/seeds/:titleId/download` | Download seed .dat file |
| GET | `/api/seeds/:titleId/qr` | Get QR code info |
| POST | `/api/seeds/refresh` | Refresh from external sources |
| POST | `/api/seeds/upload` | Upload seeddb.bin |

### Statistics & Logs
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/stats` | Get comprehensive statistics |
| GET | `/api/stats/uploads` | Get upload chart data |
| GET | `/api/logs` | Get activity logs |
| DELETE | `/api/logs` | Clear all logs |

## Using with FBI

### Installing CIA Files
1. Open FBI on your 3DS
2. Go to **Remote Install**
3. Select **Scan QR Code**
4. Point camera at the QR code from the eShop

### Installing Seeds
Seeds are required for some CIA files to run:
1. Go to the **Seeds** section
2. Find the title ID
3. Scan QR code or download the .dat file
4. Seeds are saved to `sd:/fbi/seed/<titleid>.dat`

## Sample Data

The app includes sample data for:
- 12 3DS games (with icons and product codes)
- 5 DLC packs
- 6 system apps
- 15 homebrew applications
- 50+ Virtual Console titles across 7 systems
- 1800+ FBI seeds

## Technologies Used

| Component | Technology |
|-----------|------------|
| Frontend | HTML5, CSS3, JavaScript |
| UI Framework | Bootstrap 5.3.2 |
| Icons | Bootstrap Icons |
| Charts | Chart.js |
| QR Codes | QRCode.js |
| Backend | Node.js, Express 4 |
| File Upload | Multer |
| Database | JSON files |
| Logging | Morgan |

## Credits

- **Icons:** [3DS Game Icons](https://github.com/wildfirebill-nintendo-3ds/3dsgamesicons)
- **Seeds:** [3DS-rom-tools](https://github.com/ihaveamac/3DS-rom-tools)
- **Hack Guide:** [3ds.hacks.guide](https://3ds.hacks.guide)

## License

MIT License
