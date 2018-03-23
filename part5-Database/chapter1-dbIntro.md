# The Database: A Pet with Strong Configuration Management

The first major component of our pipeline is our database server. We'll make use of Block Storage for the first time, install and configure our preferred RDBMS, and use a provider-level firewall to insure that nobody can access the database outside of our network.

## The Hybrid Approach: Why not Docker-ize the Database?

Since our front-end web server and CF engine will both run in Docker and we know that we're going to invest some time into configuring at least one Docker instance anyway, why not do the same with the database?

The answer is that, while it's perfectly valid to run your database as a container, the up-front investment of time places it outside the scope of this guide. The benefits of containerizing your database for production systems are realized primarily when you need a distributed \(Master/Slave\) database, and that is a much later-stage scalability concern than our web and application servers that benefit from containerization on day one.

#### ...but we'll still containerize the database for Development.

Since we want a portable and easily-replicated database for our developers, we'll use Docker in the Development stage of the pipeline later in the guide.

# Provisioning From the Template

We'll use the template we created in [Part 4](//part4-ourFirstVM/chapter1.md) as the foundation for our database droplet.  Select **Create Droplet** and then the **Snapshots sub-menu. **The snapshot we created will be called **Ubuntu template** -- DigitalOcean prepends the snapshot name with the OS name, and **template** is the name we assigned, so our Create Droplets page should look like this:

![](/assets/snip_20180322114159.png)

Select an instance size with at least 3 or 4 GB of RAM, and this time we're going to add **Block Storage.**

![](/assets/snip_20180322124340.png)We'll put our database and log files on the block storage drive. It's trivial to enlarge block storage devices later, so unless you're importing existing databases, 20 GB should be more than enough for our initial database storage.

Don't forget to enable **Private Networking **since we'll want our application server droplet\(s\) to access the database.

Give your droplet a name like **database** and once it's ready, we'll learn how to assign a floating IP address and attach block storage to our instance.

![](/assets/snip_20180322130047.png)
