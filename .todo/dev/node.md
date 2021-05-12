Installer
    npm install pm2@latest -g

Start
    pm2 start app.js

    pm2 stop        <app_name|namespace|id|'all'|json_conf>
    pm2 restart     <app_name|namespace|id|'all'|json_conf>
    pm2 delete      <app_name|namespace|id|'all'|json_conf>

Lister
    pm2 ls

Logs
    pm2 logs

Monitoring 
    pm2 monit
