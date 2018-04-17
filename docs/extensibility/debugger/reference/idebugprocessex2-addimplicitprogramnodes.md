---
title: IDebugProcessEx2::AddImplicitProgramNodes |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 22f6cadaa88d6cc87ec70451d9da850cd49b7753
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
このメソッドは、指定された各デバッグ エンジン (DE) のプログラムのノードを追加します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT AddImplicitProgramNodes(  
   REFGUID guidLaunchingEngine,  
   GUID*   rgguidSpecificEngines,  
   DWORD   celtSpecificEngines  
);  
```  
  
```csharp  
int AddImplicitProgramNodes(  
   ref Guid guidLaunchingEngine,  
   Guid[]   rgguidSpecificEngines,  
   uint     celtSpecificEngines  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `guidLaunchingEngine`  
 [in]`GUID`を使用してプログラムを起動する (および独自のプログラムのノードを追加すると見なされます) DE のです。  
  
 `rgguidSpecificEngines`  
 [in]配列`GUID`の DEs ノードを追加するプログラムを選択します。  
  
 `celtSpecificEngines`  
 [in]数`GUID`内、`rgguidSpecificEngines`配列。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 [ノードをプログラム](../../../extensibility/debugger/program-nodes.md)に示されている各 DE 用に追加されます`rgguidSpecificEngines`-起動エンジンを除く (で指定されている`guidLaunchingEngine`)、プログラムを起動するときに、独自のプログラム ノードを追加すると見なされます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)   
 [プログラム ノード](../../../extensibility/debugger/program-nodes.md)