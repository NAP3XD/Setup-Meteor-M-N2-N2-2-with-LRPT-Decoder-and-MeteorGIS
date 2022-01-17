# Setup-Meteor-M-N2-N2-2-with-LRPT-Decoder-and-MeteorGIS

<!DOCTYPE html>
<html class="no-js" lang="en">
  <head>
    <meta http-equiv="content-type" content="text/html; charset=UTF-8">
    <meta charset="utf-8">
    <meta http-equiv="x-ua-compatible" content="ie=edge">
    <title>Setup Meteor M-N2/N2-2 with LRPTDecoder</title>
    <meta name="description" content="">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="canonical" href="http://html5-templates.com/">
    <link rel="apple-touch-icon" href="apple-touch-icon.png">
    <!-- Place favicon.ico in the root directory -->
    <link rel="stylesheet" href="style.css">
    <script src="js/vendor/modernizr-2.8.3.min.js"></script>
  </head>
  <body>
    <!--[if lt IE 8]>
            <p class="browserupgrade">You are using an <strong>outdated</strong> browser. Please <a href="https://browsehappy.com/">upgrade your browser</a> to improve your experience.</p>
        <![endif]-->
    <div class="wrapAll clearfix">
      <div class="mainsection"><br>
        <div class="article">
          <h1>Setup Meteor M-N2/N2-2 with LRPT-Decoder</h1>
          <h1> </h1>
          <div class="articleRight"> <img src="img/meteor_m_2.gif"
              alt="sat" width="121" height="70"><br>
          </div>
          <br>
          <p style="box-sizing: border-box; outline: none; margin: 0px
            0px 17px; padding: 0px; font-size: 14px; line-height: 1.8;
            color: rgb(49, 49, 49); font-family: Oxygen, sans-serif;
            font-style: normal; font-variant-ligatures: normal;
            font-variant-caps: normal; font-weight: 400; letter-spacing:
            normal; orphans: 2; text-align: start; text-indent: 0px;
            text-transform: none; white-space: normal; widows: 2;
            word-spacing: 0px; -webkit-text-stroke-width: 0px;
            background-color: rgb(255, 255, 255); text-decoration-style:
            initial; text-decoration-color: initial;">The Meteor-M
            series are equipped with two imaging payloads. MSU-MR is a
            low-resolution instrument operating at visible-light and
            near-infrared wavelengths.<br>
            It will take wide-angle images of the Earth to help monitor
            cloud cover and the icecaps. The second imager, KMSS-2,
            provides complimentary high-resolution visible-light images
            of more specific areas. <br>
            The satellite also carries two sounding instruments: the
            MTVZA-GYa microwave radiometer and IKFS-2 infrared
            spectrometer, which will build profiles of temperatures,
            humidity and wind conditions within the atmosphere.</p>
          <p style="box-sizing: border-box; outline: none; margin: 0px
            0px 17px; padding: 0px; font-size: 14px; line-height: 1.8;
            color: rgb(49, 49, 49); font-family: Oxygen, sans-serif;
            font-style: normal; font-variant-ligatures: normal;
            font-variant-caps: normal; font-weight: 400; letter-spacing:
            normal; orphans: 2; text-align: start; text-indent: 0px;
            text-transform: none; white-space: normal; widows: 2;
            word-spacing: 0px; -webkit-text-stroke-width: 0px;
            background-color: rgb(255, 255, 255); text-decoration-style:
            initial; text-decoration-color: initial;">As well as direct
            weather monitoring, Meteor-M series are used to relay data
            from automated weather stations across the Earths surface. <br>
            BRK, also known as SSPD, is the communications payload that
            will facilitate this, receiving data from stations and
            re-transmitting it for collection and analysis. <br>
            A Kospas-SARSAT emergency communications payload, RK-SM-MKA,
            is also carried to detect and relay distress signals, aiding
            search-and-rescue operations around the world.<br>
          </p>
          <p style="box-sizing: border-box; outline: none; margin: 0px
            0px 17px; padding: 0px; font-size: 14px; line-height: 1.8;
            color: rgb(49, 49, 49); font-family: Oxygen, sans-serif;
            font-style: normal; font-variant-ligatures: normal;
            font-variant-caps: normal; font-weight: 400; letter-spacing:
            normal; orphans: 2; text-align: start; text-indent: 0px;
            text-transform: none; white-space: normal; widows: 2;
            word-spacing: 0px; -webkit-text-stroke-width: 0px;
            background-color: rgb(255, 255, 255); text-decoration-style:
            initial; text-decoration-color: initial;">As for searching
            continuous ways to improve Meteor reception, Vasili
            (rtl-sdr.ru - Plugins) and Oleg (LrptDecoder) did have the
            great idea to develop a QPSK Plugin in order to receive
            Meteor M-N2 images in real time thru LrptDecoder.<br>
            Since 2019 there are 2 Meteor satellites so we need another
            config/setup and trying to automate configuration changes
            with having minimal user input.</p>
          <p style="box-sizing: border-box; outline: none; margin: 0px
            0px 17px; padding: 0px; font-size: 14px; line-height: 1.8;
            color: rgb(49, 49, 49); font-family: Oxygen, sans-serif;
            font-style: normal; font-variant-ligatures: normal;
            font-variant-caps: normal; font-weight: 400; letter-spacing:
            normal; orphans: 2; text-align: start; text-indent: 0px;
            text-transform: none; white-space: normal; widows: 2;
            word-spacing: 0px; -webkit-text-stroke-width: 0px;
            background-color: rgb(255, 255, 255); text-decoration-style:
            initial; text-decoration-color: initial;">(Check current
            Meteor Mode's overhere: <a
              href="http://happysat.nl/Meteor/html/Meteor_Status.html"
              target="_blank">http://happysat.nl/Meteor/html/Meteor_Status.html</a>)<br>
          </p>
          <br>
          <div class="contentsPanel">
            <div class="contentsHeader">Contents</div>
            <ul>
              <li> <span>1</span>Overview
                <ul>
                  <li><span>1.1&nbsp; <a href="#Hardware_Details">Hardware</a></span>
                  </li>
                  <li><span>1.2&nbsp; <a href="#Software_">Software</a></span>
                  </li>
                  <li><span>1.3&nbsp; <a href="#Setup_Orbitron_">Setup
                        Orbitron/SDRSharp</a><br>
                    </span></li>
                  <li><span>1.4&nbsp; <a
                        href="#Setup_DDE-Tracking_Client__SDRSharp">Setup
                        DDE-Tracker</a></span><br>
                  </li>
                  <li><span>1.5&nbsp; <a href="#Setup_QPSK_Plugin_">Setup
                        Meteor Demodulator Plugin</a></span><br>
                  </li>
                  <li><span>1.6 </span><span><a
                        href="#Setup_LRPT-Decoder_for">LRPT-Decoder
                        Meteor M-N2/2-2</a> </span></li>
                  <li><span>1.7 </span><a href="#Setup_MeteorGIS_">Setup
                      MeteorGIS M-N2 and N2-2<br>
                    </a></li>
                  <li>1.8&nbsp; <a href="#Manual_LRPT-Decoder_setup_">Manual
                      LRPT-Decoder setup</a></li>
                  <li>1.9&nbsp; <a href="#Other_Tools_">Other Tools</a></li>
                  <li><span>2.0 <a href="#Telemetry_Unpacker_">Telemetry
                        Unpacker</a></span></li>
                  <li><span>2.1 <a
                        href="#Amateur_Meteor_Images_Global_Observation">AMIGOS</a><br>
                    </span></li>
                </ul>
              </li>
            </ul>
          </div>
          <h2><a name="Hardware_Details"></a>Hardware<br>
          </h2>
          <br>
          To Use Real time image processing with Meteor, the following
          is needed for setup:<br>
          <br>
          <b>SDR Radio capable receiver:</b><br>
          <br>
          <br>
          <a href="https://airspy.com/airspy-r2/" target="_blank"><img
              src="img/airspy.png" alt="" width="256" height="204"
              border="0"></a><br>
          <br>
          <a href="https://airspy.com/airspy-r2/" target="_blank"
            style="text-decoration:none">Airspy R2</a><br>
          <br>
          Airspy R2 sets a new level of performance in the reception of
          the VHF and UHF bands thanks to its low-IF architecture based
          on Rafael Micro R820T2 and a high quality Oversampling 12bit
          ADC and state of the art DSP.<br>
          In Oversampling Mode, the Airspy R2 applies Analog RF and IF
          filtering to the signal path and increases the resolution to
          up to 16-bit using the software decimation. <br>
          <br>
          The Airspy R2, is 100% compatible with all the existing
          software including the de facto scanning standard SDR#, but
          also a number of popular software defined radio applications
          such as:<br>
          SDR-Radio, HDSDR, GQRX and GNU Radio.<br>
          <br>
          Continuous 24 – 1700 MHz native RX range.<br>
          3.5 dB NF between 42 and 1002 MHz, Maximum RF input of +10 dBm
          Tracking RF filters.<br>
          12bit ADC @ 20 MSPS (10.4 ENOB, 70dB SNR, 95dB SFDR), 10MSPS
          IQ output.<br>
          4.5v software switched Bias-Tee to power LNA’s and
          up/down-converters.<br>
          <br>
          <br>
          <br>
          <a
href="https://www.nooelec.com/store/sdr/sdr-receivers/nesdr/nesdr-smartee-sdr.html"
            target="_blank"><img src="img/nesdr.png" alt="" width="306"
              height="161" border="0"></a><br>
          <br>
          <a
