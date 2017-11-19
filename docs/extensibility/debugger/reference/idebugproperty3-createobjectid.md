---
title: "IDebugProperty3::CreateObjectID |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty3::CreateObjectID
helpviewer_keywords: IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 363a43c71a6812ee69e1fda5778eb992579e9c76
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
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