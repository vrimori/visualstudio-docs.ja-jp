---
title: "全般 タブのプロパティ ダイアログ ボックスの処理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 54e4eb317b4bd40ce21c4cfcd9a3c1db3948e36f
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/04/2018
---
# <a name="general-tab-process-properties-dialog-box"></a>[全般] タブ ([プロセス プロパティ] ダイアログ ボックス)
使用して、**全般**特定のプロセスに関する詳細を確認するには、タブ。 表示する、[プロセス プロパティ ダイアログ ボックス](../debugger/process-properties-dialog-box.md)にフォーカスを移動する、[プロセス ビュー](../debugger/processes-view.md)ウィンドウです。 ツリーで、プロセスの任意のノードを選択し、**プロパティ**から、**ビュー**メニュー。  
  
 次の設定が [利用可能な**全般**] タブ。  
  
|入力|説明|  
|-----------|-----------------|  
|**モジュール名**|モジュールの名前。|  
|**プロセス ID**|このプロセスの一意の ID。 プロセス ID 番号は再利用され、そのプロセスの有効期間にのみそのプロセスを識別します。 プログラムを実行すると、プロセス オブジェクトの種類が作成されます。 プロセス内のすべてのスレッドは、同じアドレス領域を共有して、同じデータにアクセスします。|  
|**優先度ベース**|このプロセスの現在の基本優先順位。 プロセス内のスレッドを発生させるし、プロセスの基本優先度基準とした独自の基本優先順位を下げます。|  
|**スレッド**|このプロセスで現在アクティブなスレッドの数。|  
|**CPU 時間**|総 CPU 時間は、このプロセスは、そのスレッドで費やされました。 ユーザーの時間と特権モード時間等しい。|  
|**ユーザー時間**|このプロセスのスレッドが非アイドルのスレッドでユーザー モードでコードの実行に費やさ累積的な経過時間。 アプリケーションは、ウィンドウ マネージャーや、グラフィックス エンジンなどのサブシステムと同様に、ユーザー モードで実行されます。|  
|**特権モード時間**|経過時間の合計このプロセスが実行されて特権モードで非アイドルのスレッドにします。 サービス層、Executive ルーチンおよびカーネル特権モードで実行します。 グラフィックス アダプターおよびプリンター以外のほとんどのデバイスのデバイス ドライバーは、特権モードでも実行します。 他のサブシステム プロセスの特権モード時間に加え、アプリケーションの Windows ではいくつかの作業があります。|  
|**経過時間**|このプロセスが実行されている合計経過時間。|