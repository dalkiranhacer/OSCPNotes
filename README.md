# OSCP Notes – Quick Snippets

This repository contains small, copy-paste ready commands and one-liners I frequently use during OSCP-style labs and exams.

> ⚠️ For educational purposes only.  
> Do not use these techniques on systems you do not own or have explicit permission to test.

---

## ⚡ Quick Snippets (Copy-Paste Ready)

### 🔐 Generate NTLM Hash from a Plain Password
```bash
python3 -c 'import hashlib; print(hashlib.new("md4", "purPLE9795!@".encode("utf-16le")).hexdigest())'
