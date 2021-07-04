---
title: "Cold Storage: Dateien verschlüsseln und auf B2 archivieren"
layout: post
tags: pgp bash script backblaze-b2
categories: derEntwickler
---

Eine wunderbare Möglichkeit Dateien zu archivieren bietet der unschlagbar günstige Object-Storage von Backblaze B2. Da es sich um eine "public" Cloud handelt,
sollte jede Datei, die hochgeladen wird, verschlüsselt werden.

Aufgrund seiner Langlebigkeit und erwiesenen Sicherheit nutze ich PGP um Datei-Archive zu verschlüsseln. Das Backblaze B2 CLI ist lässt allerdings nicht zu, mehrere Dateien auf einen Schlag hochzuladen, weswegen ich ein kleines Script schreiben musste, um alle Dateien innerhalb eines Verzeichnis zu verschlüsseln und hochzuladen.


```bash
echo "Enter target bucket name"
read TARGET_BUCKET

echo "Enter target directory"
read TARGET_DIR

echo "Enter key to be used (email)
read GPG_KEY

cd $1
for i in *; do
   echo ------------------------------------------
   echo The current file is $i

   ENC=$i.asc
   echo Encrypting the file to $ENC...

   gpg \
    --encrypt \
    --recipient $GPG_KEY \
    --armour \
    --batch \
    $i

   echo Encryption finished!
   echo -------------------------------------------
   echo Uploading to b2
   b2 upload_file $TARGET_BUCKET $ENC $TARGET_DIR/$ENC
   echo Upload finished, removing $ENC
   rm $ENC
   echo "Done! Next file..."
done
```