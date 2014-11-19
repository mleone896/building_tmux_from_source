# Install tmux on Centos release 6.5
# 

# READ THIS FIRST!!!
# MAKE SURE YOU HAVE BUILD TOOLS/COMPILERS TO BUILD STUFF FROM SOURCES
# yum groupinstall "Development Tools"


# CD TO TEMPORARY DIRECTORY
cd < build dir> 

# INSTALL NCURSES DEVEL
yum -y install ncurses-devel

# DOWNLOAD SOURCES FOR LIBEVENT AND MAKE AND INSTALL
#### wget https://github.com/downloads/libevent/libevent/libevent-2.0.21-stable.tar.gz
curl -OL https://github.com/downloads/libevent/libevent/libevent-2.0.21-stable.tar.gz
tar -xvzf libevent-2.0.21-stable.tar.gz
cd libevent-2.0.21-stable
./configure
make
sudo make install

# DOWNLOAD SOURCES FOR TMUX AND MAKE AND INSTALL
#### wget http://downloads.sourceforge.net/tmux/tmux-1.9a.tar.gz
curl -OL http://downloads.sourceforge.net/tmux/tmux-1.9a.tar.gz
tar -xvzf tmux-1.9a.tar.gz
cd tmux-1.9a
./configure
make
sudo make install

# SWITCH BACK TO REGULAR USER AND EDIT YOUR BASHRC (OR ZSH CONFIG)
echo export LD_LIBRARY_PATH=/usr/local/lib >> ~/.bash_profile
. ~/.bash_profile
#### source ~/.bash_profile
