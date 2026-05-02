# Employee Break Scheduler & PTO Tracker

A modern, feature-rich web application for scheduling and managing employee breaks with **user authentication**, real-time timeline visualization, conflict detection, personalized alarm notifications, integrated PTO (Paid Time Off) tracking system, and **automated shift-end voice announcements**.

**🔥 Latest Update (April 20, 2026)**: Automated voice announcement at 8 PM shift end!

**Previous Update (March 30, 2026)**: Critical fixes for PTO approval, background tab alarms, and smart break type auto-selection!

---

## 📚 Documentation

**New to this project?** Start with the guides below:

**🔥 NEW - Critical Fixes:**
- 🛠️ **[Critical Fixes Complete](CRITICAL_FIXES_COMPLETE.md)** - Latest bug fixes and new features (MUST READ!)
- 🧪 **[Quick Testing Guide](TESTING_GUIDE_QUICK.md)** - Test all fixes in 20 minutes

**Essential Guides:**
- 📖 **[Quick User Guide](QUICK_USER_GUIDE.md)** - 30-second start guide for all users
- 📋 **[Final Implementation Status](FINAL_IMPLEMENTATION_STATUS.md)** - Complete feature list and testing results
- ✅ **[Options 2 & 3 Complete](OPTIONS_2_3_COMPLETE.md)** - Grouped breaks & PTO tracker details
- 🔐 [Authentication Guide](AUTHENTICATION.md) - User login system and personalized notifications

**Additional Resources:**
- 🚀 [Quick Start Guide](QUICKSTART.md) - Get started in 3 minutes
- 🔔 [Alarm Features](ALARM_FEATURES.md) - Technical deep dive into alarm system
- 🧪 [Testing Guide](TESTING.md) - How to test and troubleshoot
- 📝 [Changes Summary](CHANGES.md) - What was implemented and why

---

## 🌐 Live Demo

Access your deployed website through the **Publish tab** to get your live URL.

## ✨ Features

### Currently Completed Features

#### 📢 Automated Voice Announcements (NEW! - April 20, 2026)

**Shift-End Announcement (8:00 PM Daily)**:
- **Train Station Chime**: Nostalgic 4-tone Westminster bell before announcement
- **Automatic Playback**: Plays at 8:00 PM every day without user action
- **BambooHR Reminder**: "End of shift. If you need to take overtime, please file OT. Please do not forget to logout to your Bamboo HR after shift."
- **Triple Repetition**: Repeats 3 times with 2-second gaps
- **Female Voice**: Natural text-to-speech synthesis

**Random Ticket Reminders (2x per shift)**:
- **Smart Scheduling**: 2 random times generated daily between 12 PM - 8 PM
- **Work Reminder**: "If not busy, please work on your pending tickets."
- **Single Play**: Each reminder plays once (no repetition)
- **Train Station Chime**: Same nostalgic 4-tone bell before message
- **Different Daily**: New random times each day

**Features**:
- ✅ All users hear announcements simultaneously
- ✅ No duplicates (localStorage tracking)
- ✅ Browser-based (no server needed)
- ✅ Professional audio quality

**⚠️ Note**: Page must be open for announcements to play. Keep browser tab active during work hours.

#### 🔐 User Authentication System
- **Login Screen**: Full-screen profile selection with photos
- **7 User Profiles**: June, Mary, Angel, Jay, Charist, Noel, Drich
- **Session Persistence**: Login survives page refresh via localStorage
- **Auto-Fill Names**: Logged-in user's name automatically fills booking form
- **User Badge**: Header displays current user with profile photo
- **Logout Functionality**: Explicit logout button to switch users
- **Personalized Notifications**: Each user only receives their own break alarms

#### 🔔 Enhanced Alarm System
- **Personalized Alarms**: Only notify the logged-in user for their breaks
- **Break Start Alert**: Notification when user's break begins
- **Break End Warning**: Alarm 30 seconds before break ends (at 14:30 mark)
- **Continuous Audio**: Two-tone alarm pattern (880Hz/1100Hz) until dismissed
- **Visual Alerts**: Modal popup with animated ringing bell icon
- **Desktop Notifications**: Windows/browser notification API integration
- **Toast Messages**: Non-intrusive corner notifications
- **No Cross-User Interference**: Other users' breaks don't trigger alarms

