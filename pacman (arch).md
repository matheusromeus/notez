
https://wiki.archlinux.org/title/Pacman/Rosetta

-S, -R, -Q

-S = sync
y = refresh the database
u = upgrade

pacman -Syyuw -> does everything and downloads it locally, i can choose to manually install it (the double yy force refreshes the database)

apt update = -Sy
apt upgrade = -Su

pacman -Ss vim = search all the vim packages

pacman -Rns vim = remove vim, system configs and if this package is needed by some other packages, then we have to remove that first (that check is the 's' flag)

pacman -Q = list out all packages you have

pacman -Qe = list out packages you explicitly installed

pacman -Qn = only from main repo
pacman -Qm = only from AUR

pacman -Qdt = unneeded dependencies

pacman -Qs vim = search vim locally 

pacman -Sc = remove obsolete packages (older installations)

run pacman -Qq | less and then put that in a cronjob and push to github as a cron. then you can make an install script to clone your laptop in secs

pacman -Ql vim = directories that vim install files are there