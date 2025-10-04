# Docker Multi-Container Setup Guide

## Setting up 2 Containers for Docker

### Initial Setup Steps

1. **Comment the app part** in docker-compose.yml file
2. **Comment the run start command** in Dockerfile
3. **Start containers**: `docker-compose up`

### Database Container Verification

1. **Open another bash terminal** to check the database container:

   ```bash
   # Check running containers
   docker ps
   
   # Access database container
   docker exec -it <container id> sh
   
   # Connect to MySQL
   mysql -u root -p
   # Password: 123456
   
   # Check databases
   show databases;
   
   # Use specific database
   use <database name>;
   
   # Check tables
   show tables;
   
   # Exit MySQL
   exit;
   ```

### Application Setup

1. **Return to previous bash terminal**
2. **Comment out docker-compose file app part**
3. **Start services**: `docker-compose up`
4. **Wait for database seed to complete`

### Final Configuration

1. **In Dockerfile**:
   - Comment out `run seed`
   - Comment out `run start`

2. **Rebuild containers**: `docker-compose build`
3. **Start final setup**: `docker-compose up`

### Testing

1. **Check in Postman** :-)

## Workflow Summary

1. **Database Setup** → Comment app, start DB container
2. **Verify Database** → Check tables and data
3. **Application Setup** → Uncomment app, start both containers
4. **Final Configuration** → Comment seed/start, rebuild
5. **Testing** → Verify with Postman

## Key Commands

```bash
# Start containers
docker-compose up

# Check running containers
docker ps

# Access container shell
docker exec -it <container id> sh

# Rebuild containers
docker-compose build
```
