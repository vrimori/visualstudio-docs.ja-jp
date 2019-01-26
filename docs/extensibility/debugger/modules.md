---
title: モジュール |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cdcaa4afb2191c80a8b5bed1bedf68f4c217f029
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55008310"
---
# <a name="modules"></a>モジュール
デバッガーのアーキテクチャの観点から、*モジュール*:  
  
-   実行可能ファイルや DLL などのコードの物理的なコンテナーです。  
  
-   そのシンボルを再読み込みし、それ自体を記述できます。 モジュールの説明は、IDE の [モジュール] ウィンドウに表示されます。  
  
-   によって表される、 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)モジュールを記述するデバッグ エンジンによって作成されるインターフェイス。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)