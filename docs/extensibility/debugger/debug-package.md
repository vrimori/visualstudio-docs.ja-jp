---
title: "パッケージのデバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eccd258476f82871732ef7b16f0282d2f945b9ee
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="debug-package"></a>パッケージをデバッグします。
デバッグ パッケージは、Visual Studio シェルで動作し、すべての UI を処理します。 Visual Studio のデバッグのインターフェイスを処理し、セッションのデバッグ マネージャー (SDM) と通信します。  
  
 中断イベント、SDM 経由で送信は、実行モードから中断モードと、中断が発生したプログラムにフォーカスを変更するデバッガーを切り替えます。 デバッグ パッケージは、イベントによって送信される情報をスタック フレームとスレッドを追跡します。  
  
 デバッグ パッケージには、言語、または実行時環境の依存関係がありません。 実装するか、デバッグのパッケージを変更する必要はありません。  
  
 デバッグ パッケージが vsdebug.dll によって実装されます。  
  
## <a name="see-also"></a>関連項目  
 [セッションのデバッグ マネージャー](../../extensibility/debugger/session-debug-manager.md)   
 [スタック フレーム](../../extensibility/debugger/stack-frames.md)   
 [スレッド](../../extensibility/debugger/threads.md)   
 [デバッガーのコンポーネント](../../extensibility/debugger/debugger-components.md)