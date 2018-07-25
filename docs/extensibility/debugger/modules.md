---
title: モジュール |Microsoft Docs
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
ms.openlocfilehash: 8750c1f6676966be8564fbf4a175a66fa180a401
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2018
ms.locfileid: "39233166"
---
# <a name="modules"></a>モジュール
デバッガーのアーキテクチャの観点から、*モジュール*:  
  
-   実行可能ファイルや DLL などのコードの物理的なコンテナーです。  
  
-   そのシンボルを再読み込みし、それ自体を記述できます。 モジュールの説明は、IDE の [モジュール] ウィンドウに表示されます。  
  
-   によって表される、 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)モジュールを記述するデバッグ エンジンによって作成されるインターフェイス。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)