#### Index
- [Hyper-V Guest OS stopped unexpectedly (停止中 suspended / shutting down all the time)](https://github.com/fahmifahim/windows-daily/blob/master/windows.md#hyper-v-guest-os-stopped-unexpectedly-%E5%81%9C%E6%AD%A2%E4%B8%AD-suspended--shutting-down-all-the-time)
- [Find Windows 10 Serial Number](https://github.com/fahmifahim/windows-daily/blob/master/windows.md#find-windows-10-serial-number)


#### Hyper-V Guest OS stopped unexpectedly (停止中 suspended / shutting down all the time)
```bat
# 1. Execute cmd as Administrator


# 2. Check the current vm process (in NORMAL condition without error vm)
$ tasklist /FI "IMAGENAME eq vm*"

IMAGENAME                     PID  SESSION          SESSION #   MEMORY USAGE
========================= ======== ================ =========== ============
vmms.exe                      5368 Services                   0     19,788 K
vmcompute.exe                 6904 Services                   0      6,492 K


# 3. Tasklist when one vm is hangout/suspended/shutting down all the time
$ tasklist /FI "IMAGENAME eq vm*"

IMAGENAME                     PID  SESSION          SESSION #   MEMORY USAGE
========================= ======== ================ =========== ============
vmms.exe                      5368 Services                   0     19,788 K
vmcompute.exe                 6904 Services                   0      6,492 K
vmwp.exe                     19104 Services                   0     15,296 K
vmmem                        20200 Services                   0          N/A


# 4. Kill with force the wmp.exe (process that hold the suspended guest os vm)
$ taskkill /F /PID 19104


# 5. Start the guest os as usual
```

#### Find Windows 10 Serial Number
```bash
# command
wmic csproduct get identifyingnumber

# result
IdentifyingNumber     Name
JPA3039FWR              HP EliteBook 2570p

-or-
# command 
wmic bios get serialnumber

# result
Serial Number
JPA3039FWR

```
