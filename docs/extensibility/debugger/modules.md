---
title: モジュール |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f587e015263336436588d14edeeb5c6935872950
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="modules"></a>モジュール
デバッガーのアーキテクチャの観点から、**モジュール**:  
  
-   実行可能ファイルまたは DLL などのコードの物理的なコンテナーです。  
  
-   そのシンボルを再読み込みし、自己記述できます。 モジュールの説明は、IDE の [モジュール] ウィンドウに表示されます。  
  
-   によって表される、 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)モジュールを記述するデバッグ エンジンによって作成されるインターフェイス。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)