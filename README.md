# KL-01_HX_ERK_INIT
#!/bin/bash
set -e

ARCHIVE="../KL-01_declaration_2025-08-23.zip"
TARGET_DIR="KL-01_declaration_2025-08-23"
REMOTE_URL="git@github.com:elancray/TON_REPO.git"   # remplace par ton repo

# vérification
[ -f "$ARCHIVE" ] || { echo "Archive manquante: $ARCHIVE"; exit 1; }

mkdir -p "$TARGET_DIR" && cd "$TARGET_DIR"
unzip -o "$ARCHIVE"
git init
git add .
git commit -m "KL–01 declaration 2025-08-23"
git branch -M main
git remote add origin "$REMOTE_URL"
git push -u origin main

# optionnel : upload IPFS (si ipfs est installé)
# CID=$(ipfs add -Q -r .)
# echo "IPFS CID: $CID"
# echo "CID ajouté au manifest.yaml"