---
title: パッケージのデバッグ |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 16464e90f5cdfe8f953a2c3d28f3b67c1f1b4f20
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53822892"
---
# <a name="debug-package"></a>パッケージをデバッグします。
デバッグ パッケージは、Visual Studio シェルで実行し、すべての UI を処理します。 Visual Studio のデバッグのインターフェイスを使用し、セッション デバッグ マネージャー (SDM) と通信します。  
  
 中断イベントが、SDM を経由して送信は、中断モード、中断が発生したプログラムにフォーカスを変更して、実行モードからデバッガーを切り替えます。 デバッグ パッケージは、イベントによって送信される情報のスタック フレームとスレッドを追跡します。  
  
 パッケージのデバッグには、言語またはランタイム環境の依存関係がありません。 実装またはデバッグ パッケージを変更する必要はありません。  
  
 デバッグ パッケージがによって実装される*vsdebug.dll*します。  
  
## <a name="see-also"></a>関連項目  
 [セッション デバッグ マネージャー](../../extensibility/debugger/session-debug-manager.md)   
 [スタック フレーム](../../extensibility/debugger/stack-frames.md)   
 [スレッド](../../extensibility/debugger/threads.md)   
 [デバッガーのコンポーネント](../../extensibility/debugger/debugger-components.md)