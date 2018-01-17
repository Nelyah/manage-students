Manage Students scripts
=======================

This repos is made for the class UE 1I002 at UPMC. In there you will find scripts allowing you to perform various task teacher-related:
* Create for each student a separate folder containing all of their submitted TMEs
* Check submissions of each student, with the possibility to get a mail report
* Mailing individually each student with all comments made during the correction
* Sending a mail to all students present in the group

Setup:
------

*All scripts should be executed from the git repo folder. I didn't test their behaviour outside of it.*
Two files are mandatory to have inside this directory:
- ´logins´
- ´${GROUP}.csv´

The ´GROUP.csv´ file can be downloaded from the [DBUFR website][1]. The ´logins´ file *must* define the following variables:
- GROUP: The name of your group (e.g. GROUP=G22.1)
- CSV: The name of the CSV file in the directory
- NB_WEEK: How many weeks will there be througout this semester?
- USER_MAIL: CAS authentication login (used to connect to UPMC mailserver to send mails)
- PASSWD_MAIL: CAS authentication password (same reason)
- URL_TME: You should be able to leave it to default (http://webia.lip6.fr/~li115/enseignants)

Usage:
------

Download the ´GROUP.csv´ file from [DBUFR][1] and place it in this directory. Set up all variables in the ´logins´ file correctly. Now, run:

    ./formatCSV
This will change the format of the CSV file to our liking as well as removing special characters.

    ./setup
This will create all subfolders for each students.

If you want to send a mail to all students, edit the ´send_mail_to_students´ script and execute it.

    ./send_mail_to_students

To see students marks:

    ./get_marks -i 1
will output marks for TME-solo1. Adding the option ´-w´ will effectively write in each student's commentary file the total note (summed of all exercises).
Some modifications can be made to the global mark (for example: exam submitted late). This is done by adding a line beginning with "MALUS". Some reason can then be given, and the factor following the colon (:) will be applied.

    MALUS (Je suis de mauvaise humeur) : -6
Will apply a -6 point malus to the global mark.
For sending marks to students, edit the file ´send_student_mark´ accordingly then execute it.

By running the ´routine.sh´ script, the program will fetch every TME for each student, check their submissions and send you a report.

[1]: https://www-dbufr.ufr-info-p6.jussieu.fr/lmd/2004/dbufr2/auths/
