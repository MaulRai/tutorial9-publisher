a. How much data your publisher program will send to the message broker in one
> Program publisher tersebut akan mengirim 5 buah pesan ke message broker dalam satu kali eksekusi. Masing-masing pesan merupakan instance dari struct UserCreatedEventMessage yang berisi dua field: user_id dan user_name, keduanya berupa string. Karena pesan dikodekan menggunakan Borsh (yang relatif efisien dalam serialisasi), total data yang dikirim bergantung pada panjang string-string tersebut. Secara kasar, jika setiap pesan memiliki sekitar 30–40 byte (tergantung panjang string), maka total data yang dikirim ke broker adalah sekitar 150–200 byte. Namun, ini belum termasuk overhead protokol AMQP dan metadata lainnya.

b. The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber
program, what does it mean?
> URL “amqp://guest:guest@localhost:5672” yang digunakan baik di program subscriber maupun publisher menunjukkan bahwa keduanya terhubung ke broker message yang sama, yaitu RabbitMQ (atau broker lain yang kompatibel dengan AMQP) yang berjalan secara lokal di komputer (localhost) pada port 5672. Penggunaan username dan password yang sama, yaitu “guest”, menandakan bahwa keduanya menggunakan kredensial default untuk mengakses broker. Ini berarti publisher akan mengirim pesan ke broker, dan subscriber akan menerima pesan dari broker yang sama, memungkinkan terjadinya komunikasi antar program secara asynchronous.

### running RabbitMQ
![running RabbitMQ.](images/running-rabbitmq.png)

### publisher connected
![running RabbitMQ.](images/publisher-connected.png)

### subscriber connected
![running RabbitMQ.](images/subscriber-connected.png)

### Monitoring chart based on publisher
![running RabbitMQ.](images/monitoring-chart-based-on-publisher.png)