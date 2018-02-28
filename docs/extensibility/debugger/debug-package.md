---
title: "パッケージのデバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a2cbb124dcb2d2d7a0bbcba1bc57eb3c704dd770
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="debug-package"></a>パッケージをデバッグします。
デバッグ パッケージは、Visual Studio シェルで動作し、すべての UI を処理します。 Visual Studio のデバッグのインターフェイスを処理し、セッションのデバッグ マネージャー (SDM) と通信します。  
  
 中断イベント、SDM 経由で送信は、実行モードから中断モードと、中断が発生したプログラムにフォーカスを変更するデバッガーを切り替えます。 デバッグ パッケージは、イベントによって送信される情報をスタック フレームとスレッドを追跡します。  
  
 デバッグ パッケージには、言語、または実行時環境の依存関係がありません。 実装するか、デバッグのパッケージを変更する必要はありません。  
  
 デバッグ パッケージが vsdebug.dll によって実装されます。  
  
## <a name="see-also"></a>参照  
 [セッションのデバッグ マネージャー](../../extensibility/debugger/session-debug-manager.md)   
 [スタック フレーム](../../extensibility/debugger/stack-frames.md)   
 [スレッド](../../extensibility/debugger/threads.md)   
 [デバッガーのコンポーネント](../../extensibility/debugger/debugger-components.md)