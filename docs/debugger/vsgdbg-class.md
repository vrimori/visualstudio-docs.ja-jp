---
title: "VsgDbg クラス | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VsgDbg クラス
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

グラフィックス診断のアプリ内コンポーネントのプログラムによる制御のインターフェイスを表します。  
  
## 構文  
  
```cpp  
class VsgDbg;  
```  
  
## メンバー  
 `VsgDbg` クラスは、次のメンバーをサポートします。  
  
### パブリック コンストラクター  
  
|名前|説明|  
|--------|--------|  
|[VsgDbg::VsgDbg \(コンストラクター\)](../Topic/VsgDbg::VsgDbg%20\(Constructor\).md)|`VsgDbg` クラスのインスタンスを構築し、オプションで、グラフィックス情報をアクティブにキャプチャして記録するようにグラフィックス診断のアプリ内コンポーネントを準備します。|  
|[VsgDbg::~VsgDbg \(デストラクター\)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)|`VsgDbg` クラスのインスタンスを破棄します。|  
  
### パブリック メソッド  
  
|名前|説明|  
|--------|--------|  
|[AddMessage](../debugger/addmessage.md)|グラフィックス診断の HUD \(ヘッドアップ ディスプレイ\) にカスタム メッセージを追加します。|  
|[BeginCapture](../debugger/begincapture.md)|`EndCapture` で終了するキャプチャ区間を開始します。|  
|[CaptureCurrentFrame](../debugger/capturecurrentframe.md)|現在のフレームの残りの部分を、グラフィックス ログ ファイルにキャプチャします。|  
|[コピー \(プログラムによるキャプチャ\)](../debugger/copy-programmatic-capture.md)|アクティブなグラフィックス ログ \(.vsglog\) ファイルの内容を、新しいファイルにコピーします。|  
|[EndCapture](../debugger/endcapture.md)|`BeginCapture` で開始されたキャプチャ区間を終了します。|  
|[Init](../debugger/init.md)|グラフィックス情報をアクティブにキャプチャして記録するように、グラフィックス診断のアプリ内コンポーネントを準備します。|  
|[ToggleHUD](../debugger/togglehud.md)|グラフィックス診断の HUD オーバーレイのオンとオフを切り替えます。|  
|[UnInit](../debugger/uninit.md)|グラフィックス ログ ファイルを終了して閉じ、アプリケーションがアクティブにグラフィックス情報を記録したときに使用されたリソースを解放します。|  
  
## 解説  
 `VsgDbg` クラスは、グラフィック診断機能をプログラムで制御するために使用できるインターフェイスを表します。  グラフィックス情報をアクティブにキャプチャおよび記録していないときでも、一部の機能を使用できます。これには、`AddMessage` メンバー関数や `ToggleHUD` メンバー関数が含まれます。  他のメンバー関数は、グラフィックス情報のアクティブなキャプチャを開始または停止するようにグラフィックス診断のアプリ内コンポーネントを準備します。または、アプリケーションがグラフィックス情報をアクティブにキャプチャしてグラフィックス ログ ファイルに記録している間に呼び出される必要があります。