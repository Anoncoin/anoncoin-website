---
title: Pull request conflicts
permalink: /Pull_request_conflicts/
---

``
`yo@yo-VirtualBox ~/anoncoin $ git fetch origin`
`yo@yo-VirtualBox ~/anoncoin $ git checkout -b gr_develop origin/gr_develop`
`Branch gr_develop set up to track remote branch gr_develop from origin.`
`Switched to a new branch 'gr_develop'`
`yo@yo-VirtualBox ~/anoncoin $ git merge master`
`warning: Cannot merge binary files: src/qt/res/images/splash_testnet.png (HEAD vs. master)`
`warning: Cannot merge binary files: src/qt/res/images/splash.png (HEAD vs. master)`
`warning: Cannot merge binary files: src/qt/res/icons/toolbar_testnet.png (HEAD vs. master)`
`warning: Cannot merge binary files: src/qt/res/icons/toolbar.png (HEAD vs. master)`
`warning: Cannot merge binary files: src/qt/res/icons/anoncoin.icns (HEAD vs. master)`
`warning: Cannot merge binary files: share/pixmaps/nsis-wizard.bmp (HEAD vs. master)`
`warning: Cannot merge binary files: share/pixmaps/nsis-header.bmp (HEAD vs. master)`
`warning: Cannot merge binary files: share/pixmaps/favicon.ico (HEAD vs. master)`
`warning: Cannot merge binary files: contrib/macdeploy/background.png (HEAD vs. master)`
`Auto-merging src/walletdb.h`
`CONFLICT (content): Merge conflict in src/walletdb.h`
`Auto-merging src/walletdb.cpp`
`CONFLICT (content): Merge conflict in src/walletdb.cpp`
`Auto-merging src/wallet.h`
`CONFLICT (content): Merge conflict in src/wallet.h`
`Auto-merging src/wallet.cpp`
`CONFLICT (content): Merge conflict in src/wallet.cpp`
`Auto-merging src/version.h`
`CONFLICT (content): Merge conflict in src/version.h`
`CONFLICT (modify/delete): src/version.cpp deleted in HEAD and modified in master. Version master of src/version.cpp left in tree.`
`Auto-merging src/util.h`
`CONFLICT (content): Merge conflict in src/util.h`
`Auto-merging src/util.cpp`
`CONFLICT (content): Merge conflict in src/util.cpp`
`Auto-merging src/ui_interface.h`
`CONFLICT (content): Merge conflict in src/ui_interface.h`
`Auto-merging src/txdb.cpp`
`CONFLICT (content): Merge conflict in src/txdb.cpp`
`Auto-merging src/test/util_tests.cpp`
`Auto-merging src/test/transaction_tests.cpp`
`CONFLICT (content): Merge conflict in src/test/transaction_tests.cpp`
`CONFLICT (modify/delete): src/test/test_bitcoin.cpp deleted in HEAD and modified in master. Version master of src/test/test_bitcoin.cpp left in tree.`
`Auto-merging src/test/scrypt_tests.cpp`
`CONFLICT (add/add): Merge conflict in src/test/scrypt_tests.cpp`
`Auto-merging src/test/rpc_tests.cpp`
`CONFLICT (content): Merge conflict in src/test/rpc_tests.cpp`
`Auto-merging src/test/netbase_tests.cpp`
`CONFLICT (content): Merge conflict in src/test/netbase_tests.cpp`
`Auto-merging src/test/miner_tests.cpp`
`CONFLICT (content): Merge conflict in src/test/miner_tests.cpp`
`Auto-merging src/test/key_tests.cpp`
`CONFLICT (content): Merge conflict in src/test/key_tests.cpp`
`Auto-merging src/test/data/base58_keys_valid.json`
`CONFLICT (content): Merge conflict in src/test/data/base58_keys_valid.json`
`CONFLICT (modify/delete): src/test/data/alertTests deleted in HEAD and modified in master. Version master of src/test/data/alertTests left in tree.`
`Auto-merging src/test/bloom_tests.cpp`
`CONFLICT (content): Merge conflict in src/test/bloom_tests.cpp`
`Auto-merging src/test/base58_tests.cpp`
`CONFLICT (content): Merge conflict in src/test/base58_tests.cpp`
`CONFLICT (modify/delete): src/test/alert_tests.cpp deleted in HEAD and modified in master. Version master of src/test/alert_tests.cpp left in tree.`
`Auto-merging src/test/DoS_tests.cpp`
`CONFLICT (content): Merge conflict in src/test/DoS_tests.cpp`
`Auto-merging src/test/Checkpoints_tests.cpp`
`CONFLICT (content): Merge conflict in src/test/Checkpoints_tests.cpp`
`Auto-merging src/serialize.h`
`CONFLICT (content): Merge conflict in src/serialize.h`
`Auto-merging src/scrypt.h`
`CONFLICT (add/add): Merge conflict in src/scrypt.h`
`Auto-merging src/scrypt.cpp`
`CONFLICT (add/add): Merge conflict in src/scrypt.cpp`
`Auto-merging src/script.h`
`CONFLICT (content): Merge conflict in src/script.h`
`Auto-merging src/script.cpp`
`CONFLICT (content): Merge conflict in src/script.cpp`
`Auto-merging src/rpcwallet.cpp`
`CONFLICT (content): Merge conflict in src/rpcwallet.cpp`
`CONFLICT (rename/rename): Rename "src/bitcoinrpc.h"->"src/rpcserver.h" in branch "HEAD" rename "src/bitcoinrpc.h"->"src/anoncoinrpc.h" in "master"`
`Auto-merging src/rpcrawtransaction.cpp`
`CONFLICT (content): Merge conflict in src/rpcrawtransaction.cpp`
`Auto-merging src/rpcnet.cpp`
`CONFLICT (content): Merge conflict in src/rpcnet.cpp`
`Auto-merging src/rpcmining.cpp`
`CONFLICT (content): Merge conflict in src/rpcmining.cpp`
`Auto-merging src/rpcdump.cpp`
`CONFLICT (content): Merge conflict in src/rpcdump.cpp`
`Auto-merging src/rpcblockchain.cpp`
`CONFLICT (content): Merge conflict in src/rpcblockchain.cpp`
`Auto-merging src/qt/walletview.cpp`
`CONFLICT (content): Merge conflict in src/qt/walletview.cpp`
`CONFLICT (modify/delete): src/qt/walletstack.h deleted in HEAD and modified in master. Version master of src/qt/walletstack.h left in tree.`
`Auto-merging src/qt/walletmodel.h`
`CONFLICT (content): Merge conflict in src/qt/walletmodel.h`
`Auto-merging src/qt/walletmodel.cpp`
`CONFLICT (content): Merge conflict in src/qt/walletmodel.cpp`
`Auto-merging src/qt/walletframe.h`
`CONFLICT (content): Merge conflict in src/qt/walletframe.h`
`Auto-merging src/qt/walletframe.cpp`
`CONFLICT (content): Merge conflict in src/qt/walletframe.cpp`
`Auto-merging src/qt/transactionview.cpp`
`CONFLICT (content): Merge conflict in src/qt/transactionview.cpp`
`Auto-merging src/qt/test/uritests.cpp`
`CONFLICT (content): Merge conflict in src/qt/test/uritests.cpp`
`Auto-merging src/qt/splashscreen.cpp`
`CONFLICT (content): Merge conflict in src/qt/splashscreen.cpp`
`Auto-merging src/qt/signverifymessagedialog.cpp`
`CONFLICT (content): Merge conflict in src/qt/signverifymessagedialog.cpp`
`Auto-merging src/qt/sendcoinsentry.cpp`
`CONFLICT (content): Merge conflict in src/qt/sendcoinsentry.cpp`
`Auto-merging src/qt/sendcoinsdialog.h`
`CONFLICT (content): Merge conflict in src/qt/sendcoinsdialog.h`
`Auto-merging src/qt/sendcoinsdialog.cpp`
`CONFLICT (content): Merge conflict in src/qt/sendcoinsdialog.cpp`
`Auto-merging src/qt/rpcconsole.cpp`
`CONFLICT (content): Merge conflict in src/qt/rpcconsole.cpp`
`Auto-merging src/qt/res/images/splash_testnet.png`
`CONFLICT (content): Merge conflict in src/qt/res/images/splash_testnet.png`
`Auto-merging src/qt/res/images/splash.png`
`CONFLICT (content): Merge conflict in src/qt/res/images/splash.png`
`Auto-merging src/qt/res/icons/toolbar_testnet.png`
`CONFLICT (content): Merge conflict in src/qt/res/icons/toolbar_testnet.png`
`Auto-merging src/qt/res/icons/toolbar.png`
`CONFLICT (content): Merge conflict in src/qt/res/icons/toolbar.png`
`CONFLICT (modify/delete): src/qt/res/icons/bitcoin_testnet.png deleted in HEAD and modified in master. Version master of src/qt/res/icons/bitcoin_testnet.png left in tree.`
`CONFLICT (modify/delete): src/qt/res/icons/bitcoin_testnet.ico deleted in HEAD and modified in master. Version master of src/qt/res/icons/bitcoin_testnet.ico left in tree.`
`CONFLICT (modify/delete): src/qt/res/icons/bitcoin.png deleted in HEAD and modified in master. Version master of src/qt/res/icons/bitcoin.png left in tree.`
`CONFLICT (modify/delete): src/qt/res/icons/bitcoin.ico deleted in HEAD and modified in master. Version master of src/qt/res/icons/bitcoin.ico left in tree.`
`Auto-merging src/qt/res/icons/anoncoin.icns`
`CONFLICT (add/add): Merge conflict in src/qt/res/icons/anoncoin.icns`
`Auto-merging src/qt/res/anoncoin-qt-res.rc`
`CONFLICT (content): Merge conflict in src/qt/res/anoncoin-qt-res.rc`
`CONFLICT (modify/delete): src/qt/qrcodedialog.cpp deleted in HEAD and modified in master. Version master of src/qt/qrcodedialog.cpp left in tree.`
`Auto-merging src/qt/paymentserver.cpp`
`CONFLICT (content): Merge conflict in src/qt/paymentserver.cpp`
`Auto-merging src/qt/optionsmodel.h`
`CONFLICT (content): Merge conflict in src/qt/optionsmodel.h`
`Auto-merging src/qt/optionsmodel.cpp`
`CONFLICT (content): Merge conflict in src/qt/optionsmodel.cpp`
`Auto-merging src/qt/optionsdialog.h`
`CONFLICT (content): Merge conflict in src/qt/optionsdialog.h`
`Auto-merging src/qt/optionsdialog.cpp`
`CONFLICT (content): Merge conflict in src/qt/optionsdialog.cpp`
`Auto-merging src/qt/macnotificationhandler.mm`
`CONFLICT (add/add): Merge conflict in src/qt/macnotificationhandler.mm`
`Auto-merging src/qt/macnotificationhandler.h`
`CONFLICT (add/add): Merge conflict in src/qt/macnotificationhandler.h`
`Auto-merging src/qt/macdockiconhandler.mm`
`CONFLICT (content): Merge conflict in src/qt/macdockiconhandler.mm`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_zh_TW.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_zh_TW.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_zh_CN.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_zh_CN.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_uk.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_uk.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_tr.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_tr.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_th_TH.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_th_TH.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_sv.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_sv.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_sr.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_sr.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_sk.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_sk.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_ro_RO.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_ro_RO.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_pt_PT.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_pt_PT.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_pt_BR.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_pt_BR.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_nl.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_nl.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_nb.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_nb.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_lv_LV.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_lv_LV.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_lt.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_lt.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_la.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_la.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_ja.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_ja.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_it.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_it.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_hu.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_hu.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_hr.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_hr.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_he.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_he.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_fr_CA.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_fr_CA.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_fr.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_fr.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_fi.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_fi.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_fa_IR.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_fa_IR.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_fa.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_fa.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_eu_ES.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_eu_ES.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_et.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_et.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_es_CL.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_es_CL.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_es.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_es.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_eo.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_eo.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_en.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_en.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_de.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_de.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_da.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_da.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_cy.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_cy.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_ca_ES.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_ca_ES.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_ca.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_ca.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_bs.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_bs.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_bg.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_bg.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_ar.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_ar.ts left in tree.`
`CONFLICT (modify/delete): src/qt/locale/bitcoin_af_ZA.ts deleted in HEAD and modified in master. Version master of src/qt/locale/bitcoin_af_ZA.ts left in tree.`
`Auto-merging src/qt/locale/anoncoin_zh_HK.ts`
`CONFLICT (content): Merge conflict in src/qt/locale/anoncoin_zh_HK.ts`
`Auto-merging src/qt/locale/anoncoin_ru.ts`
`CONFLICT (content): Merge conflict in src/qt/locale/anoncoin_ru.ts`
`Auto-merging src/qt/locale/anoncoin_pl.ts`
`CONFLICT (content): Merge conflict in src/qt/locale/anoncoin_pl.ts`
`Auto-merging src/qt/locale/anoncoin_hi_IN.ts`
`CONFLICT (content): Merge conflict in src/qt/locale/anoncoin_hi_IN.ts`
`Auto-merging src/qt/locale/anoncoin_el_GR.ts`
`CONFLICT (content): Merge conflict in src/qt/locale/anoncoin_el_GR.ts`
`Auto-merging src/qt/locale/anoncoin_cs.ts`
`CONFLICT (content): Merge conflict in src/qt/locale/anoncoin_cs.ts`
`Auto-merging src/qt/i2poptionswidget.h`
`CONFLICT (add/add): Merge conflict in src/qt/i2poptionswidget.h`
`Auto-merging src/qt/i2poptionswidget.cpp`
`CONFLICT (add/add): Merge conflict in src/qt/i2poptionswidget.cpp`
`Auto-merging src/qt/guiutil.h`
`CONFLICT (content): Merge conflict in src/qt/guiutil.h`
`Auto-merging src/qt/guiutil.cpp`
`CONFLICT (content): Merge conflict in src/qt/guiutil.cpp`
`Auto-merging src/qt/forms/signverifymessagedialog.ui`
`CONFLICT (content): Merge conflict in src/qt/forms/signverifymessagedialog.ui`
`Auto-merging src/qt/forms/sendcoinsdialog.ui`
`CONFLICT (content): Merge conflict in src/qt/forms/sendcoinsdialog.ui`
`Auto-merging src/qt/forms/rpcconsole.ui`
`CONFLICT (content): Merge conflict in src/qt/forms/rpcconsole.ui`
`Auto-merging src/qt/forms/overviewpage.ui`
`CONFLICT (content): Merge conflict in src/qt/forms/overviewpage.ui`
`Auto-merging src/qt/forms/optionsdialog.ui`
`CONFLICT (content): Merge conflict in src/qt/forms/optionsdialog.ui`
`Auto-merging src/qt/forms/coincontroldialog.ui`
`CONFLICT (add/add): Merge conflict in src/qt/forms/coincontroldialog.ui`
`Auto-merging src/qt/forms/addressbookpage.ui`
`CONFLICT (content): Merge conflict in src/qt/forms/addressbookpage.ui`
`Auto-merging src/qt/forms/aboutdialog.ui`
`CONFLICT (content): Merge conflict in src/qt/forms/aboutdialog.ui`
`Auto-merging src/qt/coincontroltreewidget.h`
`CONFLICT (add/add): Merge conflict in src/qt/coincontroltreewidget.h`
`Auto-merging src/qt/coincontroltreewidget.cpp`
`CONFLICT (add/add): Merge conflict in src/qt/coincontroltreewidget.cpp`
`Auto-merging src/qt/coincontroldialog.h`
`CONFLICT (add/add): Merge conflict in src/qt/coincontroldialog.h`
`Auto-merging src/qt/coincontroldialog.cpp`
`CONFLICT (add/add): Merge conflict in src/qt/coincontroldialog.cpp`
`Auto-merging src/qt/clientmodel.h`
`CONFLICT (content): Merge conflict in src/qt/clientmodel.h`
`Auto-merging src/qt/clientmodel.cpp`
`CONFLICT (content): Merge conflict in src/qt/clientmodel.cpp`
`CONFLICT (modify/delete): src/qt/bitcoinunits.cpp deleted in HEAD and modified in master. Version master of src/qt/bitcoinunits.cpp left in tree.`
`CONFLICT (modify/delete): src/qt/bitcoinstrings.cpp deleted in HEAD and modified in master. Version master of src/qt/bitcoinstrings.cpp left in tree.`
`CONFLICT (modify/delete): src/qt/bitcoingui.cpp deleted in HEAD and modified in master. Version master of src/qt/bitcoingui.cpp left in tree.`
`CONFLICT (modify/delete): src/qt/bitcoin.qrc deleted in HEAD and modified in master. Version master of src/qt/bitcoin.qrc left in tree.`
`Auto-merging src/qt/anoncoingui.h`
`CONFLICT (content): Merge conflict in src/qt/anoncoingui.h`
`CONFLICT (rename/delete): src/qt/anoncoin.cpp deleted in HEAD and renamed in master. Version master of src/qt/anoncoin.cpp left in tree.`
`Auto-merging src/qt/addressbookpage.cpp`
`CONFLICT (content): Merge conflict in src/qt/addressbookpage.cpp`
`CONFLICT (modify/delete): src/qt/aboutdialog.cpp deleted in HEAD and modified in master. Version master of src/qt/aboutdialog.cpp left in tree.`
`Auto-merging src/protocol.h`
`CONFLICT (content): Merge conflict in src/protocol.h`
`Auto-merging src/noui.cpp`
`CONFLICT (content): Merge conflict in src/noui.cpp`
`Auto-merging src/netbase.h`
`CONFLICT (content): Merge conflict in src/netbase.h`
`Auto-merging src/netbase.cpp`
`CONFLICT (content): Merge conflict in src/netbase.cpp`
`Auto-merging src/net.h`
`CONFLICT (content): Merge conflict in src/net.h`
`Auto-merging src/net.cpp`
`CONFLICT (content): Merge conflict in src/net.cpp`
`Auto-merging src/miner.h`
`CONFLICT (add/add): Merge conflict in src/miner.h`
`Auto-merging src/miner.cpp`
`CONFLICT (add/add): Merge conflict in src/miner.cpp`
`CONFLICT (modify/delete): src/makefile.unix deleted in HEAD and modified in master. Version master of src/makefile.unix left in tree.`
`CONFLICT (modify/delete): src/makefile.osx deleted in HEAD and modified in master. Version master of src/makefile.osx left in tree.`
`CONFLICT (modify/delete): src/makefile.mingw deleted in HEAD and modified in master. Version master of src/makefile.mingw left in tree.`
`CONFLICT (modify/delete): src/makefile.linux-mingw deleted in HEAD and modified in master. Version master of src/makefile.linux-mingw left in tree.`
`Auto-merging src/main.h`
`CONFLICT (content): Merge conflict in src/main.h`
`Auto-merging src/main.cpp`
`CONFLICT (content): Merge conflict in src/main.cpp`
`Auto-merging src/leveldb/util/hash.cc`
`CONFLICT (content): Merge conflict in src/leveldb/util/hash.cc`
`Auto-merging src/leveldb/util/env_posix.cc`
`CONFLICT (content): Merge conflict in src/leveldb/util/env_posix.cc`
`Auto-merging src/leveldb/include/leveldb/db.h`
`CONFLICT (content): Merge conflict in src/leveldb/include/leveldb/db.h`
`Auto-merging src/leveldb/db/filename.cc`
`Auto-merging src/leveldb/build_detect_platform`
`CONFLICT (content): Merge conflict in src/leveldb/build_detect_platform`
`Auto-merging src/leveldb/Makefile`
`CONFLICT (content): Merge conflict in src/leveldb/Makefile`
`Auto-merging src/keystore.h`
`CONFLICT (content): Merge conflict in src/keystore.h`
`Auto-merging src/keystore.cpp`
`CONFLICT (content): Merge conflict in src/keystore.cpp`
`Auto-merging src/key.h`
`CONFLICT (content): Merge conflict in src/key.h`
`Auto-merging src/key.cpp`
`CONFLICT (content): Merge conflict in src/key.cpp`
`Auto-merging src/init.h`
`CONFLICT (content): Merge conflict in src/init.h`
`Auto-merging src/init.cpp`
`CONFLICT (content): Merge conflict in src/init.cpp`
`Auto-merging src/hash.h`
`CONFLICT (content): Merge conflict in src/hash.h`
`Auto-merging src/db.cpp`
`CONFLICT (content): Merge conflict in src/db.cpp`
`Auto-merging src/crypter.h`
`CONFLICT (content): Merge conflict in src/crypter.h`
`Auto-merging src/coincontrol.h`
`CONFLICT (add/add): Merge conflict in src/coincontrol.h`
`Auto-merging src/clientversion.h`
`CONFLICT (content): Merge conflict in src/clientversion.h`
`Auto-merging src/checkpoints.cpp`
`CONFLICT (content): Merge conflict in src/checkpoints.cpp`
`Auto-merging src/bloom.h`
`CONFLICT (content): Merge conflict in src/bloom.h`
`Auto-merging src/bloom.cpp`
`CONFLICT (content): Merge conflict in src/bloom.cpp`
`Auto-merging src/base58.h`
`CONFLICT (content): Merge conflict in src/base58.h`
`CONFLICT (rename/delete): src/anoncoinrpc.cpp deleted in HEAD and renamed in master. Version master of src/anoncoinrpc.cpp left in tree.`
`Auto-merging src/allocators.h`
`CONFLICT (content): Merge conflict in src/allocators.h`
`Auto-merging src/alert.cpp`
`CONFLICT (content): Merge conflict in src/alert.cpp`
`Auto-merging src/addrman.h`
`CONFLICT (content): Merge conflict in src/addrman.h`
`Auto-merging share/setup.nsi.in`
`CONFLICT (content): Merge conflict in share/setup.nsi.in`
`CONFLICT (modify/delete): share/qt/clean_mac_info_plist.py deleted in HEAD and modified in master. Version master of share/qt/clean_mac_info_plist.py left in tree.`
`CONFLICT (modify/delete): share/qt/Info.plist deleted in HEAD and modified in master. Version master of share/qt/Info.plist left in tree.`
`Auto-merging share/pixmaps/nsis-wizard.bmp`
`CONFLICT (content): Merge conflict in share/pixmaps/nsis-wizard.bmp`
`Auto-merging share/pixmaps/nsis-header.bmp`
`CONFLICT (content): Merge conflict in share/pixmaps/nsis-header.bmp`
`Auto-merging share/pixmaps/favicon.ico`
`CONFLICT (content): Merge conflict in share/pixmaps/favicon.ico`
`CONFLICT (modify/delete): share/pixmaps/bitcoin64.xpm deleted in HEAD and modified in master. Version master of share/pixmaps/bitcoin64.xpm left in tree.`
`CONFLICT (modify/delete): share/pixmaps/bitcoin64.png deleted in HEAD and modified in master. Version master of share/pixmaps/bitcoin64.png left in tree.`
`CONFLICT (modify/delete): share/pixmaps/bitcoin32.xpm deleted in HEAD and modified in master. Version master of share/pixmaps/bitcoin32.xpm left in tree.`
`CONFLICT (modify/delete): share/pixmaps/bitcoin32.png deleted in HEAD and modified in master. Version master of share/pixmaps/bitcoin32.png left in tree.`
`CONFLICT (modify/delete): share/pixmaps/bitcoin256.xpm deleted in HEAD and modified in master. Version master of share/pixmaps/bitcoin256.xpm left in tree.`
`CONFLICT (modify/delete): share/pixmaps/bitcoin256.png deleted in HEAD and modified in master. Version master of share/pixmaps/bitcoin256.png left in tree.`
`CONFLICT (modify/delete): share/pixmaps/bitcoin16.xpm deleted in HEAD and modified in master. Version master of share/pixmaps/bitcoin16.xpm left in tree.`
`CONFLICT (modify/delete): share/pixmaps/bitcoin16.png deleted in HEAD and modified in master. Version master of share/pixmaps/bitcoin16.png left in tree.`
`CONFLICT (modify/delete): share/pixmaps/bitcoin128.xpm deleted in HEAD and modified in master. Version master of share/pixmaps/bitcoin128.xpm left in tree.`
`CONFLICT (modify/delete): share/pixmaps/bitcoin128.png deleted in HEAD and modified in master. Version master of share/pixmaps/bitcoin128.png left in tree.`
`CONFLICT (modify/delete): share/pixmaps/bitcoin.ico deleted in HEAD and modified in master. Version master of share/pixmaps/bitcoin.ico left in tree.`
`CONFLICT (modify/delete): share/pixmaps/bitcoin-bc.ico deleted in HEAD and modified in master. Version master of share/pixmaps/bitcoin-bc.ico left in tree.`
`Auto-merging doc/unit-tests.md`
`CONFLICT (content): Merge conflict in doc/unit-tests.md`
`Auto-merging doc/release-process.md`
`CONFLICT (content): Merge conflict in doc/release-process.md`
`Auto-merging doc/release-notes.md`
`CONFLICT (content): Merge conflict in doc/release-notes.md`
`CONFLICT (modify/delete): doc/readme-qt.rst deleted in HEAD and modified in master. Version master of doc/readme-qt.rst left in tree.`
`Auto-merging doc/build-unix.md`
`CONFLICT (content): Merge conflict in doc/build-unix.md`
`Auto-merging doc/build-osx.md`
`CONFLICT (content): Merge conflict in doc/build-osx.md`
`Auto-merging doc/build-msw.md`
`CONFLICT (content): Merge conflict in doc/build-msw.md`
`CONFLICT (modify/delete): doc/Tor.txt deleted in HEAD and modified in master. Version master of doc/Tor.txt left in tree.`
`Auto-merging doc/README_windows.txt`
`CONFLICT (content): Merge conflict in doc/README_windows.txt`
`Auto-merging doc/README.md`
`CONFLICT (content): Merge conflict in doc/README.md`
`CONFLICT (modify/delete): contrib/wallettools/walletunlock.py deleted in HEAD and modified in master. Version master of contrib/wallettools/walletunlock.py left in tree.`
`CONFLICT (modify/delete): contrib/wallettools/walletchangepass.py deleted in HEAD and modified in master. Version master of contrib/wallettools/walletchangepass.py left in tree.`
`CONFLICT (modify/delete): contrib/verifysfbinaries/verify.sh deleted in master and modified in HEAD. Version HEAD of contrib/verifysfbinaries/verify.sh left in tree.`
`Auto-merging contrib/testgen/gen_base58_test_vectors.py`
`CONFLICT (content): Merge conflict in contrib/testgen/gen_base58_test_vectors.py`
`Auto-merging contrib/seeds/makeseeds.py`
`CONFLICT (content): Merge conflict in contrib/seeds/makeseeds.py`
`Auto-merging contrib/macdeploy/macdeployqtplus`
`CONFLICT (content): Merge conflict in contrib/macdeploy/macdeployqtplus`
`Auto-merging contrib/macdeploy/fancy.plist`
`CONFLICT (content): Merge conflict in contrib/macdeploy/fancy.plist`
`Auto-merging contrib/macdeploy/background.png`
`CONFLICT (content): Merge conflict in contrib/macdeploy/background.png`
`CONFLICT (modify/delete): contrib/homebrew/makefile.osx.patch deleted in HEAD and modified in master. Version master of contrib/homebrew/makefile.osx.patch left in tree.`
`Auto-merging contrib/gitian-downloader/win32-download-config`
`CONFLICT (content): Merge conflict in contrib/gitian-downloader/win32-download-config`
`Auto-merging contrib/gitian-downloader/linux-download-config`
`CONFLICT (content): Merge conflict in contrib/gitian-downloader/linux-download-config`
`CONFLICT (modify/delete): contrib/gitian-descriptors/qt-win32.yml deleted in HEAD and modified in master. Version master of contrib/gitian-descriptors/qt-win32.yml left in tree.`
`CONFLICT (modify/delete): contrib/gitian-descriptors/gitian.yml deleted in HEAD and modified in master. Version master of contrib/gitian-descriptors/gitian.yml left in tree.`
`CONFLICT (modify/delete): contrib/gitian-descriptors/gitian-win32.yml deleted in HEAD and modified in master. Version master of contrib/gitian-descriptors/gitian-win32.yml left in tree.`
`CONFLICT (modify/delete): contrib/gitian-descriptors/deps-win32.yml deleted in HEAD and modified in master. Version master of contrib/gitian-descriptors/deps-win32.yml left in tree.`
`CONFLICT (modify/delete): contrib/gitian-descriptors/boost-win32.yml deleted in HEAD and modified in master. Version master of contrib/gitian-descriptors/boost-win32.yml left in tree.`
`Auto-merging contrib/debian/manpages/bitcoin.conf.5`
`Auto-merging contrib/debian/manpages/bitcoin-qt.1`
`Auto-merging contrib/debian/examples/bitcoin.conf`
`CONFLICT (content): Merge conflict in contrib/debian/examples/bitcoin.conf`
`Auto-merging contrib/debian/bitcoin-qt.desktop`
`CONFLICT (content): Merge conflict in contrib/debian/bitcoin-qt.desktop`
`Auto-merging contrib/bitrpc/bitrpc.py`
`CONFLICT (content): Merge conflict in contrib/bitrpc/bitrpc.py`
`CONFLICT (rename/delete): anoncoin-qt.pro deleted in HEAD and renamed in master. Version master of anoncoin-qt.pro left in tree.`
`Auto-merging README.md`
`CONFLICT (content): Merge conflict in README.md`
`Auto-merging INSTALL`
`CONFLICT (content): Merge conflict in INSTALL`
`Auto-merging COPYING`
`CONFLICT (content): Merge conflict in COPYING`
`Auto-merging .gitignore`
`CONFLICT (content): Merge conflict in .gitignore`
`Automatic merge failed; fix conflicts and then commit the result.`
`yo@yo-VirtualBox ~/anoncoin $`