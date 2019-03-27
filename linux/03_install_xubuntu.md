# Install Xubuntu

Now that we have a virtual machine, we need to install an operating system for the virtual machine. We will use [Xubuntu](https://xubuntu.org) because [Ubuntu](https://www.ubuntu.com/) is a very popular distribution of Linux, and most bioinformatics programs and scripts should be able to run on a Ubuntu system.

1. Make sure that the `Xubuntu` virtual machine from the previous step is selected, then click the `Start` button to start the machine.

    ![Start Machine](assets/03-01_install_xubuntu.png)

2. Click on the `folder` icon to choose the `Xubuntu ISO` downloaded previously.

    ![Start Machine](assets/03-02_install_xubuntu.png)

3. Navigate to the folder where the `Xubuntu ISO` was downloaded, select the file, and click the `Open` button to continue.

    ![Start Machine](assets/03-03_install_xubuntu.png)

4. Make sure that the `xubuntu-18.04-desktop-amd64.iso` file is selected in the menu.

    ![Start Machine](assets/03-04_install_xubuntu.png)

5. When given the options to `Try Xubuntu` or `Instal Xubuntu`, select `Install Xubuntu`.

    ![Start Machine](assets/03-05_install_xubuntu.png)

6. Keyboard layout selected should be `English (US)`, then click the `Continue` button to go to the next step.

    ![Start Machine](assets/03-06_install_xubuntu.png)

7. Select the `Download updates while installing Xubuntu` option to download necessary updates to the operating system, then click `Continue`.

    ![Start Machine](assets/03-07_install_xubuntu.png)

8. Select the `Erase disk and install Xubuntu` option, then click the `Install Now` button to proceed.

    ![Start Machine](assets/03-08_install_xubuntu.png)

9. Confirm the installation procedue by selecting the `Continue` button.

    ![Start Machine](assets/03-09_install_xubuntu.png)

10. Select `Seoul` on the map to set the time of the operating system, then click `Continue`.

    ![Start Machine](assets/03-10_install_xubuntu.png)

11. Finally, enter your `name`, `username`, and selected a `password` for your Xubuntu account. Click the `Continue` button to start the installation procedure.

    ![Start Machine](assets/03-11_install_xubuntu.png)

12. Xubuntu will now be installed on the virtual machine environment, this step can take several minutes or longer depending on the speed of your computer.

    ![Start Machine](assets/03-12_install_xubuntu.png)

13. After the install procedure is finished, click the `Restart Now` button to restart the Xubuntu system.

    ![Start Machine](assets/03-13_install_xubuntu.png)

14. After Xubuntu has finished re-starting (you might have to enter the password you created in step `11`), enter your account password to log-in to Xubuntu.

    ![Start Machine](assets/03-14_install_xubuntu.png)

15. Xubuntu should ask if you would like to update the operating system and other necessary software. Click the `Install Now` button, and then re-start Xubuntu after the updated software has been installed if necessary.

    ![Start Machine](assets/03-15_install_xubuntu.png)


Now, `Xubuntu` should be successfully installed on your VirtualBox machine. Next, we will install Python, R and other common programming and statistical packages using the best available management and distribution system for data scientists and analysts: [Anaconda](https://anaconda.org).


[ [Index](./README.md) ] [ [Back](./02_install_virtualbox.md) ] [ [Next](./04_install_anaconda.md) ]