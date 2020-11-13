## PHP + MSSQL + nginx

Here is a example of two or more php websites inside separate dockers running on a custom php-fpm image with a nginx serving the two websites.

I didn't found anything like it online and it was a pain to get working, got bits and pieces from everywhere, the main problem was configuring nginx to function with 2 fpm servers.

But now that I made this example it is easy.

Just remember to delete de volumes when updating the images.