Denna template kommer sätta upp följande,

Just nu kan enbart detta sättas upp i europe-se-1a inte europe-se-1b

Webserver med PHP och Apache2 
NFS server med NFS delade mappar med webservarna
DB server med MariaDB
Lastbalanserare i Binerocloud som använder round-robin för att skicka vidare traffik från port 80 och 443 till webserverna


Du behöver en ssh-key / nyckel par och ett privat nät uppsatt på ditt konto för att köra denna template
Du kan använda template Privat nätverk för att sätta upp ett privat nät om du inte redan skapat ett själv.

Backup alternativet kommer enbart ta backup på NFS och MariaDB volymerna och inte web volymen. Web instancens filer ligger delade på NFS instancens, så dem tas redan med och backupas genom NFS instancens backup.
