# Software Design Document - Ordinals Art Marketplace

## Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [System Overview](#2-system-overview)
3. [Architectural Design](#3-architectural-design)
4. [Component Design](#4-component-design)
5. [Data Design](#5-data-design)
6. [Interface Design](#6-interface-design)
7. [Security Design](#7-security-design)
8. [Performance Design](#8-performance-design)
9. [Deployment Design](#9-deployment-design)
10. [Testing Strategy](#10-testing-strategy)

---

## 1. Executive Summary

### 1.1 Purpose
The Ordinals Art Marketplace is a decentralized ecosystem that bridges Bitcoin Ordinals with Ethereum smart contracts, creating a comprehensive platform for digital art creation, curation, and trading. This document outlines the complete software design, providing a high-level walkthrough of all system components and their interactions.

### 1.2 Scope
This system encompasses:
- Multi-chain blockchain integration (Bitcoin + Ethereum)
- Web3 marketplace functionality
- Decentralized governance system
- Reputation and incentive mechanisms
- Real-time communication features
- Cross-chain oracle infrastructure

### 1.3 Key Stakeholders
- **Artists**: Create and monetize digital art as Bitcoin Ordinals
- **Galleries**: Curate collections and facilitate art discovery
- **Benefactors**: Provide liquidity and earn rewards
- **Collectors**: Purchase and trade digital artworks
- **Platform Operators**: Maintain and govern the ecosystem

---

## 2. System Overview

### 2.1 High-Level Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                         Frontend Layer                           │
│  ┌─────────────┐  ┌──────────────┐  ┌────────────────────┐    │
│  │   Next.js   │  │    React     │  │  Wallet Adapters   │    │
│  │  App Router │  │  Components  │  │ MetaMask + Xverse  │    │
│  └─────────────┘  └──────────────┘  └────────────────────┘    │
└─────────────────────────────────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────┐
│                         API Gateway                              │
│  ┌─────────────┐  ┌──────────────┐  ┌────────────────────┐    │
│  │   NestJS    │  │   GraphQL    │  │    WebSocket       │    │
│  │   REST API  │  │   Endpoint   │  │    (Socket.io)     │    │
│  └─────────────┘  └──────────────┘  └────────────────────┘    │
└─────────────────────────────────────────────────────────────────┘
                                │
                ┌───────────────┼───────────────┐
                ▼               ▼               ▼
┌──────────────────┐  ┌──────────────┐  ┌──────────────────┐
│  Business Logic  │  │   Database   │  │  Blockchain      │
│  ┌─────────────┐ │  │  ┌─────────┐ │  │  ┌────────────┐ │
│  │   Services  │ │  │  │PostgreSQL│ │  │  │  Ethereum  │ │
│  │  Modules    │ │  │  └─────────┘ │  │  │  Contracts │ │
│  └─────────────┘ │  │  ┌─────────┐ │  │  └────────────┘ │
│  ┌─────────────┐ │  │  │  Redis  │ │  │  ┌────────────┐ │
│  │   Domain    │ │  │  │  Cache  │ │  │  │  Bitcoin   │ │
│  │   Logic     │ │  │  └─────────┘ │  │  │  Ordinals  │ │
│  └─────────────┘ │  │  ┌─────────┐ │  │  └────────────┘ │
│                  │  │  │  IPFS   │ │  │  ┌────────────┐ │
│                  │  │  └─────────┘ │  │  │ TEE Oracle │ │
│                  │  │              │  │  └────────────┘ │
└──────────────────┘  └──────────────┘  └──────────────────┘
```

### 2.2 Core Principles

1. **Decentralization**: No single point of failure, community governance
2. **Cross-chain Interoperability**: Seamless Bitcoin-Ethereum integration
3. **Security First**: Multiple layers of security, TEE oracle validation
4. **Scalability**: Horizontal scaling capabilities, efficient caching
5. **User Experience**: Web2-like UX with Web3 security
6. **Modularity**: Loosely coupled components for maintainability

### 2.3 Technology Stack

**Frontend**:
- Next.js 14 (App Router)
- TypeScript
- Tailwind CSS
- React Query
- Zustand (State Management)
- Ethers.js & Bitcoin Libraries

**Backend**:
- NestJS (Node.js)
- TypeScript
- Prisma ORM
- PostgreSQL
- Redis
- IPFS
- Socket.io

**Blockchain**:
- Solidity (Ethereum Smart Contracts)
- Foundry (Contract Development)
- Bitcoin Core (Ordinals)
- BlockyTEE Oracle

**Infrastructure**:
- Docker & Kubernetes
- GitHub Actions (CI/CD)
- Prometheus & Grafana (Monitoring)
- NGINX (Load Balancing)

---

## 3. Architectural Design

### 3.1 Layered Architecture

#### 3.1.1 Presentation Layer
- **Responsibility**: User interface and interaction
- **Components**: 
  - Next.js pages and components
  - Responsive design system
  - Wallet integration adapters
  - Real-time UI updates

#### 3.1.2 Application Layer
- **Responsibility**: Business logic and orchestration
- **Components**:
  - API Gateway (REST/GraphQL)
  - Authentication & Authorization
  - Request validation
  - Response transformation

#### 3.1.3 Domain Layer
- **Responsibility**: Core business rules
- **Components**:
  - User management (Artist/Gallery/Benefactor roles)
  - Artwork lifecycle management
  - Marketplace operations
  - Governance mechanisms
  - Reputation calculations

#### 3.1.4 Infrastructure Layer
- **Responsibility**: Technical capabilities
- **Components**:
  - Database access (Prisma)
  - Blockchain interactions
  - External service integrations
  - Caching strategies
  - Message queuing

### 3.2 Microservices Architecture

```
┌─────────────────────────────────────────────────────────┐
│                   API Gateway                            │
└─────────────────────────────────────────────────────────┘
     │         │         │         │         │         │
     ▼         ▼         ▼         ▼         ▼         ▼
┌─────────┐ ┌─────┐ ┌────────┐ ┌──────┐ ┌──────┐ ┌──────┐
│  Auth   │ │User │ │Artwork │ │Market│ │Govern│ │Oracle│
│ Service │ │Mgmt │ │Service │ │place │ │ance  │ │Bridge│
└─────────┘ └─────┘ └────────┘ └──────┘ └──────┘ └──────┘
```

Each service is:
- Independently deployable
- Horizontally scalable
- Database-per-service pattern
- Communicates via API/events

### 3.3 Event-Driven Architecture

**Event Bus**: Redis Pub/Sub + WebSocket

**Key Events**:
1. **Artwork Events**:
   - `artwork.created`
   - `artwork.listed`
   - `artwork.sold`
   - `artwork.bid.placed`

2. **User Events**:
   - `user.registered`
   - `user.verified`
   - `user.role.changed`

3. **Blockchain Events**:
   - `ordinal.inscribed`
   - `transaction.confirmed`
   - `contract.event`

4. **Governance Events**:
   - `proposal.created`
   - `vote.cast`
   - `proposal.executed`

### 3.4 Cross-Chain Architecture

```
Bitcoin Network                    Ethereum Network
      │                                   │
      ▼                                   ▼
┌─────────────┐                   ┌──────────────┐
│  Ordinals   │                   │Smart Contract│
│ Inscription │                   │  Ecosystem   │
└─────────────┘                   └──────────────┘
      │                                   │
      └──────────► TEE Oracle ◄───────────┘
                        │
                        ▼
                 ┌─────────────┐
                 │  Verified   │
                 │   State     │
                 └─────────────┘
```

**TEE Oracle Responsibilities**:
- Monitor Bitcoin transactions
- Verify ordinal inscriptions
- Update Ethereum state
- Maintain cross-chain consistency

---

## 4. Component Design

### 4.1 Frontend Components

#### 4.1.1 Page Components
```typescript
// App Router Structure
/app
├── (public)
│   ├── page.tsx                 // Landing page
│   ├── marketplace/
│   │   ├── page.tsx            // Browse marketplace
│   │   └── artwork/[id]/page.tsx
│   └── profile/[id]/page.tsx
├── (authenticated)
│   ├── artist/
│   │   ├── page.tsx            // Artist dashboard
│   │   ├── create/page.tsx
│   │   └── collaborations/[id]/page.tsx
│   ├── gallery/
│   │   ├── page.tsx
│   │   ├── create/page.tsx
│   │   └── dashboard/page.tsx
│   └── benefactor/
│       └── dashboard/page.tsx
└── (shared)
    ├── governance/page.tsx
    ├── reputation/page.tsx
    └── community/
        └── forums/page.tsx
```

#### 4.1.2 Component Hierarchy
```
<AppLayout>
  <NavigationHeader />
  <WalletProvider>
    <AuthProvider>
      <NotificationProvider>
        <RouterOutlet>
          {/* Page Components */}
        </RouterOutlet>
      </NotificationProvider>
    </AuthProvider>
  </WalletProvider>
  <ChatWidget />
  <Footer />
</AppLayout>
```

#### 4.1.3 State Management
```typescript
// Global State (Zustand)
interface AppState {
  // User State
  user: User | null;
  wallets: {
    ethereum: WalletState;
    bitcoin: WalletState;
  };
  
  // UI State
  notifications: Notification[];
  modals: ModalState;
  
  // Data State
  artworks: Map<string, Artwork>;
  proposals: Map<string, Proposal>;
  
  // Actions
  connectWallet: (type: WalletType) => Promise<void>;
  disconnectWallet: (type: WalletType) => void;
  fetchUserData: () => Promise<void>;
}
```

### 4.2 Backend Components

#### 4.2.1 Module Structure
```typescript
// NestJS Module Organization
@Module({
  imports: [
    AuthModule,
    UsersModule,
    ArtworkModule,
    MarketplaceModule,
    GovernanceModule,
    ReputationModule,
    BlockchainModule,
    ChatModule,
    ForumModule,
  ],
  controllers: [AppController],
  providers: [AppService],
})
export class AppModule {}
```

#### 4.2.2 Service Layer Pattern
```typescript
@Injectable()
export class ArtworkService {
  constructor(
    private prisma: PrismaService,
    private ipfs: IpfsService,
    private blockchain: BlockchainService,
    private events: EventEmitter2,
  ) {}

  async createArtwork(data: CreateArtworkDto): Promise<Artwork> {
    // 1. Validate input
    // 2. Upload to IPFS
    // 3. Create database record
    // 4. Emit creation event
    // 5. Return artwork
  }

  async listForSale(id: string, price: BigNumber): Promise<Listing> {
    // 1. Verify ownership
    // 2. Create listing transaction
    // 3. Update database
    // 4. Emit listing event
    // 5. Return listing
  }
}
```

#### 4.2.3 Repository Pattern
```typescript
@Injectable()
export class ArtworkRepository {
  constructor(private prisma: PrismaService) {}

  async findById(id: string): Promise<Artwork | null> {
    return this.prisma.artwork.findUnique({
      where: { id },
      include: {
        artist: true,
        listings: true,
        bids: true,
      },
    });
  }

  async findByArtist(artistId: string, options: PaginationOptions) {
    return this.prisma.artwork.findMany({
      where: { artistId },
      skip: options.offset,
      take: options.limit,
      orderBy: { createdAt: 'desc' },
    });
  }
}
```

### 4.3 Smart Contract Components

#### 4.3.1 Contract Architecture
```solidity
// Core Contracts
├── GalleryFactory.sol      // Deploy new galleries
├── GalleryMarketplace.sol  // NFT trading
├── ArtistERC721.sol       // Artist NFT collections
├── BenefactorLP.sol       // Liquidity pool
├── BenefactorGovernance.sol // Voting mechanism
├── BenefactorReputation.sol // Reputation tracking
├── BlockyTEEOracle.sol    // Cross-chain oracle
└── interfaces/
    └── IOrdinalOracle.sol // Oracle interface
```

#### 4.3.2 Upgradability Pattern
```solidity
// Proxy Pattern for Upgradability
contract GalleryFactoryProxy is TransparentUpgradeableProxy {
    constructor(
        address _logic,
        address admin_,
        bytes memory _data
    ) TransparentUpgradeableProxy(_logic, admin_, _data) {}
}

// Implementation Contract
contract GalleryFactoryV1 is Initializable, OwnableUpgradeable {
    mapping(address => address[]) public userGalleries;
    
    function initialize() public initializer {
        __Ownable_init();
    }
    
    function createGallery(
        string memory name,
        uint256 commission
    ) external returns (address) {
        // Gallery creation logic
    }
}
```

---

## 5. Data Design

### 5.1 Database Schema

#### 5.1.1 Core Entities

```sql
-- Users Table
CREATE TABLE users (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    wallet_address VARCHAR(42) UNIQUE NOT NULL,
    bitcoin_address VARCHAR(62),
    username VARCHAR(50) UNIQUE,
    role ENUM('ARTIST', 'GALLERY', 'BENEFACTOR', 'COLLECTOR'),
    reputation_score INTEGER DEFAULT 0,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Artworks Table
CREATE TABLE artworks (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    title VARCHAR(200) NOT NULL,
    description TEXT,
    artist_id UUID REFERENCES users(id),
    ordinal_id VARCHAR(100) UNIQUE,
    ipfs_hash VARCHAR(100),
    metadata JSONB,
    status ENUM('DRAFT', 'MINTED', 'LISTED', 'SOLD'),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Listings Table
CREATE TABLE listings (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    artwork_id UUID REFERENCES artworks(id),
    seller_id UUID REFERENCES users(id),
    price DECIMAL(36, 18),
    currency ENUM('ETH', 'BTC'),
    status ENUM('ACTIVE', 'SOLD', 'CANCELLED'),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Bids Table
CREATE TABLE bids (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    listing_id UUID REFERENCES listings(id),
    bidder_id UUID REFERENCES users(id),
    amount DECIMAL(36, 18),
    status ENUM('ACTIVE', 'ACCEPTED', 'REJECTED', 'WITHDRAWN'),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Galleries Table
CREATE TABLE galleries (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    owner_id UUID REFERENCES users(id),
    name VARCHAR(100) NOT NULL,
    contract_address VARCHAR(42) UNIQUE,
    commission_rate DECIMAL(5, 2),
    metadata JSONB,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Collaborations Table
CREATE TABLE collaborations (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    title VARCHAR(200) NOT NULL,
    description TEXT,
    status ENUM('PLANNING', 'ACTIVE', 'COMPLETED'),
    revenue_split JSONB,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

#### 5.1.2 Relationships

```sql
-- Many-to-Many Relationships
CREATE TABLE collaboration_artists (
    collaboration_id UUID REFERENCES collaborations(id),
    artist_id UUID REFERENCES users(id),
    role VARCHAR(50),
    revenue_share DECIMAL(5, 2),
    PRIMARY KEY (collaboration_id, artist_id)
);

CREATE TABLE gallery_artists (
    gallery_id UUID REFERENCES galleries(id),
    artist_id UUID REFERENCES users(id),
    joined_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    status ENUM('INVITED', 'ACTIVE', 'INACTIVE'),
    PRIMARY KEY (gallery_id, artist_id)
);

-- Reputation Events
CREATE TABLE reputation_events (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    user_id UUID REFERENCES users(id),
    event_type VARCHAR(50),
    points INTEGER,
    domain ENUM('ART', 'CURATION', 'GOVERNANCE', 'COMMUNITY'),
    metadata JSONB,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### 5.2 Caching Strategy

#### 5.2.1 Redis Cache Structure
```
# User Sessions
session:{userId} -> User session data (TTL: 24h)

# Artwork Cache
artwork:{artworkId} -> Artwork details (TTL: 1h)
artwork:list:{filter} -> Filtered artwork lists (TTL: 5m)

# Price Data
price:eth:usd -> Current ETH price (TTL: 1m)
price:btc:usd -> Current BTC price (TTL: 1m)

# Hot Data
trending:artworks -> Trending artwork IDs (TTL: 15m)
featured:galleries -> Featured gallery list (TTL: 1h)

# Rate Limiting
rate:limit:{userId}:{action} -> Request count (TTL: 1m)
```

#### 5.2.2 Cache Invalidation
```typescript
class CacheInvalidationService {
  // Invalidate on write
  async onArtworkUpdated(artworkId: string) {
    await this.redis.del(`artwork:${artworkId}`);
    await this.redis.del('artwork:list:*'); // Pattern delete
  }

  // Time-based invalidation
  async refreshTrendingData() {
    const trending = await this.calculateTrending();
    await this.redis.setex('trending:artworks', 900, trending);
  }
}
```

### 5.3 IPFS Storage

#### 5.3.1 Content Structure
```
/artworks
  /{artworkId}
    /metadata.json     # Artwork metadata
    /image.jpg        # Main image
    /thumbnail.jpg    # Optimized thumbnail
    /certificate.pdf  # Authenticity certificate

/profiles
  /{userId}
    /avatar.jpg       # Profile picture
    /banner.jpg       # Profile banner
    /portfolio.json   # Portfolio metadata
```

#### 5.3.2 Pinning Strategy
- Primary: Local IPFS node
- Secondary: Pinata/Infura pinning service
- Backup: Distributed pinning across gallery nodes

---

## 6. Interface Design

### 6.1 API Design

#### 6.1.1 RESTful Endpoints
```
# Authentication
POST   /api/auth/connect-wallet
POST   /api/auth/verify-signature
POST   /api/auth/logout

# Users
GET    /api/users/:id
PUT    /api/users/:id
GET    /api/users/:id/artworks
GET    /api/users/:id/reputation

# Artworks
POST   /api/artworks
GET    /api/artworks
GET    /api/artworks/:id
PUT    /api/artworks/:id
DELETE /api/artworks/:id

# Marketplace
POST   /api/listings
GET    /api/listings
GET    /api/listings/:id
POST   /api/listings/:id/bids
PUT    /api/listings/:id/accept-bid

# Governance
GET    /api/proposals
POST   /api/proposals
GET    /api/proposals/:id
POST   /api/proposals/:id/votes
```

#### 6.1.2 GraphQL Schema
```graphql
type Query {
  # User queries
  user(id: ID!): User
  users(filter: UserFilter, pagination: Pagination): UserConnection!
  
  # Artwork queries
  artwork(id: ID!): Artwork
  artworks(filter: ArtworkFilter, pagination: Pagination): ArtworkConnection!
  
  # Marketplace queries
  listing(id: ID!): Listing
  listings(filter: ListingFilter, pagination: Pagination): ListingConnection!
  
  # Analytics queries
  marketStats(period: Period!): MarketStats!
  trendingArtworks(limit: Int!): [Artwork!]!
}

type Mutation {
  # User mutations
  updateProfile(input: UpdateProfileInput!): User!
  
  # Artwork mutations
  createArtwork(input: CreateArtworkInput!): Artwork!
  listArtwork(input: ListArtworkInput!): Listing!
  
  # Bidding mutations
  placeBid(input: PlaceBidInput!): Bid!
  acceptBid(bidId: ID!): Transaction!
  
  # Governance mutations
  createProposal(input: CreateProposalInput!): Proposal!
  castVote(input: CastVoteInput!): Vote!
}

type Subscription {
  # Real-time updates
  artworkUpdated(id: ID!): Artwork!
  newBid(listingId: ID!): Bid!
  proposalUpdated(id: ID!): Proposal!
}
```

#### 6.1.3 WebSocket Events
```typescript
// Client -> Server
socket.emit('join:artwork', { artworkId });
socket.emit('join:chat', { roomId });
socket.emit('send:message', { roomId, message });
socket.emit('place:bid', { listingId, amount });

// Server -> Client
socket.on('artwork:updated', (data) => {});
socket.on('bid:placed', (data) => {});
socket.on('message:received', (data) => {});
socket.on('user:online', (data) => {});
```

### 6.2 Blockchain Interfaces

#### 6.2.1 Smart Contract ABIs
```typescript
// Gallery Factory Interface
interface IGalleryFactory {
  createGallery(name: string, commission: number): Promise<string>;
  getGalleryCount(): Promise<number>;
  getUserGalleries(user: string): Promise<string[]>;
}

// Marketplace Interface
interface IMarketplace {
  listNFT(tokenAddress: string, tokenId: number, price: BigNumber): Promise<void>;
  buyNFT(listingId: number): Promise<void>;
  cancelListing(listingId: number): Promise<void>;
}

// Governance Interface
interface IGovernance {
  propose(description: string, actions: Action[]): Promise<number>;
  castVote(proposalId: number, support: boolean): Promise<void>;
  execute(proposalId: number): Promise<void>;
}
```

#### 6.2.2 Oracle Interface
```typescript
interface ITEEOracle {
  // Submit Bitcoin transaction proof
  submitOrdinalProof(
    txId: string,
    proof: MerkleProof,
    inscriptionData: InscriptionData
  ): Promise<void>;
  
  // Verify ordinal ownership
  verifyOwnership(
    ordinalId: string,
    owner: string
  ): Promise<boolean>;
  
  // Get attestation data
  getAttestation(
    ordinalId: string
  ): Promise<Attestation>;
}
```

---

## 7. Security Design

### 7.1 Authentication & Authorization

#### 7.1.1 Wallet-Based Authentication
```typescript
// Authentication Flow
1. Client requests nonce: GET /api/auth/nonce
2. Client signs message with wallet
3. Client submits signature: POST /api/auth/verify
4. Server verifies signature and issues JWT
5. Client includes JWT in subsequent requests
```

#### 7.1.2 Role-Based Access Control
```typescript
enum Role {
  ARTIST = 'ARTIST',
  GALLERY = 'GALLERY',
  BENEFACTOR = 'BENEFACTOR',
  COLLECTOR = 'COLLECTOR',
  ADMIN = 'ADMIN'
}

// Permission Matrix
const permissions = {
  [Role.ARTIST]: [
    'artwork:create',
    'artwork:update:own',
    'artwork:list:own',
    'collaboration:join'
  ],
  [Role.GALLERY]: [
    'gallery:manage:own',
    'artist:invite',
    'exhibition:create',
    'collection:curate'
  ],
  [Role.BENEFACTOR]: [
    'liquidity:provide',
    'liquidity:withdraw',
    'governance:vote:enhanced',
    'benefits:claim'
  ]
};
```

### 7.2 Smart Contract Security

#### 7.2.1 Security Patterns
```solidity
// Reentrancy Guard
modifier nonReentrant() {
    require(!locked, "No reentrancy");
    locked = true;
    _;
    locked = false;
}

// Access Control
modifier onlyGalleryOwner(uint256 galleryId) {
    require(galleries[galleryId].owner == msg.sender, "Not owner");
    _;
}

// Pausable
modifier whenNotPaused() {
    require(!paused, "Contract paused");
    _;
}
```

#### 7.2.2 Audit Checklist
- [ ] Reentrancy protection
- [ ] Integer overflow/underflow checks
- [ ] Access control validation
- [ ] Input validation
- [ ] Gas optimization
- [ ] Emergency pause mechanism
- [ ] Upgrade safety
- [ ] Oracle manipulation resistance

### 7.3 Data Security

#### 7.3.1 Encryption
```typescript
// Sensitive Data Encryption
class EncryptionService {
  // At-rest encryption for sensitive data
  encrypt(data: string): string {
    return crypto.AES.encrypt(data, process.env.ENCRYPTION_KEY);
  }
  
  // TLS for data in transit
  // Enforced at infrastructure level
}
```

#### 7.3.2 API Security
- Rate limiting per user/IP
- Request signing for critical operations
- CORS configuration
- Input sanitization
- SQL injection prevention (Prisma)
- XSS protection

### 7.4 Infrastructure Security

#### 7.4.1 Network Security
```yaml
# Kubernetes Network Policies
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: api-network-policy
spec:
  podSelector:
    matchLabels:
      app: api
  policyTypes:
  - Ingress
  - Egress
  ingress:
  - from:
    - podSelector:
        matchLabels:
          app: frontend
    ports:
    - protocol: TCP
      port: 3001
```

#### 7.4.2 Secrets Management
- Kubernetes secrets for sensitive data
- Environment-specific configurations
- Rotating API keys and tokens
- Secure key storage (HSM for production)

---

## 8. Performance Design

### 8.1 Frontend Performance

#### 8.1.1 Optimization Strategies
```typescript
// Code Splitting
const MarketplacePage = lazy(() => import('./pages/Marketplace'));

// Image Optimization
<Image
  src={artwork.image}
  alt={artwork.title}
  width={800}
  height={600}
  placeholder="blur"
  loading="lazy"
/>

// Query Optimization
const { data } = useQuery({
  queryKey: ['artworks', filters],
  queryFn: fetchArtworks,
  staleTime: 5 * 60 * 1000, // 5 minutes
  cacheTime: 10 * 60 * 1000, // 10 minutes
});
```

#### 8.1.2 Performance Metrics
- First Contentful Paint (FCP) < 1.8s
- Time to Interactive (TTI) < 3.9s
- Cumulative Layout Shift (CLS) < 0.1
- Largest Contentful Paint (LCP) < 2.5s

### 8.2 Backend Performance

#### 8.2.1 Database Optimization
```sql
-- Indexes for common queries
CREATE INDEX idx_artworks_artist_id ON artworks(artist_id);
CREATE INDEX idx_artworks_status ON artworks(status);
CREATE INDEX idx_listings_status_created ON listings(status, created_at DESC);
CREATE INDEX idx_bids_listing_id_amount ON bids(listing_id, amount DESC);

-- Composite indexes for complex queries
CREATE INDEX idx_artwork_search ON artworks(status, created_at DESC) 
  WHERE status IN ('LISTED', 'SOLD');
```

#### 8.2.2 Caching Strategy
```typescript
// Multi-level caching
class CacheService {
  // L1: In-memory cache (Node.js)
  private memoryCache = new LRUCache({ max: 1000 });
  
  // L2: Redis cache
  private redis: Redis;
  
  async get(key: string) {
    // Check L1
    let value = this.memoryCache.get(key);
    if (value) return value;
    
    // Check L2
    value = await this.redis.get(key);
    if (value) {
      this.memoryCache.set(key, value);
      return value;
    }
    
    return null;
  }
}
```

### 8.3 Blockchain Performance

#### 8.3.1 Gas Optimization
```solidity
// Batch operations
function batchListArtworks(
    uint256[] calldata tokenIds,
    uint256[] calldata prices
) external {
    require(tokenIds.length == prices.length, "Length mismatch");
    
    for (uint i = 0; i < tokenIds.length; i++) {
        _listArtwork(tokenIds[i], prices[i]);
    }
}

// Storage optimization
uint256 private constant ROLE_ARTIST = 1 << 0;
uint256 private constant ROLE_GALLERY = 1 << 1;
uint256 private constant ROLE_BENEFACTOR = 1 << 2;
```

#### 8.3.2 Oracle Optimization
- Batch attestation submissions
- Merkle proof compression
- Result caching
- Parallel verification

---

## 9. Deployment Design

### 9.1 Container Architecture

#### 9.1.1 Docker Configuration
```dockerfile
# Frontend Dockerfile
FROM node:18-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

FROM nginx:alpine
COPY --from=builder /app/out /usr/share/nginx/html
COPY nginx.conf /etc/nginx/nginx.conf
```

#### 9.1.2 Docker Compose
```yaml
version: '3.8'
services:
  frontend:
    build: ./packages/frontend
    ports:
      - "3000:80"
    environment:
      - NEXT_PUBLIC_API_URL=http://api:3001
  
  api:
    build: ./packages/backend
    ports:
      - "3001:3001"
    environment:
      - DATABASE_URL=postgresql://user:pass@postgres:5432/db
      - REDIS_URL=redis://redis:6379
    depends_on:
      - postgres
      - redis
  
  postgres:
    image: postgres:15
    environment:
      - POSTGRES_USER=user
      - POSTGRES_PASSWORD=pass
      - POSTGRES_DB=db
    volumes:
      - postgres_data:/var/lib/postgresql/data
  
  redis:
    image: redis:7-alpine
    volumes:
      - redis_data:/data
```

### 9.2 Kubernetes Deployment

#### 9.2.1 Deployment Configuration
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: api-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: api
  template:
    metadata:
      labels:
        app: api
    spec:
      containers:
      - name: api
        image: ordinals-marketplace/api:latest
        ports:
        - containerPort: 3001
        env:
        - name: DATABASE_URL
          valueFrom:
            secretKeyRef:
              name: db-secret
              key: url
        resources:
          requests:
            memory: "256Mi"
            cpu: "250m"
          limits:
            memory: "512Mi"
            cpu: "500m"
        livenessProbe:
          httpGet:
            path: /health
            port: 3001
          initialDelaySeconds: 30
          periodSeconds: 10
        readinessProbe:
          httpGet:
            path: /ready
            port: 3001
          initialDelaySeconds: 5
          periodSeconds: 5
```

#### 9.2.2 Auto-scaling
```yaml
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: api-hpa
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: api-deployment
  minReplicas: 3
  maxReplicas: 10
  metrics:
  - type: Resource
    resource:
      name: cpu
      target:
        type: Utilization
        averageUtilization: 70
  - type: Resource
    resource:
      name: memory
      target:
        type: Utilization
        averageUtilization: 80
```

### 9.3 CI/CD Pipeline

#### 9.3.1 GitHub Actions Workflow
```yaml
name: Deploy to Production
on:
  push:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '18'
      - run: npm ci
      - run: npm test
      - run: npm run test:e2e

  build:
    needs: test
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Build Docker images
        run: |
          docker build -t ordinals-marketplace/frontend:${{ github.sha }} ./packages/frontend
          docker build -t ordinals-marketplace/api:${{ github.sha }} ./packages/backend
      - name: Push to registry
        run: |
          docker push ordinals-marketplace/frontend:${{ github.sha }}
          docker push ordinals-marketplace/api:${{ github.sha }}

  deploy:
    needs: build
    runs-on: ubuntu-latest
    steps:
      - name: Deploy to Kubernetes
        run: |
          kubectl set image deployment/frontend-deployment frontend=ordinals-marketplace/frontend:${{ github.sha }}
          kubectl set image deployment/api-deployment api=ordinals-marketplace/api:${{ github.sha }}
          kubectl rollout status deployment/frontend-deployment
          kubectl rollout status deployment/api-deployment
```

### 9.4 Monitoring & Observability

#### 9.4.1 Metrics Collection
```yaml
# Prometheus Configuration
global:
  scrape_interval: 15s
  evaluation_interval: 15s

scrape_configs:
  - job_name: 'api-metrics'
    static_configs:
      - targets: ['api-service:3001']
    metrics_path: '/metrics'
  
  - job_name: 'node-exporter'
    static_configs:
      - targets: ['node-exporter:9100']
```

#### 9.4.2 Logging Architecture
```typescript
// Structured Logging
import { Logger } from '@nestjs/common';
import * as winston from 'winston';

const logger = winston.createLogger({
  format: winston.format.json(),
  transports: [
    new winston.transports.Console(),
    new winston.transports.File({ filename: 'app.log' }),
  ],
});

// Log aggregation with ELK stack
// Elasticsearch -> Logstash -> Kibana
```

---

## 10. Testing Strategy

### 10.1 Test Pyramid

```
         /\
        /  \    E2E Tests (10%)
       /────\   - Critical user flows
      /      \  - Cross-browser testing
     /────────\ Integration Tests (30%)
    /          \- API endpoint tests
   /            \- Database integration
  /──────────────\- Smart contract tests
 /                \ Unit Tests (60%)
/──────────────────\- Business logic
                    - Utility functions
                    - Component tests
```

### 10.2 Testing Frameworks

#### 10.2.1 Frontend Testing
```typescript
// Unit Tests (Jest + React Testing Library)
describe('ArtworkCard', () => {
  it('should display artwork information', () => {
    const artwork = mockArtwork();
    const { getByText, getByAltText } = render(
      <ArtworkCard artwork={artwork} />
    );
    
    expect(getByText(artwork.title)).toBeInTheDocument();
    expect(getByAltText(artwork.title)).toHaveAttribute('src', artwork.image);
  });
});

// E2E Tests (Playwright)
test('user can purchase artwork', async ({ page }) => {
  await page.goto('/marketplace');
  await page.click('[data-testid="artwork-card"]');
  await page.click('[data-testid="buy-now-button"]');
  await page.waitForSelector('[data-testid="transaction-success"]');
});
```

#### 10.2.2 Backend Testing
```typescript
// Unit Tests
describe('ArtworkService', () => {
  let service: ArtworkService;
  let prisma: MockPrismaService;

  beforeEach(() => {
    const module = Test.createTestingModule({
      providers: [ArtworkService, MockPrismaService],
    }).compile();
    
    service = module.get<ArtworkService>(ArtworkService);
    prisma = module.get<MockPrismaService>(PrismaService);
  });

  it('should create artwork', async () => {
    const dto = mockCreateArtworkDto();
    const result = await service.createArtwork(dto);
    
    expect(result).toMatchObject(dto);
    expect(prisma.artwork.create).toHaveBeenCalledWith({
      data: expect.objectContaining(dto),
    });
  });
});

// Integration Tests
describe('POST /api/artworks', () => {
  it('should create artwork with valid data', async () => {
    const response = await request(app.getHttpServer())
      .post('/api/artworks')
      .set('Authorization', `Bearer ${validToken}`)
      .send(mockArtworkData)
      .expect(201);
    
    expect(response.body).toHaveProperty('id');
    expect(response.body.title).toBe(mockArtworkData.title);
  });
});
```

#### 10.2.3 Smart Contract Testing
```solidity
// Foundry Tests
contract GalleryFactoryTest is Test {
    GalleryFactory factory;
    address alice = address(0x1);
    
    function setUp() public {
        factory = new GalleryFactory();
    }
    
    function testCreateGallery() public {
        vm.prank(alice);
        address gallery = factory.createGallery("Test Gallery", 10);
        
        assertEq(factory.getGalleryCount(), 1);
        assertEq(factory.getUserGalleries(alice)[0], gallery);
    }
    
    function testFailCreateGalleryWithInvalidCommission() public {
        vm.prank(alice);
        factory.createGallery("Test Gallery", 101); // Should fail
    }
}
```

### 10.3 Test Coverage Requirements

- **Overall Coverage**: ≥ 90%
- **Unit Tests**: ≥ 95%
- **Integration Tests**: ≥ 85%
- **E2E Tests**: Critical paths 100%
- **Smart Contracts**: 100% (including edge cases)

### 10.4 Performance Testing

#### 10.4.1 Load Testing
```javascript
// K6 Load Test Script
import http from 'k6/http';
import { check } from 'k6';

export let options = {
  stages: [
    { duration: '5m', target: 100 },  // Ramp up
    { duration: '10m', target: 100 }, // Stay at 100 users
    { duration: '5m', target: 200 },  // Ramp up more
    { duration: '10m', target: 200 }, // Stay at 200 users
    { duration: '5m', target: 0 },    // Ramp down
  ],
  thresholds: {
    http_req_duration: ['p(95)<500'], // 95% of requests under 500ms
    http_req_failed: ['rate<0.01'],   // Error rate under 1%
  },
};

export default function() {
  let response = http.get('https://api.ordinals-marketplace.com/artworks');
  check(response, {
    'status is 200': (r) => r.status === 200,
    'response time < 500ms': (r) => r.timings.duration < 500,
  });
}
```

#### 10.4.2 Stress Testing
- Concurrent user limits
- Database connection pooling
- Memory leak detection
- CPU utilization under load
- Network bandwidth usage

---

## Summary

This Software Design Document provides a comprehensive overview of the Ordinals Art Marketplace platform, covering:

1. **System Architecture**: Multi-layered, microservices-based design with cross-chain integration
2. **Component Design**: Detailed frontend and backend component structures
3. **Data Management**: Comprehensive database schema with caching strategies
4. **Security**: Multi-level security from authentication to infrastructure
5. **Performance**: Optimization strategies across all layers
6. **Deployment**: Container-based deployment with auto-scaling
7. **Testing**: Comprehensive testing strategy with high coverage requirements

The system is designed to be scalable, secure, and maintainable while providing a seamless user experience for all stakeholders in the digital art ecosystem.