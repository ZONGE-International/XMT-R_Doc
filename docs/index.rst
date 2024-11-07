import os

# Sphinx documentation generation for XMT-R including images
sphinx_doc = """
Geophysical Transmitter Controller (XMT-R) Documentation
=======================================================

Introduction
------------
The XMT-R by Zonge International is a specialized transmitter controller designed for geophysical applications. The device can be controlled through two main interfaces:

1. Directly on the hardware using its screen and physical buttons.
2. Remotely via a web interface, accessible when Wi-Fi is enabled on the device.

1. Hardware Control
--------------------

1.1 Main Page Overview
^^^^^^^^^^^^^^^^^^^^^^
The main page provides a quick view of essential information, including:

- **Selected Mode**: Displays the current operational mode.
- **Frequency**: Shows the frequency setting in use.

.. image:: img/hardware/img---3.gif
   :alt: Main page overview

The top section of the screen displays:

- **Number of Satellites**: Indicates the GPS satellite connection status.
- **Sync Status**: Displays "Searching for Sync" or "Locked."
- **XMT ID**: Identifies the unique transmitter ID.
- **Wi-Fi Status**: Shows if Wi-Fi is enabled or disabled.

.. image:: img/hardware/img---4.gif
   :alt: XMT ID display

1.2 Navigation and Buttons
^^^^^^^^^^^^^^^^^^^^^^^^^^
The XMT-R hardware includes:

- **UP Button**: Scrolls up through available options.
- **DOWN Button**: Scrolls down through options.
- **NEXT Button**: Short press cycles through options, while pressing for two seconds accesses the MENU page.

.. image:: screenshot/Screenshot\ 2024-11-06\ at\ 10.11.01.png
   :alt: Navigation buttons overview

1.3 Mode Adjustment on Main Page
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
To switch modes directly from the Main Page:

1. Make sure you have MODE selected (using the NEXT button).
2. Press and hold the UP or DOWN button for two seconds to change the mode. (This delay is for safety reasons to prevent accidental mode changes.)

.. image:: img_n/img---2.gif
   :alt: Mode adjustment illustration

1.4 Frequency Adjustment on Main Page
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
To adjust the frequency directly from the Main Page:

1. Make sure you have FREQUENCY selected (using the NEXT button).
2. Press the UP or DOWN button to increase or decrease the frequency setting.

.. image:: screenshot/Screenshot\ 2024-11-06\ at\ 10.34.56.png
   :alt: Frequency adjustment

1.5 Menu Options
^^^^^^^^^^^^^^^^
In the MENU page:

- **Mode Selection**: Choose between "Basic" and "Advanced" modes.
  - Basic Mode offers two options:
    - **100% DC**: Allows frequency selection from 0.000376 Hz up to 8192 Hz.
    - **50%**: Limits frequency selection to a range of 0.000376 Hz up to 64 Hz.
  - Advanced Mode includes additional options:
    - **100% DC**: Frequency range from 0.000376 Hz up to 8192 Hz.
    - **50%**: Frequency range from 0.000376 Hz up to 64 Hz.
    - **Custom**: Allows frequency selection from 0.000376 Hz up to 8192 Hz.
    - **MMR 5Hz**: Specialized mode for MMR applications, fixed at 5 Hz.
- **GPS Information**: Displays the current GPS status and satellite data.
- **Firmware Version**: Shows the firmware version installed.
- **Screen Light Control**: Turn the screen light on or off.
- **Wi-Fi Control**: Enable or disable Wi-Fi and view the device's IP address if Wi-Fi is active.

.. image:: img_n/img---3.gif
   :alt: Menu options overview

2. Web Interface Control
------------------------
The XMT-R also supports control through a web interface when Wi-Fi is enabled. Upon activation, an IP address is provided, allowing users to access the transmitter remotely.

2.1 Main Page Overview
^^^^^^^^^^^^^^^^^^^^^^
The main page of the web interface displays the same core information as the device screen:

- **Number of Satellites**: Indicates GPS connection status.
- **Sync Status**: Displays "Searching for Sync" or "Locked."
- **XMT ID**: Identifies the unique transmitter ID.
- **Mode Selection Dropdown**: Allows the user to select the desired mode.
- **Frequency Selection Dropdown**: Allows the user to select the frequency based on the current mode.

.. image:: screenshot/Screenshot\ 2024-11-06\ at\ 10.31.01.png
   :alt: Web interface main page overview

Additionally, a More button is available that:

- Displays detailed GPS Information.
- Provides access to switch between Advanced and Basic Mode settings.

2.2 Mode and Frequency Adjustment
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Users can interact with dropdown menus to select the desired Mode and Frequency based on their current mode. This selection is similar to using the hardware buttons but with the convenience of point-and-click interaction.

In **Custom Mode**, users also have the ability to: (This option is only available through the web app.)

- **Upload User Profiles**: These profiles are stored within the transmitter, allowing the user to switch easily between different pre-configured settings.

.. image:: img_n/img---5.gif
   :alt: User profile upload option

2.3 Admin Page
^^^^^^^^^^^^^^
The web interface includes an **Admin Page** that offers additional settings and firmware management options:

- **Firmware/Spiff Updates**: Users can upload new firmware versions or Spiff files.
- **FPGA Updates**: Update the internal FPGA of the transmitter.
- **Wi-Fi Settings**: Set the Wi-Fi mode to either Hotspot mode or connect to a Local Network by providing the network credentials.

.. image:: screenshot/Screenshot\ 2024-11-06\ at\ 10.33.01.png
   :alt: Admin page options
"""

# Save the generated Sphinx documentation to a .rst file
output_file_path = '/mnt/data/XMT-R_documentation.rst'
with open(output_file_path, 'w') as file:
    file.write(sphinx_doc)

output_file_path
