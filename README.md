```
setlocal enabledelayedexpansion
 
echo MEMULAI PROSES BACKUP DATA...
echo ==============================
 
set "sumber=%USERPROFILE%\Desktop\simulasidriveD"
set "tujuan=%USERPROFILE%\Desktop\SimulasiDrive_Backup"
 
:: Membuat folder backup dengan timestamp
for /f "tokens=1-4 delims=/: " %%a in ("%date% %time%") do (
   set "datetime=%%d-%%b-%%a_%%c-%%d-%%e"
)
set "backup_folder=Backup_%datetime%"
mkdir "%tujuan%\%backup_folder%"
 
echo Sumber  : %sumber%
echo Tujuan  : %tujuan%\%backup_folder%
echo.
 
REM Inisialisasi counter dan log file
set /a count=0
set "logFile=%tujuan%\%backup_folder%\backup_log.txt"
echo Proses backup dimulai pada %date% %time% > "%logFile%"
 
echo Menyalin file .pdf dan .docx...
 
REM Loop untuk backup file .pdf dan .docx
for /r "%sumber%" %%f in (*.pdf *.docx) do (
   set /a count+=1
   set "srcfile=%%f"
   set "filename=%%~nxf"
 
   REM Copy file ke folder backup
   copy /y "%%f" "%tujuan%\%backup_folder%\!filename!" >nul
 
   REM Verifikasi ukuran file sumber dan tujuan
   for %%A in ("%%f") do set "sizeSrc=%%~zA"
   for %%B in ("%tujuan%\%backup_folder%\!filename!") do set "sizeDest=%%~zB"
 
   if !sizeSrc! EQU !sizeDest! (
       echo !count!. !filename! - Copy berhasil, Ukuran: !sizeDest! bytes
       echo !count!. !filename! - Copy berhasil, Ukuran: !sizeDest! bytes >> "%logFile%"
   ) else (
       echo !count!. !filename! - Gagal copy!
       echo !count!. !filename! - Gagal copy! >> "%logFile%"
   )
 
   REM Progress bar (dot setiap file)
   <nul set /p=.
)
 
echo.
echo Total file yang disalin: %count%
echo ==============================
echo Backup selesai pada %date% %time% >> "%logFile%"
 
REM Compress hasil backup ke file ZIP dengan powershell
set "zipFile=%tujuan%\Backup_%datetime%.zip"
powershell Compress-Archive -Path "%tujuan%\%backup_folder%\*" -DestinationPath "%zipFile%" -Force
 
echo Backup telah dikompresi ke:
echo %zipFile%
 
pause
```
