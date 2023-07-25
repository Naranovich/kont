Сделать chroot для /bin/bash и перенести в новй корень программу ls
nikita@nikita-VirtualBox:~$ sudo chroot GB
[sudo] пароль для nikita: 
bash-5.1# exit 
exit
nikita@nikita-VirtualBox:~$ where is ls
where: команда не найдена
nikita@nikita-VirtualBox:~$ whereis ls
ls: /usr/bin/ls /usr/share/man/man1/ls.1.gz
nikita@nikita-VirtualBox:~$ makedir GB/usr
Команда «makedir» не найдена. Возможно, вы имели в виду:
  command 'makedic' from deb makedic (6.5deb2-13)
Try: sudo apt install <deb name>
nikita@nikita-VirtualBox:~$ mkdir GB/usr
nikita@nikita-VirtualBox:~$ mkdir GB/usr/bin
nikita@nikita-VirtualBox:~$ ldd /usr/bin/ls
	linux-vdso.so.1 (0x00007ffc94da5000)
	libselinux.so.1 => /lib/x86_64-linux-gnu/libselinux.so.1 (0x00007fafaff55000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fafafc00000)
	libpcre2-8.so.0 => /lib/x86_64-linux-gnu/libpcre2-8.so.0 (0x00007fafafebe000)
	/lib64/ld-linux-x86-64.so.2 (0x00007fafaffb4000)
nikita@nikita-VirtualBox:~$ cp /usr/bin/ls GB/usr/bin/
nikita@nikita-VirtualBox:~$ cp /lib/x86_64-linux-gnu/libselinux.so.1 GB/lib/
nikita@nikita-VirtualBox:~$ cp /lib/x86_64-linux-gnu/libc.so.6  GB/lib/
nikita@nikita-VirtualBox:~$ cp /lib/x86_64-linux-gnu/libpcre2-8.so.0 GB/lib/
nikita@nikita-VirtualBox:~$ cp /lib64/ld-linux-x86-64.so.2 GB/lib64/
nikita@nikita-VirtualBox:~$ sudo chroot GB
bash-5.1# ls -l 
total 16
drwxrwxr-x 2 1000 1000 4096 Jul 25 19:23 bin
drwxrwxr-x 2 1000 1000 4096 Jul 25 19:41 lib
drwxrwxr-x 2 1000 1000 4096 Jul 25 19:32 lib64
drwxrwxr-x 3 1000 1000 4096 Jul 25 20:13 usr
bash-5.1# 

