# Ordinals Art Marketplace - Comprehensive Site Outline

This document provides a detailed breakdown of every page, component, and feature in the Ordinals Art Marketplace application, including all copy requirements and UI elements.

## Table of Contents

1. [Home Page](#1-home-page-)
2. [Artist Dashboard](#2-artist-dashboard-artist)
3. [Gallery Dashboard](#3-gallery-dashboard-gallery)
4. [Benefactor Dashboard](#4-benefactor-dashboard-benefactor)
5. [NFT Marketplace](#5-nft-marketplace-marketplace)
6. [Governance Portal](#6-governance-portal-governance)
7. [Reputation Center](#7-reputation-center-reputation)
8. [Community Hub](#8-community-hub-community)
9. [User Profile](#9-user-profile-profileid)
10. [Showcase](#10-showcase-showcase)
11. [Global Components](#11-global-components)

---

## 1. **Home Page** (`/`)

### Purpose
Main landing page and entry point for all users

### Key Elements

#### Header Section
- **Logo**: "The Nursery" branding
- **Tagline**: "A decentralized ecosystem connecting Artists, Galleries, and Benefactors through Bitcoin Ordinals"
- **Navigation**: Links to main sections (hidden until wallet connected)

#### Wallet Connection Section
- **Title**: "Connect Your Wallet to Get Started"
- **MetaMask Button**: 
  - Text: "Connect MetaMask"
  - Subtext: "For Ethereum transactions"
  - Icon: MetaMask fox logo
- **Xverse Button**:
  - Text: "Connect Xverse"
  - Subtext: "For Bitcoin Ordinals"
  - Icon: Xverse logo
- **Status Indicator**: Shows connection status and address when connected

#### Role Selection Cards
- **Section Title**: "Choose Your Role in The Nursery"
- **Cards Layout**: 2x2 grid

1. **Benefactor Card**
   - Title: "Become a Benefactor"
   - Description: "Provide liquidity to support artists and earn rewards through our unique governance system"
   - Benefits List:
     - "Earn trading fees from marketplace activity"
     - "Get discounted minting rates"
     - "Participate in platform governance"
   - CTA Button: "Enter as Benefactor"

2. **Gallery Card**
   - Title: "Create a Gallery"
   - Description: "Curate collections, host virtual exhibitions, and connect with talented artists"
   - Benefits List:
     - "Deploy your own gallery smart contract"
     - "Earn commissions on sales"
     - "Build your curatorial reputation"
   - CTA Button: "Enter as Gallery"

3. **Artist Card**
   - Title: "Join as Artist"
   - Description: "Create Bitcoin Ordinals, showcase your work, and connect with collectors"
   - Benefits List:
     - "Mint artwork as Bitcoin Ordinals"
     - "Access to global collector base"
     - "Collaborative project tools"
   - CTA Button: "Enter as Artist"

4. **Marketplace Card**
   - Title: "Browse Marketplace"
   - Description: "Discover and collect unique digital art from verified artists"
   - Benefits List:
     - "Secure blockchain transactions"
     - "Direct artist support"
     - "Exclusive collections"
   - CTA Button: "Enter Marketplace"

#### Feature Highlights Section
- **Title**: "Platform Features"
- **Grid of Features**:
  - "Cross-chain Integration" - Bitcoin Ordinals + Ethereum Smart Contracts
  - "Decentralized Governance" - Community-driven decision making
  - "Reputation System" - Build trust and earn rewards
  - "TEE Oracle Security" - Secure cross-chain communication

#### Footer Links
- Governance Portal
- Reputation Center
- Community Hub
- Documentation
- About The Nursery

### Copy Requirements
- Welcome messaging that explains the platform
- Role-specific value propositions
- Clear CTAs for each user type
- Technical feature explanations in simple terms
- Trust and security messaging

---

## 2. **Artist Dashboard** (`/artist`)

### Purpose
Central hub for artists to manage their creative work and business

### Navigation Tabs
- Overview | Profile | Create Ordinal | My Artworks | Collaborations | Governance | Chain Sync

### Tab Details

#### Overview Tab
**Stats Dashboard**
- Card 1: "Total Artworks" - Number with trend indicator
- Card 2: "Total Sales" - ETH/BTC value with USD equivalent
- Card 3: "Active Collaborations" - Count with status
- Card 4: "Governance Power" - Voting weight display

**Revenue Chart**
- Title: "Revenue Over Time"
- Toggle: Monthly/Weekly/Daily view
- Chart Type: Line graph with ETH and BTC values

**Recent Activity Feed**
- Title: "Recent Activity"
- Items:
  - "New bid on [Artwork Name] - [Amount] ETH"
  - "[User] started following you"
  - "Sale completed for [Artwork Name]"
  - "Collaboration invite from [Gallery Name]"

**Quick Actions**
- Button: "Create New Ordinal"
- Button: "List Artwork"
- Button: "Check Messages"
- Button: "View Analytics"

#### Profile Tab
**Profile Editor Form**
- **Display Name**: Text input with validation
- **Bio**: Rich text editor (500 char limit)
- **Avatar**: Image upload with preview
- **Cover Image**: Banner upload
- **Social Links**:
  - Twitter/X handle
  - Instagram username
  - Personal website
  - Discord ID
- **Verification Section**:
  - KYC Status indicator
  - Wallet verification badge
  - Email verification (optional)
- **Save Button**: "Update Profile"

**Portfolio Display**
- Title: "Your Portfolio"
- View Toggle: Grid/List
- Sort Options: Recent/Popular/Price
- Artwork Cards showing:
  - Thumbnail
  - Title
  - Status (Listed/Sold/Draft)
  - Price/Last Sale

#### Create Ordinal Tab (`/artist/create`)
**Creation Form**
- **Title**: "Create New Bitcoin Ordinal"
- **Artwork Details**:
  - Title: Text input (required)
  - Description: Text area (1000 chars)
  - Category: Dropdown (Digital Art, Photography, Generative, etc.)
- **File Upload**:
  - Drag-drop zone
  - Supported formats: JPG, PNG, GIF, MP4
  - Max size: 50MB
  - Preview panel
- **Metadata**:
  - Traits: Key-value pairs
  - Properties: Rarity, Edition info
  - Unlockable content: Optional hidden content
- **Inscription Settings**:
  - Fee Rate: Slider (sats/vByte)
  - Estimated Cost: Live calculation
  - Priority: Normal/High
- **Preview Panel**: Live preview of ordinal appearance
- **Action Buttons**:
  - "Save as Draft"
  - "Mint Ordinal" (triggers wallet transaction)

**Minting Progress**
- Step 1: "Preparing inscription data"
- Step 2: "Broadcasting to Bitcoin network"
- Step 3: "Waiting for confirmation"
- Step 4: "Syncing with Ethereum"
- Success Message: "Ordinal successfully created!"

#### My Artworks Tab
**Artwork Management Grid**
- **Filters**:
  - Status: All/Listed/Unlisted/Sold
  - Type: Ordinals/Collaborations
  - Date Range picker
- **Bulk Actions**:
  - Select multiple items
  - Bulk list/delist
  - Export metadata
- **Individual Artwork Actions**:
  - Edit metadata
  - List/Delist toggle
  - Set/Update pricing
  - View on blockchain
  - Share link
  - Download certificate

**Performance Metrics per Artwork**
- Views count
- Likes count
- Bids received
- Watch list adds

#### Collaborations Tab
**Active Collaborations List**
- **Collaboration Cards**:
  - Project thumbnail
  - Title and description
  - Participants (with avatars)
  - Progress bar
  - Status: Active/Pending/Completed
  - Your role: Lead/Contributor
  - Revenue split percentage

**Collaboration Actions**
- "View Details"
- "Message Collaborators"
- "Update Milestone"

#### Collaboration Details (`/artist/collaborations/[id]`)
**Project Overview**
- Banner image
- Title and description
- Creation date
- Total milestones

**Participants Section**
- List of all participants with:
  - Avatar and name
  - Role in project
  - Revenue share percentage
  - Contribution status

**Milestones Timeline**
- Visual timeline with:
  - Milestone name
  - Due date
  - Status (Pending/In Progress/Complete)
  - Assigned to
  - Deliverables

**Revenue Management**
- Total revenue generated
- Distribution breakdown
- Pending payouts
- Claim button

**Communication Thread**
- Integrated chat for collaborators
- File sharing capability
- Decision voting

#### Governance Tab
**Voting Power Display**
- **Your Voting Power**: Number based on ordinals held
- **Power Breakdown**:
  - Base power from ordinals
  - Reputation multiplier
  - Domain bonuses
  - Delegation received

**Active Proposals**
- **Filter**: All/Artist Domain/Active/Ended
- **Proposal Cards**:
  - Title and summary
  - Proposer info
  - Time remaining
  - Current vote tally
  - Your vote status

**Voting Interface**
- Proposal details view
- Vote options: For/Against/Abstain
- Vote weight allocation (for quadratic voting)
- Delegation option
- Submit vote button

#### Chain Sync Tab
**Oracle Status Dashboard**
- **TEE Oracle Status**: Online/Offline indicator
- **Last Sync**: Timestamp
- **Pending Transactions**: Count
- **Success Rate**: Percentage

**Cross-chain Activity Log**
- Table with columns:
  - Transaction Type
  - Bitcoin TX ID
  - Ethereum TX ID
  - Status
  - Timestamp
  - Action buttons

**Manual Sync Tools**
- "Force Sync" button
- "Verify Ordinal" tool
- "Report Issue" link

### Copy Needed
- Onboarding flow text
- Tool tips for each feature
- Form validation messages
- Success/error notifications
- Empty state messages
- Help documentation links

---

## 3. **Gallery Dashboard** (`/gallery`)

### Purpose
Gallery owners curate collections and manage exhibitions

### Main Navigation
Create Gallery | Gallery Dashboard

### Create Gallery (`/gallery/create`)
**Gallery Setup Wizard**

**Step 1: Basic Information**
- **Gallery Name**: Text input with availability check
- **Tagline**: Short description (100 chars)
- **Description**: Rich text editor
- **Gallery Type**: Traditional/Experimental/Themed
- **Website**: Optional URL

**Step 2: Curation Philosophy**
- **Mission Statement**: Text area
- **Focus Areas**: Multi-select checkboxes
  - Contemporary Digital Art
  - Generative Art
  - Photography
  - 3D/VR Art
  - Conceptual Art
- **Artist Criteria**: Text area

**Step 3: Commission Structure**
- **Commission Rate**: Slider (5-50%)
- **Special Rates**: Optional tiered structure
- **Payment Terms**: Immediate/Net 30
- **Revenue Sharing**: Additional beneficiaries

**Step 4: Smart Contract Deployment**
- **Network Selection**: Ethereum/Polygon
- **Contract Parameters**: Read-only display
- **Deployment Cost**: Estimated gas fees
- **Deploy Button**: Triggers wallet transaction

**Success Screen**
- Confirmation message
- Gallery contract address
- Next steps checklist

### Gallery Management (`/gallery/dashboard`)

#### Overview Tab
**Gallery Metrics Dashboard**
- **Card 1: Total Artists** - Count with growth indicator
- **Card 2: Total Artworks** - Active listings count
- **Card 3: Total Sales** - Volume in ETH/USD
- **Card 4: Commission Earned** - Total earnings
- **Card 5: Visitor Count** - Unique visitors
- **Card 6: Conversion Rate** - Sales/Visits percentage

**Revenue Analytics**
- **Chart Title**: "Gallery Performance"
- **Metrics**:
  - Sales volume over time
  - Commission earnings
  - Top performing artists
  - Category breakdown

**Recent Gallery Activity**
- New artist applications
- Recent sales
- New artwork submissions
- Visitor interactions

#### Collections Tab
**Collection Creator**
- **Button**: "Create New Collection"
- **Form Fields**:
  - Collection Name
  - Theme/Concept
  - Cover Image
  - Description
  - Curatorial Statement

**Collection Manager**
- **Collection Cards**:
  - Cover image
  - Title and artwork count
  - Featured/Hidden toggle
  - Edit/Delete actions
- **Artwork Assignment**:
  - Drag-drop interface
  - Search and filter tools
  - Bulk assignment

**Pricing Tools**
- Bulk pricing adjustments
- Discount campaigns
- Special offers setup

#### Exhibitions Tab
**Virtual Exhibition Builder**
- **3D Gallery Spaces**:
  - Template selection
  - Custom room builder
  - Lighting controls
  - Artwork placement tools
- **Exhibition Details**:
  - Title and dates
  - Curatorial essay
  - Artist statements
  - Press materials

**Event Scheduler**
- **Event Types**:
  - Opening night
  - Artist talks
  - Collector previews
  - Live auctions
- **Event Management**:
  - RSVP system
  - Reminder emails
  - Virtual event links

**Marketing Tools**
- Exhibition landing pages
- Social media templates
- Embed codes
- QR codes for physical spaces

#### Collaborations Tab
**Partnership Manager**
- **Collaboration Types**:
  - Gallery exchanges
  - Joint exhibitions
  - Artist residencies
- **Collaboration Proposals**:
  - Incoming requests
  - Sent proposals
  - Active partnerships

**Cross-promotion Tools**
- Shared exhibition spaces
- Combined marketing
- Revenue sharing setup

#### Artists Network Tab
**Artist Discovery**
- **Search Filters**:
  - Art style/medium
  - Verification status
  - Sales history
  - Reputation score
  - Location
- **Artist Cards**:
  - Portfolio preview
  - Stats summary
  - Recent works
  - Invite button

**Invitation System**
- **Invitation Form**:
  - Personal message
  - Commission terms
  - Benefits offered
  - Exhibition opportunities
- **Invitation Tracking**:
  - Sent invitations
  - Response status
  - Follow-up reminders

**Artist Relationship Management**
- Artist notes and tags
- Communication history
- Performance tracking

### Copy Requirements
- Gallery onboarding instructions
- Curation best practices
- Exhibition planning guides
- Invitation templates
- Marketing copy templates
- Success metrics explanations

---

## 4. **Benefactor Dashboard** (`/benefactor`)

### Purpose
Liquidity providers manage investments and track rewards

### Main Dashboard (`/benefactor/dashboard`)

#### Liquidity Overview Section
**Key Metrics Cards**
- **Total Value Locked (TVL)**
  - Your contribution amount
  - Percentage of total pool
  - Current value in USD
- **Current APY**
  - Base APY percentage
  - Bonus APY from governance
  - Projected annual returns
- **Rewards Accumulated**
  - Pending rewards amount
  - Claimable rewards
  - Next distribution date
- **Pool Share**
  - Your percentage
  - Voting power derived
  - Tier status

#### Pool Management Interface
**Add Liquidity**
- **Input Form**:
  - Amount input (ETH)
  - USD equivalent display
  - Gas fee estimate
  - Slippage settings
- **Pool Information**:
  - Total pool size
  - Current utilization
  - Average APY
- **Confirmation Modal**:
  - Transaction summary
  - Expected rewards
  - Lock period info
  - Confirm button

**Remove Liquidity**
- Withdrawal amount selector
- Penalty calculator (if early)
- Remaining position display
- Impact on benefits warning

**Pool Performance Charts**
- TVL growth over time
- APY historical data
- Your position value chart
- Reward distribution history

#### Benefits Display
**Tier System**
- **Bronze Tier** (0.1-1 ETH):
  - 5% minting discount
  - Basic governance rights
- **Silver Tier** (1-10 ETH):
  - 10% minting discount
  - Enhanced voting power
  - Priority marketplace access
- **Gold Tier** (10-50 ETH):
  - 15% minting discount
  - Maximum voting power
  - Early access to drops
  - Exclusive events
- **Platinum Tier** (50+ ETH):
  - 20% minting discount
  - Veto rights
  - Direct artist access
  - Custom benefits

**Active Benefits**
- Current discount rate
- Special access list
- Governance multiplier
- Exclusive features unlocked

#### Transaction History
**Table Columns**:
- Date/Time
- Transaction Type (Deposit/Withdrawal/Reward)
- Amount
- Status
- Transaction Hash
- Actions (View on Etherscan)

**Filters**:
- Date range
- Transaction type
- Amount range
- Export CSV option

#### Governance Participation
**Voting Power Summary**
- Base power from liquidity
- Reputation bonus
- Total voting weight
- Delegation status

**Recent Proposals**
- Benefactor-specific proposals
- Your voting history
- Upcoming votes
- Proposal outcomes

### Copy Requirements
- Investment explanation and risks
- Reward calculation methodology
- Tier benefits descriptions
- APY disclaimers
- Withdrawal terms
- Governance participation guide

---

## 5. **NFT Marketplace** (`/marketplace`)

### Purpose
Browse, discover, and purchase digital art

### Main Browse View

#### Search and Filter Section
**Search Bar**
- Placeholder: "Search by artwork, artist, or collection..."
- Auto-complete suggestions
- Recent searches dropdown

**Filter Panel** (Collapsible Sidebar)
- **Status Filters**:
  - [ ] For Sale
  - [ ] In Auction
  - [ ] Sold (view only)
  - [ ] Coming Soon
- **Price Range**:
  - Min/Max inputs
  - Currency toggle (ETH/USD)
  - Quick ranges (Under 1 ETH, 1-5 ETH, etc.)
- **Categories**:
  - [ ] Digital Paintings
  - [ ] Photography
  - [ ] Generative Art
  - [ ] 3D Art
  - [ ] Video Art
  - [ ] Conceptual
- **Artist Verification**:
  - [ ] Verified Artists Only
  - [ ] Rising Artists
  - [ ] Established Artists
- **Ordinal Properties**:
  - Inscription date range
  - Rarity filters
  - Edition types

**View Controls**
- Toggle: Grid/List view
- Sort Dropdown:
  - Recently Listed
  - Price: Low to High
  - Price: High to Low
  - Most Viewed
  - Ending Soon
  - Most Liked
- Results per page: 24/48/96

#### Artwork Grid/List Display
**Grid View - Artwork Cards**
- Thumbnail image (hover for preview)
- Title (truncated)
- Artist name with verification badge
- Current price or highest bid
- Time remaining (if auction)
- Like count
- Quick actions (Like/Watchlist)

**List View - Artwork Rows**
- Larger thumbnail
- Full title and description preview
- Artist info with avatar
- Detailed pricing info
- Creation date
- View/Like/Bid counts
- Action buttons

#### Featured Section (Top of page)
- **Hero Banner**: Rotating featured artworks
- **Trending Collections**: Horizontal scroll
- **Hot Auctions**: Items ending soon
- **New Drops**: Recently minted ordinals

### Artwork Detail Page (`/marketplace/artwork/[id]`)

#### Main Display Section
**Artwork Viewer**
- High-resolution image display
- Zoom controls (+/- buttons, mouse wheel)
- Fullscreen toggle
- For videos: Play controls
- For 3D: Interactive viewer
- Download preview button

**Artwork Information**
- **Title**: Large heading
- **Artist**: Name with link to profile
- **Created**: Date and inscription number
- **Description**: Full text with "Read more" toggle
- **Collection**: If part of a collection

#### Trading Section
**For Direct Sale**
- **Current Price**: Large display in ETH and USD
- **Buy Now Button**: Prominent CTA
- **Make Offer Button**: Secondary option
- **Add to Cart**: For multi-purchase

**For Auction**
- **Current Bid**: Amount and leader
- **Bid Increment**: Minimum next bid
- **Time Remaining**: Countdown timer
- **Bid History**: Collapsible table
  - Bidder (anonymized)
  - Amount
  - Time
- **Place Bid Form**:
  - Bid amount input
  - Quick bid buttons (+10%, +25%)
  - Terms checkbox
  - Submit bid button

**Seller Information**
- Seller avatar and name
- Seller reputation score
- Other items from seller
- Contact seller button

#### Metadata Panel
**Blockchain Details**
- **Ordinal Details**:
  - Inscription ID
  - Bitcoin block height
  - Transaction ID
  - View on Ordinals.com
- **Ethereum Details**:
  - Contract address
  - Token ID
  - View on Etherscan
- **Verification Status**:
  - TEE Oracle verified ✓
  - Ownership confirmed ✓

**Properties and Traits**
- Trait type and value pairs
- Rarity percentages
- Special attributes

**Provenance**
- Creation transaction
- Ownership history
- Price history graph

#### Social Features
**Engagement**
- Like button with count
- Share buttons:
  - Twitter/X
  - Facebook
  - Copy link
  - Embed code
- Report listing option

**Comments Section**
- Comment form (if logged in)
- Comments list with:
  - User avatar and name
  - Comment text
  - Timestamp
  - Like/Reply options
- Sort options: Newest/Popular

#### Related Artworks
- "More from this artist"
- "Similar artworks"
- "Also viewed" recommendations
- Carousel navigation

### Copy Requirements
- Category descriptions
- Filter explanations
- Sorting option labels
- Purchase flow instructions
- Bidding rules and terms
- Trust and authenticity messaging
- Empty state messages
- Loading states
- Error messages

---

## 6. **Governance Portal** (`/governance`)

### Purpose
Decentralized decision-making platform

### Main Governance Page

#### Governance Overview
**Your Governance Stats**
- **Voting Power**: Total across all domains
- **Proposals Participated**: Count and percentage
- **Successful Proposals**: Your voting accuracy
- **Delegations**: Received and given

#### Proposal List Section
**Filters and Controls**
- **Status Filter**:
  - [ ] Active (voting open)
  - [ ] Pending (not started)
  - [ ] Executed
  - [ ] Defeated
  - [ ] Cancelled
- **Domain Filter**:
  - [ ] Artist Governance
  - [ ] Gallery Operations
  - [ ] Platform Development
  - [ ] Treasury Management
- **Sort Options**:
  - Ending Soon
  - Most Votes
  - Recently Added
  - High Impact

**Proposal Cards**
- **Card Header**:
  - Proposal ID and title
  - Proposer name and avatar
  - Domain tag
  - Status badge
- **Card Body**:
  - Brief description (200 chars)
  - Key metrics:
    - For: X votes (Y%)
    - Against: X votes (Y%)
    - Quorum: Z% reached
  - Time remaining or ended date
- **Card Footer**:
  - Vote button (if active)
  - View details link
  - Your vote indicator

#### Create Proposal Interface
**Proposal Form**
- **Basic Information**:
  - Title (100 chars max)
  - Summary (500 chars)
  - Full description (Markdown editor)
  - External links/documentation
- **Governance Details**:
  - Domain selection dropdown
  - Impact level (Low/Medium/High)
  - Implementation timeline
- **Technical Parameters**:
  - Required quorum percentage
  - Voting period (days)
  - Execution delay
  - Budget required (if any)
- **Supporting Materials**:
  - File attachments
  - Reference proposals
  - Technical specifications

**Preview and Submit**
- Preview mode toggle
- Proposal cost display
- Submit button (requires stake)

#### Voting Interface (Proposal Detail)
**Proposal Header**
- Full title
- Proposer information
- Proposal status
- Domain and tags

**Proposal Content**
- Full description with formatting
- Technical specifications
- Implementation plan
- Budget breakdown
- Risk assessment

**Voting Section**
- **Current Results**:
  - For votes with percentage
  - Against votes with percentage
  - Abstain votes
  - Quorum progress bar
- **Your Voting Power**:
  - Base power
  - Domain weight applied
  - Delegated power
  - Total voting weight
- **Cast Vote**:
  - Vote options (For/Against/Abstain)
  - Vote weight allocation (quadratic)
  - Delegation option
  - Vote reason (optional text)
  - Confirm vote button

**Veto Section** (if eligible)
- Veto power status
- Veto threshold
- Cast veto button
- Veto justification required

**Discussion Thread**
- Comments from voters
- Proposer responses
- Sorted by relevance
- Reply functionality

#### Governance History
**Executed Proposals**
- Implementation status
- Actual vs projected outcomes
- Community feedback
- Rollback options (if applicable)

**Your Voting History**
- Past votes table
- Voting power over time
- Delegation history
- Participation rate

### Copy Requirements
- Governance rules documentation
- Proposal templates for each domain
- Voting mechanism explanations
- Domain weight calculations
- Quorum requirements
- Veto process explanation
- Implementation timelines
- Risk disclaimers

---

## 7. **Reputation Center** (`/reputation`)

### Purpose
Track and display user reputation across the ecosystem

### Reputation Dashboard

#### Overall Reputation Score
**Score Display**
- **Large Numerical Score**: 0-1000 scale
- **Rank Badge**: Bronze/Silver/Gold/Platinum
- **Percentile**: "Top X% of users"
- **Trend Arrow**: Up/down from last period

**Reputation Breakdown Wheel**
- Visual pie chart showing:
  - Artistic Contribution (%)
  - Curation Quality (%)
  - Governance Participation (%)
  - Community Engagement (%)
  - Transaction Reliability (%)

#### 60-Day Decay System
**Decay Warning Panel**
- **Status Bar**: Visual timeline showing decay
- **Days Until Decay**: Countdown
- **Projected Score**: After decay
- **Actions to Prevent**:
  - List of activities that reset timer
  - Points needed to maintain
  - Quick action buttons

**Activity Requirements**
- Minimum actions per domain
- Current period progress
- Suggested activities

#### Domain-Specific Scores
**Domain Tabs**: Art | Curation | Governance | Community

**Art Domain**
- Artworks created
- Sales volume
- Collector satisfaction
- Innovation score
- Collaboration success

**Curation Domain**
- Collections curated
- Artist discovery
- Sales facilitated
- Exhibition success
- Taste-maker influence

**Governance Domain**
- Proposals created
- Voting participation
- Proposal success rate
- Delegation received
- Domain expertise

**Community Domain**
- Forum contributions
- Helpful responses
- Content quality
- Mentorship activities
- Event participation

#### Activity Timeline
**Recent Reputation Events**
- "+10 points - Artwork sold"
- "+5 points - Governance vote cast"
- "+15 points - Helpful forum post"
- "-20 points - Inactivity penalty"
- "+25 points - Successful collaboration"

**Filters**:
- Date range
- Event type
- Domain
- Point changes only

### Achievement System

#### Achievement Gallery
**Categories**:
- **Creator Achievements**
  - First Mint
  - Prolific Creator (10, 50, 100 works)
  - Trending Artist
  - Collaboration Master
- **Collector Achievements**
  - First Purchase
  - Patron (10, 50, 100 purchases)
  - Taste Maker
  - Early Supporter
- **Governance Achievements**
  - First Vote
  - Proposal Creator
  - Governance Leader
  - Domain Expert
- **Community Achievements**
  - Helpful Member
  - Discussion Starter
  - Event Organizer
  - Mentor

**Achievement Cards**
- Badge icon
- Achievement name
- Description
- Progress bar (if incomplete)
- Rarity indicator
- Points awarded
- Unlock date

**Showcase Selection**
- Choose featured achievements
- Profile badge display
- Rarity combinations

### Leaderboard

#### Global Rankings
**Leaderboard Controls**
- Time period: All-time/Monthly/Weekly
- Category: Overall/Domain-specific
- Filter: Following only

**Ranking Table**
- Rank number
- User avatar and name
- Reputation score
- Change indicator
- Primary domain
- View profile link

**Your Position**
- Highlighted row
- Nearby competitors
- Points to next rank

#### Domain-Specific Rankings
- Top artists
- Top curators
- Top governance participants
- Top community contributors
- Rising stars (biggest gains)

### Copy Requirements
- Reputation system explanation
- Scoring methodology
- Decay mechanism details
- Achievement descriptions
- Activity suggestions
- Ranking criteria
- Improvement tips
- Badge rarity explanations

---

## 8. **Community Hub** (`/community`)

### Purpose
Social features and community engagement

### Forum System (`/community/forums`)

#### Forum List Page
**Forum Categories**
- **General Discussion**
  - Platform updates
  - Feature requests
  - General chat
- **Artist Corner**
  - Technique sharing
  - Work in progress
  - Collaboration calls
- **Collector's Lounge**
  - Market analysis
  - Collection showcases
  - Investment strategies
- **Gallery Operators**
  - Curation tips
  - Exhibition planning
  - Artist relations
- **Technical Support**
  - Wallet issues
  - Transaction help
  - Bug reports

**Topic List**
- **Topic Row Information**:
  - Topic title with tags
  - Author avatar and name
  - Creation date
  - Reply count
  - View count
  - Last reply info
  - Pinned indicator

**List Controls**
- Sort: Latest/Popular/Unanswered
- Filter by tag
- Search within category
- Mark all as read

**Create Topic Button**
- Prominent CTA
- Required reputation level

### Create Topic (`/community/forums/create`)
**Topic Creation Form**
- **Title**: Clear, descriptive (100 chars)
- **Category**: Dropdown selection
- **Tags**: Multi-select (max 5)
  - Help Needed
  - Discussion
  - Showcase
  - Tutorial
  - Announcement
- **Content Editor**:
  - Rich text formatting
  - Image upload
  - Code blocks
  - Link embedding
  - Mention users (@)
- **Attachments**:
  - File upload (10MB max)
  - Supported formats list
- **Posting Options**:
  - [ ] Subscribe to replies
  - [ ] Allow comments
  - [ ] Make wiki (editable)
- **Preview/Submit**:
  - Preview toggle
  - Save draft
  - Publish button

### Topic View (`/community/forums/topic/[id]`)
**Original Post**
- **Header**:
  - Title with tags
  - Author info with reputation
  - Posted date
  - Edit/Delete (if owner)
- **Content**:
  - Full formatted text
  - Embedded media
  - Attachments
- **Engagement**:
  - Like button and count
  - Share options
  - Follow thread toggle
  - Report button

**Reply Section**
- **Reply Form**:
  - Quick reply box
  - Full editor option
  - Quote selection
  - Mention autocomplete
- **Reply List**:
  - Threaded/Flat view toggle
  - User avatar and info
  - Reply content
  - Timestamp
  - Like/Reply buttons
  - Best answer indicator
- **Pagination**:
  - Posts per page
  - Jump to page
  - Load more button

**Thread Tools**
- Subscribe/Unsubscribe
- Mark as solved
- Move to category (mods)
- Lock thread (mods)
- Pin/Unpin (mods)

### Community Features
**User Mentions**
- @ mention autocomplete
- Notification on mention
- Link to profile

**Reputation Integration**
- User badges display
- Reputation requirements
- Trust levels

**Moderation Tools**
- Report system
- Moderation queue
- Ban/timeout options
- Edit/delete posts

### Copy Requirements
- Forum guidelines
- Category descriptions
- Posting rules
- Tag definitions
- Moderation policies
- Trust level explanations
- Notification preferences
- Search help

---

## 9. **User Profile** (`/profile/[id]`)

### Purpose
Public-facing user profiles

### Profile Header
**User Information**
- **Avatar**: Large profile image
- **Display Name**: With verification badge
- **Username**: @handle
- **Role Badges**: Artist/Gallery/Benefactor/Collector
- **Reputation Score**: With rank badge
- **Join Date**: Member since
- **Location**: Optional
- **Bio**: User description (500 chars)

**Social Links**
- Website
- Twitter/X
- Instagram
- Discord
- Email (if public)

**Action Buttons**
- Follow/Unfollow
- Message (if connected)
- Share Profile
- Report User

### Profile Tabs

#### Portfolio Tab
**For Artists**
- **Artwork Grid**:
  - Created works
  - Collaboration pieces
  - Sort options
  - Filter by status
- **Statistics**:
  - Total creations
  - Total sales
  - Floor price
  - Volume traded

**For Collectors**
- **Collection Display**:
  - Owned artworks
  - Collection value
  - Favorite pieces
  - Private/Public toggle

**For Galleries**
- **Gallery Information**:
  - Gallery name and link
  - Featured exhibitions
  - Represented artists
  - Curation philosophy

#### Activity Feed Tab
**Activity Timeline**
- Created new artwork
- Listed item for sale
- Made a purchase
- Joined collaboration
- Cast governance vote
- Achieved milestone
- Forum activity

**Activity Filters**
- All activities
- Creations only
- Transactions only
- Social only
- Date range

#### Achievements Tab
**Achievement Showcase**
- Featured badges
- All achievements grid
- Rarity indicators
- Progress tracking
- Total points

#### Stats Tab
**User Statistics**
- **Trading Stats**:
  - Buy/Sell volume
  - Average price
  - Success rate
  - Favorite categories
- **Engagement Stats**:
  - Forum posts
  - Votes cast
  - Proposals created
  - Collaborations
- **Reputation History**:
  - Score over time graph
  - Domain breakdown
  - Major milestones

### Copy Requirements
- Default bio prompts
- Activity type descriptions
- Stat explanations
- Privacy settings info
- Share functionality text
- Achievement tooltips
- Empty state messages

---

## 10. **Showcase** (`/showcase`)

### Purpose
Curated gallery of featured artworks

### Showcase Layout

#### Featured Banner
**Hero Section**
- **Rotating Featured Artworks**:
  - Full-width image
  - Artwork title and artist
  - Brief description
  - View/Buy buttons
  - Auto-rotation with manual controls
- **Featured Exhibition**:
  - Current virtual exhibition
  - Gallery name
  - Duration
  - Enter exhibition button

#### Curated Collections
**Staff Picks**
- Section title: "Curated by The Nursery"
- Grid of 6-8 artworks
- Curator's note
- Refresh weekly

**Trending This Week**
- Algorithm-based selection
- View velocity
- Engagement metrics
- Social sharing count

**New Artists Spotlight**
- First-time creators
- Rising talent
- Brief artist intro
- 3-4 featured works each

#### Virtual Gallery Experience
**3D Gallery Mode**
- Enter VR Gallery button
- Walk-through experience
- Artwork information panels
- Social viewing options
- Audio guide availability

**Gallery Themes**
- Contemporary Space
- Classical Museum
- Outdoor Sculpture Park
- Abstract Dimensions
- User custom spaces

#### Discovery Tools
**Artwork Randomizer**
- "Discover Something New"
- Random quality artwork
- Refresh button
- Save to favorites

**Themed Collections**
- Seasonal collections
- Cultural celebrations
- Artistic movements
- Technical innovations

### Copy Requirements
- Curatorial statements
- Artist spotlight intros
- Collection descriptions
- Gallery experience instructions
- Discovery prompts
- Exhibition announcements

---

## 11. **Global Components**

### Navigation Header
**Logo Section**
- The Nursery logo
- Tagline on hover

**Main Navigation**
- Marketplace
- Governance
- Community
- My Dashboard (role-based)

**User Section**
- Wallet connection status
  - Connected: Address (shortened)
  - Network indicator
  - Balance display
- Notification Bell
  - Badge with count
  - Dropdown with recent
- User Menu
  - Profile
  - Settings
  - Help
  - Disconnect

### Chat System
**Chat Widget**
- **Floating Button**:
  - Chat bubble icon
  - Unread count badge
  - Minimize/maximize
- **Chat Window**:
  - Conversation list
  - Search conversations
  - New message button
- **Conversation View**:
  - Message history
  - User online status
  - Typing indicators
  - File sharing
  - Emoji picker
- **Artwork-Specific Chat**:
  - Context about artwork
  - Quick responses
  - Make offer button

### Notification System
**Notification Types**
- **Sales**: "Your artwork sold for X ETH"
- **Bids**: "New bid on [Artwork]"
- **Governance**: "New proposal in your domain"
- **Social**: "X started following you"
- **System**: "Maintenance scheduled"

**Notification Center**
- All notifications list
- Filter by type
- Mark as read
- Settings link
- Clear all button

### Footer
**Link Sections**
- **Platform**:
  - About The Nursery
  - How it Works
  - Fees
  - Security
- **Resources**:
  - Documentation
  - API Docs
  - Brand Assets
  - Integration Guide
- **Community**:
  - Discord
  - Twitter/X
  - Blog
  - Newsletter
- **Legal**:
  - Terms of Service
  - Privacy Policy
  - Cookie Policy
  - Compliance

**Newsletter Signup**
- Email input
- Subscribe button
- Privacy note

**Language/Region**
- Language selector
- Currency preference

### Common UI States
**Loading States**
- Skeleton screens
- Progress indicators
- Loading messages

**Empty States**
- Friendly messages
- Suggested actions
- Helpful graphics

**Error States**
- Clear error messages
- Recovery actions
- Support links

**Success States**
- Confirmation messages
- Next steps
- Celebration animations

### Copy Requirements
- Navigation labels
- Wallet connection instructions
- Notification templates
- Error message library
- Success message library
- Loading state messages
- Empty state messages
- Footer content
- Legal documents
- Help documentation
- Tooltips throughout

---

## Technical Implementation Notes

### Frontend Stack
- **Framework**: Next.js 14 with App Router
- **Styling**: Tailwind CSS with custom design system
- **State Management**: React Context + Zustand
- **Forms**: React Hook Form with Zod validation
- **Real-time**: Socket.io for chat and live updates
- **Blockchain**: Ethers.js and Bitcoin libraries

### Backend Stack
- **Framework**: NestJS
- **Database**: PostgreSQL with Prisma ORM
- **Caching**: Redis
- **File Storage**: IPFS
- **WebSockets**: Socket.io
- **Authentication**: JWT with wallet signatures

### Smart Contract Integration
- **Ethereum**: Gallery Factory, Marketplace, Governance
- **Bitcoin**: Ordinals inscription and verification
- **Cross-chain**: BlockyTEE Oracle for secure bridging

### API Structure
- RESTful API design
- GraphQL for complex queries
- WebSocket for real-time features
- Rate limiting and caching
- Comprehensive error handling

This outline serves as the complete blueprint for content creation, UX design, and development of the Ordinals Art Marketplace platform.