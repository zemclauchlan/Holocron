> This step is optional.

If you are programming on a desktop computer or laptop (not chromebook), it is possible to configure your device to develop this project on.

First you need to install **Visual Studio Code** and **Docker**.

Once that's been done, you can clone the project to your computer. 


Open the project in Visual Studio code by choosing Open Folder from the file menu. Choose the folder that you clones the project into.

![[vsCodeOpen.png]]

When the project opens, you'll be asked whether you want to reopen the project in the container.

![[vsCodeOpenInContainer.png]]

Choose that option and the project will reopen, as well as Docker in the background. 

You can continue to configure and develop the project as normal.

## Why?

This configures your device in the same manner as Codespaces, except you're developing on your computer, meaning it's a bit faster, and less reliant on a stable internet connection.

# Debug Option

> [!Note]- This may only work in VSCode
> This may speed up development time.

One of the main annoyances with developing in Flask is that you have to stop and restart the server when developing to test new code.
Running the server in **debug** mode can make this process faster as you don't need to restart the server!

## Initialise

Click on the `Run and Debug` tab, and click on the run button indicated

![[flaskDebugRun.png]]


The remainder of your development process will be the same, except you **do not** need to regularly restart the server to test new code!