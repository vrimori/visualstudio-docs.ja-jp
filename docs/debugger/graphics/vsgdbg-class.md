---
title: VsgDbg クラス |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f457d35725a0a6041fe82b06853a6dffdf69b53d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53922456"
---
# <a name="vsgdbg-class"></a>VsgDbg クラス
グラフィックス診断のアプリ内コンポーネントのプログラムによる制御のインターフェイスを表します。  
  
## <a name="syntax"></a>構文  
  
```C++  
class VsgDbg;  
```  
  
## <a name="members"></a>メンバー  
 `VsgDbg` クラスは、次のメンバーをサポートします。  
  
### <a name="public-constructors"></a>パブリック コンストラクター  
  
|name|説明|  
|----------|-----------------|  
|[VsgDbg::VsgDbg (コンストラクター)](vsgdbg-vsgdbg-constructor.md)|`VsgDbg` クラスのインスタンスを構築し、オプションで、グラフィックス情報をアクティブにキャプチャして記録するようにグラフィックス診断のアプリ内コンポーネントを準備します。|  
|[VsgDbg::~VsgDbg (デストラクター)](vsgdbg-tilde-vsgdbg-destructor.md)|`VsgDbg` クラスのインスタンスを破棄します。|  
  
### <a name="public-methods"></a>パブリック メソッド  
  
|name|説明|  
|----------|-----------------|  
|[AddMessage](addmessage.md)|グラフィックス診断の HUD (ヘッドアップ ディスプレイ) にカスタム メッセージを追加します。|  
|[BeginCapture](begincapture.md)|`EndCapture` で終了するキャプチャ区間を開始します。|  
|[CaptureCurrentFrame](capturecurrentframe.md)|現在のフレームの残りの部分を、グラフィックス ログ ファイルにキャプチャします。|  
|[コピー (プログラムによるキャプチャ)](copy-programmatic-capture.md)|アクティブなグラフィックス ログ (.vsglog) ファイルの内容を、新しいファイルにコピーします。|  
|[EndCapture](endcapture.md)|`BeginCapture` で開始されたキャプチャ区間を終了します。|  
|[Init](init.md)|グラフィックス情報をアクティブにキャプチャして記録するように、グラフィックス診断のアプリ内コンポーネントを準備します。|  
|[ToggleHUD](togglehud.md)|グラフィックス診断の HUD オーバーレイのオンとオフを切り替えます。|  
|[UnInit](uninit.md)|グラフィックス ログ ファイルを終了して閉じ、アプリケーションがアクティブにグラフィックス情報を記録したときに使用されたリソースを解放します。|  
  
## <a name="remarks"></a>コメント  
 `VsgDbg` クラスは、グラフィックス診断機能をプログラムで制御するために使用できるインターフェイスを表します。 グラフィックス情報をアクティブにキャプチャおよび記録していないときでも、一部の機能を使用できます。これには、`AddMessage` メンバー関数や `ToggleHUD` メンバー関数が含まれます。 他のメンバー関数は、グラフィックス情報のアクティブなキャプチャを開始または停止するようにグラフィックス診断のアプリ内コンポーネントを準備します。または、アプリケーションがグラフィックス情報をアクティブにキャプチャしてグラフィックス ログ ファイルに記録している間に呼び出される必要があります。