#### 📊 Timeline Visualization
- **Interactive Timeline View**: Visual representation of breaks from 12 PM to 8 PM (8-hour shift)
- **Precise Time Alignment**: Red line showing current time position with exact accuracy
- **Multi-Row Layout**: Automatically arranges overlapping breaks in separate rows
- **Active Break Highlighting**: Pulsing animation for breaks currently in progress
- **Smooth Scrolling**: Timeline automatically scrolls to current time on load

#### 📅 Break Management
- **Book Breaks**: Schedule breaks for employees with name, type, date, and time
- **Two Break Types**: 
  - Break 1 (☕) - Teal/turquoise color
  - Break 2 (🍵) - Orange color
- **🆕 Smart Break Type Auto-Selection**: System automatically suggests the next break type based on what you've already taken today
  - First break of the day → defaults to Break 1 ☕
  - After Break 1 → suggests Break 2 🍵
  - After Break 2 → suggests Break 1 ☕
  - Multiple breaks → suggests the less frequent type
  - Manual override still available
- **15-Minute Duration**: All breaks are standardized to 15 minutes
- **Conflict Detection**: Prevents double-booking of time slots
- **Validation**: Ensures breaks are within working hours (6 AM - 10 PM)
- **Delete Functionality**: Remove breaks with hover-to-reveal delete button

#### 📈 Statistics Dashboard
- **Total Breaks Today**: Count of all breaks for the selected date
- **Break Type Breakdown**: Separate counts for Break 1 and Break 2
- **Employee Count**: Number of unique employees with breaks scheduled
- **Real-Time Updates**: Stats update automatically when breaks are added/removed

#### 📆 Date Navigation
- **Previous/Next Day**: Navigate through dates with arrow buttons
- **Today Button**: Quickly return to current date
- **Friendly Date Display**: Shows "Today", "Tomorrow", "Yesterday" or full date

#### 🔔 Alarm System
- **🆕 Background Tab Support**: Alarms now work even when the tab is not active or window is minimized!
  - Multiple redundant audio systems (Web Audio API + HTML5 Audio)
  - Aggressive AudioContext resume before every beep
  - Window focus attempts to bring tab to front
  - Works in background tabs, minimized windows, and inactive applications
- **Continuous Audio Alert**: Web Audio API-based alarm that runs until dismissed
- **Enhanced Two-Tone Pattern**: Square wave oscillators at 1200 Hz / 900 Hz (louder and more attention-grabbing)
- **Increased Volume**: 0.7 gain for better audibility
- **Faster Beeps**: 400ms intervals with 300ms beep duration
- **Smooth Fade-Out**: 300ms fade when dismissed
- **Animated Bell Icon**: Ringing bell animation while alarm is active
- **Modal Lock**: Dialog cannot be dismissed by clicking outside - only "Dismiss Alarm" button stops it
- **Windows Notifications**: Pop-up desktop notification using Notification API (works in background!)
- **Toast Notifications**: Non-intrusive corner notifications
- **Session Memory**: Prevents duplicate alarms during same session
- **Auto-Permission Request**: Requests notification permission on first page load
- **Break End Warning**: Second alarm fires 30 seconds before break ends

#### 📋 Schedule List (Grouped by User)
- **Profile Cards**: Displays breaks grouped by user with profile pictures
- **Break Count**: Shows total breaks per user ("2 breaks")
- **Vertical Stack**: All breaks for a user shown in one card
- **Color-Coded**: Visual indicators matching break types (Break 1: teal, Break 2: orange)
- **Individual Delete**: Hover to reveal delete button for each break
- **Alphabetically Sorted**: Users displayed in alphabetical order
- **Current Shift Only**: Shows only today's scheduled breaks
- **Responsive Grid**: Adapts to screen size
- **Empty State**: Friendly message when no breaks are scheduled

