# How to update Linux machine

###### [Home](https://eduardo-granados.github.io/)

---


- I wrote up a script to help users keep their Kali Linux users that use apt-get to stay up-to date.
- Check out how to set this up as a root user and have it run automatically as a [cron job](/blog_posts/cron_jobs.md).
- The `apt` command is a part of the package management software also named apt. Apt contains a whole suite of tools that allows us to manage the packages and sources of our software, and to install or remove software at the same time.



```bash
#! /bin/bash



startTime=$(date) # Time program starts



# Displays to terminal
echo "****************************************************"
echo "STARTING @ $startTime"
echo "****************************************************"



# Update commands - this part alone can be copied and the echo's can be removed
sudo apt-get update
echo "****************************************************"
sudo apt-get dist-upgrade -Vy
echo "****************************************************"
sudo apt-get autoremove -y
echo "****************************************************"
sudo apt-get autoclean
echo "****************************************************"
sudo apt-get clean



endTime=$(date) # Time program ends
# Display to terminal
echo ""
sleep 1s


# Displays to terminal
echo "****************************************************"
echo "ENDING @ $endTime"
echo "****************************************************"
```