---
layout: page
title: Anci2pd batch
permalink: /Anci2pd_batch/
---

{% highlight PowerShell %}

@ECHO OFF
REM BFCPEOPTIONSTART
REM Advanced BAT to EXE Converter www.BatToExeConverter.com
REM BFCPEEXE=StartANCI2PdPortable.exe
REM BFCPEICON=Logo3c-A.ico
REM BFCPEICONINDEX=-1
REM BFCPEEMBEDDISPLAY=0
REM BFCPEEMBEDDELETE=1
REM BFCPEADMINEXE=0
REM BFCPEINVISEXE=0
REM BFCPEVERINCLUDE=1
REM BFCPEVERVERSION=1.0.12.0
REM BFCPEVERPRODUCT=ANCI2Pd Portable
REM BFCPEVERDESC=ANCI2Pd Anoncoin & I2Pd bundle
REM BFCPEVERCOMPANY=Anoncoin Core & PurpleI2P
REM BFCPEVERCOPYRIGHT=© 2013-2016 Anoncoin Core & PurpleI2P
REM BFCPEOPTIONEND
@ECHO ON
@echo off
title ANCI2Pd - Anoncoin preconfigured for I2Pd - launcher
set $pause=ping.exe 0.0.0.0 -n
ver| find “6.” >nul && set $pause=timeout.exe /t
set ANCqtc=anoncoin-qtc.exe
set ANCopt=-i2p.options.enabled=1 -onlynet=i2p
set ANCdir=Anoncoin\data
set i2pd=i2pd.exe 
taskList|find /i “%i2pd%”>nul&&(goto runANC)||(goto starti2p)
:starti2p
start "" “I2Pd/%i2pd%”
echo I2Pd Router starting
echo Please wait
echo -------------------------------------
for /L %%B in (0,1,35) do (call :EchoWithoutCrLf “.” && %$pause% 2 >nul)
echo .
echo -------------------------------------
echo Welcome to I2P Network
:runANC
IF NOT EXIST %ANCdir% mkdir %ANCdir%
cls
echo.
echo Press g for Anoncoin to generate a new static destination...
echo ------------------------------------------------------------
choice /c gn /T 2 /D n
if errorlevel 2 goto runANCnow
if errorlevel 1 goto runANCgen
:runANCgen
cls
echo.
echo ============================================================
echo ... Generating a new static destination now
echo ============================================================
IF EXIST %ANCdir%\i2pkey.dat del %ANCdir%\i2pkey.dat
start "" “Anoncoin/%ANCqtc%” %ANCopt% -datadir=%ANCdir% -generatei2pdestination
%$pause% 5 >nul
exit /b 0
:runANCnow 
cls
echo.
echo ============================================================
IF NOT EXIST %ANCdir%\i2pkey.dat echo ... Anoncoin running with a dynamic destination
IF EXIST %ANCdir%\i2pkey.dat echo ... Anoncoin running with a static destination
echo ============================================================
start "" “Anoncoin/%ANCqtc%” %ANCopt% -datadir=%ANCdir%
%$pause% 5 >nul
exit /b 0 
rem ==========================================================================
rem ==========================================================================
rem Procedure EchoWithoutCrLf
rem 
rem %1 : text for output.
rem ==========================================================================
:EchoWithoutCrLf
   
   <nul set /p strTemp=%~1
   exit /b 0
rem ==========================================================================

{% endhighlight %}

