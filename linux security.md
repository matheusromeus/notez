
1. users, groups & sudo
2. understand permissions


least required privilege

add a user using `useradd` 

useradd -m kevin

groups kevin

usermod -aG wheel, users kevin

passwd boris

visudo 

chmod 7 7 7
owner, group, others
u - owner

	superuser will always have UID as 0 in POSIX systems

/etc/sudoers