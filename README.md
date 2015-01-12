Sugar Listens Installation
==========================

Speech recognition for the Sugar Learning Platform.

##Introduction
Sugar Listens is a GSoC 2014 project that seeks to provide speech recognition capabilities to Sugar Activity developers. For more information, please refer to the [project proposal](https://wiki.sugarlabs.org/go/Summer_of_Code/2014/Sugar_Listens). It has been made by [Rodrigo Parra](https://twitter.com/rparrapy) under the mentoring of [Martin Abente Lahaye](https://twitter.com/tchx84)

This guide has been made for a Fedora 20 machine running sugar environment, similar steps can be followed to install it on other Operating Systems, with minor changes. 

If you are successfully able to follow all the given steps, you will have a Maze activity controllable by Speech. And you can further use the installed sugar listens to use it with other activities! 

##Setup and Run

1. Follow the steps on http://developer.sugarlabs.org/dev-environment.md.html to have `sugar-build` up and running

2. Install the dependencies with [in sugar's shell]
  ```
  sudo yum install pocketsphinx pocketsphinx-libs pocketsphinx-plugin pocketsphinx-devel pocketsphinx-python pocketsphinx-models git python-setuptools python-lockfile
  ```
 This command is required for the Sugar Listens code to work, as it installes the dependencies that the code requires.

3. Clone https://github.com/rparrapy/sugarlistens and https://github.com/rparrapy/sugar/tree/speech-recognition/extensions/deviceicon/speech
  ```
  git clone -b speech-recognition https://github.com/rparrapy/sugar
  cd sugar-build
  git clone https://github.com/rparrapy/sugarlistens
  ```

4. Generate Sugar Listens [RPM] (https://en.wikipedia.org/wiki/RPM_Package_Manager)
  ```
  cd sugar-build/sugarlistens
  sudo yum install rpmdevtools rpmlint
  ./genrpm.sh 0.0.1
  ```
 
5. Installing the RPM (this will install Sugar Listens on your machine, as a [systemd service] (https://wiki.archlinux.org/index.php/Systemd))
  ```
  cd  $HOME/rpmbuild/RPMS/noarch
  sudo yum install sugarlistens-0.0.1-1.noarch.rpm
  ```

6. Install Sugar Listens [in sugar's shell]
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

9. Copy the speech folder from the directory sugar/extensions/deviceicon/speech ['sugar' is the clone we did of the speech-recognition branch of https://github.com/rparrapy/sugar repository] and paste it inside sugar-build/build/out/install/share/sugar/extensions/deviceicon/ 

10. Clone the [voice enabled maze activity](https://github.com/rparrapy/maze) so that you can test your sugar listens,
  ```
  cd sugar-build/activities
  git clone https://github.com/rparrapy/maze
  ```
  
11. Run sugar
  ```
  ./osbuild run
  ```


##Note 
* We are generating a RPM, so that it can be installed as a systemd service. Which would then, enable us to run the service parallel to running the sugar environment, and also to integrate the two, we need to install it under sugar, by using the python install command.
* Wherever it is written that the commands need to be run in sugar's shell, first you would need to run the following commands:

  ```
  cd sugar-build
  ./osbuild shell
  ```

##Still need help?
* You can find a video guide of the above steps at http://youtu.be/kbs8Iw2oVuI
* You can feel free to contact me, at dakshshah@live.com or the [developer of the activity](https://github.com/rparrapy)

##Source
Sugar Listens repository: https://github.com/rparrapy/sugarlistens

##Credits
This guide has been made by Daksh Shah, as a part of Google Code In 2014, task: https://www.google-melange.com/gci/task/view/google/gci2014/5253486857945088
