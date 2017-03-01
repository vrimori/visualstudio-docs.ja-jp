---
title: "スレッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 6faced71ba03bcf1c4bf1849515bdf7b4fe455f8
ms.lasthandoff: 02/22/2017

---
# <a name="threads"></a>スレッド
デバッガーのアーキテクチャの観点から、**スレッド**:  
  
-   計算の基本的な単位です。 スレッドは、順番に、1 回の呼び出し履歴は、次に、1 つのコードのコンテキストから移動のコンテキスト内では、その指示を実行します。  
  
-   それ自体で実行しているとという名前、中断して再開プログラムを識別できます。 スレッドでは、また、関連するスタック フレームを列挙し、いくつかの条件下では、別のスタック フレームに移動できます。 スタック フレームのコンテキストを指定するには、スレッド返すことができます、関連付けられている論理スレッド存在する場合。 スレッドには、IDE の [スレッド] ウィンドウに表示できる中断カウントなどのプロパティがあります。  
  
-   によって表される、 [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)インターフェイス、通常、デバッグ エンジン (DE) またはプログラムを実行する対象のバーチャル マシンが作成されます。  
  
## <a name="see-also"></a>関連項目  
 [プログラム](../../extensibility/debugger/programs.md)   
 [スタック フレーム](../../extensibility/debugger/stack-frames.md)   
 [エンジンをデバッグします。](../../extensibility/debugger/debug-engine.md)   
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [セッションのデバッグ マネージャー](../../extensibility/debugger/session-debug-manager.md)
