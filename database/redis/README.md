This service sets up a Redis Server with Ubuntu 20.

The output of deployment will be:
1. Ubuntu User Password - To ssh into Redis Server
2. Port on which Redis Server is running
3. Password for Authentication to Redis

Note: To access Redis Server from any other client instance, the user needs to add the 'bin-redis-client' Security group. This security group is to be assigned to any instance that should be allowed to access Redis instances.