#### 💾 Data Persistence
- **Cloud Database Storage**: All break data saved to server database
- **Multi-Device Sync**: Access same schedule from any computer/device
- **Auto-Refresh**: Data syncs automatically every 30 seconds
- **Real-Time Updates**: Changes immediately reflected across all devices
- **RESTful API Integration**: Professional backend data management
- **Automatic Saving**: All changes instantly saved to server
- **Reset Functionality**: Clear all data with confirmation modal
- **localStorage**: Session persistence and PTO data storage

#### 📅 PTO Tracker System (Integrated)
- **Glowing Navigation Button**: Neon yellow (#EFFF00) button with corner animations
- **Monthly Calendar View**: Team schedule with color-coded days
  - 🟢 Green: On Duty
  - ⚪ Grey: Rest Day
  - 🟡 Yellow: Approved PTO
- **Month Navigation**: Previous/Next buttons to view different months
- **PTO Request System**: Users can request time off with mandatory explanations
- **June's Auto-Approval**: Admin (June) bypasses approval for self
- **🆕 Password-Protected Approvals**: June sets password on first approval - **NOW WORKING!**
  - ✅ Approval executes immediately after password entry
  - ✅ Notifications disappear from June's list instantly
  - ✅ Calendar updates in real-time (turns yellow)
  - ✅ Users receive approval notifications automatically
- **Locked Notifications**: Requests must be approved or declined (cannot dismiss)
- **Approve Workflow**: Password verification → Success message → Calendar turns yellow → User notified with DEEL message
- **Decline Workflow**: Mandatory explanation required → User notified with reason
- **Universal Retraction**: 
  - June can retract team PTO (password + explanation)
  - June can retract own PTO (no password/explanation)
  - Users can retract own PTO (no password/explanation)
- **Original Color Reversion**: Retracted dates return to roster color
- **🆕 Break Alarms on PTO Page**: Break alarms also fire when viewing the PTO tracker
- **Separate Application**: Accessible via glowing button in header

#### 🎨 User Interface
- **Dark Theme**: Modern dark color scheme with purple/teal accents
- **Responsive Design**: Works on desktop, tablet, and mobile devices
- **Smooth Animations**: Hover effects, transitions, and visual feedback
- **Modal Dialogs**: Conflict warnings, alarms, and confirmations
- **Toast Notifications**: Success, error, and info messages
- **Live Clock**: Real-time clock display in header (12-hour format)

#### ⚡ User Experience
- **Form Validation**: Visual feedback for missing or invalid fields
- **Shake Animation**: Input fields shake when validation fails
- **Hover Effects**: Interactive feedback on buttons and break blocks
- **Keyboard Support**: Press Enter to submit booking form
- **Tooltips**: Hover over break blocks for full details
- **Auto-scroll**: Timeline centers on current time for today's view

## 🚀 Functional Entry URIs

### Main Applications
- **`/` or `/index.html`**: Break Scheduler - Main application page (includes automatic 8 PM shift-end announcement)
- **`/pto-tracker.html`**: PTO Tracker - Paid time off management system

### Break Scheduler Features Access
All features are accessible from the single-page application:
- **Login Screen**: Full-screen profile selection (first load or after logout)
- **Timeline View**: Main card showing 12 PM - 8 PM shift
- **Booking Form**: "Book a Break" card with auto-filled name
- **Schedule List**: "All Scheduled Breaks" card with grouped profile cards
- **Statistics**: Four stat cards showing daily metrics
- **PTO Tracker Button**: Glowing yellow button in header
- **Automatic Shift-End Announcement**: Plays at 8:00 PM daily (NEW!)

### PTO Tracker Features Access
- **Team Calendar**: Monthly grid view with color-coded days
- **Request Form**: PTO request submission with reason field
- **Pending Requests** (June only): Approve/decline notifications
- **Month Navigation**: Previous/Next buttons

### No Query Parameters Required
Both applications are fully self-contained and don't require URL parameters.

## 📦 Data Storage

### Cloud Database (RESTful API)

#### Breaks Table
- **Table**: `breaks`
- **API Endpoint**: `tables/breaks`
- **Format**: JSON records with system fields
- **Schema**: 
  ```json
  {
    "id": "unique_id",
    "name": "Employee Name",
    "type": "Break 1" or "Break 2",
    "date": "YYYY-MM-DD",
    "startMinutes": 540,
    "created_at": 1234567890,
    "updated_at": 1234567890,
    "gs_project_id": "project_id",
    "gs_table_name": "breaks"
  }
  ```



### Multi-Device Synchronization
- **Automatic Sync**: Data refreshes every 30 seconds
- **Cross-Device**: Access from any computer or device
- **Real-Time**: Changes appear immediately on all devices
- **Conflict-Free**: Server manages data consistency

### Browser Storage (localStorage)
Used for PTO Tracker and session management:
- **`currentUser`**: Current logged-in user (shared between both apps)
- **`ptoRequests`**: Pending PTO requests array
- **`approvedPTO`**: Approved PTO records array
- **`junePassword`**: June's admin password (encrypted)

**Note**: PTO data is stored locally and not synced across devices. Future versions will use cloud database for PTO data.

## 🎯 How to Use

### Logging In
1. Open the website
2. Login screen displays with 7 employee profiles
3. Click on your profile photo/card
4. System logs you in and displays main scheduler
5. Your name appears in header badge
6. Booking form auto-fills with your name

### Booking a Break (When Logged In)
1. Name field is automatically filled with your username (read-only)
2. Select break type (Break 1 or Break 2)
3. Choose date (defaults to today)
4. Select start time (defaults to next 15-min interval)
5. Click "Book Break" button

### Receiving Notifications
- **Break Start**: When your break begins, you'll receive:
  - Continuous audio alarm
  - Modal popup with details
  - Desktop notification (if permitted)
  - Toast message
- **Break End Warning**: 30 seconds before your break ends:
  - Second alarm triggers
  - "Break ending soon!" message
  - Countdown notification
- **Other Users**: Will NOT be notified of your breaks

### Logging Out
1. Click "Logout" button in header (red button)
2. Login screen reappears
3. Select different user or same user to log back in

### Viewing Breaks
- **Timeline**: Visual representation with color-coded blocks
- **Schedule List**: Detailed list below the form
- **Statistics**: Quick overview in stat cards

### Navigating Dates
- Use ◂ and ▸ buttons to navigate days
- Click "Today" to return to current date
- Timeline automatically shows current time indicator for today

### Deleting Breaks
- **From Timeline**: Hover over break block, click ✕ button
- **From List**: Click 🗑 button on the right side of each item

### Resetting Data
1. Click "Reset All Data" button (red button)
2. Confirm in the modal dialog
3. All breaks will be permanently deleted

### Using PTO Tracker

#### Accessing PTO Tracker
1. Look for the **glowing yellow "📅 PTO Tracker" button** in the header
2. Click it to open the PTO Tracker application
3. Your login session carries over (same user)

#### For Standard Users (Non-June)
1. **View Team Calendar**: See everyone's schedule with color codes
   - 🟢 Green = On Duty
   - ⚪ Grey = Rest Day
   - 🟡 Yellow = Approved PTO
2. **Request PTO**: 
   - Click a date on the calendar
   - Enter reason (MANDATORY - cannot skip)
   - Click "Submit Request"
   - Wait for June's approval
3. **Retract Your Own PTO**:
   - Click your yellow (approved) PTO date
   - Confirm retraction
   - No password or explanation needed

#### For June (Admin)
1. **File Your Own PTO**:
   - Click a date
   - Click "Submit Request"
   - Instantly approved (no reason needed)
   - Date turns yellow immediately

2. **Review Pending Requests**:
   - Scroll to "Pending Requests" section
   - See each request with user, date, and reason

3. **Approve Request**:
   - Click "Approve" button
   - First time: Set admin password
   - Subsequent times: Enter password
   - See message: "Approved, you can file this on Deel."
   - Calendar turns yellow

4. **Decline Request**:
   - Click "Decline" button
   - Enter explanation (MANDATORY)
   - Request is declined and user notified

5. **Retract Team PTO**:
   - Click any yellow (team member's) date
   - Enter admin password
   - Enter explanation (MANDATORY)
   - Date reverts to original roster color

6. **Retract Your Own PTO**:
   - Click your yellow date
   - Confirm retraction
   - No password/explanation needed
   - Date reverts to original color

#### Month Navigation
- Click **◀ Previous** to view previous month
- Click **▶ Next** to view next month
- Calendar updates with correct color coding

## 📚 Additional Documentation

This project includes comprehensive documentation:

- **[QUICK_USER_GUIDE.md](QUICK_USER_GUIDE.md)**: 30-second quick start guide for all users
  - Getting started in 3 clicks
  - Break scheduler how-to
  - PTO tracker how-to
  - Pro tips and common scenarios
  - Troubleshooting guide
  - Best practices

- **[FINAL_IMPLEMENTATION_STATUS.md](FINAL_IMPLEMENTATION_STATUS.md)**: Complete status report
  - All completed features
  - Testing results (all 14 tests passed)
  - File structure and technical stack
  - Performance metrics
  - Support and troubleshooting

- **[OPTIONS_2_3_COMPLETE.md](OPTIONS_2_3_COMPLETE.md)**: Detailed feature documentation
  - Grouped schedule breaks implementation
  - PTO Tracker system (all 7 requirements)
  - Visual design examples
  - Testing results

- **[AUTHENTICATION.md](AUTHENTICATION.md)**: Complete user authentication system guide
  - User login and profile management
  - Session persistence and recovery
  - Personalized notification system
  - Auto-fill form functionality
  - Security considerations
  - Testing checklist and troubleshooting

- **[MULTI_DEVICE_SYNC.md](MULTI_DEVICE_SYNC.md)**: Multi-device synchronization explained
  - Cloud database storage
  - Real-time sync features
  - API integration details
  - Cross-device collaboration
  - Troubleshooting sync issues

- **[ALARM_FEATURES.md](ALARM_FEATURES.md)**: Deep dive into the enhanced alarm system
  - Web Audio API implementation details
  - Two-tone alternating pattern specifications
  - Modal lock behavior
  - Animated bell icon mechanics
  - Windows notification integration
  - Error handling and state management

- **[TESTING.md](TESTING.md)**: Complete testing guide
  - Quick test instructions
  - Feature verification checklist
  - Browser compatibility testing
  - Troubleshooting common issues
  - Quality assurance checklist

## 🛠️ Technical Details

### Technologies Used
- **HTML5**: Semantic structure
- **CSS3**: Modern styling with CSS variables, animations, flexbox, grid
- **Vanilla JavaScript**: No dependencies, pure JavaScript with async/await
- **RESTful API**: Cloud database for multi-device sync
- **Web Audio API**: Continuous oscillator-based alarm sound with triangle waveform
- **Notification API**: Windows/desktop pop-up notifications for break alerts

### Browser Compatibility
- Modern browsers (Chrome, Firefox, Safari, Edge)
- Requires JavaScript enabled
- Requires internet connection for data sync
- Web Audio API for alarm sounds (required for audio alerts)
- Notification API for Windows/desktop notifications (optional but recommended)

### Performance Features
- **Efficient Rendering**: Only re-renders when data changes
- **Optimized Timeline**: Greedy algorithm for row assignment
- **Minimal DOM Manipulation**: Updates only necessary elements
- **Lightweight**: No external dependencies, small file size

## 🎨 Color Scheme

### Primary Colors
- **Background**: `#0f1117` (Dark blue-black)
- **Surface**: `#1a1d2e` (Dark blue-gray)
- **Accent**: `#6c63ff` (Purple)
- **Break 1**: `#4ecdc4` (Teal/turquoise)
- **Break 2**: `#ff9f43` (Orange)

### Status Colors
- **Success**: `#2ed573` (Green)
- **Warning**: `#ffa502` (Orange)
- **Danger**: `#ff4757` (Red)
- **Current Time**: `#ff4757` (Red line)

## 🔮 Features Not Yet Implemented

### Potential Future Enhancements
1. **Break Duration Options**: Allow customizable break lengths (15, 30, 45 minutes)
2. **Enhanced Employee Profiles**: Advanced preferences and settings
3. **Break History**: View past breaks with analytics
4. **Export/Import**: Export schedule to CSV, import from file
5. **Recurring Breaks**: Schedule repeating breaks (daily, weekly)
6. **Team Management**: Organize employees by departments/teams
7. **Notifications Settings**: Customize alarm timing (5 min before, etc.)
8. **Print View**: Printer-friendly schedule format
9. **Multi-Day View**: Week or month calendar view
10. **Break Notes**: Add notes or comments to breaks
11. **Email Notifications**: Send reminders via email
12. **Mobile App**: Native iOS/Android applications
13. **Dev Panel (Jay)**: Add/delete/edit profiles with password 5537
14. **Admin Dashboard**: Enhanced management panel for supervisors
15. **Break Swap**: Allow employees to swap breaks
16. **Overtime Tracking**: Integration with time tracking
17. **Calendar Integration**: Sync with Google/Outlook calendars
18. **Dark/Light Theme Toggle**: User preference for color scheme
19. **Deel Integration**: Automatic PTO filing integration

### ✅ Recently Implemented (v3.1)
- ✅ **Multi-User Authentication**: 7 user profiles with photos
- ✅ **Session Persistence**: Login survives page refresh
- ✅ **User-Specific Alarms**: Only logged-in user receives notifications
- ✅ **Grouped Schedule Display**: Profile cards with all breaks per user
- ✅ **PTO Tracker System**: Full paid time off management
- ✅ **Password-Protected Approvals**: June's admin security
- ✅ **12 PM - 8 PM Timeline**: 8-hour shift view
- ✅ **Precise Time Alignment**: Exact current-time indicator

## 📝 Recommended Next Steps

### Immediate Improvements (Phase 2)
1. **Dev Panel for Jay** - Password-protected profile management (password: 5537)
2. **Implement undo functionality** - Restore accidentally deleted breaks
3. **Add keyboard shortcuts** - Quick navigation and booking
4. **Improve mobile responsiveness** - Optimize for smaller screens

### Medium-Term Goals (Phase 3)
1. **Break History & Analytics** - Usage patterns and insights
2. **Notification Customization** - Allow users to configure alarm timing
3. **Email/SMS Integration** - Alternative notification methods
4. **Deel Integration** - Automatic PTO filing

### Long-Term Vision (Phase 4)
1. **Enterprise Features** - Role-based access, compliance reporting
2. **Integration APIs** - Connect with HR and scheduling systems
3. **Machine Learning** - Predict optimal break times based on patterns
4. **Mobile Applications** - Native apps for iOS and Android

## 🐛 Known Limitations

1. **Internet Required**: Requires connection for data sync across devices (PTO Tracker works offline with localStorage)
2. **Single Break Type Per Slot**: Can't have overlapping breaks at the same time
3. **Fixed Break Duration**: All breaks are 15 minutes
4. **No Timezone Support**: Uses local browser time
5. **30-Second Sync Delay**: Changes may take up to 30 seconds to appear on other devices
6. **Client-Side PTO Data**: PTO requests stored in localStorage (not synced across devices)
7. **localStorage Dependency**: Session data stored in browser (clearing cache logs out users)

## 📄 License

This project is provided as-is for demonstration and educational purposes.

## 🙏 Credits

- **Design**: Modern dark UI inspired by contemporary scheduling apps
- **Icons**: Emoji icons for visual clarity
- **Fonts**: System fonts for optimal performance

## 📞 Support

For questions or issues:
1. Check the application's built-in help tooltips
2. Review this README documentation
3. Test in different browsers if issues occur
4. Clear browser cache and LocalStorage if experiencing data issues

---

**Note**: To deploy this application online, use the **Publish tab** in your development environment to get a live URL that you can share with others.