href="https://www.nooelec.com/store/sdr/sdr-receivers/nesdr/nesdr-smartee-sdr.html"
            target="_blank">Nooelec NESDR SMArTee - Premium RTL-SDR</a><br>
          <br>
          Premium RTL-SDR w/ aluminum enclosure, always-on bias tee,
          0.5PPM TCXO and SMA input.<br>
          <br>
          The new PCB design of the NESDR SMArTee results in lower
          temperatures.<br>
          A custom heatsink is affixed to the primary PCB with 3M
          thermal adhesive, to wick heat away from the circuit board and
          towards the enclosure.<br>
          <br>
          Power consumption has been reduced by an average of 10mA,
          which means less heat is generated compared to other designs.<br>
          The result is much lower board-level temperatures--increasing
          stability, improving sensitivity and ensuring maximum
          frequency range capability.<br>
          <br>
          Bias-Tee features:<br>
          RF-suitable 4.2V regulator provides DC output to power your
          active electronics.<br>
          Bias-tee does NOT need to be enabled with hardware or software
          hacks. <br>
          No need to mess around with software or drivers to enable your
          bias tee!<br>
          <br>
          RTL2832U Demodulator/USB interface IC, R820T2 tuner IC<br>
          4.2V 200mA always-on bias tee<br>
          0.5PPM, ultra-low phase noise TCXO<br>
          Integrated custom heatsink, Female SMA antenna input<br>
          High-quality black brushed aluminum enclosure<br>
          <br>
          <br>
          <b>LNA/Filter:</b><br>
          <br>
          <a
href="https://www.nooelec.com/store/sdr/sdr-addons/sawbird/sawbird-plus-noaa-308.html"
            target="_blank"><img src="img/Sawbird.png" alt=""
              width="314" height="254" border="0"></a><br>
          <br>
          <a
href="https://www.nooelec.com/store/sdr/sdr-addons/sawbird/sawbird-plus-noaa-308.html"
            target="_blank">Nooelec SAWbird+ NOAA - Premium SAW Filter
            &amp; Cascaded Ultra-Low Noise LNA Module 137MHz Center
            Frequency.</a><br>
          <br>
          SAWbird+ NOAA is a self-contained dual LNA module with an
          integrated high-performance SAW filter, designed for Meteor
          and NOAA weather satellites.<br>
          And filter out unwanted interfering signals like pagers from
          airport's or other electronic pollution.<br>
          <br>
          It has a very high attenuation outside of the 5MHz bandpass
          region, centered around 137.5MHz, and a minimum of 30dB of
          gain within the bandpass region. <br>
          Nominal current draw is 180mA.<br>
          <br>
          The SAWbird+ series contains 2 ultra-low-noise LNAs sandwiched
          around a custom-designed, high-performance SAW filter centered
          at the frequency of interest. <br>
          Each LNA module has 2 EMI shields to separate each delicate
          LNA from external interference. <br>
          There are also M3 mounting holes available to mount the PCB in
          your custom enclosure or project with standard hardware.<br>
          <br>
          Each module allows for 3 different power options, but you
          should only power with one option at any given time!<br>
          The recommended power input through the SMA output port (for
          bias-tee capable SDRs like the above NESDR SMArTee) is 3V-5V
          DC. <br>
          Alternatively, if you don't have a bias-tee capable SDR, you
          can use the external power options through the microUSB port
          or the power input header.<br>
          <br>
          <br>
          <b>Antenna's:</b><br>
          <br>
          137Mhz Antenna Double Cross, Qfh, Turnstile or V-Dipoles:<br>
          <br>
          <a href="http://happysat.nl/Double_Cross/" target="_blank"
            style="text-decoration:none">Double Cross Jerry Martes
            Design</a><br>
          <br>
          <a href="http://jcoppens.com/ant/qfh/calc.en.php"
            target="_blank" style="text-decoration:none">QFH John
            Coppens</a><br>
          <br>
          <a
href="http://lu1epc.blogspot.com/2017/01/dibujo-antena-turnstile-137-mhz.html"
            target="_blank" style="text-decoration:none">Turnstile I6IBE</a><br>
          <br>
          <a
