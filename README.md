# LAB 2  Rooting Android

 Cours  Sécurité des applications mobiles
---

## Objectif du lab

Dans ce lab, je vais rooter un environnement Android (AVD) afin de comprendre l'impact du root sur la sécurité du système.

---

## Étape 1  Rooter l'AVD

J'active le mode root s

```bash
adb root
```

Vérification 

![Activation du mode root ADB](images/imagesadb_root.png)

---

Je remonte la partition système en lectureécriture 

```bash
adb remount
```

Vérification 

![Remontage partition système](images/imagesadb_remount.png)

---

## Étape 2  Vérification du root

Je vérifie mes privilèges 

```bash
adb shell id
```

Vérification 

![Vérification uid=0 root](images/imagesadb_shell_id.png)

---

Je vérifie l'état du système 

```bash
adb shell getprop ro.boot.verifiedbootstate
```

Vérification 

![État du verified boot](images/imagesverified_boot.png)

---

Je teste la commande `su` 

```bash
adb shell su -c id
```

Vérification 

![Test commande su](images/imagessu_test.png)

---

## Étape 3  Vérifier l'AVD

```bash
adb devices
```

* Vérification 

![Liste des appareils connectés](images/imagesadb_devices.png)

---

## Étape 4  Installer l'application

```bash
adb install app-debug.apk
```

Vérification 

![Installation de l'APK](images/imagesinstall_apk.png)

--- 
## Étape 5 Désactiver Verity 

```bash
adb disable-verity
adb reboot
adb remount
```

Vérification 

![Désactivation de dm-verity](images/imagesdisable_verity.png)

---

## Étape 6  Journalisation

```bash
adb logcat -d  tail -n 200  logcat_root_check.txt
```

Vérification 

![Capture des logs logcat](images/imageslogcat.png)

---

## Étape 7  Traçabilité

Je vérifie que l'application fonctionne correctement 

Vérification 

![Application fonctionnelle](images/imagesapp_launched.png)

---

Je confirme que le root est actif 

Vérification 

![Root confirmé et actif](images/imagesroot_success.png)

---



## Conclusion

Dans ce lab, j'ai appris que le root donne un contrôle total sur Android mais compromet la sécurité du système. Il doit être utilisé uniquement dans un environnement de test isolé.


--- 