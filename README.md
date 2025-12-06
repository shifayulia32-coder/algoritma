```
@echo off
title Recovery Data - Modified
setlocal enabledelayedexpansion

:: === Folder sumber dan backup ===
set SOURCE=C:\simulasiDrive
set BACKUP=backup_result
set ZIPFILE=backup_result.zip

:: === Membuat folder backup jika belum ada ===
if not exist "%BACKUP%" mkdir "%BACKUP%"

echo =======================================
echo       RECOVERY & BACKUP SYSTEM
echo =======================================
echo.

:: === Hitung total file .pdf dan .docx ===
set count=0
for %%f in ("%SOURCE%\*.pdf" "%SOURCE%\*.docx") do (
    if exist "%%f" (
        set /a count+=1
    )
)

echo Total file yang akan dibackup: %count%
echo.

:: === Proses backup + progress counter ===
set processed=0
for %%f in ("%SOURCE%\*.pdf" "%SOURCE%\*.docx") do (
    if exist "%%f" (
        copy "%%f" "%BACKUP%" >nul
        set /a processed+=1
        echo [!processed!/%count%] Memproses: %%~nxf
    )
)

echo.
echo Backup selesai!
echo.

:: === Verifikasi checksum ===
echo Membuat file checksum...
echo ============================ > checksum.txt

for %%f in ("%BACKUP%\*.pdf" "%BACKUP%\*.docx") do (
    echo File: %%~nxf >> checksum.txt
    certutil -hashfile "%%f" SHA256 >> checksum.txt
    echo. >> checksum.txt
)

echo Checksum selesai dibuat: checksum.txt
echo.

:: === Compress ke ZIP ===
echo Mengcompress folder backup...
powershell -command "Compress-Archive -Path '%BACKUP%\*' -DestinationPath '%ZIPFILE%' -Force"

echo Compress selesai: %ZIPFILE%
echo.

echo ==== PROSES SELESAI ====
pause

```
