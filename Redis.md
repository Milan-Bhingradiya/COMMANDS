# Redis Complete Guide

## Installing Redis

### Linux (Ubuntu/Debian)
```sh
sudo apt update
sudo apt install redis-server
```

### macOS (Using Homebrew)
```sh
brew install redis
```

### Windows (Using WSL or Docker)
Redis is not officially supported on Windows, but you can use WSL or Docker:

#### Using WSL
```sh
sudo apt update
sudo apt install redis-server
```

#### Using Docker
```sh
docker run --name redis -d -p 6379:6379 redis
```

---

## Starting and Stopping Redis

```sh
redis-server         # Start Redis server
redis-cli           # Start Redis CLI
sudo systemctl start redis   # Start Redis (Linux)
sudo systemctl stop redis    # Stop Redis (Linux)
sudo systemctl restart redis # Restart Redis
```

## Checking Redis Version
```sh
redis-server --version
```

## Basic Redis Commands

```sh
SET key value       # Store a key-value pair
GET key            # Retrieve a value
DEL key            # Delete a key
EXISTS key         # Check if a key exists
EXPIRE key seconds # Set expiration time
TTL key            # Check remaining time to live
```

## Working with Lists
```sh
LPUSH list value   # Push a value to a list (left)
RPUSH list value   # Push a value to a list (right)
LPOP list         # Remove and get first element
RPOP list         # Remove and get last element
LRANGE list 0 -1  # Get all elements in a list
```

## Working with Hashes
```sh
HSET user:id name "John Doe"
HGET user:id name
HGETALL user:id
```

## Working with Sets
```sh
SADD myset value1 value2 value3  # Add multiple values
SMEMBERS myset                   # Get all set members
SREM myset value1                 # Remove a value from set
```

## Working with Sorted Sets
```sh
ZADD leaderboard 100 user1 200 user2 150 user3
ZRANGE leaderboard 0 -1 WITHSCORES
```

## Persisting Data
```sh
SAVE  # Save snapshot of DB synchronously
BGSAVE  # Save snapshot asynchronously
```

## Configuring Redis
Configuration file is located at `/etc/redis/redis.conf` (Linux) or `/usr/local/etc/redis.conf` (macOS).

To modify configurations, open the file:
```sh
sudo nano /etc/redis/redis.conf
```
Restart Redis after changes:
```sh
sudo systemctl restart redis
```

## Enabling Redis as a Service
```sh
sudo systemctl enable redis
```

## Checking Redis Logs
```sh
tail -f /var/log/redis/redis-server.log
```

