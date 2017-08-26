# Google-Search-Auto-Complete
This project is to implement the basic function of auto complete. The input from users can be completed automatically and the probable results can be ordered according to the frequency of appearance.
#Usage
1.Get the conifguration of PC to build connection between map reduce and PC.
$ ifconfig | grep inet | grep broadcast 
2.Get MySQL port and password
$ SHOW VARIABLES WHERE Variable_name = 'port' ;
or
$ status;
#Scalibility
1.When the data is too big, we can use trie tree to optimize.
