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
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e17bbfc494fb305e9a264c31c3b82936681347f0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53867330"
---
# <a name="modules"></a>モジュール
デバッガーのアーキテクチャの観点から、*モジュール*:  
  
-   実行可能ファイルや DLL などのコードの物理的なコンテナーです。  
  
-   そのシンボルを再読み込みし、それ自体を記述できます。 モジュールの説明は、IDE の [モジュール] ウィンドウに表示されます。  
  
-   によって表される、 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)モジュールを記述するデバッグ エンジンによって作成されるインターフェイス。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)