# 問題発生  
mbedはオフライン環境で各種コンパイラでコンパイルできるようにエクスポートする機能がある。  
が、HRM1017を使った時に gccでオフラインコンパイルして作成したバイナリを書き込んでも動作しなかった。  
  
# 原因  
gccの場合、生成したバイナリに加えて、nRF51822のファームウェアのバイナリをマージする必要がある  
  
# 解決法  
makefileを見るとmake mergeというコマンドがあるのでこれを使う、  
srec_catコマンドが使える必要があるので、SRecordを入れる。  
macなら```brew install srecord```でインストールできる。  
さらにマージするHexのパスが間違っているのでmakefileの  
```SOFTDEVICE = mbed/TARGET_HRM1017/TARGET_NORDIC/TARGET_MCU_NRF51822/Lib/s110_nrf51822_7_1_0/s110_nrf51822_7.1.0_softdevice.hex```
この部分を
```SOFTDEVICE = mbed/TARGET_HRM1017/TARGET_NORDIC/TARGET_MCU_NRF51822/Lib/s130_nrf51822_1_0_0/s130_nrf51_1.0.0_softdevice.hex```  
と修正する。  
