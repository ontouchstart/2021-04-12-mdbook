FROM debian:stable
RUN apt-get update -qy
RUN apt-get install -qy make groff
RUN sed -i 's/papersize a4/papersize letter/' /usr/share/groff/current/font/devpdf/DESC # set groff papersize to letter
RUN dpkg -l
