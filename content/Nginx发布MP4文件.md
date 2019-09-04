Title: Nginx发布MP4文件
Date: 2019-07-27
Category: Nginx
Tags: nginx,mp4

    server {
        listen  80;
        server_name  video.example.com;

        location / {
            root /usr/share/nginx/html/videos;
            mp4;
            mp4_buffer_size     1m;
            mp4_max_buffer_size 4096m;
        }
    }
