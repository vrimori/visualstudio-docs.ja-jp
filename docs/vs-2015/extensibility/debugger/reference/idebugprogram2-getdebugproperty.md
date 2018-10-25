---
title: IDebugProgram2::GetDebugProperty |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 870c4e80b6fa942ff3dc950376039fc7a7d84ac3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919625"
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

プログラムのプロパティを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetDebugProperty(   
   IDebugProperty2** ppProperty  
);  
```  
  
```csharp  
int GetDebugProperty(   
   out IDebugProperty2 ppProperty  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppProperty`  
 [out]返します、 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)プログラムのプロパティを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドによって返されるプロパティは、プログラムに固有です。 プログラムは、1 つ以上のプロパティを返す必要がある場合、 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)このメソッドによって返されるオブジェクトは、追加のプロパティと呼び出し元のコンテナー、 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)メソッドを返します、。すべてのプロパティの一覧です。  
  
 任意の数と種類の追加のプロパティを使用して記述できるプログラムが公開される可能性が、`IDebugProperty2`インターフェイス。 IDE が汎用プロパティ ブラウザーのユーザー インターフェイスを通じて追加のプログラムのプロパティを表示します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)

