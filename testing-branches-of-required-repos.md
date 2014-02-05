Using docker if you need to test a specific branch of one of our required repositories, like unilangs or babelsubs, you can open a bash shell of the docker images, and then change branches there.

1. Run the command to open a bash shell to the amara-dev image, adding in the -p argument to pass the port out.

<tt>
docker run -i -t -h=unisubs.example.com -cidfile=/home/jed/unisubs/docker-dev-environment/cidfiles/amara-dev-shell-130a53ea8e -p 8000:8000 -e DJANGO_SETTINGS_MODULE=docker_dev_settings -v /home/jed/unisubs:/opt/apps/unisubs -w /opt/apps/unisubs/ amara-dev /bin/bash  --init-file /opt/ve/unisubs/bin/activate
</tt>

2.  <code>cd /opt/ve/unisubs/src/<repo> </code> and check out the correct branch
3. Delete the existing src from the python site packages.
ex:  babelsubs from /opt/ve/unisubs/lib/python/site-packages/babelsubs*
4. Run setup.py install for that package
ex:  <code> /opt/ve/unisubs/bin/python setup.py install </code> 
5. Go back to /opt/apps/unisubs
6. execute runserver
<code>/opt/ve/unisubs/bin/python manage.py runserver 0.0.0.0:8000</code>

If you want to run the selenium tests in there...

You'll need to run xvfb, set the display for the DJANGO_LIVE_SERVER_PORTS, then run the tests.

1. <code>xvfb -ac :99 &</code>

2. <code> export DJANGO_LIVE_TEST_SERVER_ADDRESS=localhost:8090-8100,9000-9200 </code>

3. <code>export DISPLAY=:99</code>

4. <code>/opt/ve/unisubs/bin/python manage.py test webdriver_testing --settings=dev_settings_selenium </code>

