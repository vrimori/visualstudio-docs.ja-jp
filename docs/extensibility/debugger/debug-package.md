---
title: "パッケージをデバッグします。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[デバッグの SDK] をデバッグするには、パッケージ化します。"
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# パッケージをデバッグします。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

UI の Visual Studio Shell およびハンドルすべてのデバッグ パッケージを実行します。  またデバッグ セッション マネージャー \(SDM\) と Visual Studio のデバッグし通信インターフェイスを実装します。  
  
 実行モードで中断モードに SDM スイッチを使用して送られたイベント デバッガーが中断されますが中断が発生したプログラムにフォーカスを変更します。  デバッグのパッケージはイベントによって送信された情報のスタック フレームおよびスレッドを追跡します。  
  
 デバッグのパッケージには言語ランタイム環境の依存関係はありません。  デバッグのパッケージを実行または変更する必要はありません。  
  
 デバッグのパッケージは vsdebug.dll によって実装されます。  
  
## 参照  
 [セッションのデバッグ マネージャー](../../extensibility/debugger/session-debug-manager.md)   
 [スタック フレーム](../../extensibility/debugger/stack-frames.md)   
 [スレッド](../../extensibility/debugger/threads.md)   
 [デバッガーのコンポーネント](../../extensibility/debugger/debugger-components.md)