href="http://lna4all.blogspot.com/2017/02/diy-137-mhz-wx-sat-v-dipole-antenna.html"
            target="_blank" style="text-decoration:none">Horizontal
            V-Dipole</a><br>
          <br>
          <h2><a name="Software_"></a>Software<br>
          </h2>
          <br>
          <div class="articleRight"> <img src="img/sharp.png"
              alt="sdrsharp" width="558" height="203"><br>
            SDRSharp, Orbitron, LRPT-Decoder<br>
          </div>
          <a href="https://airspy.com/download" target="_blank"
            style="text-decoration:none">SDRSharp</a><br>
          <br>
          <p class="_1qeIAgB0cPwnLhDF9XSiJM" style="margin: 0px;
            padding: 0.25em 0px; border: 0px; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-variant-numeric: inherit; font-variant-east-asian:
            inherit; font-weight: 400; font-stretch: inherit; font-size:
            14px; line-height: inherit; font-family: &quot;Noto
            Sans&quot;, Arial, sans-serif; vertical-align: baseline;
            color: rgb(26, 26, 27); letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; background-color: rgb(255,
            255, 255); text-decoration-style: initial;
            text-decoration-color: initial;"><a
              href="http://happysat.nl/meteor_2.3.zip">Meteor
              Demodulator Plugin v2.3</a><br>
            <br>
            Added interaction with Meteor LRPT-Decoder via socket and
            write control commands from the scheduler.<br>
            Added a mode of automatic detection of symbol speed.<br>
          </p>
          <br>
          <img src="img/OQPSK.jpg" alt="" width="230" height="556"><br>
          <br>
          <a href="http://rtl-sdr.ru/uploads/download/ddetracker.zip"
            target="_blank" style="text-decoration:none">DDE Tracking
            Client v1.2</a><br>
          <br>
          <img src="img/ddetracker.jpg" alt="" width="226" height="191"><br>
          <br>
          Download Meteor Demodulator, DDE-Tracking Plugins and add to
          SDRSharp folder and copy the lines inside magic.txt to
          plugins.xml.<br>
          <br>
          M2 LRPT Decoder V56:<br>
          <br>
          - Returned the window size in height to the value that was
          used previously.<br>
          - Fixed a bug that prevented using different paths for the
          output files from M2 and M22.<br>
          <br>
          <p class="_1qeIAgB0cPwnLhDF9XSiJM" style="margin: 0px;
            padding: 0.25em 0px; border: 0px; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-variant-numeric: inherit; font-variant-east-asian:
            inherit; font-weight: 400; font-stretch: inherit; font-size:
            14px; line-height: inherit; font-family: &quot;Noto
            Sans&quot;, Arial, sans-serif; vertical-align: baseline;
            color: rgb(26, 26, 27); letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; background-color: rgb(255,
            255, 255); text-decoration-style: initial;
            text-decoration-color: initial;"><a
              href="http://happysat.nl/LRPT_Decoder_v56.zip">http://happysat.nl/LRPT_Decoder_v56.zip</a><br>
          </p>
          <p class="_1qeIAgB0cPwnLhDF9XSiJM" style="margin: 0px;
            padding: 0.25em 0px; border: 0px; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-variant-numeric: inherit; font-variant-east-asian:
            inherit; font-weight: 400; font-stretch: inherit; font-size:
            14px; line-height: inherit; font-family: &quot;Noto
            Sans&quot;, Arial, sans-serif; vertical-align: baseline;
            color: rgb(26, 26, 27); letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; background-color: rgb(255,
            255, 255); text-decoration-style: initial;
            text-decoration-color: initial;"><br>
            <img src="img/decoder_m2-2.png" alt="" width="686"
              height="376"><br>
          </p>
          <p class="_1qeIAgB0cPwnLhDF9XSiJM" style="margin: 0px;
            padding: 0.25em 0px; border: 0px; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-variant-numeric: inherit; font-variant-east-asian:
            inherit; font-weight: 400; font-stretch: inherit; font-size:
            14px; line-height: inherit; font-family: &quot;Noto
            Sans&quot;, Arial, sans-serif; vertical-align: baseline;
            color: rgb(26, 26, 27); letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; background-color: rgb(255,
            255, 255); text-decoration-style: initial;
            text-decoration-color: initial;"><br>
          </p>
          <p class="_1qeIAgB0cPwnLhDF9XSiJM" style="margin: 0px;
            padding: 0.25em 0px; border: 0px; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-variant-numeric: inherit; font-variant-east-asian:
            inherit; font-weight: 400; font-stretch: inherit; font-size:
            14px; line-height: inherit; font-family: &quot;Noto
            Sans&quot;, Arial, sans-serif; vertical-align: baseline;
            color: rgb(26, 26, 27); letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; background-color: rgb(255,
            255, 255); text-decoration-style: initial;
            text-decoration-color: initial;">This version of LRPTDecoder
            will work with both Meteor M-N2 and Meteor M-N2-2.</p>
          <p class="_1qeIAgB0cPwnLhDF9XSiJM" style="margin: 0px;
            padding: 0.25em 0px; border: 0px; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-variant-numeric: inherit; font-variant-east-asian:
            inherit; font-weight: 400; font-stretch: inherit; font-size:
            14px; line-height: inherit; font-family: &quot;Noto
            Sans&quot;, Arial, sans-serif; vertical-align: baseline;
            color: rgb(26, 26, 27); letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; background-color: rgb(255,
            255, 255); text-decoration-style: initial;
            text-decoration-color: initial;">By design, Meteor
            Demodulator will manage the settings of the decoder and this
            should reduce the number of settings,<br>
            that must be done when Meteor changes operating modes.<br>
          </p>
          <p class="_1qeIAgB0cPwnLhDF9XSiJM" style="margin: 0px;
            padding: 0.25em 0px; border: 0px; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-variant-numeric: inherit; font-variant-east-asian:
            inherit; font-weight: 400; font-stretch: inherit; font-size:
            14px; line-height: inherit; font-family: &quot;Noto
            Sans&quot;, Arial, sans-serif; vertical-align: baseline;
            color: rgb(26, 26, 27); letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; background-color: rgb(255,
            255, 255); text-decoration-style: initial;
            text-decoration-color: initial;">Example M2_LRPT_Decoder.ini
            configuration files for other modes are attached in the
            archive!<br>
          </p>
          <br>
          Download:<a href="http://www.meteorgis.space/" target="_blank">MeteorGIS</a><br>
          <br>
          Many changes read the changelog.<br>
          Use the tool "MeteorGIS_Configurator" who verify the .ini, and
          let you edit it more friendly. <br>
          <br>
          A Satellite Tracking program like Orbitron (<a
            href="http://www.stoff.pl" target="_blank"
            style="text-decoration:none">http://www.stoff.pl</a>) or
          WXTrack (<a
            href="http://www.satsignal.eu/software/wxtrack.htm"
            target="_blank" style="text-decoration:none">http://www.satsignal.eu/software/wxtrack.htm</a>).<br>
          <br>
          <h2><a name="Setup_Orbitron_"></a>Setup Orbitron/SDRSharp<br>
          </h2>
          <br>
          In short explained:<br>
          <br>
          Orbitron or WXtrack taking care of the doppler shift frequency
          correction for the carrier of the Meteor Demodulator Plugin.<br>
          DDE Tracking client Plugin collects data from Orbitron or any
          other Tracking client.<br>
          <br>
          Note it's not gonna be used for correcting the main tuned
          frequency in SDRSharp the signal will be unlocked from the
          QPSK Plugin using that! <br>
          <br>
          If Satellite elevation &gt; 0 (AOS) trigger the start of
          applications needed for the receiving session:<br>
          start decoder program, set modulation and bandwidth, start
          some plugins (Meteor Demodulator, LRPT-Decoder, MeteorGIS, IF
          or Baseband recorder).<br>
          <br>
          And send frequency correction (optional some stations report
          better reception without when having low or bad signal).<br>
          <br>
          Meteor Demodulator first synchronizes with the signal in
          frequency configuration of the modulation speed and modulation
          type (satellite name).<br>
          If the satellite is gone (LOS) - stop recorders, Radio,
          Tracking and other plugins.<br>
          <br>
          <b>Setup: </b><br>
          <br>
          Open Folder install location Orbitron\Config\setup.cfg in the
          driver section (end of file) below add this line required to
          point out your working SDRSharp install/location:<br>
          <br>
          [Drivers]<br>
          <br>
          SDRSharp=&lt;your path to SDRSharp
          folder&gt;\SDRSharp\SDRSharp.exe<br>
          <br>
          Save and start Orbitron, make sure you have a up to date TLE
          file containing Meteor M-N2 and M-N2-2 Satellite's.<br>
          Insert this url in Main/Click Tools Icon/TLE Updater
          (http://www.celestrak.com/NORAD/elements/weather.txt).<br>
          <br>
          Select Meteor M2 in the right list with the checkbox.<br>
          &nbsp;<br>
          <img src="img/Orbitron_1.jpg" alt="" width="672" height="525"><br>
          <br>
          Goto Main/Setup (the tool icon) Miscellaneous tab and set AOS
          notification to 0 (or any other elevation value when Meteor is
          receivable in your location).<br>
          <br>
          <img src="img/Orbitron_2.jpg" alt="" width="674" height="532"><br>
          <br>
          Then goto Extra tab last option AOS Notification: Make
          satellite active.<br>
          <br>
          <img src="img/Orbitron_3.jpg" alt="" width="673" height="525"><br>
          <br>
          Repeat these steps to add Meteor M-N2-2.<br>
          <b>Check the correct time zone!</b><br>
          <br>
          Fill in your location/GPS coordinates in the location tab.<br>
          <br>
          <img src="img/Orbitron_4.jpg" alt="" width="676" height="533"><br>
          <br>
          Goto tab Rotor/Radio, make sure in Dnlink/MHz: 137.100Mhz is
          filled in (Check current Meteor Mode's overhere: <a
            href="http://happysat.nl/Meteor/html/Meteor_Status.html">http://happysat.nl/Meteor/html/Meteor_Status.html</a>),<br>
          Dnlink mode: FM-W, select SDRSharp from the Driver dropdown
          box and click the icon next to it above the lock symbol.<br>
          <br>
          SDRSharp will start.<br>
          <br>
          Main Frequency in SDRSharp must be set to (Check current
          Meteor Mode's overhere: <a
            href="http://happysat.nl/Meteor/html/Meteor_Status.html">http://happysat.nl/Meteor/html/Meteor_Status.html</a>)
          Modulation WFM and preferred bandwidth 90000 Hz.<br>
          Tuner bandwidth to 1.4MSPS, 1.4 MSPS is needed IF samplerate
          will be &gt; 288 kHz<br>
          Meteor Demodulator plugin will show a warning when using <b>lower
            bitrates! </b><br>
          <h2><a name="Setup_DDE-Tracking_Client__SDRSharp"></a>Setup
            DDE-Tracking Client<br>
          </h2>
          <br>
          Who can better explain this then the author himself :)<br>
          <br>
          <a
href="https://translate.googleusercontent.com/translate_c?depth=1&amp;hl=ru&amp;rurl=translate.google.ru&amp;sl=ru&amp;sp=nmt4&amp;tl=en&amp;u=http://rtl-sdr.ru/page/komplekt-plaginov-dlja-priema-ka-meteor-i-drugih&amp;xid=17259,15700022,15700043,15700186,15700191,15700256,15700259,15700262&amp;usg=ALkJrhj069dszuCsI-UTiZ3RdsUTETCZWw"
            target="_blank" style="text-decoration:none">Follow this
            guide from RTL-sdr.ru in English</a><br>
          <br>
          In options button you can choose which Tracking program is
          going to be used, default is Orbitron.<br>
          <br>
          Check the box in the DDE Tracking client Plugin 'Satellite
          Tracking' and after a few seconds the sat name, frequency,
          elevation is listed from Orbitron with Meteor's details
          indicating doppler is active.<br>
          <br>
          A minimal elevation can be set like in Orbitron for example
          above 5 Degrees so the tracking client will be active and not
          on very low passes.<br>
          <br>
          The config button display's the available commands in the
          scheduler.<br>
          <br>
          <img src="img/M-N2_cfg.png" alt="" width="720" height="368"><br>
          <br>
          <b>AOS window section command explanation:</b><br>
          <br>
          radio start - SDRSharp start playing. (not visible on the
          screenshot left).<br>
          radio_modulation_type&lt;wfm&gt; - Modulation Wide Band FM
          (not visible on the screenshot left).<br>
          radio_center_frequency_Hz&lt;137570000&gt; - set's the center
          frequency to 137.570000MHz. ( we want the stream on the edge
          left if VDL2 signal from airports flies thru the spectrum, not
          visible on the screenshot left).<br>
          radio_frequency_Hz&lt;137100000&gt; - Tunes into 137.100MHz
          Meteors LRPT Frequency (not visible on the screenshot left).<br>
          radio_bandwidth_Hz&lt;90000&gt; - Bandwidth used 90000 Hz
          recommend.<br>
          set PSK_set_SymbolRate &lt;Auto&gt; - Meteor Demodulator
          plugin automatic detection mode of symbol rate.<br>
          M2_decoder_init_Line &lt;rgb=123.jpg&gt; or (rgb=125,444,555
          depending which mode Meteor is using), overrides path in
          decoder ini file.<br>
          M2_decoder_init_Line&lt;path=C:\Meteor\ImagesM2&gt; - Path to
          save images for M-N2, overrides path in decoder ini file.<br>
          M2_decoder_init_Line&lt;RoughStartTimeUTC=now&gt; - Using
          RoughStartTimeUTC = Now from the plugin, then Time will be
          initialized automatically at the moment of receipt of the
          first data, overrides path in decoder ini file.<br>
          M2_decoder_init_Line&lt;TleFileName=C:\Meteor\LRPT_Decoder\M2-2.txt&gt;
          - Path Meteor TLE File for Georef, overrides path in decoder
          ini file.<br>
          QPSK_demodulator_Start - QPSK Plugin is triggered to start
          from DDE Tracking Client by this command only for M-N2.<br>
          OQPSK_demodulator_Start - QPSK Plugin is triggered to start
          from DDE Tracking Client by this command Needed for M-N2-2.<br>
          send_tracking_frequency_On - Starting Doppler frequency
          correction for Meteor Demodulator Plugin carrier if the
          Satellite is active (If this is unwanted remove the command).<br>
          start_program_Path - LRPT-Decoder folder which includes
          run.bat, pointing to LRPT_Decoder.exe, explained more below.<br>
          <br>
          <b>LOS window section command explanation:</b><br>
          <br>
          send_Tracking_Frequency_Off - Doppler correction for Meteor
          Demodulator Plugin Carrier stops.<br>
          QPSK_demodulator_Stop - Stop Meteor Demodulator Plugin, only
          for M-N2.<br>
          OQPSK_demodulator_Stop - Stop Meteor Demodulator Plugin,
          needed for M-N2-2.<br>
          radio_stop - SDRSharp stops playing.<br>
          start_programm_Path - Optional custom batch file with some
          commands to put s-files in another folder when both Meteor's
          are received to separate them.<br>
          <br>
          <br>
          Disable recorder and socket not needed.<br>
          radio_tracking_frequency_On not needed for meteors. <br>
          Use only with NOAA and voice satellite! <br>
          For meteors need use send_tracking_frequency_On only!<br>
          tracking_frequency_Hz is a internal command, part of
          send_tracking_frequency. <br>
          Not needed add to scheduler manually!<br>
          <h2><a name="Setup_QPSK_Plugin_"></a>Setup Meteor Demodulator
            Plugin<br>
          </h2>
          <p> <br>
            Meteor Demodulator plugin sends received data in real time
            to Lrpt-Decoder via TCP Local Host connection (127.0.0.1)
            and/or can record and write a raw file called S-file.<br>
            <br>
            Auto searchcarrier inside the Meteor Demodulator Plugin
            tunes to (Check current Meteor Mode's overhere: <a
              href="http://happysat.nl/Meteor/html/Meteor_Status.html">http://happysat.nl/Meteor/html/Meteor_Status.html</a>).<br>
            Meteor streams and lock on the signal if its strong enough.</p>
          <p> When Sat Tracking is checked it uses Doppler correction
            for a faster signal lock.</p>
          <br>
          <img src="img/OQPSK.jpg" alt="" width="230" height="556"><br>
          <br>
          <p>Note Tracking info will only displayed when the Satellite
            is active!</p>
          <p>Config button is used to change the default PLL Bandwidth
            Value and a save path for writing the S-file.</p>
          <img src="img/oqpsk.png" alt="" width="237" height="317"><br>
          <br>
          People who are not using DDE-Tracking Client, and running the
          Meteor Demodulator Plugin manual <b>Meteor M-N2-2 is using
            OQPSK Modulation</b>, make sure to select it!<br>
          <br>
          How Meteor Demodulator plugin works:<br>
          <br>
          If Satellite elevation &gt; 0 (AOS) trigger the start of
          applications needed for the receiving session:<br>
          Meteor Demodulator first synchronizes with the signal in
          frequency configuration of the modulation speed and modulation
          type (satellite name).<br>
          Automatic speed detection determines the symbolic flow rate.<br>
          <br>
          There is no need to change the decoder settings when changing
          72K / 80K and M2 / M2.2. <br>
          LRPT-Decoder will receive signal information from the Meteor
          Demodulator plugin.<br>
          &nbsp;<br>
          Only after synchronization in frequency and symbol rate Meteor
          Demodulator plugin begin to transmit data to the decoder.<br>
          In the first block of data, the settings go to the decoder
          (automatically determined or set). <br>
          <br>
          <img src="img/small.jpg" alt="" width="404" height="362"><br>
          <br>
          The decoder, until it receives data keeps the decoder window
          minimized.<br>
          <br>
          After receiving the first data block, the decoder is
          initialized and begins to work building up an image line by
          line.<br>
          Without capturing the signal by Meteor Demodulator (after all,
          reception goes through the demodulator), the window will not
          close. <br>
          <br>
          <p>If Meteors pass is over (LOS) Plugin will be inactive and
            LrptDecoder also quits saving received images.<br>
          </p>
          <br>
          Since Meteor Demodulator V2.3 a new scheduler command
          "M2_decoder_init_Line &lt;&gt;" has been added to the plugin.<br>
          <br>
          Using it, you can transfer any commands that are in the
          M2_LRPT_Decoder.ini file of the LRPT-Decoder.<br>
          <br>
          <b>Example scheduler options:</b><br>
          <br>
          M2_decoder_init_Line &lt;rgb=123.jpg&gt; or (rgb=125,444,555
          depending which mode Meteor is using), overrides path in
          decoder ini file.<br>
          M2_decoder_init_Line&lt;path=C:\Meteor\ImagesM2&gt; - Path to
          save images for M-N2 or M-N2-2, overrides path in decoder ini
          file.<br>
          <br>
          M2_decoder_init_Line&lt;RoughStartTimeUTC=now&gt; - Using
          RoughStartTimeUTC = Now from the plugin, then Time will be
          initialized automatically at the moment of receipt of the
          first data, overrides path in decoder ini file.<br>
          M2_decoder_init_Line&lt;TleFileName=C:\Meteor\LRPT_Decoder\M2-2.txt&gt;
          - Path Meteor TLE File for Georef, overrides path in decoder
          ini file.<br>
          <br>
          Make sure to enter these commands before the demodulator and
          decoder start entries.<br>
          QPSK_demodulator_Start<br>
          start_program_Path - Path&nbsp; to LRPT-Decoder<br>
          <br>
          <b>In order for the decoder to work with Meteor Demodulator,
            the ini-file mode and sat entries must be assigned to auto!</b><br>
          <br>
          Inside M2_LRPT_Decoder.ini change:<br>
          <br>
          mode=auto<br>
          sat=auto<br>
          <br>
          There is no need to change the decoder settings when changing
          72K / 80K and M2 / M2.2. <br>
          <br>
          LRPT-Decoder will receive signal information from the Meteor
          Demodulator plugin automatic detection mode of symbol speed. <br>
          And the type of modulation is determined by the choice of
          satellite M2 / M22.<br>
          <br>
          In this mode, you can generally remove the term
          PSK_set_SymbolRate &lt;&gt; from the scheduler or set
          PSK_set_SymbolRate &lt;Auto&gt;. <br>
          Changes practically do not affect the reception quality. <br>
          <br>
          It is enough to change the speed in the scheduler.<br>
          <br>
          M2 LRPT-Decoder compatible with these functions is above
          Version 50.<br>
          <h2><a name="Setup_LRPT-Decoder_for"></a>Setup LRPT-Decoder
            for Meteor M-N2 and M-N2-2</h2>
          <br>
          The idea is to run 1 LRPT-Decoder for both Meteor satellite's
          and this should reduce the number of settings that must be
          done when Meteor changes operating modes.<br>
          <br>
          This allows to modify the settings when changing the reception
          conditions only in the scheduler from DDE Tracking Client,<br>
          and not in the entire chain of programs for processing the
          signal from the satellite.<br>
          <br>
          <b>DDE-Tracker client scheduler setup for Meteor M-N2:</b><br>
          <br>
          <img src="img/M-N2_cfg.png" alt="" width="720" height="368"><br>
          <br>
          The<b> difference between Meteor M-N2 and N2-2 is QPSK
            Modulation</b> &lt;- QPSK_demodulator_Start mode must be
          selected for M-N2!<br>
          <br>
          set PSK_set_SymbolRate &lt;Auto&gt; - Meteor Demodulator
          plugin automatic detection mode of symbol rate.<br>
          <br>
          M2_decoder_init_Line &lt;rgb=123.jpg&gt; or (rgb=125,444,555
          depending which mode Meteor is using), overrides path in
          decoder ini file.<br>
          <br>
          <b>If you do not want all received images into 1 folder:</b><br>
          M2_decoder_init_Line&lt;path=C:\Meteor\ImagesM2&gt; - Path to
          save images for M-N2, overrides path in decoder ini file.<br>
          <br>
          <b>If you want to use georeference for mapping boundaries or
            test ect, include:</b><br>
          M2_decoder_init_Line&lt;RoughStartTimeUTC=now&gt; - Using
          RoughStartTimeUTC = Now from the plugin, then Time will be
          initialized automatically at the moment of receipt of the
          first data, overrides path in decoder ini file.<br>
          M2_decoder_init_Line&lt;TleFileName=C:\Meteor\LRPT_Decoder\M2-2.txt&gt;
          - Path Meteor TLE File for Georef, overrides path in decoder
          ini file.<br>
          <br>
          QPSK_demodulator_Start - QPSK Plugin is triggered to start
          from DDE Tracking Client by this command only for M-N2.<br>
          send_tracking_frequency_On - Starting Doppler frequency
          correction for Meteor Demodulator Plugin carrier if the
          Satellite is active (If this is unwanted remove the command).<br>
          <br>
          start_program_Path - Path&nbsp; to LRPT-Decoder for startup
          run.bat (do not use a path with spaces example program
          files!).<br>
          The batch file run.bat point's to LRPTDecoder.exe and already
          included in the LRPT-decoder folder/archive, just enter its
          path &lt;your path\run.bat&gt; to the scheduler.<br>
          <br>
          <b>Batch file contents:</b><br>
          <br>
          START M2_LRPT_Decoder.exe M2_LRPT_Decoder.ini<br>
          <br>
          <br>
          <b>DDE-Tracker client scheduler setup for Meteor M-N2-2:</b><br>
          <br>
          <img src="img/M-N2.2_cfg.png" alt="" width="722" height="368"><br>
          <br>
          The <b>difference between Meteor M-N2-2 and N2 is OQPSK
            Modulation</b> &lt;- OQPSK_demodulator_Start must be
          selected for M-N2-2!<br>
          <br>
          <b>If you want to use georeference for mapping boundaries or
            test ect, include:</b><br>
          M2_decoder_init_Line&lt;RoughStartTimeUTC=now&gt; - Using
          RoughStartTimeUTC = Now from the plugin, then Time will be
          initialized automatically at the moment of receipt of the
          first data, overrides path in decoder ini file.<br>
          M2_decoder_init_Line&lt;TleFileName=C:\Meteor\LRPT_Decoder\M2-2.txt&gt;
          - Path Meteor TLE File for Georef, overrides path in decoder
          ini file.<br>
          <br>
          M2_decoder_init_Line &lt;rgb=123.jpg&gt; or (rgb=125,444,555
          depending which mode Meteor is using), overrides path in
          decoder ini file.<br>
          <br>
          <b>If you do not want all received images into 1 folder:</b><br>
          M2_decoder_init_Line&lt;path=C:\Meteor\ImagesM22&gt; - Path to
          save images for M-N2-2, overrides path in decoder ini file.<br>
          <br>
          OQPSK_demodulator_Start - QPSK Plugin is triggered to start
          from DDE Tracking Client by this command only for M-N2-2.<br>
          send_tracking_frequency_On - Starting Doppler frequency
          correction for Meteor Demodulator Plugin carrier if the
          Satellite is active (If this is unwanted remove the command).<br>
          <br>
          start_program_Path - Path to LRPT-Decoder for startup run.bat.<br>
          <b>It must be the very same path as setup above for Meteor
            M-N2! (we use 1 Decoder).</b><br>
          <br>
          <img src="img/decoder_m2-2.png" alt="" width="690"
            height="378"><br>
          <br>
          In Extracted downloaded LRPTDecoder archive<br>
          <br>
          <b>Open M2_LRPT_Decoder.ini</b><br>
          <br>
          <b>Edit:</b><br>
          <br>
          [IN]<br>
          source=TCP <br>
          mode=auto<br>
          sat=auto<br>
          host=localhost<br>
          port=2011<br>
          <br>
          [OUT]<br>
          rgb=123.jpg <br>
          rgb_q=100<br>
          mono=yes<br>
          logs=no<br>
          APID70=no<br>
          VCDU=no<br>
          path=C:\Meteor\ImagesM22 (edit to your path of images)<br>
          path =C:\Meteor\Images\M20 for Meteor-M No. 2<br>
          pathM22 =C:\Meteor\Images\M22 for Meteor-M No. 2.2<br>
          <br>
          If you want to use georeference for mapping boundaries
          include:<br>
          GEO Creates a gcp which can be used for MeteorGIS or
          LRPT_Places to insert boundaries or cities..<br>
          <br>
          [GEO]<br>
          RoughStartTimeUTC=18-8-2019<br>
          TleFileName=C:\Meteor\LRPT_Decoder\M2-2.txt&nbsp; (Use <a
href="file:///D:/Program%20Files/SDR/Setup/Audio/Deadsat_website/Setup_Meteor/Setup.html#LRPT_Places_">Meteor
            TLE-Loader</a> paste M-N2-2 TLE info into new text file
          called M2-2.txt).<br>
          Alfa_M2=110.8<br>
          Delta_M2=32<br>
          Alfa_M22=110.8<br>
          Delta_M22=-4.8<br>
          <br>
          Alfa - camera angle<br>
          Delta - offset along the line<br>
          &nbsp;<br>
          Selecting Delta achieve alignment of the coastline in the
          center of the image. <br>
          Then, changing Alfa, you can expand / contract images on a
          line.<br>
          <br>
          When choosing delta, be aware that a change of 1 will result
          in a shift of about 1 km for misplaced overlay correction.<br>
          <br>
          For AMIGOS (Only Meteor M-N2)<br>
          <br>
          [GLOB]<br>
          AmigoID=0 <br>
          mode=UDP<br>
          path=C:\Meteor\Tools\AMIGOS\ShareFolder (edit to your path of
          AMIGOS when used or leave out [GLOB] section )<br>
          host=185.26.115.106<br>
          port=2013<br>
          <br>
          [FAST]<br>
          FORMAT=jpg<br>
          R=1<br>
          G=2<br>
          B=3<br>
          <br>
          <b>Save M2_LRPT_Decoder.ini</b><br>
          <p> </p>
          <h2><a name="Setup_MeteorGIS_"></a>Setup MeteorGIS Meteor-M-N2
            and N2-2<br>
          </h2>
          <br>
          <b>Make sure to read and understand the</b> <a
            target="_blank"
href="https://drive.google.com/file/d/0B9HuDROb5aCyeUF2VlVUQjVaZjQ/view?usp=sharing"
            style="font-family: &quot;Times New Roman&quot;; font-size:
            medium; font-style: normal; font-variant-ligatures: normal;
            font-variant-caps: normal; font-weight: 400; letter-spacing:
            normal; orphans: 2; text-align: -webkit-center; text-indent:
            0px; text-transform: none; white-space: normal; widows: 2;
            word-spacing: 0px; -webkit-text-stroke-width: 0px;">Guide
            for MeteorGIS software for meteor MN2</a><br>
          <br>
          Download: <a href="http://www.meteorgis.space/"
            target="_blank">MeteorGIS</a><br>
          <br>
          Extract MeteorGIS and LRPT-Decoder to C:\Meteor\&nbsp; <br>
          Only the M2_LRPT_Decoder.exe is needed, ini files will be
          generated from MeteorGIS.<br>
          <br>
          <b>Do not forget </b>to copy out SGP4.dll from folder
          meteorgis\file_to_put_in_M2_LRPT_Decoder_folder\ into
          C:\Meteor\&nbsp; its needed to create the composite images
          ect.!<br>
          <br>
          To make configuration/setup of MeteorGIS easier the Authors
          did make a very handy tool:<br>
          <b>Find MeteorGIS_Configurator.exe in extracted MeteorGIS
            Folder</b> double click choose the default.ini and adjust
          your settings in the following tabs.<br>
          <br>
          <b>But first run MeteorGIS.exe once so it can create a
            default.ini configuration file to edit!<br>
            <br>
            Bug in v2.24 does not create a default.ini, <a
              href="default.zip">download default.ini overhere</a> (will
            be fixed)!<br>
          </b> <br>
          <img src="img/MeteorGIS_Configurator.png" alt="" width="1081"
            height="674"><br>
          <br>
          <b>As of MeteorGIS v.2.20 no more need of 2 ini and a batch
            file, Sat is automatically detected in auto mode.</b><br>
          <br>
          <b>For this setup you do not have to make any changes to
            M2_LRPT_Decoder.ini, MeteorGIS will handle the
            configuration.</b><br>
          <br>
          <b>Example of only the folder setup in default.ini:</b><br>
          <br>
          <b>[Program]</b><br>
          inputDir=C:\Meteor\images-M2\&nbsp; <b>&lt;&lt;-- Where
            LRPT-decoder saves images</b><br>
          outputDir=C:\Meteor\out-images-M2\&nbsp; <b>&lt;&lt;-- Here
            you will find processed images by MeteorGIS, Composite,
            Treated ect from both Meteor's.</b><br>
          <b>[M2_LRPT_Decoder]</b><br>
          pathToM2_LRPT_Decoder=C:\Meteor\&nbsp;<b>
            &lt;&lt;--LRPT-Decoder.exe </b><br>
          pathToSaveDecodedImages=C:\Meteor\images-M2\M2\&nbsp; <b>&lt;&lt;--
            Images of Meteor M2</b><br>
          pathToSaveDecodedImagesM22=C:\Meteor\images-M2\M22\ <b>&lt;&lt;--
            Images of Meteor M22</b><br>
          <br>
          The folder structure:<br>
          <br>
          <img src="img/folder3.png" alt="" width="852" height="334"><br>
          <br>
          C:\Meteor\ <br>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
          &nbsp;&nbsp; Images-M2\<br>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
          &nbsp; &nbsp; Images-M2\M2<br>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
          &nbsp; &nbsp; Images-M2\M22<br>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
          MeteorGIS<br>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
          out-images<br>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
          &nbsp; &nbsp; S_file\<br>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
          &nbsp;&nbsp; Tools\<br>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
          &nbsp; M2_LRPT-Decoder.exe<br>
          <br>
          <b>Next is setup commands for MeteorGIS in Scheduler.</b><br>
          <br>
          <b>Example Meteor M-N2 Setup in DDE Tracking Client Scheduler
            Config:</b><br>
          <br>
          <img src="img/M2_GIS.png" alt="" width="721" height="371"><br>
          <b><br>
          </b><b> These lines are important:</b><br>
          <br>
          The frequency Check current Meteor Mode's overhere: <a
            href="http://happysat.nl/Meteor/html/Meteor_Status.html"
            target="_blank">http://happysat.nl/Meteor/html/Meteor_Status.html</a><br>
          <br>
          set PSK_set_SymbolRate &lt;72000&gt; for Meteor M-N2.<br>
          <br>
          start_programm_Path&lt;C:\Meteor\MeteorGIS\MeteorGIS.exe&gt; -
          Path to MeteorGIS.exe folder (dont use a path with spaces
          example program files!.)<br>
          <b><br>
          </b><b> So change this in DDE Tracking Client schedule
            commands!</b><br>
          <br>
          <br>
          <b>Example Meteor M-N2-2 Setup in DDE Tracking Client
            Scheduler Config:</b><br>
          <br>
          <img src="img/M2-2_GIS.png" alt="" width="719" height="367"><br>
          <br>
          <b>These lines are important:</b><br>
          <br>
          The frequency Check current Meteor Mode's overhere: <a
            href="http://happysat.nl/Meteor/html/Meteor_Status.html"
            target="_blank">http://happysat.nl/Meteor/html/Meteor_Status.html</a><br>
          <br>
          set PSK_set_SymbolRate &lt;Auto&gt; <br>
          <br>
          start_programm_Path&lt;C:\Meteor\MeteorGIS\MeteorGIS.exe&gt; -
          Path to MeteorGIS.exe folder (dont use a path with spaces
          example program files!.)<br>
          <br>
          (Optional) The s_file.bat file in the scheduler contains:<br>
          <br>
          move C:\Meteor\S_file\* C:\Meteor\S_file\M22<br>
          <br>
          And does move the s-file after the pass to different folders.<br>
          <br>
          <b>So change this in DDE Tracking Client schedule commands!</b><br>
          <br>
          When Meteor rises above the horizon in Orbitron (you can check
          with simulation mode) ,<br>
          The scheduler will execute the commands, starting MeteorGIS:<br>
          <br>
          <img src="img/GIS.jpg" alt="" width="674" height="342"><br>
          <br>
          When a <b>signal lock</b> is detected LRPT Decoder will
          start:&nbsp;&nbsp; <br>
          <br>
          <img src="img/GIS_Dec.jpg" alt="" width="670" height="362"><br>
          <br>
          <span style="color: rgb(34, 34, 34); font-family: sans-serif;
            font-size: 14px; font-style: normal; font-variant-ligatures:
            normal; font-variant-caps: normal; font-weight: 400;
            letter-spacing: normal; orphans: 2; text-align: start;
            text-indent: 0px; text-transform: none; white-space: normal;
            widows: 2; word-spacing: 0px; -webkit-text-stroke-width:
            0px; background-color: rgb(255, 255, 255);
            text-decoration-style: initial; text-decoration-color:
            initial; display: inline !important; float: none;">MeteorGIS
            can manually started in offline mode with a batch file to
            re-process Meteor M-N2 and N2-2 Images, in case something
            did go wrong.</span><span style="color: rgb(34, 34, 34);
            font-family: sans-serif; font-size: 14px; font-style:
            normal; font-variant-ligatures: normal; font-variant-caps:
            normal; font-weight: 400; letter-spacing: normal; orphans:
            2; text-align: start; text-indent: 0px; text-transform:
            none; white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; background-color: rgb(255,
            255, 255); text-decoration-style: initial;
            text-decoration-color: initial; display: inline !important;
            float: none;"><span style="color: rgb(34, 34, 34);
              font-family: sans-serif; font-size: 14px; font-style:
              normal; font-variant-ligatures: normal; font-variant-caps:
              normal; font-weight: 400; letter-spacing: normal; orphans:
              2; text-align: start; text-indent: 0px; text-transform:
              none; white-space: normal; widows: 2; word-spacing: 0px;
              -webkit-text-stroke-width: 0px; background-color: rgb(255,
              255, 255); text-decoration-style: initial;
              text-decoration-color: initial; display: inline
              !important; float: none;"><br>
            </span></span><span style="color: rgb(34, 34, 34);
            font-family: sans-serif; font-size: 14px; font-style:
            normal; font-variant-ligatures: normal; font-variant-caps:
            normal; font-weight: 400; letter-spacing: normal; orphans:
            2; text-align: start; text-indent: 0px; text-transform:
            none; white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; background-color: rgb(255,
            255, 255); text-decoration-style: initial;
            text-decoration-color: initial; display: inline !important;
            float: none;"></span><br>
          <b>Command Line Options for MeteorGIS:</b><br>
          <br>
          <b>/nolive</b><br>
          By default, MeteorGIS will work in automatic mode. <br>
          It can launch the decoder (M2_LRPT_Decoder.exe) after creating
          the right ini file for it. <br>
          If you specify this option, you have to make it by yourself,
          or for treat some old images.<br>
          If you didn't use this option (mean automatic mode) take care
          to not specify an input file (but folder instead)<br>
          <br>
          <b>/notle</b><br>
          If you specify this option, the program will not try to
          download the latest available TLE. (Don't use unless you want
          to treat old .s file.)<br>
          <br>
          <b>/input:</b><br>
          Specify an input file to treat it. Could be a folder, in this
          case it will search for the last file in this folder AND
          subfolders.<br>
          File specified could be a jpg, a bmp (in this case give one of
          the 3 channels bmp name) or a .s file (Read the
          "About_.s.txt").<br>
          Jpg images are NOT post-treated.<br>
          Of course, you must have the .gcp file in relation with it
          (apart for .s file - it will be generated).<br>
          <br>
          <b>/outdir</b>:<br>
          Specify the output folder for treated files. If not exist,
          will be created.<br>
          Take care as if you put the folder embraced in quotes (") for
          example if the path contain space, to NOT PUT a \ at the end
          !!!<br>
          <br>
          <b>/type:</b><br>
          The type(s) of image(s) generated. Override the option in the
          "Program" section.<br>
          Should be one or more of the following (separate them by a
          coma ",") rgb,ir,thermal,ir_rain,rgb_rain<br>
          <br>
          <b>/proj:</b><br>
          The type of projection (UTM or LatLon). Override the option in
          the "Program" section.<br>
          Should be UTM or Mercator.<br>
          <br>
          <b>/config:</b><br>
          Specify another ini file if you want to keep different
          configurations.<br>
          <br>
          <b>/compose:</b><br>
          Specify one or more image(s) to be composed with the input
          one. Must be the entire path to the image(s).<br>
          If you specify more than one file separate them by a coma.<br>
          <br>
          <b>/composeauto</b><br>
          The program will create all image(s) specified or found in
          input (only if doesn't yet exist) plus a composition of all
          passes within the timespan Composition option of the file
          specified as input (or last one if a folder is specified).<br>
          This option is used only if you use the /nolive option (manual
          mode). In case of live reception, this option is always set.<br>
          <br>
          <b>/sat:</b><br>
          Used only if processing .s file. To give the decoder the right
          tle file and save folder + put the right sat name on
          watermark.<br>
          <span style="color: rgb(34, 34, 34); font-family: sans-serif;
            font-size: 14px; font-style: normal; font-variant-ligatures:
            normal; font-variant-caps: normal; font-weight: 400;
            letter-spacing: normal; orphans: 2; text-align: start;
            text-indent: 0px; text-transform: none; white-space: normal;
            widows: 2; word-spacing: 0px; -webkit-text-stroke-width:
            0px; background-color: rgb(255, 255, 255);
            text-decoration-style: initial; text-decoration-color:
            initial; display: inline !important; float: none;"><span
              style="color: rgb(34, 34, 34); font-family: sans-serif;
              font-size: 14px; font-style: normal;
              font-variant-ligatures: normal; font-variant-caps: normal;
              font-weight: 400; letter-spacing: normal; orphans: 2;
              text-align: start; text-indent: 0px; text-transform: none;
              white-space: normal; widows: 2; word-spacing: 0px;
              -webkit-text-stroke-width: 0px; background-color: rgb(255,
              255, 255); text-decoration-style: initial;
              text-decoration-color: initial; display: inline
              !important; float: none;">For manual mode (only for .s
              file) you need to specify the sat name (M2 or M2.2) with
              the command line /sat:</span></span><span style="color:
            rgb(34, 34, 34); font-family: sans-serif; font-size: 14px;
            font-style: normal; font-variant-ligatures: normal;
            font-variant-caps: normal; font-weight: 400; letter-spacing:
            normal; orphans: 2; text-align: start; text-indent: 0px;
            text-transform: none; white-space: normal; widows: 2;
            word-spacing: 0px; -webkit-text-stroke-width: 0px;
            background-color: rgb(255, 255, 255); text-decoration-style:
            initial; text-decoration-color: initial; display: inline
            !important; float: none;"><span style="color: rgb(34, 34,
              34); font-family: sans-serif; font-size: 14px; font-style:
              normal; font-variant-ligatures: normal; font-variant-caps:
              normal; font-weight: 400; letter-spacing: normal; orphans:
              2; text-align: start; text-indent: 0px; text-transform:
              none; white-space: normal; widows: 2; word-spacing: 0px;
              -webkit-text-stroke-width: 0px; background-color: rgb(255,
              255, 255); text-decoration-style: initial;
              text-decoration-color: initial; display: inline
              !important; float: none;"></span></span><br>
          <b><br>
          </b><b> </b><b>Make a batch file named Manual_M2_GIS.bat
            inside the MeteorGIS folder.</b><span style="color: rgb(34,
            34, 34); font-family: sans-serif; font-size: 14px;
            font-style: normal; font-variant-ligatures: normal;
            font-variant-caps: normal; font-weight: 400; letter-spacing:
            normal; orphans: 2; text-align: start; text-indent: 0px;
            text-transform: none; white-space: normal; widows: 2;
            word-spacing: 0px; -webkit-text-stroke-width: 0px;
            background-color: rgb(255, 255, 255); text-decoration-style:
            initial; text-decoration-color: initial; display: inline
            !important; float: none;"><span style="color: rgb(34, 34,
              34); font-family: sans-serif; font-size: 14px; font-style:
              normal; font-variant-ligatures: normal; font-variant-caps:
              normal; font-weight: 400; letter-spacing: normal; orphans:
              2; text-align: start; text-indent: 0px; text-transform:
              none; white-space: normal; widows: 2; word-spacing: 0px;
              -webkit-text-stroke-width: 0px; background-color: rgb(255,
              255, 255); text-decoration-style: initial;
              text-decoration-color: initial; display: inline
              !important; float: none;"><br>
            </span>&nbsp;<br>
            C:\Meteor\MeteorGIS\MeteorGIS.exe /nolive /composeauto
            /sat:M2
            /config:C:\Meteor\MeteorGIS\default.ini&nbsp;&nbsp;&nbsp;&nbsp;
            <br>
          </span><span style="color: rgb(34, 34, 34); font-family:
            sans-serif; font-size: 14px; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; background-color: rgb(255,
            255, 255); text-decoration-style: initial;
            text-decoration-color: initial; display: inline !important;
            float: none;"><br>
            <b>Make another for Manual_M2-2_GIS.bat and insert:</b><br>
            <br>
            C:\Meteor\MeteorGIS\MeteorGIS.exe /nolive /composeauto
            /sat:M2.2
            /config:C:\Meteor\MeteorGIS\default.ini&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
          </span><span style="color: rgb(34, 34, 34); font-family:
            sans-serif; font-size: 14px; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; background-color: rgb(255,
            255, 255); text-decoration-style: initial;
            text-decoration-color: initial; display: inline !important;
            float: none;"><span><br style="color: rgb(34, 34, 34);
                font-family: sans-serif; font-size: 14px; font-style:
                normal; font-variant-ligatures: normal;
                font-variant-caps: normal; font-weight: 400;
                letter-spacing: normal; orphans: 2; text-align: start;
                text-indent: 0px; text-transform: none; white-space:
                normal; widows: 2; word-spacing: 0px;
                -webkit-text-stroke-width: 0px; text-decoration-style:
                initial; text-decoration-color: initial;">
            </span></span> <br style="color: rgb(34, 34, 34);
            font-family: sans-serif; font-size: 14px; font-style:
            normal; font-variant-ligatures: normal; font-variant-caps:
            normal; font-weight: 400; letter-spacing: normal; orphans:
            2; text-align: start; text-indent: 0px; text-transform:
            none; white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">
          <span style="color: rgb(34, 34, 34); font-family: sans-serif;
            font-size: 14px; font-style: normal; font-variant-ligatures:
            normal; font-variant-caps: normal; font-weight: 400;
            letter-spacing: normal; orphans: 2; text-align: start;
            text-indent: 0px; text-transform: none; white-space: normal;
            widows: 2; word-spacing: 0px; -webkit-text-stroke-width:
            0px; background-color: rgb(255, 255, 255);
            text-decoration-style: initial; text-decoration-color:
            initial; display: inline !important; float: none;">Save, and
            run for manual re-processing.<br>
          </span><br>
          <span style="color: rgb(34, 34, 34); font-family: sans-serif;
            font-size: 14px; font-style: normal; font-variant-ligatures:
            normal; font-variant-caps: normal; font-weight: 400;
            letter-spacing: normal; orphans: 2; text-align: start;
            text-indent: 0px; text-transform: none; white-space: normal;
            widows: 2; word-spacing: 0px; -webkit-text-stroke-width:
            0px; background-color: rgb(255, 255, 255);
            text-decoration-style: initial; text-decoration-color:
            initial; display: inline !important; float: none;"><span
              style="color: rgb(34, 34, 34); font-family: sans-serif;
              font-size: 14px; font-style: normal;
              font-variant-ligatures: normal; font-variant-caps: normal;
              font-weight: 400; letter-spacing: normal; orphans: 2;
              text-align: start; text-indent: 0px; text-transform: none;
              white-space: normal; widows: 2; word-spacing: 0px;
              -webkit-text-stroke-width: 0px; background-color: rgb(255,
              255, 255); text-decoration-style: initial;
              text-decoration-color: initial; display: inline
              !important; float: none;">Offcourse you need a s-file for
              re-processing first.!</span><span style="color: rgb(34,
              34, 34); font-family: sans-serif; font-size: 14px;
              font-style: normal; font-variant-ligatures: normal;
              font-variant-caps: normal; font-weight: 400;
              letter-spacing: normal; orphans: 2; text-align: start;
              text-indent: 0px; text-transform: none; white-space:
              normal; widows: 2; word-spacing: 0px;
              -webkit-text-stroke-width: 0px; background-color: rgb(255,
              255, 255); text-decoration-style: initial;
              text-decoration-color: initial; display: inline
              !important; float: none;"><span style="color: rgb(34, 34,
                34); font-family: sans-serif; font-size: 14px;
                font-style: normal; font-variant-ligatures: normal;
                font-variant-caps: normal; font-weight: 400;
                letter-spacing: normal; orphans: 2; text-align: start;
                text-indent: 0px; text-transform: none; white-space:
                normal; widows: 2; word-spacing: 0px;
                -webkit-text-stroke-width: 0px; background-color:
                rgb(255, 255, 255); text-decoration-style: initial;
                text-decoration-color: initial; display: inline
                !important; float: none;"></span></span><span
              style="color: rgb(34, 34, 34); font-family: sans-serif;
              font-size: 14px; font-style: normal;
              font-variant-ligatures: normal; font-variant-caps: normal;
              font-weight: 400; letter-spacing: normal; orphans: 2;
              text-align: start; text-indent: 0px; text-transform: none;
              white-space: normal; widows: 2; word-spacing: 0px;
              -webkit-text-stroke-width: 0px; background-color: rgb(255,
              255, 255); text-decoration-style: initial;
              text-decoration-color: initial; display: inline
              !important; float: none;"><span style="color: rgb(34, 34,
                34); font-family: sans-serif; font-size: 14px;
                font-style: normal; font-variant-ligatures: normal;
                font-variant-caps: normal; font-weight: 400;
                letter-spacing: normal; orphans: 2; text-align: start;
                text-indent: 0px; text-transform: none; white-space:
                normal; widows: 2; word-spacing: 0px;
                -webkit-text-stroke-width: 0px; background-color:
                rgb(255, 255, 255); text-decoration-style: initial;
                text-decoration-color: initial; display: inline
                !important; float: none;"><span style="color: rgb(34,
                  34, 34); font-family: sans-serif; font-size: 14px;
                  font-style: normal; font-variant-ligatures: normal;
                  font-variant-caps: normal; font-weight: 400;
                  letter-spacing: normal; orphans: 2; text-align: start;
                  text-indent: 0px; text-transform: none; white-space:
                  normal; widows: 2; word-spacing: 0px;
                  -webkit-text-stroke-width: 0px; background-color:
                  rgb(255, 255, 255); text-decoration-style: initial;
                  text-decoration-color: initial; display: inline
                  !important; float: none;"><span style="color: rgb(34,
                    34, 34); font-family: sans-serif; font-size: 14px;
                    font-style: normal; font-variant-ligatures: normal;
                    font-variant-caps: normal; font-weight: 400;
                    letter-spacing: normal; orphans: 2; text-align:
                    start; text-indent: 0px; text-transform: none;
                    white-space: normal; widows: 2; word-spacing: 0px;
                    -webkit-text-stroke-width: 0px; background-color:
                    rgb(255, 255, 255); text-decoration-style: initial;
                    text-decoration-color: initial; display: inline
                    !important; float: none;"><br>
                  </span></span></span> Make the changes for manual
              processing in LRPT-Decoder explained <a
href="file:///D:/Program%20Files/SDR/Setup/Website/Setup_Meteor/Setup.html#Manual_LRPT-Decoder_setup_">below</a>:<br>
              <br>
            </span></span><span style="color: rgb(34, 34, 34);
            font-family: sans-serif; font-size: 14px; font-style:
            normal; font-variant-ligatures: normal; font-variant-caps:
            normal; font-weight: 400; letter-spacing: normal; orphans:
            2; text-align: start; text-indent: 0px; text-transform:
            none; white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; background-color: rgb(255,
            255, 255); text-decoration-style: initial;
            text-decoration-color: initial; display: inline !important;
            float: none;"><span style="color: rgb(34, 34, 34);
              font-family: sans-serif; font-size: 14px; font-style:
              normal; font-variant-ligatures: normal; font-variant-caps:
              normal; font-weight: 400; letter-spacing: normal; orphans:
              2; text-align: start; text-indent: 0px; text-transform:
              none; white-space: normal; widows: 2; word-spacing: 0px;
              -webkit-text-stroke-width: 0px; background-color: rgb(255,
              255, 255); text-decoration-style: initial;
              text-decoration-color: initial; display: inline
              !important; float: none;"><span style="color: rgb(34, 34,
                34); font-family: sans-serif; font-size: 14px;
                font-style: normal; font-variant-ligatures: normal;
                font-variant-caps: normal; font-weight: 400;
                letter-spacing: normal; orphans: 2; text-align: start;
                text-indent: 0px; text-transform: none; white-space:
                normal; widows: 2; word-spacing: 0px;
                -webkit-text-stroke-width: 0px; background-color:
                rgb(255, 255, 255); text-decoration-style: initial;
                text-decoration-color: initial; display: inline
                !important; float: none;"><span style="color: rgb(34,
                  34, 34); font-family: sans-serif; font-size: 14px;
                  font-style: normal; font-variant-ligatures: normal;
                  font-variant-caps: normal; font-weight: 400;
                  letter-spacing: normal; orphans: 2; text-align: start;
                  text-indent: 0px; text-transform: none; white-space:
                  normal; widows: 2; word-spacing: 0px;
                  -webkit-text-stroke-width: 0px; background-color:
                  rgb(255, 255, 255); text-decoration-style: initial;
                  text-decoration-color: initial; display: inline
                  !important; float: none;"><span style="color: rgb(34,
                    34, 34); font-family: sans-serif; font-size: 14px;
                    font-style: normal; font-variant-ligatures: normal;
                    font-variant-caps: normal; font-weight: 400;
                    letter-spacing: normal; orphans: 2; text-align:
                    start; text-indent: 0px; text-transform: none;
                    white-space: normal; widows: 2; word-spacing: 0px;
                    -webkit-text-stroke-width: 0px; background-color:
                    rgb(255, 255, 255); text-decoration-style: initial;
                    text-decoration-color: initial; display: inline
                    !important; float: none;">Tip: rename s-file without
                    _underscores for manual processing and GIS recognize
                    the format to create all images:
                    2019_11_23_LRPT_21-07-32.s into
                    2019-11-23-21-07-32.s<br>
                    Put created images in the folder you specified in
                    MeteorGIS config so GIS know where to find them.</span></span></span></span></span><span
            style="color: rgb(34, 34, 34); font-family: sans-serif;
            font-size: 14px; font-style: normal; font-variant-ligatures:
            normal; font-variant-caps: normal; font-weight: 400;
            letter-spacing: normal; orphans: 2; text-align: start;
            text-indent: 0px; text-transform: none; white-space: normal;
            widows: 2; word-spacing: 0px; -webkit-text-stroke-width:
            0px; background-color: rgb(255, 255, 255);
            text-decoration-style: initial; text-decoration-color:
            initial; display: inline !important; float: none;"><span
              style="color: rgb(34, 34, 34); font-family: sans-serif;
              font-size: 14px; font-style: normal;
              font-variant-ligatures: normal; font-variant-caps: normal;
              font-weight: 400; letter-spacing: normal; orphans: 2;
              text-align: start; text-indent: 0px; text-transform: none;
              white-space: normal; widows: 2; word-spacing: 0px;
              -webkit-text-stroke-width: 0px; background-color: rgb(255,
              255, 255); text-decoration-style: initial;
              text-decoration-color: initial; display: inline
              !important; float: none;"><span style="color: rgb(34, 34,
                34); font-family: sans-serif; font-size: 14px;
                font-style: normal; font-variant-ligatures: normal;
                font-variant-caps: normal; font-weight: 400;
                letter-spacing: normal; orphans: 2; text-align: start;
                text-indent: 0px; text-transform: none; white-space:
                normal; widows: 2; word-spacing: 0px;
                -webkit-text-stroke-width: 0px; background-color:
                rgb(255, 255, 255); text-decoration-style: initial;
                text-decoration-color: initial; display: inline
                !important; float: none;"></span></span> </span>
          <h2><a name="Manual_LRPT-Decoder_setup_"></a>Manual
            LRPT-Decoder setup<br>
          </h2>
          <br>
          Setup without using SDR in real time for manual processing
          S-files.<br>
          <b>Example ini configuration files for other modes are
            attached in the archive!</b><br>
          <br>
          <img src="img/decoder_m2.jpg" alt="" width="879" height="478"><br>
          <br>
          <b>Open M2_LRPT_Decoder.ini</b><br>
          <br>
          <b>Edit:</b><br>
          <br>
          [IN]<br>
          source=man or file path tcp will not work!<br>
          sat=M2 or M2.2 <br>
          mode=72k or 80k<br>
          <br>
          [OUT]<br>
          rgb=123.jpg (Meteor once in a while has maintenance cooling
          then IR channel's are turned off for some days making Channel
          1,2 and 3 active then this line must be inserted rgb=123.jpg 3
          visible channels + no IR otherwise when IR is active use
          125.jpg)<br>
          rgb_q=100<br>
          mono=yes<br>
          logs=no<br>
          APID70=no<br>
          VCDU=no<br>
          path=C:\Meteor\images-M2\<br>
          <br>
          GEO Creates a gcp which can be used for MeteorGIS or
          LRPT_Places to insert boundaries or cities..<br>
          <br>
          [GEO]<br>
          RoughStartTimeUTC=18-8-2019&nbsp; &lt;&lt;-- change to current
          date or date of re-processed s-file.<br>
          TleFileName=C:\Meteor\LRPT_Decoder\M2-2.txt&nbsp; &lt;&lt;--
          point to M2_tle.txt or M22 in MeteorGIS LRPT-Decoder folder.<br>
          Alfa_M2=110.8<br>
          Delta_M2=32<br>
          Alfa_M22=110.8<br>
          Delta_M22=-4.8<br>
          <br>
          Alfa - camera angle<br>
          Delta - offset along the line<br>
          &nbsp;<br>
          Selecting Delta achieve alignment of the coastline in the
          center of the image. <br>
          Then, changing Alfa, you can expand / contract images on a
          line.<br>
          <br>
          When choosing delta, be aware that a change of 1 will result
          in a shift of about 1 km for misplaced overlay correction.<br>
          <br>
          [FAST]<br>
          FORMAT=jpg<br>
          R=1<br>
          G=2<br>
          B=3<br>
          <br>
          (Meteor once in a while has maintenance cooling then IR
          channel's are turned off for some days making Channel 1,2 and
          3 active so the config is RGB 123, when IR is active use RGB
          125).<br>
          <br>
          <b>Save M2_LRPT_Decoder.ini</b><br>
          <h2><a name="Other_Tools_"></a>Other Tools<br>
          </h2>
          Image editing:<br>
          <br>
          There are 2 excellent programs to edit Meteor's saved images,
          SmoothMeteor from Les Hamilton and LRPT Image Processor from
          David Taylor both are freeware.<br>
          They have option to rectify the image so the 'Fish-eye' effect
          is gone, Create False colors on RGB125 images, Flip Infrared
          Nighttime images and convert them with a negative effect so
          they look like NOAA IR Images.<br>
          And many other options.<br>
          <br>
          Some extra explanation about Meteor images:<br>
          &nbsp;<br>
          When you save a Meteor image as an RGB125 BMP image, the image
          actually contains all the information for the three separate
          channels.<br>
          &nbsp;If you wish to store your Meteor images for the future,
          this is the best way.<br>
          &nbsp;<br>
          The new version of SmoothMeteor recognizes the 125.BMP part of
          the filename, and opens up the Palette menu.<br>
          &nbsp;<br>
          Here you find options to add palettes to the images.<br>
          &nbsp;<br>
          But you can also combine the channels in different ways: the
          RGB122 that is often used in LRPTofflineDecoder, but also the
          RGB125 (using the inverted channel 5), which is the same as
          the common colour composites made from NOAA HRPT channels
          1+2+4.<br>
          &nbsp;<br>
          There are also options to save each of the individual grey
          scale channels.<br>
          <br>
          http://leshamilton.co.uk/meteor3m.htm<br>
          <br>
          So change in LRPToffLineDecoder.ini :<br>
          <br>
          [OUT]<br>
          rgb=125.jpg<br>
          <br>
          <img src="img/smooth.jpg" alt="" width="906" height="682"><br>
          <br>
          SmoothMeteor - <a
            href="http://leshamilton.co.uk/meteor3m.htm" target="_blank"
            style="text-decoration:none">http://leshamilton.co.uk/meteor3m.htm</a><br>
          <br>
          <img src="img/lrptproc.jpg" alt="" width="712" height="674"><br>
          <br>
          LRPT Image Processor - <a
            href="http://www.satsignal.eu/software/LRPT-processor.html"
            target="_blank" style="text-decoration:none">http://www.satsignal.eu/software/LRPT-processor.html</a><br>
          <br>
          <h2><a name="Telemetry_Unpacker_"></a>Telemetry Unpacker<br>
          </h2>
          <br>
          Meteor M-N2-2 Telemetry Unpacker:<br>
          <br>
          Only for Meteor M-N2-2!<br>
          N-2-2 has a new different way of processing Telemetry on PID70
          e.g. info from Glonass and its position.<br>
          <br>
          Program for unpacking telemetry from APID70 for testing.<br>
          <br>
          Set APID70=yes in M2_LRPT_Decoder.ini [OUT] section.<br>
          <br>
          It starts like this:<br>
          <br>
          M22TelemetryUnpaker.exe 2019_07_29_LRPT_14-39-35.s.70<br>
          for unpacking 2019_07_29_LRPT_14-39-35.s.70,<br>
          will be formed 2019_07_29_LRPT_14-39-35.s.70.csv<br>
          <br>
          Added to the telemetry unpacker information of TLE and the
          calculation of coefficients, polynomials of the fourth degree
          representing the roll, pitch and yaw of Meteor M-N2-2.<br>
          TLE can be used in Orbitron and for geo-referencing
          processing. <br>
          Roll, pitch, yaw can improve snapping to absolute accuracy!<br>
          <br>
          Download <a href="http://happysat.nl/Telemetry.zip">Telemetry
            Unpacker</a><br>
          <br>
          <br>
          <h1 style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-style: normal; font-variant-ligatures:
            normal; font-variant-caps: normal; letter-spacing: normal;
            orphans: 2; text-align: start; text-indent: 0px;
            text-transform: none; white-space: normal; widows: 2;
            word-spacing: 0px; -webkit-text-stroke-width: 0px;
            text-decoration-style: initial; text-decoration-color:
            initial;"><a name="Amateur_Meteor_Images_Global_Observation"></a><font
              color="#FF0000">A</font>mateur<span>&nbsp;</span><font
              color="#FF0000">M</font>eteor<span>&nbsp;</span><font
              color="#FF0000">I</font>mages<span>&nbsp;</span><font
              color="#FF0000">G</font>lobal<span>&nbsp;</span><font
              color="#FF0000">O</font>bservation<span>&nbsp;</span><font
              color="#FF0000">S</font>ystem.</h1>
          <br>
          For AMIGOS (Only Meteor M-N2)<br>
          <br>
          Users of LRPT decoder will automatically send UDP packets via
          port 2013 to the server,<br>
          if section global in M2_LRPT_Decoder.ini config file contains
          AMIGO Setup.<br>
          <br>
          And if they work online, they become anonymous members of
          AMIGOS.<br>
          <br>
          Setup M2_LRPT_Decoder:<br>
          <br>
          If the new decoder is never started there is a section line
          called:<br>
          <br>
          [GLOB]<br>
          AmigoID=0<br>
          <br>
          After first start it will generate a uniqe ID for you, so
          meteor robonuka-servers can see from who this data is.<br>
          <br>
          Setup parameter AmigoID=0. Zero means that ID will be
          generated automatically.<br>
          For anonymus ID&gt;10000, for registred(future) ID&lt;10000<br>
          <br>
          Example (AmigoID=1174299964)<br>
          <br>
          Open M2_LRPT_Decoder.ini<br>
          <br>
          Add or change:<br>
          <br>
          [GLOB]<br>
          AmigoID=0<br>
          mode=UDP<br>
          path=C:\AMIGOS\ShareFolder (edit to your path of AMIGOS)<br>
          host=185.26.115.106<br>
          port=2013<br>
          <br>
          Save and Close.<br>
          <br>
          AmigosViewer is a program to view received data from users on
          the server as an image.<br>
          <br>
          Download: <a href="http://happysat.nl/AMIGOS.zip">
            AmigosViewer</a><br>
          <br>
          Setup AmigosViewer:<br>
          <br>
          1. Run AmigosViewer.exe.<br>
          2. If after run in Caption of AmigosViewer window you can see<br>
          &nbsp;&nbsp; "Amigos Viewer [FTP][LOGIN]" it is OK and you can
          go next paragraph.<br>
          &nbsp;&nbsp; If not it means a problems offline.<br>
          3. Click "Start".<br>
          4. If you want see picture realtime - click big button
          "START". If you want<br>
          &nbsp;&nbsp; to see old data - uncheck "Online image" and set
          datetime and after click the "START".<br>
          <br>
          <img src="img/AMIGOS_2.jpg" alt="" width="619" height="433"><br>
          <br>
          5. Wait the end of process.<br>
          <br>
          <img src="img/AMIGOS.jpg" alt="" width="629" height="438"><br>
          <br>
          6. Click "StopAndSave" pictures of the viewer are saved in
          AMIGOS/IMAGES.<br>
          7. Click "Exit".<br>
          8. You can now view or process from folder images.<br>
          <br>
          <a href="http://185.26.115.106:8080/" target="_blank">AMIGOS
            Webserver</a><br>
          <br>
          Special thanks to:<br>
          Oleg (LRPT-Decoder), Vasili (Meteor Demodulator/DDE-Tracker
          Plugins), Christoper Marchand and Thibaut Fouine (MeteorGIS),
          Youssef Touil (SDR#/Airspy Radio), Nooelec.com, Les Hamilton
          (SmoothMeteor),&nbsp; David Taylor (LRPT Image Processor),
          Herman-PB0AHX (Host), Mother Russia (Meteor M-N-Serie), and
          everybody on the Facebook APT-Group!<br>
        </div>
        <div class="pagefooter"> This page was last edited on 22.08.2020
          | Setup Meteor M-N2/N2-2 with LRPT-Decoder by Happysat </div>
      </div>
    </div>
    <script src="https://code.jquery.com/jquery-1.12.0.min.js"></script>
    <script>window.jQuery || document.write('<script src="js/vendor/jquery-1.12.0.min.js"><\/script>')</script>
    <script src="script.js"></script>
  </body>
</html>
