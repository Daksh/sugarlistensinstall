Sugar Listens Installation
==========================

Sugarlistens repo: https://github.com/rparrapy/sugarlistens

##Setup and Run

1. Follow the steps on http://developer.sugarlabs.org/dev-environment.md.html to have sugar-build up and running

2. Instal the dependencies with [in sugar's shell]
  ```
  sudo yum install pocketsphinx pocketsphinx-libs pocketsphinx-plugin pocketsphinx-devel pocketsphinx-python pocketsphinx-models git python-setuptools python-lockfile
  ```

3. Clone https://github.com/rparrapy/sugarlistens and https://github.com/rparrapy/sugar/tree/speech-recognition/extensions/deviceicon/speech
  ```
  git clone -b speech-recognition https://github.com/rparrapy/sugar
  cd sugar-build
  git clone https://github.com/rparrapy/sugarlistens
  ```

4. Generate sugarlistens rpm
  ```
  cd sugar-build/sugarlistens
  sudo yum install rpmdevtools rpmlint
  ./genrpm.sh 0.0.1
  ```
 
5. Installing the rpm (this will install sugarlistens on your machine, as a systemd service)
  ```
  cd  $HOME/rpmbuild/RPMS/noarch
  sudo yum install sugarlistens-0.0.1-1.noarch.rpm
  ```

6. Install sugarlistens [in sugar's shell]
  ```
  cd sugarlistens
  python setup.py install
  ```

7. Enable the systemd service [Only Once]
  ```
  systemctl --user enable sugarlistens
  ```

8. Start the systemd service
  ```
  systemctl --user start sugarlistens 
  ```

9. Copy the speech folder from the dir sugar/extensions/deviceicon/speech ['sugar' is the clone we did of the speech-recognition branch of https://github.com/rparrapy/sugar repository] and paste it inside sugar-build/build/out/install/share/sugar/extensions/deviceicon/ 

10. Clone the maze activity 
  ```
  cd sugar-build/activities
  git clone https://github.com/rparrapy/maze
  ```
  
11. Run sugar
  ```
  ./osbuild run
  ```


Note: Where ever it is written that the commands need to be run in sugar's shell, You need to 
```
cd sugar-build
./osbuild shell
```
and then run those commands
