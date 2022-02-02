FROM debian:latest

WORKDIR /app

RUN apt update

RUN apt install -y gpg wget lsb-release ca-certificates apt-transport-https software-properties-common gnupg2

RUN wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg

RUN echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" | tee /etc/apt/sources.list.d/sury-php.list

RUN gpg --no-default-keyring --keyring /usr/share/keyrings/sury-archive-keyring.gpg --keyserver https://packages.sury.org/php/apt.gpg --recv-keys

RUN apt update 

RUN apt install -y apache2 php curl php-xml php-intl php-mbstring php-mysql php-curl php-sybase

RUN curl -s https://getcomposer.org/installer | php

RUN mv composer.phar /usr/local/bin/composer

EXPOSE 80

CMD ["-D", "FOREGROUND"]

ENTRYPOINT ["apachectl"]

#ENTRYPOINT [ "/etc/init.d/apache2 start" ]

#CMD [ "systemctl ", " start " , " apache2 "]