# Password Changes & User Maint

To change password on backend for a specific user

echo -e "Cerner123\nCerner123" | passwd b088060 chage -d 0 b088060

To change acct expire date

chage -E 2022-12-31 b088060
