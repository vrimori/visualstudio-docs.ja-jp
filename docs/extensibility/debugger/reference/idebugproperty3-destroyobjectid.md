---
title: IDebugProperty3::DestroyObjectID |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f776feafe86180c60df7cc69a2c4afb6a3070012
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917948"
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
呼び出し元がこのプロパティの他のすべてのプロパティから一意に識別する気不要になったことを示す、このプロパティに関連付けられた一意 ID を破棄します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DestroyObjectID(  
   void  
);  
```  
  
```csharp  
int DestroyObjectID();  
```  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 デバッグ エンジンは、(その既には追跡するために内部的には一意に) プロパティの一意の Id をサポートする必要がある場合、単に返すことができますし、`E_NOTIMPL`このメソッドにします。  
  
 呼び出しに一意の Id を作成、 [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)メソッドの呼び出し元がこのプロパティは、その他のすべてのプロパティの間で一意に識別することを確認する場合。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)