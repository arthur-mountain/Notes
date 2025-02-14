# Wi-Fi 網路中的運作原理

Before we start, please make sure you have read the

1. [DHCP 伺服器](./dhcp.md) 和 [NAT](./nat.md)

2. [DHCP 和 NAT 的協作](./dhcp-and-nat.md)

## Summary

**Wi-Fi 連接的原理確實和有線網路的連接相似**，

在進行網路通信時也遵循相同的 IP、端口、NAT、DHCP 等網路協定原則。

Wi-Fi 實際上只是物理層(OSI 第一層)和數據鏈路層(OSI 第二層)的一種無線連接方式，

它和有線網路的主要區別在於 **連接的媒介不同**(無線 vs. 有線)，但在網路層(OSI 第三層)以上的運作方式基本一致。

## 1. 具體來說，Wi-Fi 網路中的運作原理如下

首先，路由器會是 Wi-Fi 路由器

1. **Wi-Fi 的 IP 分配與 DHCP**:

   同 [DHCP 和 NAT 的協作](/network/dhcp-and-nat.md#1-dhcp-server-如何分配私有-ip)

2. **Wi-Fi 中的 NAT**：

   同 [DHCP 和 NAT 的協作](/network/dhcp-and-nat.md#2-nat-如何知道將數據轉發給哪個私有-ip)

3. **Wi-Fi 的安全機制**(附加的特點)：

   - Wi-Fi 除了基本的 IP、NAT、端口等網路協定，還有自己的 **加密協定**(如 WPA2、WPA3)來保護無線傳輸的數據，防止未授權的設備竊聽和連接。

   - 這些加密機制主要運行在 **數據鏈路層**(第二層)，確保無線信號的安全性，但它們不影響之後的網路層以上的運作方式。

## 2. Wi-Fi 與有線網路在不同層的差異

### 第一層(物理層)的差異

- **有線網路**:

  使用物理介質(例如網線)來傳輸數據，通過電信號在銅線中傳輸，或通過光纖傳輸光信號。

- **Wi-Fi**:

  使用無線電波在空中傳輸數據，通常在 2.4GHz 或 5GHz 頻段，設備間無需物理連接。這使得 Wi-Fi 更加靈活，但也容易受干擾影響。

### 第二層(數據鏈路層)的差異

- 在數據鏈路層:

  - **有線網路**: 一般使用 **以太網協定**(Ethernet)

  - **Wi-Fi**: 則使用 **IEEE 802.11 標準**，包括不同的 Wi-Fi 版本(如 802.11n、802.11ac、802.11ax 等)。

- **MAC 層地址處理**:

  無論是 Wi-Fi 還是有線網路，都使用 MAC 位址來標識每個網路設備。

  但是，由於 Wi-Fi 是無線網路，數據鏈路層還增加了加密(如 WPA2、WPA3)和驗證機制，以確保數據在無線傳輸時的安全性。

- **碰撞檢測和避免**:

  有線網路可以使用碰撞檢測(CSMA/CD)技術，而 Wi-Fi 使用碰撞避免(CSMA/CA)技術來處理可能的數據衝突。

### 第三層(網路層)及以上的相同點

在第三層(網路層)及其以上，Wi-Fi 和有線網路的原理是一致的，原因如下：

- **IP 分配和 DHCP**：無論是 Wi-Fi 還是有線網路，設備都可以通過 DHCP 獲取私有 IP 位址。

- **NAT 和端口轉換**：Wi-Fi 路由器上的 NAT 會將私有 IP 位址映射到公有 IP，並分配外部端口，這與有線網路中的 NAT 功能相同。

- **傳輸協定**：無論是 Wi-Fi 還是有線網路，都可以使用 TCP 或 UDP 等傳輸層協定來管理數據的可靠傳輸。

- **應用層協定**：在應用層(如 HTTP、HTTPS、FTP 等)，Wi-Fi 和有線網路也是完全一致的，所有應用程序的數據傳輸方式和連接流程相同。

### 總結

- **DHCP 伺服器的端口分配和 NAT 的處理**:

  在 Wi-Fi 中與有線網路一致，均由 DHCP 伺服器動態分配端口，而 NAT 則進行私有 IP 與公有 IP 之間的轉換。

- **物理層和數據鏈路層的差異**:

  Wi-Fi 和有線網路在第一層和第二層的運作不同。

  Wi-Fi 使用無線頻率傳輸，並有額外的加密和驗證機制，而有線網路使用物理介質傳輸，通常採用以太網協定。

- **網路層及以上的相似性**:

  在第三層及以上，Wi-Fi 與有線網路的運作原理相同，包括 IP 分配、NAT、端口管理和應用層協定等。

因此，Wi-Fi 和有線網路在網路層以上的協定和功能完全一致，真正的差異主要在物理層和數據鏈路層。
