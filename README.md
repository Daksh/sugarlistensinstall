Sugar Listens Installation
==========================

Sugarlistens repo: https://github.com/rparrapy/sugarlistens

##Setup and Run

1. Follow the steps on http://developer.sugarlabs.org/dev-environment.md.html to have sugar-build up and running

2. Clone https://github.com/rparrapy/sugarlistens and https://github.com/rparrapy/sugar/tree/speech-recognition/extensions/deviceicon/speech

3. Instal the dependencies with 
  ```sudo yum install pocketsphinx pocketsphinx-libs pocketsphinx-plugin pocketsphinx-devel pocketsphinx-python pocketsphinx-models git python-setuptools python-lockfile```

4. Generate sugarlistens rpm
  ```
    sudo yum install rpmdevtools rpmlint
    ./genrpm.sh 0.0.1
  ```
 
5. Installing the rpm
  ```
    cd  $HOME/rpmbuild/RPMS/noarch
    yum install sugarlistens-0.0.1-1.noarch.rpm (this will install sugarlistens on your machine, as a systemd service)
  ```

6. Enable the systemd service [Only Once]
  ```systemctl --user enable sugarlistens```

7. Start the systemd service
  ```systemctl --user start sugarlistens ```

8. Clone the maze activity and run it in a separate terminal
