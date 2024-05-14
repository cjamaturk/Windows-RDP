# Windows-RDP
Gitpod kullanarak açacağımız Windows RDP
________________________________________________
# Yine bir Gitpod Workspace oluşturmamız gerekecek
![Gitpod New Workspace](https://raw.githubusercontent.com/cjamaturk/XFCE4-VDS/main/gitpodnw.png)

![Gitpod Seçilecek Repo](https://raw.githubusercontent.com/cjamaturk/XFCE4-VDS/main/gitpodrepo.png)

![Gitpod Terminal+Large](https://raw.githubusercontent.com/cjamaturk/XFCE4-VDS/main/gitpod.png)

Continue dedikten sonra karşımıza şöyle bir terminal açılacak:

![Gitpod Terminal](https://raw.githubusercontent.com/cjamaturk/XFCE4-VDS/main/gitpodterminal.png)

# Artık hazırız.Kodları yazalım.
Tabiki de ilk önce update+upgrade

```bash
sudo apt update -y
sudo apt upgrade -y
sudo apt install virtualbox -y
```
# Şimdi Windows 10 kurulum dosyamızı indirelim.

```bash
wget -O windows10.zip https://download1530.mediafire.com/9fshjehpgopgN23aZvWPSkdWO0ohQidr0K3dWb4mpmB64L4k6cSEiXRYxyQsRsy2TwgQHhl66zLVSmDRkQ3yQr3Kq1a9k2cQOWwZl402AM6Nr9fEAgqi9657CMbDTNOuAl4UbYFrffy5jhtSuM8S77B5JFIW2WXt2brBplhBj49xuQ/zcq26ogtvhuwjnn/TR_ISO_x64_2021_TeknikNot.com.zip
```

# Türkçe LTSC dosyasını başka türlü bulamadım.Bu yüzden unzip yapacağız.

```bash
unzip windows10.zip
sudo rm windows10.zip
sudo mv tr-tr_windows_10_enterprise_ltsc_2021_x64_dvd_e55b1896.iso windows.iso
```

# Şimdi sanal makineyi kurmak kaldı.

vboxmanage createvm --name "Windows" --ostype "Windows10_64" --register
vboxmanage modifyvm "Windows" --memory 12288 --vram 128
vboxmanage storagectl "Windows" --name "SATA Controller" --add sata --controller IntelAhci
vboxmanage storageattach "Windows" --storagectl "SATA Controller" --port 0 --device 0 --type hdd --medium "windows.vdi"
vboxmanage storageattach "Windows" --storagectl "SATA Controller" --port 1 --device 0 --type dvddrive --medium "windows.iso"
vboxmanage startvm "Windows" --type headless




# yarıda kaldı devamı sonra inşallah
