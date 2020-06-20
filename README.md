# ICND IP Route
路由器針對路徑之選擇

為了使資訊能從一網路傳送到另一網路，必須有相關設備，路由器便是將一項資訊從一處送到另一處的過程，例如一個位在 10.120.2.0 子網路中的主機要連到另一部位於 172.16.1.9 網段上的主機時，中間的路由器群便需要學習、選擇、維持（更新）所需要的路徑。


一路由器或是第三層交換器設備需要知道重要訊息包含：

- [x] DES Addr (發送端主機負責)

- [x] Info SRC (資訊來源讓路由學到通往目的地的路徑)

- [x] Possible Route (可能路徑)

- [x] Best Route (最佳路徑)

- [x] Maintenance & Verification (維護和確認)

# 路由表

路由器學習到的路由資訊將存放在路由表中，路由器也是根據路由表決定要使用哪一個連接埠將封包往外傳送到其它目的地。

倘若目的地網段與路由器直接相連，則路由器會知道要使用哪個連接埠傳送此封包，倘若未與網段直接相連，則需要學習、計算最佳路徑：

學習方式：

靜態路由，由網路管理者設定。

動態路由，藉由設定好的程序，動態演算與收集而來。

# 動態路由

可以選擇靜態路由，亦或是動態路由，動態路由包含：

* RIP 路由資訊通訊協定

      Router# sh ip route
      Router# debug ip rip
      

* IGRP 內部閘道路由通訊協定(一個自主系統內)

       Router(config-router)#router-idrp as-no.
       Router(config-router)#network net-no.
       Router(config-router)#traffic-share balanced

* EIGRP 加強式內部閘道路由通訊協定（多個自主系統間，混合 RIP 和 OSPF 演算法）

* OSPF 啟用最短路徑通訊協定（又稱為 Link-state）

* BGP 邊界閘道器通訊協定

# 靜態路由指令

    Router(config)#ip route + <通往目的地子網路的路徑 IP/subnetMask> + <通往目的地途經的 Next Hops IP add>
    
* 預設所有路徑都要通過某閘道

      Router(config)#ip route + 0.0.0.0 0.0.0.0 + <通往目的地途經的 Next Hops IP add>




