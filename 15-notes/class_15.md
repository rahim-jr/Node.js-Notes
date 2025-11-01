# HTTP Request Methods and OSI Model - Class 15

## HTTP Request Methods

There are 5 main types of HTTP requests:

### 1. GET Request
- **Purpose**: Client wants to retrieve information
- **Action**: Server sends information to the client
- **Example**: Fetching a list of posts

### 2. POST Request
- **Purpose**: Create new resources
- **Action**: Server takes information from client, creates new data, saves to database
- **Example**: Creating a new post

### 3. PUT Request
- **Purpose**: Complete update of existing resource
- **Action**: Total information update
- **Example**: Updating all fields of a post

### 4. PATCH Request
- **Purpose**: Partial update of existing resource
- **Action**: Update only specific fields of stored information
- **Example**: Updating only the title of a post

### 5. DELETE Request
- **Purpose**: Remove resources
- **Action**: Delete information from database
- **Example**: Deleting a post

## Facebook Example

Using Facebook status feature as an example:

1. **View Status List**: Client sends GET request → Server sends status list
2. **Create Status**: Client sends POST request → Server creates post in database
3. **Update Status**: Client sends PUT request → Server updates entire status
4. **Partial Update**: Client sends PATCH request → Server updates specific fields
5. **Delete Status**: Client sends DELETE request → Server removes status

## OSI Model (Open Systems Interconnection)

The OSI model has 7 layers:

1. **Physical Layer** - Hardware and physical connections
2. **Data Link Layer** - Error detection and correction
3. **Network Layer** - Routing and addressing
4. **Transport Layer** - Responsible for port management
   - Determines how many ports can be created on a computer
   - **Total available ports**: 65,535 ports per computer
5. **Session Layer** - Manages communication sessions
6. **Presentation Layer** - Data encryption and compression
7. **Application Layer** - User interface and application services

### Port Management
- Each computer can have up to **65,535 ports**
- Ports are managed by the Transport Layer
- Ports allow multiple services to run simultaneously on one computer
