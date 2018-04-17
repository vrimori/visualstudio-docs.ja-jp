---
title: IDebugProperty3::CreateObjectID |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: df4e45c442745652b3305fd91146bd31ffe79e4b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
その他のすべてのプロパティの間で一意であることを確認するこのプロパティの一意の ID を作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateObjectID(  
   void  
);  
```  
  
```csharp  
int CreateObjectID();  
```  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 セッションのデバッグ マネージャーが他のすべてのプロパティと共に、このプロパティを一意に識別することを確認するときに、このメソッドが呼び出されます。 デバッグ エンジン (DE) は、処理のプロパティは既に一意に識別しない限り、このメソッドをサポートしています。 返すかどうか、DE は、このメソッドをサポートしていません、`E_NOTIMPL`です。  
  
 一意の ID が作成された`CreateObjectID`が破棄されるときに、 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)メソッドが呼び出されます。 これも終えたことをこのプロパティを一意に識別する必要の。  
  
> [!NOTE]
>  デできる一意の Id に対応して必要なために、この一意の ID を取得するメソッドがない場合に、`CreateObjectID`メソッドが呼び出されます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)