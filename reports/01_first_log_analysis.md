Last login: Tue Dec  2 12:40:53 on console
juanpablo@Mini-de-Juan ~ % who

juanpablo        console      Dec  2 12:40 
juanpablo        ttys000      Dec  3 20:32 
juanpablo@Mini-de-Juan ~ % last | head -n 10
juanpablo  ttys000                         Wed Dec  3 20:32   still logged in
juanpablo  console                         Tue Dec  2 12:40   still logged in
reboot time                                Tue Dec  2 12:40
shutdown time                              Tue Dec  2 00:28
juanpablo  console                         Mon Dec  1 23:23 - 00:28  (01:04)
reboot time                                Mon Dec  1 23:21
shutdown time                              Mon Oct 20 18:16
juanpablo  console                         Mon Oct 20 14:42 - 18:16  (03:33)
reboot time                                Mon Oct 20 14:44
shutdown time                              Tue Sep 23 17:24
juanpablo@Mini-de-Juan ~ % ls /var/log

CoreDuet			shutdown_monitor.log
DiagnosticMessages		system.log
PrivacyPreservingMeasurement	system.log.0.gz
alf.log				system.log.1.gz
apache2				uucp
asl				wifi.log
com.apple.wifi.analytics	wifi.log.0.bz2
com.apple.wifivelocity		wifi.log.1.bz2
com.apple.xpc.launchd		wifi.log.10.bz2
cups				wifi.log.2.bz2
dm				wifi.log.3.bz2
fsck_apfs.log			wifi.log.4.bz2
fsck_apfs_error.log		wifi.log.5.bz2
fsck_hfs.log			wifi.log.6.bz2
install.log			wifi.log.7.bz2
mDNSResponder			wifi.log.8.bz2
powermanagement			wifi.log.9.bz2
ppp
juanpablo@Mini-de-Juan ~ % sudo tail -n 50 /var/log/auth.log

Password:
tail: /var/log/auth.log: No such file or directory
juanpablo@Mini-de-Juan ~ % JuanReyReal
zsh: command not found: JuanReyReal
juanpablo@Mini-de-Juan ~ % cd ~/Desktop/CYBERSCHOOL

juanpablo@Mini-de-Juan CYBERSCHOOL % touch 01_first_log_analysis.md

juanpablo@Mini-de-Juan CYBERSCHOOL % open 01_first_log_analysis.md

No application knows how to open URL file:///Users/juanpablo/Desktop/CYBERSCHOOL/01_first_log_analysis.md (Error Domain=NSOSStatusErrorDomain Code=-10814 "kLSApplicationNotFoundErr: E.g. no application claims the file" UserInfo={_LSLine=1747, _LSFunction=runEvaluator}).
juanpablo@Mini-de-Juan CYBERSCHOOL % open -e 01_first_log_analysis.md

juanpablo@Mini-de-Juan CYBERSCHOOL % 
