
Next-Gen ERD: Design, Explore, Document and Analyze your database
https://github.com/azimuttapp/azimutt 



Run Docker:
```
docker run -d --name azimutt \
--env-file .env \
-p 4000:4000 \
ghcr.io/azimuttapp/azimutt:main
tail -f /dev/null && cat ~/.bash_history
```