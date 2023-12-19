---
title: "Nvidia Jetson Nano Basic Setup Guide"
date: "Mar 13, 2023"
---
<div>
  <style>
    /* Neon colors */
    :root {
      --neon-yellow: #f4d03f;
      --neon-pink: #f62459;
      --neon-blue: #0dc9f7;
      --neon-green: #39ff14;
      --neon-purple: #586AE2;
    }
  </style>

  <h3>Here's a record of my setup process. If you need guidance for <a style="color: var(--neon-pink);" href="https://github.com/davidmallasen/LiveChess2FEN">LiveChess2FEN</a>, refer to the original author's page, ensuring you check the version before installation!</h3>
    <h3 style="color: var(--neon-yellow);"><b>1.Writing image file and bootup</b></h3>
    <ol type="I">
        <li><span style="color: var(--neon-purple);">Format your microSD via SD Memory Card Formatter</span>
        <img src="https://developer.nvidia.com/sites/default/files/akamai/embedded/images/jetsonNano/gettingStarted/Jetson_Nano-Getting_Started-Windows-SD_Card_Formatter.png" loading="lazy" >
        </li>
        <li><span style="color: var(--neon-purple);">Wrting image file into microSD via balenaEtcher</span><br>
        For LiveChess2FEN, I recommend using<a style="color: var(--neon-pink);" href="https://developer.nvidia.com/embedded/jetpack-sdk-46">JetPack 4.6</a>
        <img src="https://developer.nvidia.com/sites/default/files/akamai/embedded/images/jetsonNano/gettingStarted/Jetson_Nano-Getting_Started-Windows-Etcher.png" loading="lazy" >
        </li>
        <li><span style="color: var(--neon-purple);">First boot</span><br>
        Note: If you using DC power supply, you will need to fit a jumper to J48. You may check the detail on this <a style="color: var(--neon-pink);" href="https://forums.developer.nvidia.com/t/power-supply-considerations-for-jetson-nano-developer-kit/71637">page</a>.
        <img src="https://global.discourse-cdn.com/nvidia/original/3X/7/8/787490861ef6850d88bc66323867e4b180f6930a.png" loading="lazy" >
        The green LED next to the Micro-USB connector will light as soon as the board is power on. When you boot the first time, you will need to set some operating system setting.
        </li>
        <li><span style="color: var(--neon-purple);">WiFi dongle(Optional)</span><br>
        If your WiFi adapters that are based on the RTL8812BU and RTL8822BU chipset, you will need to install drivers for the adapters.
        You can find more details on this <a style="color: var(--neon-pink);" href="https://github.com/morrownr/88x2bu-20210702">page</a><br>
        Note: Try NOT to plug your adapter in before the installation is completed. Since the OS will try to install drivers that won't fit, then you have to remove the one OS installed before you do the following steps.
            <ol type = "1">
                <li>Update and upgrade system packages(you will need to connect your Nano to internet via LAN cable).<br>
                Open terminal then: 
{%highlight python%}
 sudo apt update && sudo apt upgrade
{%endhighlight%}
                Once the update & upgrade is completed, reboot your board.
{%highlight python%}
 sudo reboot
{%endhighlight%}
                </li>
                <li>Install the required packages<br>
{%highlight python%}
 sudo apt install -y build-essential dkms git iw
{%endhighlight%}
                </li>
                <li>Download the driver and run the installation script<br>
{%highlight python%}
 mkdir -p ~/src
 cd ~/src
 git clone https://github.com/morrownr/88x2bu-20210702.git
 cd ~/src/88x2bu-20210702
 sudo ./install-driver.sh
{%endhighlight%}        
                After reboot, your WiFi adapter should work just fine.       
                </li>
            </ol>
        </li>
    </ol>
</div>

    


