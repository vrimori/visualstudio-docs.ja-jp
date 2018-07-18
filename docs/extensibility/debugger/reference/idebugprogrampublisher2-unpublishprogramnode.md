---
title: IDebugProgramPublisher2::UnpublishProgramNode |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgramNode
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgramNode
ms.assetid: 57c7e6e1-b84e-4e14-ad83-cbbb64e2f526
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d62c68bfc8e43370105a94818437bb0cfa2221e8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31117876"
---
# <a name="idebugprogrampublisher2unpublishprogramnode"></a>IDebugProgramPublisher2::UnpublishProgramNode
エンジン (DEs) と、セッション デバッグ マネージャー (SDM) をデバッグする可用性から指定したプログラム ノードを削除します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT UnpublishProgramNode(  
   IDebugProgramNode2* pProgramNode  
);  
```  
  
```csharp  
int UnpublishProgramNode(  
   IDebugProgramNode2 pProgramNode  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pProgramNode`  
 [in][IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)を削除するプログラムのノードを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 削除した後、[プログラム] ノードはプログラム情報の照会に使用できるではなくなりました。  
  
 プログラムのノードを使用できるようにするには、呼び出し、 [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)メソッドです。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)