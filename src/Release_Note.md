# [Release_Note] aic8800d_linux_sdk_V5.0_2026_0509_2195ae36

## Driver

### All driver 
- fix CHANNEL_ACCESS_REQ commond param err
- support NL80211_IFTYPE_AP_VLAN
- add IEEE80211_HE_MAC_CAP3_MAX_AMPDU_LEN_EXP_VHT_2 to fix be200/tplink-be9300 rxrate low in apmode
- fix iw dev wlan0 station dump no output in stamode
- fw_panic_ind update
-  modify funcs use wrong vif when use P2P0
- fix csa match vif fail when interface down
- fix memleak with amsdu in ap mode
- fix rwnx_txdatacfm cfg80211_mgmt_tx_status panic after del interface
- 8800d80x2 user_ext_flags support USER_CAPA_CALIB_DISABLE_FLAG
- rx msg add msgid parser, fix potential memleak if invalid msg taskid or id_idx recvd
- default CONFIG_TEMP_COMP = y consistent with lmacfw

### USB driver
- support NL80211_IFTYPE_AP_VLAN
- add set_chan_calib & rdwr_gpio rfcmd
- compatibility D80ND40N
- add RDWR_EFUSE_BT_LNA_MODE cmd
- add CONFIG_REKEY_OFFLOAD for D80ND40N (need fw support)

### SDIO driver
-  fix some build errors on kernel 5.15
- first add D80ND40N support
- fix D80X2 D80ND40N rftest error
-  add temp ctrl api

### PCIE driver
- add m80x2p fw with usb bt support
- add more arch support

### wifi_hal

+ N/A

## BT Patch

- D80ND40N

  1.add patch for efuse_block_write;
  2.add usb sleep mode, need lpm_en==2;
  3.modify for sleep;
  4.modify for sco data report err;
  5.improve transmission rate and dynamically adjust power when wifi connect;
  6.add set bt_pwr_ofst through hci cmd;
  7.close iso feature, and add wakeup for ipc while deep sleep.
  8.first add u02c bt patch

- D80D40

  1.fix a assert about error irq;
  2.add ps evt duration when device as source;
  3.fix the issue of music stuttering while inq;
  4.modify for coex with sco;
  5.add usb sleep mode;
  6.fix the codes error that ble con_intv_max was not updated in the con upd;
  7.modify for lmp packet type table req reply delay which make the lc state error;
  8.modify for coex with btacl + lecon + btsniff mouse;
  9.change the lmp name req before role switch;
  10.add poll packet during page;
  11.modify for scan and inq with page, and make ch_derta to 25 as dft;
  12.modify for a2dp sink and btdm err irq;
  13.modify for check rfcom of l2cap_info due to unknown cid;
  14.add le enc tx delay for enc err, modify for err irq,and pta,add lpm==2 mode;
  15.add page duration when a bt link has exist;
  16.fix the esco would be established failed when desco equeals;
  17.modify for ICR_LOWPOWER_WIFI_INIT_DONE_POS from 8 to 9,fix conflict of wifi fw;
  18.add condition for wlan rf init;
  19.add macro for pmic_pmu_init_u02_h and pmic_pmu_init_u02;
  20.fix issue that rf lose when extwakeup occured while going to sleep;
  21.modify for adv recovery with rpa, and le con err sync for first anchor point;
  22.enable bb_rx_test_result_report patch;
  23.allow role switch for pair issue,and fix assert about direct adv;
  24.modify for role switch no rsp while iphone make mss twice in one enc pause;
  25.modify for l2cap btbh err, case of sdp pkt too long;
  26.add patch for uart resume while slp en to clean patch data type,and add lld scan high prio, both off as dft;
  27.add l2cap compute, and modify for pta with file trans;

## WiFi Firmware

### D80N/D40N

-  解决优化配置 loft mem后出现的5G RX接收不满的问题
- 修复部分非信令测试问题
- 非信令固件增加 BT LNA MODE efuse bit配置
- 优化杂散问题

### D80/D40X2

- 增加电容校准配置，固件默认开启，驱动可关闭
- 缩减dpd/pwr功率校准时间，降低校准电流
- 增加 8822S 支持
- rftest增加 SET_CHAN_CALIB / RDWR_GPIO 命令
- 优化非信令srrc指令

### D80D40 T/H 
- SDIO fix txpwr 18 with evm

### DCDWDL T/H

## Tools
- **wifi_test** add GET_BONDID cmd
- new static code analysis tool cppcheck

## AIC_Docs
- AIC8800D80N_RF_wifi_test_v20.pdf